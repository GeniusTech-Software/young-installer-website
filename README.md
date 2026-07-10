# ySpace Download Page

A simple, mobile-first landing page for downloading the ySpace HR Android app.

## Project Structure

```
yspace-download/
├── index.html                          # Main landing page
├── assets/
│   ├── app/                            # (no longer used; APK hosted on Google Drive)
│   └── images/
│       ├── app-logo.png                # ySpace app logo
│       ├── company-logo.png            # Young Investment Group logo
│       └── install-steps/              # Install guide screenshots
│           ├── step-1.jpg              # Step 1: Download the APK
│           ├── step-2.jpg              # Step 2: Tap Install
│           ├── step-3.jpg              # Step 3: Wait for installation
│           └── step-4.jpg              # Step 4: Open ySpace
└── README.md
```

## Getting Started

No build step is required. You can open `index.html` directly in a browser for local testing.

For a more realistic test, serve the folder with a local server:

```bash
# Using Python
python3 -m http.server 8080

# Or using Node.js
npx serve .
```

Then open `http://localhost:8080` in your browser.

## Replacing Assets

### 1. APK file

The APK is hosted on Google Drive. Update the download link and QR code URL in `index.html` if the link changes:

```html
<a
  href="https://drive.google.com/uc?export=download&id=1HGWj98lMWcgIm057f6Kme9qsT7aMKjHM"
  download
  >...</a
>
```

```js
const apkUrl =
  "https://drive.google.com/uc?export=download&id=1HGWj98lMWcgIm057f6Kme9qsT7aMKjHM";
```

### 2. Logos

Replace these files with your actual images:

- `assets/images/app-logo.png` — ySpace app icon
- `assets/images/company-logo.png` — Young Investment Group logo

Recommended format: PNG with transparent background. Suggested size: at least 512x512px for the app logo.

If a logo is missing, a fallback placeholder will be shown automatically.

### 3. Install guide images

Replace the images in:

```
assets/images/install-steps/
```

Use clear screenshots that match each step:

1. `step-1.jpg` — Opening with Package installer
2. `step-2.jpg` — Tapping Install on the confirmation dialog
3. `step-3.jpg` — Waiting for installation
4. `step-4.jpg` — Opening the installed app

Images are displayed in full using `object-contain`, so they will not be cropped.

### 4. File size

The current file size shown is **92.3 MB**. To change it, edit this line in `index.html`:

```html
<p class="text-center text-xs text-gray-400 mb-8">
  APK &bull; Version 1.0.0 &bull; 92.3 MB
</p>
```

### 5. Primary color

The primary color is defined as a CSS custom property in `index.html`:

```css
:root {
  --primary: oklch(56.48% 0.147 151.18);
}
```

To change it, update the `--primary` value and the related `--primary-light`, `--primary-soft`, and `--primary-dark` variables.

## Deploy to Cloudflare Pages

1. Push this folder to a Git repository (GitHub, GitLab, or Bitbucket).
2. Go to [Cloudflare Pages](https://dash.cloudflare.com/) and create a new project.
3. Connect your Git repository.
4. Use these build settings:
   - **Build command:** (leave empty)
   - **Build output directory:** `/`
5. Click **Save and Deploy**.

If you want to deploy only this folder from a larger monorepo, set the **Root directory** to `yspace-download` and the **Build output directory** to `/`.

## Language Support

The page supports English and Burmese (Myanmar). Users can switch languages using the **EN | MY** toggle in the header. The selected language is saved in the browser's localStorage.

To update translations, edit the `translations` object in `index.html`.

## Notes

- The QR code is generated automatically and points to the APK file URL.
- The page is mobile-first but also works well on desktop.
- The iOS section is currently a placeholder and can be enabled once the iOS app is ready.
