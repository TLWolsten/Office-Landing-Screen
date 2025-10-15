# Rugby ROC Office Display

A professional office TV display system featuring live BBC News top stories and local weather for Rugby, UK. Designed for non-interactive display on office TVs with West Coast South branding.

## Features

- **Live BBC News** - Top 9 stories updated every 5 minutes
- **Weather Widget** - Rugby, UK weather with 3-day forecast (updates every 10 minutes)
- **Live Clock** - Real-time clock and date display
- **West Coast South Branding** - Teal blue and yellow color scheme
- **Non-Interactive Design** - Perfect for TV displays

## GitHub Pages Deployment

### Quick Setup

1. **Create a new GitHub repository**
   ```bash
   # On GitHub, create a new repository (e.g., "rugby-roc-display")
   ```

2. **Upload these files to your repository:**
   - `index.html`
   - `logo.jpg`
   - `README.md`

3. **Enable GitHub Pages:**
   - Go to your repository Settings
   - Navigate to "Pages" section
   - Under "Source", select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Click Save

4. **Access your display:**
   - Your site will be available at: `https://[your-username].github.io/[repository-name]/`
   - Wait a few minutes for deployment to complete

### Using Git Command Line

```bash
# Clone your repository
git clone https://github.com/[your-username]/[repository-name].git
cd [repository-name]

# Copy the files
cp /path/to/index.html .
cp /path/to/logo.jpg .
cp /path/to/README.md .

# Commit and push
git add .
git commit -m "Add Rugby ROC office display"
git push origin main
```

### Alternative: Direct Upload via GitHub Web Interface

1. Go to your repository on GitHub
2. Click "Add file" → "Upload files"
3. Drag and drop `index.html` and `logo.jpg`
4. Commit the changes
5. Enable GitHub Pages in Settings

## How It Works

- **Pure Static HTML** - No build process required
- **Client-Side RSS Parsing** - Fetches BBC feeds directly using CORS proxy
- **Auto-Refresh** - News updates every 5 minutes, weather every 10 minutes
- **Responsive Design** - 3-column grid on desktop, 2 on tablet, 1 on mobile

## Technical Details

- No backend server required
- Uses `allOrigins` CORS proxy to fetch BBC RSS feeds
- Vanilla JavaScript (no frameworks)
- Embedded CSS for styling
- Compatible with any static hosting (GitHub Pages, Netlify, Vercel, etc.)

## Files

- `index.html` - Main application file (contains HTML, CSS, and JavaScript)
- `logo.jpg` - West Coast South logo
- `README.md` - This documentation

## Browser Support

Works on all modern browsers:
- Chrome/Edge
- Firefox
- Safari
- Opera

## Customization

To customize the display, edit `index.html`:

- **Change location**: Update `BBC_WEATHER_URL` with a different location code
- **Adjust refresh rates**: Modify `setInterval` values (in milliseconds)
- **Update branding**: Replace `logo.jpg` and adjust colors in CSS
- **Change title**: Update the `<h1>` tag with your office name

## License

MIT License - Free to use and modify
