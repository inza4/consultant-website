# consultant-website

Personal website for Patricio Inzaghi, IT Consultant — available in English and French.

## Structure

```
├── index.html          ← Hostname-based redirect (FR / EN)
├── en/index.html       ← English version  (it-consultant.inzaghi.ar)
├── fr/index.html       ← French version   (consultant-it.inzaghi.ar)
├── css/style.css       ← Shared styles
├── js/main.js          ← Shared scripts (mobile nav, form feedback)
└── CNAME               ← GitHub Pages primary domain
```

## Hosting on GitHub Pages

1. Go to **Settings → Pages** in this repository.
2. Set **Source** to the branch you want to deploy (e.g. `main`) and the root `/` folder.
3. GitHub Pages will pick up the `CNAME` file and serve the site at `it-consultant.inzaghi.ar`.

### DNS setup (at your domain registrar)

Add these two CNAME records pointing to your GitHub Pages URL:

| Subdomain            | Type  | Value                          |
|----------------------|-------|--------------------------------|
| `it-consultant`      | CNAME | `inza4.github.io`              |
| `consultant-it`      | CNAME | `inza4.github.io`              |

Both subdomains serve the same repository. The root `index.html` detects the hostname
and redirects visitors automatically:

- `it-consultant.inzaghi.ar` → `/en/`
- `consultant-it.inzaghi.ar` → `/fr/`

> **Note:** GitHub Pages allows only one custom domain per repository (set via `CNAME`).
> The second subdomain works because both DNS records point to the same GitHub Pages IP.
> GitHub Pages will accept requests for any subdomain of a domain you have verified.

## Contact form

The contact form uses the browser's native `mailto:` fallback. If you want form submissions
delivered directly to your inbox without opening a mail client, sign up at
[Formspree](https://formspree.io/) and replace the form `action` attribute in both
`en/index.html` and `fr/index.html` with your Formspree endpoint:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```
