CCA Prom 2026 Playlist
Two-page app: users submit songs with a unique key, you view everything from the admin dashboard. Submissions are stored in Firebase Firestore — a free real database that works with GitHub Pages.

 Quick Setup (15 minutes)
Step 1 — Create a Firebase Project (free)
Go to console.firebase.google.com
Click "Add project" → name it (e.g. cca-prom-playlist) → Continue
Disable Google Analytics if you want → Create project
Step 2 — Create a Firestore Database
In the left sidebar click "Firestore Database"
Click "Create database"
Choose "Start in test mode" (allows reads/writes for 30 days — enough for prom!)
Pick a location → Done
Step 3 — Get Your Config
Click the gear icon → "Project settings"
Scroll to "Your apps" → click the </> (web) icon
Register an app name (anything) → click Register app
Copy the firebaseConfig object — it looks like:
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "cca-prom-playlist.firebaseapp.com",
  projectId: "cca-prom-playlist",
  storageBucket: "cca-prom-playlist.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
Step 4 — Paste Config into Both Files
Open index.html and admin.html. In each file, find this section and replace with your config:

const firebaseConfig = {
  apiKey: "PASTE_YOUR_API_KEY",
  authDomain: "PASTE_YOUR_AUTH_DOMAIN",
  ...
};
Step 5 — Change the Admin Password
In admin.html, find this line and change it:

const ADMIN_PASSWORD = "prom2026admin";
Step 6 — Deploy to GitHub Pages
Push both files to a GitHub repository
Go to Settings → Pages → Source: main branch
Done! Your URLs:
User portal: https://yourusername.github.io/repo-name/
Admin: https://yourusername.github.io/repo-name/admin.html
 User Keys
Hand each person their key privately (DM, text, etc.):

Name	Key
Ava	AV3K
Brendan	BR9M
Brooks	BK4X
Carter	CT7P
Charlotte D	CD2W
Charlotte U	CU5R
Clara	CL8N
Evelyn	EV1Q
Fin	FN6T
Grayson	GR3Y
Griffin	GF0L
Isabel	IB7S
Jaden	JD4V
Jimmy	JM2H
Julian	JL9E
Regan	RG5B
RJ	RJ0C
Ryan	RY8A
Steve	ST6Z
 What Users Submit
Song title & artist
Genre (dropdown)
Vibe/mood tags (Hype, Emotional, Chill, Dance, etc.)
Star rating 1–5
Personal note
 Admin Features
See all 19 people's submissions in card view
Switch to table view
Filter by genre, search by song/artist
Click any person's card to expand their songs
Export everything as CSV
Refresh button to pull latest submissions
 Security Note
Firebase test mode expires after 30 days. For permanent access, go to Firestore → Rules and set:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /submissions/{doc} {
      allow write: if true;
      allow read: if true;
    }
  }
}
This keeps it open (fine for a private group with keys). For extra security you can restrict reads to only admin, but that requires Firebase Auth setup.
