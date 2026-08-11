# Deploying the homepage → nicksibozhu.github.io

The site is plain self-contained HTML (no Jekyll, no build step): `index.html` + `blog/`.
`.nojekyll` keeps GitHub Pages from running Jekyll over the files.

**Writing a blog post:** `cp blog/_template.html blog/YYYY-MM-DD-your-slug.html`, write in it,
then add a `<li>` for it in `blog/index.html` (and delete the "No posts yet." line).

## One-time setup

1. **Re-auth gh as YOUR account** (this machine is currently logged in as `Timsty1`, which is
   NOT you — do not push anything before this step):
   ```
   gh auth login        # choose github.com → login as NickSiboZhu
   # or, to keep both accounts: gh auth switch --user NickSiboZhu
   ```
2. Create the user-site repo (must be exactly this name for `https://nicksibozhu.github.io`):
   ```
   gh repo create NickSiboZhu/NickSiboZhu.github.io --public
   ```
3. First publish:
   ```
   cd /home/admin/sibo/job-market/site
   git init -b main && git add .nojekyll index.html blog/ images/ && git commit -m "homepage v1"
   git remote add origin https://github.com/NickSiboZhu/NickSiboZhu.github.io.git
   git push -u origin main
   ```
   GitHub Pages auto-serves user repos named `<login>.github.io` from `main` — no settings needed.
   (Alternative: keep the site inside job-market and push a copy; decide before first publish.)

## Content TODOs before publish

- [ ] Photo at `images/self.jpg` (square, ≥440px looks sharp on retina)
- [ ] "graduate student" → exact program/year
- [ ] Month for the HyMEM acceptance news item
- [ ] Wenyi Wu / Kun Zhou link targets (their pages)
- [ ] Aether AI line — pending clearance (commented out in index.html)
- [ ] CV link in nav once resume PDF exists
- [ ] Swap HyMEM paper link to ACL Anthology page when it's indexed
