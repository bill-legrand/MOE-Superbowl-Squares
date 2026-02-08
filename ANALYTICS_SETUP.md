# Analytics Setup

## Firebase Database Rules Update

To enable analytics logging, you need to update your Firebase Realtime Database rules:

1. Go to: https://console.firebase.google.com/project/moe-superbowl-squares/database
2. Click on the **"Rules"** tab
3. Replace the existing rules with:

```json
{
  "rules": {
    "messages": {
      ".read": true,
      ".write": true,
      "$messageId": {
        ".validate": "newData.hasChildren(['username', 'text', 'timestamp']) && newData.child('text').val().length <= 200 && newData.child('username').val().length <= 20"
      }
    },
    "analytics": {
      "pageviews": {
        ".read": true,
        ".write": true
      },
      "events": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

4. Click **"Publish"**

## What Gets Tracked

### Page Views
- Timestamp
- Session ID (unique per browser session)
- User agent
- Screen resolution
- Viewport size
- Referrer
- URL

### Events Tracked
- **square_click**: When user clicks on a grid square
  - Participant name
- **chat_message**: When user sends a chat message
  - Username
  - Message length
- **tab_switch**: When user switches between tabs
  - Tab name (live/chat/admin)

## Viewing Analytics

Access the analytics dashboard at:
**https://moe-superbowl-squares.vercel.app/analytics.html**

### Features:
- Total page views
- Unique sessions count
- Chat message count
- Square click count
- Time range filter (last hour, 24 hours, week, month, all time)
- Recent page views table
- Recent events table
- Export to CSV (coming soon)

## Privacy Notes

- No personal information is collected
- Session IDs are randomly generated and stored only in browser session storage
- User agents and IP addresses may be visible but are not specifically tracked
- All data is stored in your Firebase database
- You have full control and can delete data anytime from Firebase Console
