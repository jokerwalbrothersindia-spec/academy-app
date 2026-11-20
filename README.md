# 🏏 Sports Academy Manager

A mobile-friendly app to run your sports academy (cricket now, more sports later):

- **Students**: details, parent's WhatsApp number, batch, playing role
- **Fees**: monthly, quarterly or yearly plans, plus admission and kit fees; overdue tracking; future fee increases
- **WhatsApp**: one-tap fee reminders and payment receipts
- **Attendance**: tap P or A for each student
- **Performance**: batting, bowling and fielding scores, plus coach ratings
- **Rankings**: a score out of 100 for each student
- **Many academies**: each academy logs in with its own email, and its data stays private

It works on iPhone, Android and PC, and you can install it on your home screen like an app.

---

## Files in this folder

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `firebase-config.js` | Your Firebase keys, for syncing between phone and PC (Part 3) |
| `firestore.rules` | Security rules: who can see which academy's data |
| `manifest.webmanifest`, `sw.js`, `icons/` | Make the app installable and let it work offline |

---

## Part 1: Put the app on GitHub (about 5 minutes)

1. Go to **https://github.com** and sign in. Create a free account if you don't have one.
2. Click the **+** at the top right, then **New repository**.
3. Name it, for example `academy-app`. Choose **Public**, then click **Create repository**.
4. On the new page, click **"uploading an existing file"**.
5. Unzip the folder on your PC. Drag **all the files and the `icons` folder** into the GitHub page.
   Upload the contents of the folder, not the zip file itself.
6. Click **Commit changes**.

## Part 2: Make it a live website (GitHub Pages)

1. In your repository, click **Settings**, then **Pages** in the left menu.
2. Under **Branch**, choose **main** and **/ (root)**, then click **Save**.
3. Wait 1–2 minutes and refresh. Your link appears at the top, for example:
   `https://YOUR-NAME.github.io/academy-app/`
4. Open that link. The app works straight away.

> ⚠️ Without Part 3, data is saved **only on the phone or PC where you enter it**.
> To see the same data on your iPhone and PC, do Part 3. It's free.

---

## Part 3: Sync between iPhone and PC, and logins for each academy (free, about 15 minutes)

With Firebase, **every academy logs in with its own email**.
Each login sees **only its own academy**: students, fees, attendance and rankings.
One academy can never see another academy's data. The database itself blocks it, not just the app.

### A. Create the Firebase project
1. Go to **https://console.firebase.google.com** and sign in with Gmail.
2. Click **Create a project**, name it `academy-app`, click **Continue** through the steps (you can turn Google Analytics off), then click **Create**.

### B. Turn on the database and paste the security rules
1. In the left menu, click **Build**, then **Firestore Database**, then **Create database**.
2. Choose the location **asia-south1 (Mumbai)**, then click **Next**.
3. Choose **Start in production mode**, then click **Create**.
4. Open the **Rules** tab and delete everything there.
5. Open the `firestore.rules` file from this folder in Notepad, copy **everything**, paste it into the Rules tab, and click **Publish**.
   (You don't need to change anything in this file.)

### C. Turn on email login
1. In the left menu, click **Build**, then **Authentication**, then **Get started**.
2. Click **Email/Password**, switch on the **first** option, and click **Save**.
3. Open the **Settings** tab, then **Authorized domains**, then **Add domain**. Add `YOUR-NAME.github.io`.

### D. Connect the app to Firebase
1. Click the ⚙️ next to **Project overview**, then **Project settings**.
2. Scroll to **Your apps** and click the **</>** (Web) icon. Name it `academy`, then click **Register app**.
3. Firebase shows a code block with `apiKey`, `authDomain` and so on. Keep that page open.
4. On GitHub, open the file **`firebase-config.js`**, then click the ✏️ pencil to edit it.
5. Copy each value from Firebase into the matching line between the quotes `""`. For example:
   ```js
   apiKey: "AIzaSy....",
   authDomain: "academy-app-1234.firebaseapp.com",
   projectId: "academy-app-1234",
   storageBucket: "academy-app-1234.appspot.com",
   messagingSenderId: "1234567890",
   appId: "1:1234567890:web:abc123"
   ```
6. Click **Commit changes**. Wait 1 minute, then open your app link. You will see the login screen.

### E. Create your account
1. On the login screen, tap **Create account**.
2. Enter your **academy name**, **email** and a **password** (at least 6 letters).
3. That's it. Log in with the same email on your iPhone and PC and you will see the same data.

---

## More academies = more users

- Each academy owner opens the **same app link** and taps **Create account** with **their own email**.
- Each email gets its own **separate, private academy**. Nothing mixes.
- One email = one academy. To run a second academy, use a different email.
- Forgot password? Tap **Forgot password?** on the login screen and a reset email arrives.

**Want to stop strangers from creating accounts?**
In Firebase, go to **Authentication**, then **Settings**, then **User actions**, and untick **Enable create (sign-up)**.
After that, only you can add academies: go to **Authentication**, then **Users**, then **Add user**, and enter their email and password.
They log in, enter their academy name once, and start using the app.

## Install on iPhone like an app
1. Open your app link in **Safari**.
2. Tap **Share** (the square with an arrow), then **Add to Home Screen**, then **Add**.
3. A 🏏 icon appears on your home screen and the app opens full screen.

## Install on Android or PC
- **Android (Chrome)**: tap the ⋮ menu, then **Add to Home screen** or **Install app**.
- **PC (Chrome or Edge)**: click the install icon at the right end of the address bar.

## Moving your existing data (backup and import)
1. In the old app, go to **Settings → Data & backup**, tap **Copy backup**, and paste it somewhere (for example, WhatsApp it to yourself).
2. In the new app, go to **Settings → Data & backup**, tap **Import backup**, paste the text, and tap **Import**.

## Updating the app later
Upload a new `index.html` to the GitHub repository by dragging it in and clicking **Commit**.
Your data is safe, because it is stored in Firebase and not in the files.
