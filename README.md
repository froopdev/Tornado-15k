# Spotify Now Playing

A beautiful, minimalist web application that displays your currently playing Spotify track in real-time. When you're not actively listening to music, it shows the last played song.

## Features

- 🎵 **Real-time Updates**: Automatically fetches and displays the currently playing track every 5 seconds
- 🎨 **Beautiful UI**: Modern, minimalist design with dark theme and smooth animations
- 📱 **Mobile Responsive**: Seamlessly adapts to different screen sizes
- 🔄 **Fallback Behavior**: Shows the last played song when nothing is currently playing
- ⚡ **Progress Bar**: Visual progress indicator with time display
- 🎭 **Play/Pause Indicator**: Shows the current playback state

## Setup Instructions

### 1. Create a Spotify Developer Account

1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Log in with your Spotify account (or create one if you don't have it)
3. Click "Create an App"
4. Fill in the app details:
   - **App Name**: Spotify Now Playing (or any name you prefer)
   - **App Description**: A web app to display currently playing tracks
   - **Redirect URI**: Add your website URL (e.g., `http://localhost:8000` for local testing or your production URL)
5. Check the agreement box and click "Create"

### 2. Get Your Client ID

1. Once your app is created, you'll see the **Client ID** on the app dashboard
2. Copy this Client ID

### 3. Configure the Application

1. Open `index.html` in a text editor
2. Find the line that says:
   ```javascript
   const CLIENT_ID = 'YOUR_SPOTIFY_CLIENT_ID';
   ```
3. Replace `'YOUR_SPOTIFY_CLIENT_ID'` with your actual Client ID from step 2
4. Make sure the `REDIRECT_URI` matches the URL where you'll host the application

### 4. Deploy the Application

#### Option A: Local Testing with Python
```bash
# Navigate to the project directory
cd /path/to/Tornado-15k

# Start a simple HTTP server (Python 3)
python -m http.server 8000

# Or with Python 2
python -m SimpleHTTPServer 8000
```

Then open your browser and go to `http://localhost:8000`

#### Option B: Local Testing with Node.js
```bash
# Install http-server globally
npm install -g http-server

# Navigate to the project directory
cd /path/to/Tornado-15k

# Start the server
http-server -p 8000
```

Then open your browser and go to `http://localhost:8000`

#### Option C: Deploy to GitHub Pages

1. Push your code to a GitHub repository
2. Go to repository Settings → Pages
3. Select the branch and folder to deploy from
4. Your site will be available at `https://yourusername.github.io/repository-name`
5. **Important**: Add this URL to your Spotify App's Redirect URIs in the Developer Dashboard

#### Option D: Deploy to Netlify, Vercel, or other hosting services

Simply deploy the `index.html` file and make sure to update the Redirect URI in your Spotify app settings.

### 5. Update Redirect URI in Spotify Dashboard

1. Go back to your [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Click on your app
3. Click "Edit Settings"
4. Under "Redirect URIs", add the URL where your app is hosted
   - For local testing: `http://localhost:8000/`
   - For production: Your actual domain URL (e.g., `https://yourusername.github.io/spotify-player/`)
5. Click "Add" then "Save"

## Usage

1. Open the application in your web browser
2. Click the "Connect Spotify" button
3. You'll be redirected to Spotify to authorize the app
4. After authorization, you'll be redirected back to the app
5. The app will now display your currently playing track
6. If nothing is playing, it will show your last played track

## How It Works

### Authentication
The app uses Spotify's OAuth 2.0 Implicit Grant Flow:
1. User clicks "Connect Spotify"
2. Redirected to Spotify authorization page
3. After approval, Spotify redirects back with an access token in the URL fragment
4. Token is stored in session storage for subsequent API calls

### Data Fetching
- The app polls the Spotify API every 5 seconds
- First, it checks for currently playing track using `/v1/me/player/currently-playing`
- If nothing is playing (status 204), it fetches recently played tracks using `/v1/me/player/recently-played`
- The UI updates automatically based on the response

### API Endpoints Used
- `GET /v1/me/player/currently-playing` - Get the currently playing track
- `GET /v1/me/player/recently-played` - Get recently played tracks

## Troubleshooting

### "Invalid Client" Error
- Make sure your Client ID is correct
- Verify the Redirect URI matches exactly (including trailing slashes)

### Nothing Shows After Login
- Check browser console for errors
- Ensure you have played at least one song on Spotify
- Try playing a song on Spotify and wait a few seconds

### Token Expired
- Tokens expire after 1 hour
- The app will automatically redirect you to login again when the token expires

## Browser Compatibility

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome)

## Privacy & Security

- Your access token is stored only in session storage (cleared when you close the tab)
- No data is sent to any third-party servers
- All API calls are made directly to Spotify from your browser
- The app only requests read permissions for your currently playing and recently played tracks

## Customization

Feel free to customize the appearance by modifying the CSS in `index.html`:
- Colors: Change the gradient and color values
- Animations: Adjust animation timing and effects
- Layout: Modify the responsive breakpoints
- Polling interval: Change the update frequency (default is 5 seconds)

## License

This project is open source and available for personal and educational use.

## Credits

Built with ❤️ using Spotify Web API

---

**Note**: This application requires an active Spotify account (Free or Premium) to function.
