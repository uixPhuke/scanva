# Scanva QR Studio

Run `npm install` and `npm run dev`. Build with `npm run build`.

Eight QR types: website, Wi-Fi (WPA), PDF URL, vCard, text, email, WhatsApp, social profile. Six customizable presets, colors, patterns, logo uploads, PNG/JPEG/SVG export, resolution options, and a browser-local saved library. QR codes are static: destination editing, scan analytics, hosted PDFs and cloud sync are not implemented. Preview frame labels are not included in exported artwork.

## Enable Google sign-in

1. Create a Firebase project and register a web app.
2. In Authentication → Sign-in method, enable Google and set the support email.
3. Add localhost and your production hostname under Authentication → Settings → Authorized domains.
4. Copy `.env.example` to `.env.local` and enter your Firebase web app configuration (these are public client configuration values; never add service account credentials).
5. Restart the dev server or rebuild for production.

Firebase documentation: https://firebase.google.com/docs/auth/web/google-signin

Google sign-in is intentionally disabled until configured. Authentication does not enable cloud sync: codes remain saved on the current browser. No account credentials are needed to create or export a code.

Test downloaded QR artwork on a phone before printing, especially after changing colors or adding a logo. Keep a contrasting background and quiet zone.
