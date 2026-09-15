# OrdersTrail website

Landing page for **OrdersTrail**, the order book for home bakers (Android app).
It's a plain static site: no build step, no framework.

| File | What it is |
| --- | --- |
| `index.html` | The whole landing page (CSS and JS are inline) |
| `orderstrail.apk` | The Android app that both Download buttons serve. Published automatically (see below). |
| `apk-version.txt` | Version of the published APK, written by the build |
| `og-image.png` | 1200×630 preview image for WhatsApp, LinkedIn, X and other link previews |
| `CNAME` | Custom domain (orderstrail.in). Added by GitHub Pages; don't delete it |
| `privacy/`, `terms/`, `delete-account/` | Privacy Policy, Terms of Use and account-deletion page (linked from the app and the Play listing), styled by `legal.css` |
| `sitemap.xml` | Page list for search engines |
| `404.html` | "Page not found" page |
| `favicon.svg`, `apple-touch-icon.png` | Browser and home-screen icons |
| `robots.txt` | Lets search engines crawl the site |

## How the APK gets here

The app lives in the private repo `ektasi-et/orderstrail-app`. Its **Build APK**
workflow builds a signed release APK and publishes it here as `orderstrail.apk`
whenever the app version changes, or when the workflow is run by hand. See
`BUILD.md` in that repo.

The page checks for `orderstrail.apk` when it loads:

- **File missing:** both buttons show "coming soon" and can't be clicked.
- **File present:** the buttons work, and the page shows the file's real size.

Phones save the download as `OrdersTrail.apk`.

**Size limits:** GitHub rejects files over 100 MB. The github.com web uploader only accepts files up to 25 MB, so push anything bigger with GitHub Desktop.

**Signing:** sign every release with the same release keystore. If the key changes, updates won't install over the old version.
