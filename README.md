PhoneShop — Static Site Deployment Guide

This site is a static HTML/CSS/JS storefront and can be hosted on GitHub Pages, Netlify, or Vercel.

Local preview

Open `index.html` in a browser, or run a local static server:

```bash
# from the project folder
python -m http.server 8080
# then open http://localhost:8080
```

Use the same Wi-Fi network to test from your phone:
1. Find your PC IP address with `ipconfig`.
2. Open `http://<PC_IP>:8080` on your phone browser.

GitHub Pages

1. Create a GitHub repository for this project.
2. In VS Code terminal, run:
```bash
git init
git add .
git commit -m "Initial PhoneShop site"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```
3. In GitHub repo settings, enable GitHub Pages:
   - Source: `main` branch
   - Folder: `/ (root)`
4. After a few minutes, your site will be available at `https://<username>.github.io/<repo>/`.

Optional GitHub Pages deploy with npm

If you want a reusable deploy workflow, create `package.json` and install `gh-pages`:

```bash
npm init -y
npm install --save-dev gh-pages
```

Then add this to `package.json`:

```json
"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d ."
}
```

For this simple static site, you can omit `predeploy` and just use:

```json
"scripts": {
  "deploy": "gh-pages -d ."
}
```

Deploy with:

```bash
npm run deploy
```

Netlify

1. Create an account at netlify.com.
2. Choose "Add new site" → "Import from Git".
3. Connect your GitHub repository.
4. Set build command: none
5. Set publish directory: `/`
6. Deploy the site.

Alternatively, drag-and-drop the project folder to the Netlify Sites dashboard for a direct deploy.

Vercel

1. Create an account at vercel.com.
2. Import project from GitHub.
3. Choose "Other" and deploy.
4. No build command is needed; publish directory is `/`.

Netlify config

A `netlify.toml` file is included for static deploy settings. It ensures the project publishes from the root directory.

Hosting notes

- Add `favicon.ico` to the project root so the browser icon loads correctly.
- Replace placeholder images with real product images as needed.
- If you want Google Sign-In later, set up a Google Cloud OAuth client and update the `GOOGLE_CLIENT_ID` in `index.html`.
- For contact forms, use a backend service or Netlify Forms.

Troubleshooting

- If the site does not load on your phone, check the firewall and ensure the phone and PC are on the same network.
- If `git` is not installed locally, install Git from https://git-scm.com/.
- If you need help with Netlify or GitHub, I can provide exact screenshots or commands.
