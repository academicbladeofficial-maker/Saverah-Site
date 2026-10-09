# Saverah Official Website & Compliance Portal

A lightweight, standalone static website for **Saverah**—a cultural media-sharing platform and digital time capsule designed for Google Play compliance, store listings, and user support.

Built with **vanilla HTML5 and CSS3**—zero frameworks, zero build steps, zero external tracking scripts.

---

## 📂 Repository Structure

```text
Saverah-Site/
├── index.html        # Landing page (heritage mission, features, screenshot placeholders)
├── privacy.html      # Privacy Policy (Supabase, Railway, NSFWJS moderation, deletion)
├── terms.html        # Terms of Service (acceptable use, prohibited NSFW content, termination)
├── support.html      # Support helpdesk, violation reporting & deletion instructions
├── style.css         # Modern, responsive, accessible CSS stylesheet
├── sitemap.xml       # Search engine sitemap referencing all pages
├── robots.txt        # Web crawler instructions
├── vercel.json       # Optional configuration for instant Vercel zero-config deploys
├── assets/
│   └── logo.svg      # Vector brand logo
└── README.md         # Deployment and maintenance documentation
```

---

## 🚀 Free Deployment Guide

This site requires no build command and can be served statically anywhere for free.

### Choice: GitHub Pages (Recommended)
GitHub Pages is the simplest zero-cost, permanent hosting solution for pure static repositories:
1. Create a repository on GitHub (e.g. `saverah-site` or `saverah.github.io`).
2. Push this directory to the repository:
   ```bash
   git add .
   git commit -m "Initial commit of Saverah marketing & compliance site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/saverah-site.git
   git push -u origin main
   ```
3. In GitHub, go to **Settings &rarr; Pages**.
4. Under **Build and deployment**, select **Source: Deploy from a branch**, choose branch `main` and folder `/ (root)`.
5. Click **Save**. Within 60 seconds, your site is live at:
   `https://<your-username>.github.io/saverah-site/` (or your custom domain `https://saverah.com`).

---

### Alternative: Vercel (1-Click Free Hosting)
1. Install Vercel CLI or import the GitHub repo in the [Vercel Dashboard](https://vercel.com):
   ```bash
   npx vercel
   ```
2. Select default options (framework: *Other*, root: `./`).
3. Vercel provides a free `https://saverah-*.vercel.app` domain with instant global edge caching and free SSL.

---

### Alternative: Netlify
1. Log into [Netlify](https://app.netlify.com).
2. Either drag-and-drop this folder directly into the Netlify dashboard, or connect the GitHub repository.
3. Publish directory: `.` (leave build command blank).

---

## ⚖️ Legal & App Verification Notes

### Verified Against Actual Codebase:
- **Authentication**: Powered by Supabase Auth (supports Google, Apple, Facebook OAuth and Email/Password).
- **Sub-processors**: Supabase (PostgreSQL database, authentication, media buckets: `avatars`, `videos`, `photos`, `folders`), Railway (backend API container).
- **Content Moderation**: Pre-publication scanning on public uploads using an embedded, self-hosted **NSFWJS** model (MobileNetV2 on TensorFlow.js). Media is evaluated server-side and **not shared with external third-party moderation APIs**.
- **No Ad Trackers / No Data Sales**: Backend contains zero advertising SDKs, tracking pixels, or data broker integrations.
- **Account Deletion Protocol**: Verified directly from `account_deletion_service.js`:
  - Permanently deletes all media files across Supabase Storage buckets and local server cache.
  - Cascades/deletes database records across `profiles`, `public_videos`, `public_photos`, `drafts`, `public_folders`, `private_folders`, `private_folder_members`, `private_folder_invites`, `shared_items`, `search_history`, `ai_recommendation_signals`, `video_analytics_events`, `messages`, `notifications`, and `reports`.
  - Permanently purges user identity from `auth.users` via Supabase Admin API.

### Items Marked as DRAFT for Legal Review:
Both `privacy.html` and `terms.html` contain the required top-level HTML comment:
```html
<!-- DRAFT: This document requires legal review before formal publication. -->
```
The exact legal jurisdiction, limitation of liability clauses, and dispute resolution venues should be reviewed by qualified legal counsel prior to formal Google Play production release.

---

## 🖼️ Customizing Screenshot Placeholders
In `index.html`, three styled placeholder frames are ready to receive real screenshots once the app UI is finalized:
- Replace the `.screenshot-placeholder` containers with `<img>` tags pointing to real 1080×1920 mobile captures in `assets/`.
