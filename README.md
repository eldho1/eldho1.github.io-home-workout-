# Home Workout Coach on GitHub Pages

This folder is the complete app. It is one web page plus a few small files, so GitHub Pages can host it for free.

| File | What it is |
|---|---|
| `index.html` | The app |
| `config.js` | Sign-in settings (fill in at step 2, or leave as is) |
| `sw.js`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png` | Let the app install to the home screen and open without internet |
| `firestore.rules` | Privacy rules for saved progress (used at step 2) |

## 1. Put it online (about 5 minutes)

1. Sign in at github.com, tap **New repository**, name it `home-workout`, choose **Public**, and tap **Create repository**.
2. On the new repository page, tap **uploading an existing file**. Drag in every file from this folder and tap **Commit changes**.
3. Open **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*. Set **Branch** to `main` and the folder to `/ (root)`, then tap **Save**.
4. After a minute or two the app is live at `https://YOUR-USERNAME.github.io/home-workout/`.
5. Open that link on your phone and choose **Add to Home screen**. It then opens like an app.

The app already works at this point. Without step 2, though, progress is saved on each phone only. People tap **Get started** and use it without an account.

## 2. Turn on sign-in so progress follows each person (free)

Sign-in uses Google Firebase. The free Spark plan is plenty for this app.

1. Go to console.firebase.google.com, tap **Add project**, name it (for example `home-workout`) and create it. You can switch Analytics off.
2. On the project overview, tap the **Web** icon (`</>`) to add a web app. Give it a nickname and tap **Register app**. You'll see a block of settings. Copy `apiKey`, `authDomain`, `projectId` and `appId` into `config.js`. On GitHub, open `config.js`, tap the pencil icon, paste the values, and commit.
3. In Firebase, open **Build → Authentication → Get started**. Under **Sign-in method**, enable **Google**, then enable **Email/Password**.
4. Still in Authentication, open **Settings → Authorized domains → Add domain** and add `YOUR-USERNAME.github.io`.
5. Open **Build → Firestore Database → Create database**. Choose **Production mode** and a location (`asia-south1`, Mumbai, is closest to Kerala). Then open the **Rules** tab, replace everything with the contents of `firestore.rules`, and tap **Publish**.

Reload the site. The welcome screen now offers **Continue with Google**, email sign-in and **Use without an account**. Each person's plan, workouts and weight log are saved to their own account, and only they can read them.

The `apiKey` in `config.js` is meant to be public. Firebase uses it to find your project, and the Firestore rules are what keep each person's data private.

## Updating the app later

Upload the new `index.html` over the old one (**Add file → Upload files**, then commit). Phones pick up the new version the next time they open the app online.
