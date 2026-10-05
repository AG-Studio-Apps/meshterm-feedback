# Security policy

Thank you for helping keep meshTerm and its users safe.

## Please report privately

**Do not open a public issue or discussion for a security problem.** This repository is public, and a public report can put other users at risk before a fix is available.

Instead, email **[meshterm@gmail.com](mailto:meshterm@gmail.com)** with a subject line starting `SECURITY:`.

Please include:

- what the problem is and what an attacker could do with it
- the steps to reproduce it, or a proof of concept
- the meshTerm version and build (from **Settings, General, About**, or the **Copy Details** block in **Settings, Feedback and Feature Requests**), and your iOS version
- whether you have shared it with anyone else

Please **do not** send real private keys, passwords or tokens belonging to you or anyone else. Use throwaway test credentials and test hosts.

## In scope

- the meshTerm iOS and iPadOS app
- the meshTerm push relay that delivers agent notifications
- **mtroamd**, the open-source session daemon ([AG-Studio-Apps/mtroamd](https://github.com/AG-Studio-Apps/mtroamd)); email is fine, or use that repository's private security reporting if it is enabled
- how meshTerm stores credentials, keys and secrets, and what it writes to your hosts

Problems in third-party software that meshTerm works with (OpenSSH, tmux, Tailscale, herdr, Claude Code, Codex, Gemini, Docker, Podman) should go to those projects. If you are not sure, email us anyway and we will help route it.

## What happens next

meshTerm is built by a small independent developer, so there is no formal SLA, but security reports are always handled first. We will:

1. acknowledge your report as soon as we can
2. investigate and keep you updated
3. fix it, ship the fix (TestFlight first, then the App Store), and let you know
4. credit you in the release notes if you would like to be credited

Please give us a reasonable amount of time to ship a fix before disclosing publicly. We are happy to agree a disclosure date with you.

## Not security issues

Please use the normal [bug report form](https://github.com/AG-Studio-Apps/meshterm-feedback/issues/new?template=bug_report.yml) for crashes, connection failures and other bugs that do not expose anyone's data or access.
