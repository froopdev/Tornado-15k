# Spotify Now Playing

A beautiful, minimalist web application that displays your currently playing Spotify track in real-time. When you're not actively listening to music, it shows the last played song.

## Features

- 🎵 **Real-time Updates**: Automatically fetches and displays the currently playing track every 5 seconds
- 🎨 **Beautiful UI**: Modern, minimalist design with dark theme and smooth animations
- 📱 **Mobile Responsive**: Seamlessly adapts to different screen sizes
- 🔄 **Fallback Behavior**: Shows the last played song when nothing is currently playing
- ⚡ **Progress Bar**: Visual progress indicator with time display
- 🎭 **Playback Status**: Shows whether a track is playing, paused, or was last played

## Setup Instructions

### 1. Get Your Spotify Access Token

1. Go to [Spotify Web API Console](https://developer.spotify.com/console/get-users-currently-playing-track/)
2. Click the **"Get Token"** button
3. Select the following scopes:
   - `user-read-currently-playing`
   - `user-read-playback-state`
   - `user-read-recently-played`
4. Click **"Request Token"**
5. Copy the **OAuth Token** that appears

**Note**: Tokens expire after 1 hour. You'll need to generate a new token when it expires.

### 2. Configure the Application

1. Open `index.html` in a text editor
2. Find the line that says:
   ```javascript
   const ACCESS_TOKEN = 'YOUR_SPOTIFY_ACCESS_TOKEN';
   ```
3. Replace `'YOUR_SPOTIFY_ACCESS_TOKEN'` with the token you copied in step 1

**Security Note**: 
- This is a personal application designed for single-user use
- Keep your access token private and never commit it to public repositories
- Tokens expire after 1 hour for security reasons

### 3. Deploy the Application

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

#### Option D: Deploy to Netlify, Vercel, or other hosting services

Simply deploy the `index.html` file.

## Usage

1. Open the application in your web browser
2. The app will automatically start displaying your currently playing track
3. If nothing is playing, it will show your last played track
5. The app will now display your currently playing track
6. If nothing is playing, it will show your last played track

## How It Works

### Authentication
The app uses a hardcoded Spotify access token for personal use:
1. You generate a token from Spotify's Web API Console
2. The token is hardcoded in the application
3. Token is used for all API calls

**Note**: Tokens expire after 1 hour. You'll need to generate a new token and update the code when it expires.

### Data Fetching
- The app polls the Spotify API every 5 seconds
- First, it checks for currently playing track using `/v1/me/player/currently-playing`
- If nothing is playing (status 204), it fetches recently played tracks using `/v1/me/player/recently-played`
- The UI updates automatically based on the response

### API Endpoints Used
- `GET /v1/me/player/currently-playing` - Get the currently playing track
- `GET /v1/me/player/recently-played` - Get recently played tracks

## Troubleshooting

### Token Expired Error
- Tokens expire after 1 hour for security reasons
- Generate a new token from the [Spotify Web API Console](https://developer.spotify.com/console/get-users-currently-playing-track/)
- Update the `ACCESS_TOKEN` constant in `index.html`

### Nothing Shows After Opening
- Check browser console for errors
- Verify your access token is valid
- Ensure you have played at least one song on Spotify
- Try playing a song on Spotify and wait 5 seconds for the update

### API Rate Limiting
- The app polls Spotify every 5 seconds by default
- If you experience rate limiting issues, you can increase the `UPDATE_INTERVAL_MS` constant in the code
- Spotify's rate limits are typically generous for personal use

## Browser Compatibility

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome)

## Privacy & Security

- This is a personal application designed for single-user use
- Your access token is hardcoded in the application
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
