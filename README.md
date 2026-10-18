# Voter Slip Finder — Cross-Platform Suite
### Website, PC Desktop Application, and Mobile Application

This project provides a complete, unified solution to run the **Voter Slip Finder** across the web, desktop computers, and mobile phones.

---

## 📁 Project Structure

- `www/`
  - `index.html`: Fully self-contained application (HTML + CSS + JavaScript) with voter database, search/filter algorithms, and voter slip generation inlined.
  - `manifest.webmanifest` & `sw.js`: Progressive Web App (PWA) configuration for offline caching and home screen installation.
  - `assets/`: Slip background template (`template.png`), header banner (`heading.png`), and candidate photo (`photo.jpg`).
  - `icons/`: PWA and mobile app icons (`icon-192.png`, `icon-512.png`).
  - `data/`: Raw data exports (`voters.json` and `voters.csv`).
- `Launch_PC_App.bat`: 1-click zero-install launcher for Windows.
- `Launch_PC_App.sh`: 1-click launcher for macOS & Linux.
- `run_desktop_app.py`: Standalone Python local server & launcher.
- `main.js` & `package.json`: Electron desktop wrapper and build scripts.
- `capacitor.config.json`: Capacitor mobile framework configuration.

---

## 1. 🌐 Website Deployment (Web Application)

The application in `www/` is a static web app that can be hosted on any HTTPS web hosting provider for free:

### Option A: Netlify Drop (Fastest — 30 seconds, no code required)
1. Go to [Netlify Drop](https://app.netlify.com/drop).
2. Drag and drop the `www` folder directly onto the page.
3. Netlify will generate a live HTTPS URL instantly (e.g., `https://your-app.netlify.app`).

### Option B: GitHub Pages
1. Create a GitHub repository and push the files inside `www/`.
2. In your repository, go to **Settings > Pages**.
3. Under **Branch**, select `main` (or `gh-pages`) and the root `/` folder, then click **Save**.
4. Your site will be published at `https://<username>.github.io/<repo-name>/`.

### Option C: Cloudflare Pages / Vercel
1. Link your repository or upload the `www` folder in the Cloudflare Pages or Vercel dashboard.
2. Set the build output directory to `./` (or `www`).
3. Deploy to get your custom domain with global CDN caching.

---

## 2. 💻 PC Application (Windows, macOS, Linux Desktop)

You have two ways to run and package the PC desktop application:

### Method 1: Zero-Install Instant Launchers (No setup needed)
- **Windows**: Double-click `Launch_PC_App.bat`. It automatically detects Microsoft Edge or Google Chrome and launches the app in standalone desktop application window mode (without browser toolbars, tabs, or address bars).
- **macOS / Linux**: Open Terminal and run `./Launch_PC_App.sh` (or `python3 run_desktop_app.py`).

### Method 2: Native Electron Standalone Executable (.exe, .dmg, .AppImage)
If you want to compile a standalone installer or portable `.exe` file:
1. Ensure [Node.js](https://nodejs.org/) (v18+) is installed on your computer.
2. Open Terminal or Command Prompt in this project root directory.
3. Install dependencies:
   ```bash
   npm install
   ```
4. Test run the desktop app:
   ```bash
   npm start
   ```
5. Build the standalone executable:
   - **For Windows (.exe)**:
     ```bash
     npm run build-win
     ```
     This generates a portable `.exe` in the `dist/` folder that can run on any Windows PC without installation.
   - **For macOS (.dmg)**:
     ```bash
     npm run build-mac
     ```
     *(Must be compiled on a Mac)*
   - **For Linux (.AppImage / .deb)**:
     ```bash
     npm run build-linux
     ```

---

## 3. 📱 Mobile Application (Android & iOS)

### Method 1: Instant Progressive Web App (PWA) — Recommended
Once the website is hosted online (via Netlify, GitHub Pages, etc.):
- **On Android (Google Chrome / Edge / Brave)**:
  1. Open the hosted website URL in Chrome.
  2. Tap the menu (three dots) > **Install app** (or **Add to Home screen**).
  3. The app will install with its icon on your app drawer and home screen. It launches in fullscreen mode with splash screen support and works completely offline.
- **On iPhone / iPad (Safari)**:
  1. Open the hosted website URL in Safari.
  2. Tap the **Share** button (box with an upward arrow) at the bottom.
  3. Scroll down and tap **Add to Home Screen**, then tap **Add**.
  4. The app icon will appear on your iOS home screen and launch fullscreen like a native iOS app.

### Method 2: Android APK via PWABuilder (No Android Studio required)
1. Deploy your `www/` folder to any HTTPS host (as shown in Section 1).
2. Go to [PWABuilder](https://www.pwabuilder.com/).
3. Enter your live website URL and click **Start**.
4. PWABuilder checks the manifest and service worker. Click **Package for Stores** > **Android**.
5. Download the generated ready-to-install `.apk` file or Google Play Store bundle (`.aab`).

### Method 3: Native Android Studio Build via Capacitor
If you want full native source code for Android Studio:
1. In the project folder, install Capacitor:
   ```bash
   npm install @capacitor/core @capacitor/cli @capacitor/android
   ```
2. Initialize and sync the Android project:
   ```bash
   npx cap add android
   npx cap sync
   ```
3. Open in Android Studio:
   ```bash
   npx cap open android
   ```
4. In Android Studio, select **Build > Build Bundle(s) / APK(s) > Build APK(s)** to produce your debug or release `.apk`.

---

## 🔒 Privacy & Data Notice
This application processes voter list data. Ensure you maintain compliance with applicable local data protection and election laws. Store and distribute voter data only through authorized and secure channels.
