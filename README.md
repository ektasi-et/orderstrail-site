# OrdersTrail website

Landing page for **OrdersTrail**, the order book for home bakers (Android app).
It's a plain static site: no build step, no framework.

| File | What it is |
| --- | --- |
| `index.html` | The whole landing page (CSS and JS are inline) |
| `orderstrail.apk` | The Android app that both Download buttons serve. **Not added yet.** |
| `404.html` | "Page not found" page |
| `favicon.svg`, `apple-touch-icon.png` | Browser and home-screen icons |
| `robots.txt` | Lets search engines crawl the site |

## Adding or updating the APK

1. Build the release APK from the Flutter project:

   ```
   flutter build apk --release --dart-define=SUPABASE_URL=https://<project>.supabase.co --dart-define=SUPABASE_ANON_KEY=<anon-key>
   ```

2. Copy `build/app/outputs/flutter-apk/app-release.apk` to the root of this repo and rename it to **`orderstrail.apk`**. If an old one is there, replace it.
3. Commit and push.

The page checks for `orderstrail.apk` when it loads:

- **File missing:** both buttons show "coming soon" and can't be clicked.
- **File present:** the buttons work, and the page shows the file's real size.

You don't need to edit the HTML either way. Phones save the download as `OrdersTrail.apk`.

**Size limits:** GitHub rejects files over 100 MB. The github.com web uploader only accepts files up to 25 MB, so push anything bigger with GitHub Desktop.

**Signing:** sign every release with the same release keystore. If the key changes, updates won't install over the old version.
