# Stephanie Universe — Personal Enterprise

A personal operating website that treats time as capital, skills as assets, experiences as data, and projects as investments.

## Live editing

The site now has an owner editing mode.

Normal public URL:

`https://StephanieYOU125.github.io/stephanie-intro/`

Owner editing URL:

`https://StephanieYOU125.github.io/stephanie-intro/?edit=1`

In editing mode:

1. Click **Login** (after Firebase is configured).
2. Click **Edit**.
3. Click any highlighted text block and type directly.
4. Click **Save**.
5. Changes are stored in Firestore and become visible to public visitors.

If Firebase is not configured yet, edits are saved to browser localStorage as a fallback.

## Connect Firebase

### 1. Register a Web app

Firebase Console → **Project settings** → **Your apps** → Web (`</>`).

Copy the Firebase config into `firebase-config.js`.

### 2. Enable Authentication

Firebase Console → **Authentication** → **Sign-in method** → enable **Email/Password**.

Create your own admin user. The website does not provide a public sign-up screen.

### 3. Create Firestore

Firebase Console → **Firestore Database** → create database.

### 4. Lock writes to your account

Firebase Console → **Authentication → Users** → copy your **User UID**.

Open `firestore.rules` and replace:

`PASTE_YOUR_FIREBASE_AUTH_UID_HERE`

with your actual UID.

Publish those rules in Firebase Console, or use Firebase CLI:

```bash
firebase login
firebase use --add
firebase deploy --only firestore:rules
```

## Security design

- Public visitors: read published content only.
- Owner: sign in with Firebase Authentication, edit, and publish.
- Firestore rules: only the configured owner UID can write.
- GitHub Pages remains a static public website.
- The Firebase web config can be public; authorization is enforced by Firebase Authentication + Firestore Security Rules.

## Editable areas

The page supports direct editing for:

- Hero statement and description
- Company profile / fact cards
- Mission
- Business Units
- Core Assets
- Current Strategy
- Principles
- Chinese / English / Japanese introductions
- Communication rules
- Footer note

## Keyboard shortcut

On any page load, press **Cmd/Ctrl + Shift + E** to reveal/toggle edit mode.
