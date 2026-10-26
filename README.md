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

## QR library

Create, view details, edit content and design in place, delete, and undo the last deletion. Updates preserve each record ID and creation date, and record an update timestamp. The library persists across reloads in localStorage on this browser; it is not a cloud database. Editing static codes affects future exports only. Existing printed QR artwork keeps its encoded destination.

The home page and studio use system typography, cool neutral surfaces, blue accents, translucent navigation, responsive layouts, keyboard focus indicators, modal focus trapping, Escape dismissal, and reduced-motion/transparency preferences.

## Public home and authentication

The full-width public landing page is separate from the workspace shell. Signed-out visitors stay on the home page; create and login actions open Google sign-in. Firebase's auth-state observer sends authenticated sessions to the QR library and returns signed-out sessions home. The Scanva logo always returns home; authenticated users can reopen their workspace there. There is no guest bypass into the workspace. Firebase must be configured before real sign-in can be tested. Site hosting access remains unchanged.

## Connected Firebase project

Scanva Web is registered in Firebase project `scanva-9e882`. Its public web app configuration is stored in ignored `.env.local` for local production builds. Google is enabled as a sign-in provider; localhost and the current Sites hostname are authorized. Configure the same four VITE_FIREBASE values on any new deployment host and add its hostname to the Firebase authorized domain list. No service-account credentials are used.

## Vercel deployment

The included vercel.json configures Vite, npm run build, dist output, and SPA routing. Set the four VITE_FIREBASE environment variables in Vercel before deployment. Authorize the assigned production hostname in Firebase Authentication → Settings → Authorized domains. The .vercelignore excludes local environment files and OpenAI hosting metadata.

## Account and interface

The sidebar account menu opens Profile, Personalization, Settings, Help, and Logout. Google profile photos are the default; uploaded photos are center-cropped and stored per Firebase user on this browser, with a reset-to-Google action. Display names update through Firebase Authentication. Light, Midnight, system appearance, and motion preferences persist locally. Custom listbox dropdowns support keyboard navigation, focus restoration, outside dismissal, and Escape. Profile dialogs use a portal and focus trap to stay usable with the mobile navigation drawer.
