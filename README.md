# PedalCrew Demo Website

Lightweight static site to share Android demo builds and collect feedback. Free to host, minimal to maintain.

## Files
- `index.html` – landing page with download + embedded feedback form
- `privacy.html` – minimal privacy policy
- `favicon.svg` – site icon

Update these placeholders in `index.html` before publishing:
- `DOWNLOAD_APK_URL` – direct link to your APK (e.g., GitHub Release asset)
- `GOOGLE_FORMS_EMBED_URL` – Google Forms embed URL (see below)
- `FEEDBACK_FORM_URL` – link to the same form (fallback/open in new tab)
- `YOUR_EMAIL` – your contact email (also in `privacy.html`)

---

## Easiest free hosting: GitHub Pages

1) Create a GitHub repository (or use the existing one) and push this folder content to the repository root.

2) On GitHub: Settings → Pages → Build and deployment
   - Source: "Deploy from a branch"
   - Branch: `main` (or your default), Folder: `/ (root)`
   - Save. Wait 1–2 minutes for deployment.

3) Your site will be at `https://<your-username>.github.io/<repo>/`.

4) When you change files, commit to the selected branch and Pages will auto‑update.

Optional: add a custom domain later via GitHub Pages settings.

---

## Distributing the Android APK (free & simple)

Recommended: GitHub Releases

1) Build release APK in your Flutter app repo:
   ```bash
   flutter build apk --release
   # artifact: build/app/outputs/flutter-apk/app-release.apk
   ```
2) On GitHub, go to Releases → Draft a new release.
3) Upload `app-release.apk` as a binary asset and publish the release.
4) Right‑click the uploaded `app-release.apk` and copy its direct download URL.
5) Paste that URL into `index.html` replacing `DOWNLOAD_APK_URL`.

Alternative (also free):
- Firebase App Distribution (managed testers, more steps)
- Firebase Storage (public file link)

---

## Feedback form

1) Create a quick form (Google Forms recommended for easy embed) with fields like:
   - Device model, Android version
   - What worked well? What didn’t?
   - Suggestions or bugs
2) Get the embed URL:
   - Google Forms → Send → Embed <> → Copy the `src` URL from the iframe.
   - Paste that into `GOOGLE_FORMS_EMBED_URL` in `index.html`.
3) Also copy the public link and set `FEEDBACK_FORM_URL` (used as a fallback link under the embed).
4) Optionally add the same link inside the app using `url_launcher`.

### If the form fails to load on GitHub Pages
- Some corporate networks block Google domains in iframes. The fallback link is provided right under the embed.

---

## Optional: Firebase Hosting

If you prefer Firebase Hosting instead of GitHub Pages:

```bash
npm i -g firebase-tools
firebase login
firebase init hosting
# Select your Firebase project, public directory: "." (current), single-page app: No
firebase deploy --only hosting
```

---

## Notes
- This site has no backend and stores no data; privacy is simple by design.
- For iOS demos, TestFlight via Apple Developer account is the practical route.
 - On GitHub Pages, prefer relative links (`favicon.svg`, `privacy.html`, `index.html`) to avoid 404s.


