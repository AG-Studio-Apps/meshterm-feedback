# meshTerm feedback

Welcome! This is the public home for **meshTerm** feedback: bug reports, feature requests, questions and ideas.

meshTerm is an SSH and terminal app for iPhone and iPad, built around the coding agents you run on your own servers. It speaks tmux control mode, keeps sessions alive with mtRoam, has Tailscale built in, integrates with herdr, and gives you a native chat for Claude, Codex and Gemini, plus containers, SFTP and more.

**This repository does not contain the app's source code.** It exists so you can tell us what is broken, what is missing and what you would love to see, and so everyone can see what is planned and what has shipped.

meshTerm is made by a small independent developer, AG Applications LTD. Every report is read, and the good ones genuinely shape the app.

---

## Where to go

| I want to... | Go here |
|---|---|
| Report something that is broken | [Bug report](https://github.com/AG-Studio-Apps/meshterm-feedback/issues/new?template=bug_report.yml) |
| Ask for a specific new feature or change | [Feature request](https://github.com/AG-Studio-Apps/meshterm-feedback/issues/new?template=feature_request.yml) |
| Ask a question or get help setting something up | [Discussions: Q&A](https://github.com/AG-Studio-Apps/meshterm-feedback/discussions/categories/q-a) |
| Float an early idea and see what others think | [Discussions: Ideas](https://github.com/AG-Studio-Apps/meshterm-feedback/discussions/categories/ideas) |
| Share your setup, a workflow or a screenshot you are proud of | [Discussions: Show and tell](https://github.com/AG-Studio-Apps/meshterm-feedback/discussions/categories/show-and-tell) |
| Read the docs | [docs.meshterm.com](https://docs.meshterm.com/meshterm.html) |
| Report a security problem | **Email, not GitHub.** See [SECURITY.md](SECURITY.md) |
| Anything private: billing, your account, your purchase, anything with personal details | **Email** [meshterm@gmail.com](mailto:meshterm@gmail.com) |

Not sure whether something is a bug or a question? Start a [Q&A discussion](https://github.com/AG-Studio-Apps/meshterm-feedback/discussions/categories/q-a). We can turn it into an issue if it needs one.

Refunds for App Store purchases are handled by Apple, at [reportaproblem.apple.com](https://reportaproblem.apple.com). We cannot issue them ourselves, but we are happy to help with anything else about Pro by email.

---

## Search first, then react

Before opening something new, please [search the issues](https://github.com/AG-Studio-Apps/meshterm-feedback/issues?q=is%3Aissue) (open **and** closed) and [the discussions](https://github.com/AG-Studio-Apps/meshterm-feedback/discussions). Someone may already have reported it, or it may already be fixed.

If you find a match:

- **Add a 👍 reaction to the first post.** We sort by reactions to decide what to work on next, so this is the single most useful thing you can do.
- **Please don't post "+1" or "me too" comments.** They notify everyone subscribed and do not count towards the tally.
- **Do comment if you have something new:** a different device, a way to reproduce it, a workaround, or a use case nobody has mentioned yet.

---

## What makes a great report

The forms will prompt you, but in short:

- **One problem per issue.** Two bugs in one issue tend to get half fixed.
- **Steps to reproduce.** "Connect over Tailscale, open a tmux session, rotate the phone" beats "rotation is broken".
- **What you expected, and what actually happened.**
- **How often it happens.** Every time, sometimes, or once.
- **How you connect.** Direct SSH, Tailscale, Tailscale SSH or mtRoam, and which persistence you use (tmux, mtRoam or none).
- **Your app details.** Paste the **Copy details** block (see below).
- **A screenshot or screen recording**, if it helps. Please check it for private information first.

---

## ⚠️ Privacy: this repository is public

Everything you post here can be read by anyone on the internet, indexed by search engines and kept forever, even after you edit it. **Please never post:**

- hostnames, domain names, IP addresses or tailnet names
- usernames, email addresses or anything that identifies your servers or your organisation
- SSH keys (private **or** public), passwords, passphrases, API tokens, Tailscale auth keys, relay keys or any other secret
- terminal output, session contents, scrollback or agent chat transcripts that you have not checked line by line
- logs that may contain any of the above

**Redact before you post.** Replace real values with placeholders such as `myserver`, `user`, `100.x.y.z` or `REDACTED`. For screenshots, crop or blur anything identifying, including the title bar and the host list.

If the only way to show a problem involves private information, open the issue with the redacted version and say that you can send more detail privately. We will ask you to email [meshterm@gmail.com](mailto:meshterm@gmail.com).

If you accidentally post a secret, **revoke or rotate it straight away** (deleting the comment is not enough), then edit or delete the post.

---

## The "Copy details" block

In meshTerm, go to **Settings, General, About** and tap **Copy details**. It copies a short, plain-text summary like this to your clipboard:

```text
meshTerm 2.2.0 (20261004120000)
iOS 26.0, iPhone17,1, en_GB
Plan: Pro
Features: tmux control mode, Tailscale (in-app), herdr, agents (Claude, Codex), notifications on, iCloud Sync off
```

It contains your app version and build, iOS version, device model, language and region, whether you are on the free plan or Pro, and a summary of which features are switched on. **It contains no hosts, addresses, usernames, keys or session data**, so it is safe to paste here as it is.

Paste it into the **App details** box on the bug or feature form. It saves a round of "which version are you on?" and gets your report looked at sooner.

If your version of meshTerm does not have **Copy details** yet, type the app version shown in **Settings, General, About**, your iOS version and your device model instead.

### Using an AI agent to write your report

The Copy details block is designed to be agent-friendly. If you use Claude, ChatGPT, Gemini or another assistant, you can paste it in together with a description of the problem and ask it to draft the issue for you. For example:

> Here are my meshTerm app details and a description of a bug. Please draft a GitHub issue using the meshTerm bug report form fields: summary, steps to reproduce, expected behaviour, actual behaviour, frequency, connection type, persistence and area. Keep it concise and remove any hostnames, IP addresses, usernames or secrets.

Then **read the draft yourself before posting**. You know your setup better than the agent does, and you are the last line of defence for your privacy.

---

## Labels and what happens next

Every new issue starts in **triage**. From there it moves through these stages:

| Label | Meaning |
|---|---|
| `triage` | New, not yet looked at. |
| `needs-info` | We need something from you before we can go further. Issues left in this state for a few weeks may be closed; reply and we will reopen. |
| `planned` | Accepted. We intend to do it, though not necessarily soon. |
| `in-progress` | Being worked on now. |
| `shipped` | Done. We will comment with the version it shipped in (for example "Shipped in 2.2.1") and close the issue. |
| `duplicate` | Already tracked elsewhere. We will link the original; please add your 👍 there. |
| `wontfix` | We have decided not to do this, and will try to explain why. It might be out of scope, at odds with how the app works, or not possible on iOS. |

Issues also get **type** labels (`bug`, `feature-request`) and **area** labels such as `area/tmux`, `area/tailscale` or `area/agents-chat`, so you can [browse by area](https://github.com/AG-Studio-Apps/meshterm-feedback/labels).

Fixes reach **TestFlight** before the App Store. If an issue mentions a TestFlight build, that is the place to try it first.

---

## What to expect

meshTerm is built by one independent developer. There is **no support SLA**, and replies may take a few days, longer around releases. Please don't take a quiet issue as being ignored: everything gets read and triaged, and 👍 counts are checked regularly to decide what comes next.

We cannot promise to build every request. We do promise to be honest about what is planned and what is not.

---

## Be kind

This is a friendly place. Everyone taking part is expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md). In short: be respectful, assume good intent and keep it about the app.

---

## Links

- **App Store:** [meshTerm on the App Store](APP_STORE_URL)
- **User guide:** [docs.meshterm.com/meshterm.html](https://docs.meshterm.com/meshterm.html)
- **Troubleshooting:** [docs.meshterm.com/meshterm.html#troubleshooting](https://docs.meshterm.com/meshterm.html#troubleshooting)
- **Website:** [docs.meshterm.com](https://docs.meshterm.com)
- **Privacy policy:** [docs.meshterm.com/privacy.html](https://docs.meshterm.com/privacy.html)
- **mtroamd** (the open-source session daemon): [AG-Studio-Apps/mtroamd](https://github.com/AG-Studio-Apps/mtroamd)
- **Email:** [meshterm@gmail.com](mailto:meshterm@gmail.com)

meshTerm is developed by AG Applications LTD. meshTerm is not affiliated with, endorsed by, or in partnership with Tailscale Inc., Anthropic, OpenAI, Google or the herdr project.

Thank you for helping make meshTerm better.
