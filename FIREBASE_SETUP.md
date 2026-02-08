# Firebase Setup Instructions for MOE Super Bowl Squares Chat

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Enter project name: `moe-superbowl-squares`
4. Continue through the setup (you can disable Google Analytics if you want)
5. Click "Create Project"

## Step 2: Add Web App to Firebase

1. In your Firebase project, click the web icon (`</>`) to add a web app
2. Register your app with nickname: `MOE Squares`
3. Copy the `firebaseConfig` object that appears
4. Open `firebase-config.js` in your project
5. Replace the placeholder values with your actual config

## Step 3: Set Up Realtime Database

1. In Firebase Console, go to "Realtime Database" in the left menu
2. Click "Create Database"
3. Choose location (US or closest to you)
4. Start in **TEST MODE** for now (we'll secure it later)
5. Click "Enable"

## Step 4: Configure Database Rules

For the chat to work properly, set up these database rules:

1. Go to Realtime Database > Rules tab
2. Replace with these rules:

```json
{
  "rules": {
    "messages": {
      ".read": true,
      ".write": true,
      "$messageId": {
        ".validate": "newData.hasChildren(['username', 'text', 'timestamp'])"
      }
    }
  }
}
```

3. Click "Publish"

## Step 5: Update Your App

1. Edit `firebase-config.js` with your Firebase config from Step 2
2. Deploy your app
3. Chat will now work!

## Security (Optional but Recommended)

To prevent abuse, you can add rate limiting:

```json
{
  "rules": {
    "messages": {
      ".read": true,
      ".write": "auth != null || data.child(newData.key).parent().child(newData.key).val() == null",
      "$messageId": {
        ".validate": "newData.hasChildren(['username', 'text', 'timestamp']) && newData.child('text').val().length <= 200 && newData.child('username').val().length <= 20"
      }
    }
  }
}
```

## Features

- Real-time messaging during the game
- Last 50 messages displayed
- Username persistence (saved locally)
- Auto-scroll to newest messages
- 200 character message limit
- XSS protection (HTML escaping)

## Cost

Firebase free tier includes:
- 100k simultaneous connections
- 10GB/month data transfer
- More than enough for your use case!
