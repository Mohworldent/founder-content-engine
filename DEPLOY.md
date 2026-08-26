# Deploying and maintaining this site

This site is generated. **Do not edit these files by hand** — edit `gtm/sales-page.html` in the parent repo and re-run `deploy_site.py`, which rebuilds this folder from scratch (including this deployment doc, but not `README.md`, which is hand-written for positioning and is preserved across rebuilds).

## Redeploying after a content change

```bash
cd ..                # back to the founder-content-engine project root
python deploy_site.py
cd site
git add -A
git commit -m "update site"
git push
```

GitHub Pages picks up the new commit automatically, usually within a minute.

## First-time setup (already done for this repo)

```bash
cd site
git init -b main
git add -A
git commit -m "Founder Content Engine site"
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin main
```

Then: repo **Settings → Pages → Source: Deploy from a branch → main → / (root)**.
Live in about a minute at `https://USERNAME.github.io/REPO/`.

If that URL differs from `SITE_URL` in `deploy_site.py`, update the constant and
re-run, or the social preview image and canonical URL will not resolve correctly.

## Wiring the email capture

Open `index.html`, find `var ENDPOINT = "";` near the bottom, and paste your
provider's form endpoint:

| Provider | Endpoint | Free tier |
|---|---|---|
| Buttondown | `https://buttondown.email/api/emails/embed-subscribe/YOURNAME` | 100 subscribers |
| Kit (ConvertKit) | `https://app.kit.com/forms/XXXXXXX/subscriptions` | 10,000 subscribers |
| Formspree | `https://formspree.io/f/XXXXXXX` | 50 submissions/month |

Buttondown or Kit are the better picks — they can *send* the follow-up automatically. Formspree only collects submissions, leaving you to deliver the PDF by hand.

Until an endpoint is set, the form falls back to a pre-filled `mailto:` so it is never silently broken. Either way the visitor gets the PDF immediately on submit — delivery is not gated behind confirming the email.
