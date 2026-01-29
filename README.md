# GTSC — Static Website (Ready for GitHub Pages)

This repository contains a small static site for GTSC (Global Tech Solutions & Care).

Included files
- index.html
- services.html
- about.html
- contact.html
- assets/styles.css
- assets/script.js
- assets/favicon.svg
- .github/workflows/deploy.yml (GitHub Actions auto-deploy to gh-pages)
- .gitignore
- README.md
- CNAME (optional — add your custom domain here)

Quick usage (local preview)
1. Clone locally or copy files into a folder.
2. Open `index.html` in your browser to preview.

Option A — Manual GitHub Pages (quick)
1. Create a new GitHub repository (e.g., `gtsc-website`).
2. Push the files to the `main` branch.
3. Go to repository Settings → Pages and choose the source:
   - Branch: `gh-pages` (if you use the Action below) OR
   - Branch: `main` / (root) if you prefer to serve directly from main.
4. Save — site will publish at `https://<your-username>.github.io/<repo>/` (or your custom domain if configured).

Option B — Automatic deploy with GitHub Actions (recommended)
This repo includes a workflow `.github/workflows/deploy.yml` that runs when you push to `main`. It publishes the repository contents to the `gh-pages` branch using peaceiris/actions-gh-pages.

Steps:
1. Create a new GitHub repository (or use an existing one).
2. Set the remote (example uses SSH — replace with your repo URL):
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin git@github.com:YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```
3. The Action will run and create/update the `gh-pages` branch automatically.
4. In your repository Settings → Pages:
   - Set source to: Branch `gh-pages` / folder `/ (root)` and Save.
5. After a minute or two your site will be available at:
   ```
   https://<your-username>.github.io/<your-repo>/
   ```
6. If you prefer a custom domain, add a `CNAME` file to the repo root with your domain and update DNS records to point to GitHub Pages; see GitHub Pages docs for DNS setup.

Custom domain (optional)
- Add a file named `CNAME` (no extension) at repo root with your domain, e.g.:
  example:
  ```
  www.example.com
  ```
- Configure your domain's DNS records per GitHub Pages instructions (usually an A record and/or ALIAS/ANAME depending on DNS provider).

Form submissions
- The contact form currently uses a simple client-side handler to validate and display a message.
- To receive real submissions, wire the form in `assets/script.js` to a service such as Formspree, Netlify Forms, or your own server API. Example (Formspree):
  - Replace the demo fetch with:
    ```js
    await fetch('https://formspree.io/f/YOUR_ID', {
      method: 'POST',
      body: new FormData(form),
      headers: { 'Accept': 'application/json' }
    });
    ```

Notes & next steps
- Update the content, add a logo, and replace placeholder contact details if needed.
- If you want, I can:
  - Create a repository and push these files for you (I will need the repo name and permission).
  - Wire the contact form to Formspree and test a real submission.
  - Add analytics or structured data (JSON-LD) for local business.
