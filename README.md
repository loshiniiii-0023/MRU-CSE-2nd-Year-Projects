# FloodWatch

Firebase-backed flood alert and resource coordination app.

## Setup
1. Create a Firebase project and enable Email/Password Authentication, Firestore, and Storage.
2. Copy `.env.example` to `.env.local` and fill values from Firebase Project Settings.
3. Deploy `firestore.rules` and `storage.rules` from the Firebase console or Firebase CLI.
4. Create the composite indexes requested by Firestore errors for `FloodAlerts(active, createdAt)` and `FloodReports(status, createdAt)`.
5. Run the app with `pnpm dev` or deploy through Vercel.

## First administrator
Register normally; every browser-created account is always a citizen. Using a trusted server process or Firebase Admin SDK, set a custom claim `{ role: 'administrator' }` for the first administrator, then sign out and back in. Never accept a role from the registration form. Mirror the role in `Users/{uid}` only from that trusted process.

## Data safety
Demo cards in the UI are explicitly labeled demonstration records and are never written to Firebase. Production reads and writes require Firebase configuration and authenticated users. No SMS workflow is implemented.
