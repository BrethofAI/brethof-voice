# Security Policy

## Reporting a vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.**

Email **`hello@brethof.ai`** with:

- A clear description of the issue.
- Affected version(s) of Brethof Voice Pro.
- Steps to reproduce — proof-of-concept is welcome.
- Your assessment of impact and severity (we'll re-assess; first-pass is just helpful).
- Whether you'd like public credit when we publish the fix (default: yes, with your name; we can also use a handle or stay anonymous if you prefer).

If you don't get an acknowledgement within **72 hours**, please nudge us — your email might have ended up in a spam folder.

## What we consider in-scope

- The Brethof Voice Pro installer (Windows `.exe`, Linux AppImage / `.deb` / `.rpm`).
- The Brethof Voice Pro application binary and bundled models.
- LoRA training artefacts stored under the user's profile directory.
- Update / signature verification mechanisms.
- Brethof Voice Pro's licence-server interactions (`licence.brethof.ai`).
- The `brethof.ai/voice/llms.txt` agent-readable manifest.

## What we consider out-of-scope

- Issues affecting only outdated versions (we backport critical fixes to the previous major; older than that is unsupported).
- Social engineering against Brethof employees.
- DoS attacks against `brethof.ai` infrastructure (please report to our hosting partner directly).
- Issues in dependencies we don't bundle (e.g. your OS, your distro's `glibc`).
- "Self-XSS" or issues requiring full local administrator access on the user's machine.
- Bugs that the user can already trigger themselves with the input fields we offer (e.g. transcribing arbitrary audio is a feature, not a bug).

## What you can expect from us

- **Acknowledgement within 72 hours** of your report.
- **A real fix within 30 days** for HIGH / CRITICAL severity; **90 days** for MEDIUM; lower severity at our discretion.
- **A CVE assigned where applicable** — for issues affecting all Brethof Voice Pro users.
- **Public credit** in our changelog and security advisories, unless you ask to stay anonymous.
- **No legal threats.** We support good-faith security research. Don't access other users' data, don't degrade service for others, don't keep the issue undisclosed for unbounded time — and you're safe.

## What you should NOT do

- Open a public issue for the vulnerability.
- Share proof-of-concept publicly until we've shipped a fix.
- Test against `licence.brethof.ai` in a way that affects other users' licence activations.
- Attempt to extract the bundled model weights for re-distribution (that's a licence issue separate from any security finding).

Thanks for taking the time to report responsibly.

— The Brethof AI team
