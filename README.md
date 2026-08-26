# Founder Content Engine — public site

Built by `deploy_site.py`. **Do not edit these files by hand** — edit
`gtm/sales-page.html` and re-run the script.

## Deploy to GitHub Pages

```bash
cd site
git init -b main
git add -A
git commit -m "Founder Content Engine site"
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin main
```

Then: repo **Settings -> Pages -> Source: Deploy from a branch -> main -> / (root)**.
Live in about a minute at `https://USERNAME.github.io/REPO/`.

If that URL differs from `SITE_URL` in `deploy_site.py`, update the constant and
re-run, or the social preview image will not resolve.

## Wire up the email capture

Open `index.html`, find `var ENDPOINT = "";` near the bottom, and paste your
provider's form endpoint:

| Provider  | Endpoint | Free tier |
|---|---|---|
| Buttondown | `https://buttondown.email/api/emails/embed-subscribe/YOURNAME` | 100 subscribers |
| Kit (ConvertKit) | `https://app.kit.com/forms/XXXXXXX/subscriptions` | 10,000 subscribers |
| Formspree | `https://formspree.io/f/XXXXXXX` | 50 submissions/month |

Buttondown or Kit are the better picks — they can *send* the follow-up. Formspree
only collects, leaving you to deliver by hand.

Until an endpoint is set the form falls back to a pre-filled `mailto:` so it is
never silently broken. Either way the visitor gets the PDF immediately.
