# Kairos · Faith Planner (with login, admin approval and sync)

Anyone can request access. You (the admin) approve or reject them inside the app.
Approved people can log in on any device and their planner syncs.

## Part 1 · Firebase (free)

1. Go to https://console.firebase.google.com and tap **Add project**. Name it `kairos`.
   You can turn Google Analytics off.
2. **Build → Authentication → Get started → Email/Password → Enable → Save.**
3. **Build → Firestore Database → Create database.** Choose **production mode** and a nearby
   location (for the Philippines, `asia-southeast1` Singapore works well).
4. In Firestore, open the **Rules** tab. Paste everything from `firestore.rules`
   (leave `ADMIN_UID_HERE` for now) and tap **Publish**.
5. Tap the gear icon → **Project settings → Your apps → the web icon `</>`**. Register the app,
   then copy the `firebaseConfig` values.
6. **Authentication → Settings → Authorized domains → Add domain**:
   `YOUR-USERNAME.github.io`

## Part 2 · Put your config in the app

Open `index.html` in a text editor and find `FIREBASE_CONFIG` near the top of the script.
Replace each `PASTE_...` value with the matching value from Firebase. Save, then upload all files
to your GitHub repo (replace the old ones). Wait a minute for GitHub Pages to update.

## Part 3 · Make yourself the admin

1. Open your app link, tap **New here? Request access**, and sign up with your own email.
2. You'll see the **Almost there** screen with **Your user ID**. Tap **Copy ID**.
3. Paste it into two places:
   - `index.html`: `const ADMIN_UID="PASTE_HERE";` and upload it to GitHub again.
   - Firestore **Rules**: replace `ADMIN_UID_HERE`, then **Publish**.
4. Reload the app and log in. You'll see an **Admin** button at the top.

## Using it

- **Admin** shows new requests with **Approve** / **Reject**. You can also remove access later.
- The person waiting sees "Almost there" and gets in automatically once approved.
- **Account** has Back up, Restore and Sign out.
- Photos are saved in the cloud too. Offline changes sync when you're back online.

## Good to know

- The Firebase config in `index.html` is not a secret. Your Firestore rules are what protect the data.
- Nobody gets an email when approved. They just need to open the app again.
- Calendar export and Google Calendar buttons work the same as before.
- If you leave `PASTE_...` as is, the app still works on one device without login.
