# Vastus Games — GitHub Pages website

A responsive, cinematic monochrome static website starter for Vastus Games.

## Pages and assets
- `index.html` — homepage and studio portfolio
- `hexi-trap.html` — Hexi Trap game details
- `download.html` — custom Android download page for Hexi Trap
- `privacy.html` — privacy policy draft (review and customize before launch)
- `terms.html` — terms of use draft (review and customize before launch)
- `styles.css` — responsive styling and motion
- `script.js` — mobile navigation, scroll progress, reveal animations
- `assets/` — temporary SVG brand mark, favicon and `site-config.js`
- `CNAME` — custom domain `vastusgames.indevs.in`

## Configure Hexi Trap downloads
Open `assets/site-config.js` and edit these values:

```js
window.VASTUS_CONFIG = {
  itchUrl: "https://niangamestudios.itch.io/hexitrap",
  apkUrl: "https://github.com/YOUR-USERNAME/YOUR-REPOSITORY/releases/latest/download/HexiTrap.apk",
  version: "1.0.0",
  fileSize: "28 MB",
  sha256: ""
};
```

The current itch.io page URL is configured as `https://niangamestudios.itch.io/hexitrap`. The direct APK URL stays blank until the APK is uploaded as a GitHub Release asset and the link is verified. Do not publish a guessed or untested direct APK URL. If `apkUrl` is blank, the page deliberately shows that the download link is not published yet rather than showing a broken download button. If `itchUrl` is blank, its button stays hidden.

### Recommended way to host the APK on GitHub
1. Create your GitHub repository for the website and publish the website source.
2. In the same repository, open **Releases** → **Draft a new release** (or create a separate public repository for game releases if you prefer).
3. Choose a version tag such as `hexi-trap-v1.0.0` and give the release a clear title and notes.
4. Attach your signed, tested APK as a release asset named exactly `HexiTrap.apk`, then publish the release.
5. Use the release asset's actual download URL in `assets/site-config.js`. The common `releases/latest/download/HexiTrap.apk` URL works only if that release is the latest release in the repository and the asset filename matches exactly.
6. Test the link on a phone and confirm the file installs on a supported Android device before announcing it.

**Avoid committing large APK binaries directly into the website source.** GitHub Releases is better for versioned binary downloads and keeps your code repository cleaner. Keep a backup of the original APK and publish a new release for each update. Never upload signing keys or passwords to GitHub.

### Important Android distribution notes
- Upload an APK that you own and have permission to distribute. Confirm it is signed and tested.
- Make sure the download page states the supported Android version and any permissions or compatibility requirements once known.
- Android may warn users about installing apps from outside Google Play. Explain this honestly; never ask users to disable device security broadly.
- Consider publishing a SHA-256 checksum in `site-config.js` so users can compare the downloaded file against the value you provide.
- The current itch.io page is published under the previous studio name, NianGameStudios. The Vastus Games site links to that existing page for now. Before mirroring its APK, verify that the file is the same current, signed build you intend to distribute. The listing currently displays a 28 MB APK; confirm the actual file size after upload.

## Replace placeholder branding
1. Replace `assets/vastus-mark.svg` with your real logo or update the `<img>` references if the file format/name changes.
2. Replace the abstract Hexi Trap artwork with your real game icon, screenshots and promotional art when supplied.
3. Confirm `https://www.instagram.com/VastusGames/` is your exact profile URL.
4. The contact email is set to `vastusgames@gmail.com` as provided.
5. Review and customize the privacy policy and terms. The included drafts are not legal advice and should reflect your actual game, analytics, data practices, and applicable laws.

## Preview locally
Open `index.html` in a browser. For a local server, run `python -m http.server 8000` from this directory and visit `http://localhost:8000`.

## Deploy to GitHub Pages
1. Sign in to GitHub and create a **public** repository named `vastus-games-website` (or another name you prefer).
2. Download and unzip this project. Upload the **contents** of the `vastus-games-site` folder to the repository root, so `index.html`, `CNAME`, `styles.css`, and `assets/` are directly in the root.
3. In repository **Settings → Pages**, select **Deploy from a branch**, choose `main` and `/(root)`, then save.
4. In **Settings → Pages → Custom domain**, enter `vastusgames.indevs.in` and save. The included `CNAME` file is already set to that domain.
5. In the DNS control panel for `indevs.in`, create the CNAME record for host/name `vastusgames` pointing to your GitHub Pages hostname (usually `YOUR-USERNAME.github.io`). Use the exact target GitHub shows and do not change unrelated DNS records. If you do not control this DNS zone, ask its administrator to add it.
6. Wait for DNS propagation and for GitHub's domain check. Then enable **Enforce HTTPS** when GitHub Pages makes it available.
7. Test the domain on desktop and mobile. Check every page, social links, email link, and the download buttons.

## Notes
- GitHub Pages is static hosting: it does not run server-side form processing, account systems or a CMS. The contact email uses a `mailto:` link.
- Fonts may load from Google Fonts with system fallbacks. Remove the CSS `@import` if you want no third-party font requests.
- Motion respects `prefers-reduced-motion` and navigation works on mobile.
