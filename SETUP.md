# Setting up meshterm-feedback (maintainer notes)

Notes for James. Nothing here has been run yet. Run from this directory. Needs `gh` logged in with admin on the `AG-Studio-Apps` org.

## 0. Before publishing

- [ ] Replace `APP_STORE_URL` in `README.md` with the real App Store link (`https://apps.apple.com/app/id<APPLE_ID>`).
- [ ] Confirm the support address. Every file uses `meshterm@gmail.com` (the address on docs.meshterm.com). To change it everywhere:
      `grep -rl 'meshterm@gmail.com' . | xargs sed -i 's/meshterm@gmail.com/NEW@ADDRESS/g'`
- [ ] The README and forms point users to **Settings, General, About, Copy details**. Make sure that row ships in the app (or adjust the wording) before linking people here. The 2.2 What's New also says "Settings, About, Contact", so a Contact row should point at this repo or the email.

## 1. Create the repo and push

```sh
gh repo create AG-Studio-Apps/meshterm-feedback --public \
  --description "Bug reports, feature requests and discussions for meshTerm, the SSH and agent terminal for iPhone and iPad" \
  --homepage "https://docs.meshterm.com" \
  --source . --remote origin --push
```

## 2. Settings, description, topics

```sh
gh repo edit AG-Studio-Apps/meshterm-feedback \
  --enable-discussions \
  --enable-issues \
  --enable-wiki=false \
  --enable-projects=false \
  --homepage "https://docs.meshterm.com" \
  --add-topic meshterm,ios,ipados,ssh,terminal,tmux,tailscale,herdr,sftp,ai-agents,feedback,issue-tracker
```

Also turn on private vulnerability reporting (optional; SECURITY.md works without it):

```sh
gh api -X PUT repos/AG-Studio-Apps/meshterm-feedback/private-vulnerability-reporting
```

## 3. Labels

Remove GitHub's defaults that clash with ours, then apply `.github/labels.yml` (safe to re-run; `--force` updates existing labels):

```sh
for l in enhancement question "good first issue" "help wanted" invalid documentation; do
  gh label delete "$l" --repo AG-Studio-Apps/meshterm-feedback --yes 2>/dev/null
done

python3 -c '
import yaml, shlex
for l in yaml.safe_load(open(".github/labels.yml")):
    print("gh label create %s --repo AG-Studio-Apps/meshterm-feedback --color %s --description %s --force"
          % (shlex.quote(l["name"]), l["color"], shlex.quote(l["description"])))
' | sh
```

Keep `bug`, `duplicate` and `wontfix` (they are recreated with our colours and descriptions).

## 4. Discussion categories (web UI only)

The GitHub API cannot create, rename or delete discussion categories, so this step is in the browser: **Repo, Discussions, the pencil next to Categories**.

Enabling Discussions creates the defaults: Announcements, General, Ideas, Polls, Q&A, Show and tell. The templates in `.github/DISCUSSION_TEMPLATE/` match by category **slug**, so keep these slugs exactly:

| Category | Slug (must match file) | Format | Template |
|---|---|---|---|
| Q&A | `q-a` | Question / Answer | `q-a.yml` |
| Ideas | `ideas` | Open-ended discussion | `ideas.yml` |
| Show and tell | `show-and-tell` | Open-ended discussion | `show-and-tell.yml` |
| Announcements | `announcements` | Announcement (only maintainers can post) | none |

Suggested tidy-up: delete **General** and **Polls** (or keep General if you want a catch-all), and set the category descriptions to match the README. Check the slugs afterwards:

```sh
gh api graphql -f query='{ repository(owner:"AG-Studio-Apps", name:"meshterm-feedback") { discussionCategories(first:20) { nodes { name slug isAnswerable } } } }'
```

## 5. Check it works

- Open https://github.com/AG-Studio-Apps/meshterm-feedback/issues/new/choose and confirm both forms plus the four contact links show, and there is no blank issue option.
- Start a test discussion in each category to see the form, then delete it.
- Optional: pin a welcome post in Announcements that links the README.

## Triage habits

- New issues arrive labelled `triage` plus `bug` or `feature-request`. The form's **Area** answer is not turned into a label automatically, so add the matching `area/*` label when triaging, and swap `triage` for `planned`, `needs-info`, `duplicate` or `wontfix`.
- On release, comment "Shipped in X.Y.Z", add `shipped`, and close as completed. Close `wontfix` and `duplicate` as "not planned".
- Sort by 👍: https://github.com/AG-Studio-Apps/meshterm-feedback/issues?q=is%3Aopen+sort%3Areactions-%2B1-desc
