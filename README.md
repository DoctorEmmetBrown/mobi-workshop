# MoBI 2027 website

One-page static site for the MoBI 2027 Modulation-Based Imaging Workshop (Centre Paul-Langevin, Aussois, 31 May – 4 June 2027), served with GitHub Pages.

## Files

| File | Purpose |
|---|---|
| `index.html` | The landing page |
| `img/` | The six CAES photos (credits shown on the page) |
| `favicon.svg`, `apple-touch-icon.png` | Browser tab and home-screen icons |
| `og-image.png` | Preview image shown when the link is shared (email, Slack, LinkedIn) |
| `CNAME` | Custom domain of the site (`mobi-workshop.org`) |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |
| `robots.txt` | Allows search engines to index the site |

## Using another domain name

Replace `mobi-workshop.org` in three places:
1. in `CNAME` (one line, without `https://`);
2. in `index.html`, the `<link rel="canonical" …>` tag;
3. in `index.html`, the `og:url` and `og:image` tags.

## Step 1: publish with GitHub Pages

1. Upload the content of this folder to the repository, including `img/`, `CNAME` and `.nojekyll`.
2. **Settings › Pages**: Source = *Deploy from a branch*, branch `main`, folder `/ (root)`, then **Save**.
3. After about a minute, the site is live at `https://<account>.github.io/<repository>/` (or at the custom domain once step 3 is done).

## Step 2: register the domain

Any registrar works (OVHcloud, Gandi, Cloudflare…). No hosting or email plan is needed.

## Step 3: point the domain to GitHub (DNS zone at the registrar)

Remove the default A / AAAA records on the bare domain, then add:

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | `<account>.github.io.` |

Then, in **Settings › Pages**:
1. check that *Custom domain* shows `mobi-workshop.org` (it is read from the `CNAME` file);
2. wait for the DNS check to turn green (from a few minutes to a few hours);
3. tick **Enforce HTTPS**.

Tip: GitHub also lets you *verify* the domain for your account (account **Settings › Pages**). Do it: it prevents anyone else from using the domain on GitHub.

## Updating the site

Edit `index.html` in the repository, or upload a new version under the same name. The site updates in about a minute.

## Before announcing the address

- Get the CAES's agreement to use their photos (credits are already shown under the gallery).
- Contact address: in `index.html`, find `CONTACT_EMAIL = ""` and put the address between the quotes to show the "Questions? Write to" line.
