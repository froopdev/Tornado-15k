# Quick Start Guide - Spotify Now Playing

This guide will help you get your Spotify Now Playing web app up and running in minutes.

## Prerequisites
- A Spotify account (Free or Premium)
- A web browser
- A text editor

## Step-by-Step Setup

### Step 1: Create Spotify App (5 minutes)
1. Go to https://developer.spotify.com/dashboard
2. Log in with your Spotify account
3. Click "Create an App"
4. Enter:
   - App Name: `My Spotify Player`
   - App Description: `Personal now playing display`
5. Accept terms and click "Create"
6. **Copy your Client ID** (you'll need this in Step 2)

### Step 2: Configure Redirect URI (2 minutes)
1. In your Spotify app dashboard, click "Edit Settings"
2. Under "Redirect URIs", add:
   - For local testing: `http://localhost:8000/`
   - For GitHub Pages: `https://yourusername.github.io/repository-name/`
3. Click "Add", then "Save"

### Step 3: Update the Code (1 minute)
1. Open `index.html` in a text editor
2. Find line 449: `const CLIENT_ID = 'YOUR_SPOTIFY_CLIENT_ID';`
3. Replace `YOUR_SPOTIFY_CLIENT_ID` with your actual Client ID from Step 1
4. Save the file

### Step 4: Run Locally (1 minute)

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

### Step 5: Connect & Enjoy!
1. Click "Connect Spotify" button
2. Authorize the app
3. Start playing music on Spotify
4. Watch it appear in real-time! 🎵

## Deploy to GitHub Pages (Optional)

1. Push your code to GitHub
2. Go to Settings → Pages
3. Select branch to deploy
4. Visit your site at `https://yourusername.github.io/repository-name/`
5. **Remember**: Update Redirect URI in Spotify Dashboard with this URL!

## Troubleshooting

### "Invalid Client" Error
- Double-check your Client ID is correct
- Ensure Redirect URI matches exactly (including trailing slash)

### Nothing Shows After Login
- Open browser console (F12) to check for errors
- Make sure you've played at least one song on Spotify
- Wait 5 seconds for the first update

### Token Expired After 1 Hour
- This is normal - click "Connect Spotify" again
- Tokens expire for security reasons

## Customization Tips

### Change Update Frequency
Find line 451 and modify:
```javascript
const UPDATE_INTERVAL_MS = 5000; // Change to 10000 for 10 seconds
```

### Customize Colors
Search for `#1ed760` (Spotify green) and replace with your preferred color

### Adjust Mobile Breakpoints
Look for `@media` queries in the CSS section

## Support & Issues

If you encounter problems:
1. Check the browser console for errors (F12 → Console tab)
2. Verify your Client ID and Redirect URI
3. Ensure your Spotify app is active
4. Try playing a song and wait 5-10 seconds

## What Gets Tracked?
- Currently playing track (or last played if idle)
- Track name, artist, album art
- Playback progress
- Play/pause state

## Privacy
- All data stays in your browser
- No external servers involved
- Token expires after 1 hour
- Token cleared when you close the tab

---

**Enjoy your Spotify Now Playing display!** 🎵✨
