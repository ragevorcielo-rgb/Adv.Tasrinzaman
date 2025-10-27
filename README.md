# Adv. Tasrin Zaman Rity — GitHub-ready Website

This repository is a ready-to-launch static website intended for `index.html`.  
It includes an **OTP owner login modal** (Email-based OTP) and a simple admin UI for creating posts locally.

## What I prepared for you
```
adv-tasrin-zaman-rity/
├── index.html
├── README.md
└── assets/
    ├── css/
    │   └── style.css
    ├── js/
    │   └── script.js
    └── images/
        └── logo.jpg
```

## Important: Firebase & EmailJS setup (required for OTP email delivery)
This project is now set up to work fully **locally** without external services. To enable real email sending and remote persistence, see the optional steps below:

**Local-first behavior (already enabled):**

1. OTP generation and verification works entirely in the browser. When you request an OTP, it is copied to your clipboard and your mail client is opened with a prefilled message containing the OTP for testing.
2. Admin login state and posts are persisted in your browser's `localStorage` so data survives refreshes on the same browser.

**Optional: enable real Email delivery & remote persistence**

1. **Firebase**
   - Go to the Firebase Console → Project Settings → SDK setup and configuration → copy the `firebaseConfig` block.
   - Replace the placeholder values in `assets/js/script.js` under `const firebaseConfig` (the `apiKey` is already filled with the API key you provided).

2. **EmailJS**
   - Create an account at https://www.emailjs.com/
   - Create a service and an email template. Your template should accept `to_email` and `otp_code` variables (names used in `script.js`).
   - Replace `EMAILJS_SERVICE_ID`, `EMAILJS_TEMPLATE_ID`, and `EMAILJS_PUBLIC_KEY` in `assets/js/script.js`.

If EmailJS is not configured the site will still generate OTPs but will show the OTP in an alert for testing purposes.

## Deploying to GitHub Pages
1. Create a new GitHub repository and push this folder (or upload via the web UI).
2. In repository settings → Pages, set the branch to `main` (or `gh-pages`) and folder to `/ (root)`.
3. Wait a minute — your site will be live at `https://<your-username>.github.io/<repo-name>/`.

## Notes & Next Steps
- The current admin "Publish Post" stores posts locally in the page. To persist posts across users/devices, wire the post submissions to Firestore (`firebase.firestore()`), which is scaffolded in `assets/js/script.js`.
- Replace the placeholder logo at `assets/images/logo.jpg` with your real logo (same filename).
- For additional security, keep the Firebase API key in the client (it's required), but do not commit private server keys anywhere else.

---

If you'd like, I can:
- Wire post saving to Firestore (I will need your full Firebase config & Firestore rules),
- Configure a simple EmailJS template example for you,
- Or create a `deploy.sh` that pushes to GitHub automatically.



## Optional: Enable real Email delivery & Firestore
1. Fill `assets/js/script.js` `firebaseConfig` and set `USE_FIREBASE = true` to enable Firebase. Then implement Firestore writes for posts (we can help with that).
2. Sign up for EmailJS, create a service and template, fill `EMAILJS_*` values and set `USE_EMAILJS = true` to send OTPs via EmailJS instead of the local mailto fallback.
