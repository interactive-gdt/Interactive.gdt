# GD&T in 3D

Invitation-only training site: interactive 3D GD&T lessons (ASME Y14.5-2018) and stack-up tools.
Hosted on GitHub Pages; sign-in and data on Firebase (project `interactive-gdt`, free Spark plan).

## Files
| File | What it is |
|---|---|
| `index.html` | The whole site: landing page, sign-in, lessons, tools, practice problems, management screens |
| `firebase-config.js` | Public Firebase web config (identifies the project; doesn't unlock it) |
| `firestore.rules` | The security rules. **These are the real lock.** Paste into Firebase console → Firestore → Rules after any change |

## How access works
- Only emails on the invitation list (`people/{email}` in Firestore) get in. Anyone else who signs in sees "not invited yet".
- Sign-in is a one-time email link from Firebase. No passwords.
- Lesson and tool pages are **not in this repo**. Each page body is stored in Firestore `content/{id}` and only loads for people allowed to open it. Upload pages from **Manage → Content → Upload .html**.
- The first time `interactive.gd.t@gmail.com` signs in, the site makes that account the Owner. That only works once, while the site has no `site/config` document.

## Roles
Owner · Admin · Creator-Instructor · Instructor · Student Full Access · Student Partial Access.
See **Manage → Roles & permissions** on the site, or `claude/site-access-spec.md` in the Claude project.

## Changing the site
1. Edit `index.html` (or the rules), commit to `main`. Pages updates in a minute or two.
2. If you changed `firestore.rules`, paste it into the Firebase console and click **Publish**.

## Limits on the free plan
- Practice-problem answer keys live in the browser, so treat problems as practice, not graded assessment.
- The public "Request access" form can be spammed; add Firebase App Check before advertising the site.
