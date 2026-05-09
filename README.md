# alexamousley.com

Personal academic website for Alexa Mousley. Built with [Quarto](https://quarto.org/) and deployed via GitHub Actions to GitHub Pages.

---

## What's in this repo

```
.
├── _quarto.yml             # Site config: navbar, fonts, SEO meta, structured data
├── theme-light.scss        # Light theme styling
├── theme-dark.scss         # Dark theme styling
├── styles.css              # Custom layout components (hero, social row, cards…)
├── index.qmd               # Home page
├── research.qmd            # Research themes & projects
├── publications.qmd        # Publications by year
├── talks.qmd               # Invited talks, symposia, posters
├── media.qmd               # Press & broadcast coverage
├── mentoring.qmd           # Supervision, mentoring, teaching
├── cv.qmd                  # CV summary + PDF download
├── assets/
│   ├── headshot.jpg        # ← REPLACE with your real headshot
│   ├── favicon.png         # ← Optional, replace with your own
│   └── Mousley_CV.pdf      # ← ADD this file (your CV)
├── CNAME                   # Tells GitHub Pages to serve www.alexamousley.com
├── robots.txt              # SEO crawler rules
└── .github/workflows/
    └── publish.yml         # Auto-deploys on every push to main
```

---

## First-time setup (≈30 minutes)

### 1. Install Quarto locally (so you can preview before pushing)

Download from [quarto.org/docs/get-started](https://quarto.org/docs/get-started/). Pick the installer for your OS (macOS, Windows, or Linux). Once installed, in this folder run:

```bash
quarto preview
```

This opens the site in your browser and live-reloads as you edit. **You don't need to install R or Python** — Quarto runs the markdown directly.

### 2. Add your real headshot and CV

- Replace `assets/headshot.jpg` with a square photo (≥800×800px, plain background).
- Drop your CV in `assets/` named exactly `Mousley_CV.pdf`.
- Optionally replace `assets/favicon.png` with something on-brand.

### 3. Push to GitHub

```bash
# In the project folder:
git init -b main
git add .
git commit -m "Initial site"

# Create a new repo on github.com (don't initialise with README), then:
git remote add origin https://github.com/alexamousley/alexamousley.github.io.git
git push -u origin main
```

**Important:** name the repo `alexamousley.github.io` (matching your GitHub username). It's a GitHub convention that gives your site a cleaner default URL while you're testing.

### 4. Enable GitHub Pages

In the repo on github.com:

1. Go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Push any commit (or just wait — the first push triggers the workflow). Watch it run under the **Actions** tab.

Within ~2 minutes your site will be live at `https://alexamousley.github.io`.

### 5. Point alexamousley.com at GitHub Pages

In your domain registrar's DNS settings (wherever you bought alexamousley.com), add:

| Type  | Host | Value                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| CNAME | www  | alexamousley.github.io |

Then in GitHub: **Settings → Pages → Custom domain**, enter `www.alexamousley.com` and tick **Enforce HTTPS** once it becomes available (usually within an hour).

DNS propagation takes ~10 mins to 24 hours. The `CNAME` file in this repo already tells GitHub which domain to serve.

---

## Day-to-day editing

To add a new publication, talk, or piece of press:

1. Open the relevant `.qmd` file.
2. Copy an existing entry as a template, edit, save.
3. Commit and push. The site rebuilds automatically (~90 seconds).

```bash
git add publications.qmd
git commit -m "Add 2026 paper"
git push
```

To preview locally before pushing: `quarto preview`.

---

## SEO checklist — get to #1 on Google for "Alexa Mousley"

Most of this is already wired into the site. Your part is the steps marked **[do this]**.

### Already done by this site

- ✅ Page titles include your name + role (the most important SEO field)
- ✅ Meta descriptions on every page
- ✅ `<link rel="canonical">` tag pointing to your domain
- ✅ JSON-LD `Person` structured data (tells Google explicitly who you are, your affiliation, alumni schools, and your social profiles)
- ✅ Open Graph and Twitter Card meta tags (clean previews on social media)
- ✅ Auto-generated XML sitemap (Quarto handles this)
- ✅ `robots.txt` allowing all crawlers
- ✅ Mobile-friendly responsive design
- ✅ Fast load times (static HTML, no client-side JavaScript bloat)

### **[do this]** Within the first week of going live

1. **Submit to Google Search Console.** Go to [search.google.com/search-console](https://search.google.com/search-console), add `alexamousley.com` as a property. Verify via DNS TXT record (your registrar's DNS panel). Once verified, submit the sitemap: `https://www.alexamousley.com/sitemap.xml`.

2. **Update your Cambridge staff page** to link to `alexamousley.com`. This single backlink will do more for your search ranking than almost anything else, because Cambridge has very high domain authority.

3. **Add the URL to every external profile:**
   - Google Scholar: Edit profile → Homepage
   - LinkedIn: Profile → Edit intro → Website
   - Bluesky: bio
   - GitHub: Edit profile → Website
   - ORCID: Personal information → Websites
   - OSF: Profile → Social links

4. **Use the canonical name everywhere.** Always "Alexa Mousley" on profiles (your published name variants like "A.L.S. Mousley" are fine in citations — Google clusters those automatically once the structured data tells it they're the same person).

### **[do this]** Ongoing

- Add new talks/papers as they happen — Google rewards active sites.
- Whenever a paper gets press coverage, add it to `media.qmd` and push.

### Realistic timeline

- **Week 1:** Site indexed, name search shows your site in top 10.
- **Month 1:** Top 5 for "Alexa Mousley".
- **Month 3:** #1 (assuming the Cambridge backlink is in place).

The reason it's not instant is Google needs to see other trusted sites pointing at yours. That Cambridge link is the unlock.

---

## Customisation cheatsheet

**Change the accent colour** (currently a calm blue, `#2c5e9e`):
- Edit `$primary:` in both `theme-light.scss` and `theme-dark.scss`.
- Also update the `.cv-button` background and the JSON-LD/social-row colours in `styles.css`.

**Change fonts:** edit the `@import url(...)` line and `$font-family-sans-serif` variable in both theme files.

**Add a new page:**
1. Create `newpage.qmd` with a YAML frontmatter block (copy one from existing pages).
2. Add an entry to the `navbar:` section in `_quarto.yml`.

**Disable dark mode:** in `_quarto.yml`, change the `theme:` block to just `theme: [cosmo, theme-light.scss]` (one entry, no light/dark distinction).

**Add Google Analytics later:** paste your GA4 measurement ID into the `google-analytics:` field in `_quarto.yml`.

---

## Help & references

- [Quarto websites docs](https://quarto.org/docs/websites/)
- [Quarto navigation](https://quarto.org/docs/websites/website-navigation.html)
- [Bootstrap icons](https://icons.getbootstrap.com/) — for navbar icon names
- [Font Awesome icons](https://fontawesome.com/search?o=r&m=free) — for inline `{{< fa name >}}` icons in content
