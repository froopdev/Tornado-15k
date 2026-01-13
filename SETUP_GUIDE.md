# Quick Start Guide - Spotify Now Playing

This guide will help you get your Spotify Now Playing web app up and running in minutes.

## Prerequisites
- A Spotify account (Free or Premium)
- A web browser
- A text editor

## Step-by-Step Setup

### Step 1: Get Spotify Access Token (2 minutes)
1. Go to https://developer.spotify.com/console/get-users-currently-playing-track/
2. Click the **"Get Token"** button
3. Select these scopes:
   - `user-read-currently-playing`
   - `user-read-playback-state`
   - `user-read-recently-played`
4. Click **"Request Token"**
5. **Copy the OAuth Token** that appears

### Step 2: Update the Code (1 minute)
1. Open `index.html` in a text editor
2. Find line ~449: `const ACCESS_TOKEN = 'YOUR_SPOTIFY_ACCESS_TOKEN';`
3. Replace `YOUR_SPOTIFY_ACCESS_TOKEN` with the token you copied in Step 1
4. Save the file

### Step 3: Run Locally (1 minute)

**Option A - Python (easiest):**
```bash
python3 -m http.server 8000
```
Then open: http://localhost:8000

**Option B - Node.js:**
```bash
npx http-server -p 8000
```
Then open: http://localhost:8000

**Option C - VS Code:**
Install "Live Server" extension and click "Go Live"

### Step 4: Enjoy!
1. Open the app in your browser
2. It will automatically start displaying your currently playing track
3. If nothing is playing, it shows your last played track
4. Watch it update in real-time! 🎵

## Deploy to GitHub Pages (Optional)

1. Push your code to GitHub (**don't commit your token!**)
2. Go to Settings → Pages
3. Select branch to deploy
4. Visit your site at `https://yourusername.github.io/repository-name/`
5. You'll need to update the token in the deployed file

## Troubleshooting

### Token Expired After 1 Hour
- This is normal - tokens expire for security
- Get a new token from the Web API Console
- Update the `ACCESS_TOKEN` in index.html

### Nothing Shows
- Open browser console (F12) to check for errors
- Verify your access token is valid
- Make sure you've played at least one song on Spotify
- Wait 5 seconds for the first update

## Customization Tips

### Change Update Frequency
Find line ~451 and modify:
```javascript
const UPDATE_INTERVAL_MS = 5000; // Change to 10000 for 10 seconds
```

### Customize Colors
Search for `#1ed760` (Spotify green) and replace with your preferred color

### Adjust Mobile Breakpoints
Look for `@media` queries in the CSS section

## What Gets Tracked?
- Currently playing track (or last played if idle)
- Track name, artist, album art
- Playback progress
- Play/pause state

## Privacy
- All data stays in your browser
- No external servers involved
- Token is hardcoded (keep it private!)
- Never commit your token to public repositories

---

**Enjoy your Spotify Now Playing display!** 🎵✨
