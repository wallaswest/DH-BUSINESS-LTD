# DH Business Rwanda Ltd — website

Static site (no build step). `index.html` is the whole site; CSS and JS are inline in that file.

## Folders

- `images/` — site photos. `news-1.jpg`, `news-2.jpg`, `news-3.jpg` are the current News photos.
  `images/uploads/` is created automatically the first time someone uploads a photo through the
  admin dashboard — it's fine if it doesn't exist yet.
- `content/news.json` — the News section's data. The site reads this file at runtime and renders
  it — don't hardcode news posts into `index.html` again, or the two will conflict.
- `admin/` — the Decap CMS dashboard (`/admin` on the live site) and its config (`config.yml`).

## Editing News without touching code

Once set up (see below), go to `yoursite.com/admin`, log in, and use the "News & Updates" form —
date, tag, title, photo, description. Publishing there commits straight to this repo and Netlify
rebuilds the live site automatically, usually within a minute.

## One-time setup (only needs doing once)

1. This repo must be linked to the Netlify site: **Site configuration → Build & deploy →
   Continuous deployment → Link repository**.
2. **Site configuration → Identity → Enable Identity**, registration set to "Invite only."
3. **Identity → Services → Enable Git Gateway** (lets an Identity login save changes here without
   needing a GitHub account).
4. **Identity → Invite users** → enter the owner's email. They set a password from the invite
   email, then log in at `/admin`.

Note: Git Gateway is a deprecated Netlify feature — it still works and is what Decap CMS's own
docs recommend for non-technical logins, but it's no longer being actively developed. If it ever
stops working, the News section will need a different login method wired up in
`admin/config.yml`; the rest of the site is unaffected either way.

## Making other changes (design, pages, copy)

Anything outside the News section still lives directly in `index.html`. Edit it in the repo (or
have it edited for you) and push — Netlify redeploys automatically on every push to `main`.
