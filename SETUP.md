# Games Tracker – Setup Guide

## 1. Enable GitHub Pages

1. Go to your repository on GitHub: **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Branch: `main` / Folder: `/ (root)`
4. Click **Save**
5. Your app will be live at: `https://joefrench1.github.io/Games-tracker/`

## 2. Configure Firebase Realtime Database Rules

The app uses Firebase Realtime Database at:
```
https://games-track-default-rtdb.europe-west1.firebasedatabase.app
```

You need to set the database rules to allow public read/write:

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your project (`games-track`)
3. Go to **Realtime Database → Rules**
4. Replace the rules with the contents of `firebase-rules.json`:

```json
{
  "rules": {
    "gsc": {
      ".read": true,
      ".write": true
    }
  }
}
```

5. Click **Publish**

> **Note:** These rules allow anyone with the URL to read and write game data.
> This is fine for a personal/shared tracker between known users.
> Do not store sensitive information.

## 3. Done!

Once both steps above are complete:
- Visit `https://joefrench1.github.io/Games-tracker/`
- The app will connect to Firebase and sync live across all devices
- Any game added on one device appears on all others within ~5 seconds
