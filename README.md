# House Bardies Christmas 2026 – wishlist

Static site (GitHub Pages) + Firebase (free Spark plan) for logins and data.

## Setup (about 10 minutes)
1. https://console.firebase.google.com → **Add project** (disable Analytics).
2. **Build → Authentication → Get started → Email/Password → Enable.**
3. **Build → Firestore Database → Create database** (production mode, pick a region near you).
4. **Firestore → Rules** → paste the contents of `firestore.rules` → Publish.
5. **Firestore → Start collection** `settings` → document ID `app` → field `code` (string) = your family invite code.
6. **Project settings → Your apps → Web (</>)** → register app → copy `firebaseConfig` into `index.html`.
7. **Authentication → Settings → Authorized domains** → add `YOUR-GITHUB-USERNAME.github.io` (just the domain, no `/housebardiesxmas2026`).
8. Upload `index.html`, `firestore.rules` and `README.md` to the GitHub repo **housebardiesxmas2026** (the files must sit at the top level, not in a subfolder):
   - Easiest: open the repo on github.com → **Add file → Upload files** → drag the 3 files in → **Commit changes**.
   - Then **Settings → Pages → Build and deployment → Deploy from branch → `main` / `(root)` → Save.**
   - After a minute or two the site is live at `https://YOUR-GITHUB-USERNAME.github.io/housebardiesxmas2026/`.
   - GitHub's free plan only serves Pages from a **public** repo. That is fine: the Firebase config is not a secret, and the invite code is stored in Firebase, not in the repo.
9. Share the site URL + invite code with the family.

## Admin tasks (Firebase console)
- Forgotten password: Authentication → Users → ⋮ → delete the user (they re-register; they must re-add their list).
- Remove someone: delete their user in Authentication, and their docs in Firestore.
- The Firebase `apiKey` in the page is not a secret; the rules are what protect the data.
