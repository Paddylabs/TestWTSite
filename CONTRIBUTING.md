# Updating this site — Wellness Therapeutics

This is a static site (plain HTML/CSS/JS) hosted on **Cloudflare Pages**, connected to
this GitHub repo. **Committing to `master` deploys to the live site automatically.**

> This file is in `.gitignore` on purpose — it's a local crib sheet and is NOT
> committed/published. Keep your own copy if you reclone.

---

## The page
| File | Live page |
|---|---|
| `index.html` | The whole physiotherapy site (single page) |
| `assets/wt/` | Images, logo, lotus/leaf motifs |

## Everyday workflow

### Tiny change (typo, price, swap a photo)
Fine to commit straight to `master`:
```bash
git add .
git commit -m "Update Fiona's bio"
git push
```
→ live in ~1 minute.

### Anything visual or structural (recommended: branch + preview)
```bash
git checkout -b my-change
# ...edit files...
git add .
git commit -m "Describe the change"
git push -u origin my-change     # Cloudflare builds a PREVIEW url
```
Check the preview URL, then merge:
```bash
git checkout master
git merge my-change
git push                         # → deploys to live
git branch -d my-change
```

## Booking buttons
Every **"Book an appointment"** button links to the Cliniko booking system and opens in
a new tab:
`https://wellness-therapeutics.uk1.cliniko.com/bookings#service`
It appears 4× (header, hero, CTA band, footer). If the Cliniko URL changes, update all four.

## The "Request a call back" form
The form at the bottom uses **Web3Forms** (key in the HTML) and emails the Wellness
Therapeutics inbox. It's a call-back request, separate from instant Cliniko booking.

## Treatment-card photos
Each "What we treat" card has an "Add a photo" placeholder. To add an image, replace the
placeholder `<div class="svc__photo">…</div>` with:
`<img src="assets/wt/treat-NAME.jpg" alt="...">` (suggested names in the HTML comments).
Keep images under ~300 KB; filenames are **case-sensitive** on Cloudflare.

## Images
- Resize to ~1200–1400px longest edge, JPEG ~80% quality, under ~300 KB.
- Match the exact filename case used in the HTML.

## If something breaks (rollback)
**Cloudflare dashboard → Workers & Pages → this project → Deployments →
pick the last good one → Rollback.** Instant, no git needed.

## Cross-links
The **Wellness Centre** links (header + footer) point to the St Matthew's site (a separate
repo/domain). If that domain changes, update those absolute URLs.
