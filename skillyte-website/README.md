# skillyte-website

Marketing site and store-compliance pages for **Skillyte**, a learning app with skill development programs for under-privileged young people in rural India, taught in regional Indian languages.

Plain static HTML and CSS. There is no build step and no dependencies. Fonts load from Google Fonts.

## Pages

| File | Purpose | Suggested live URL |
|---|---|---|
| `index.html` | Home page | `/` |
| `support.html` | Support URL for Google Play and the App Store | `/support` |
| `privacy-policy.html` | Privacy Policy URL for Google Play and the App Store | `/privacy-policy` |
| `delete-account.html` | Account deletion URL (Google Play Data safety form) | `/delete-account` |

Internal links use `.html` file names so the site works on any static host. Most hosts (GitHub Pages, Netlify, Vercel, Cloudflare Pages) also serve `/support` for `support.html`.

## Android APK download

The home page has an Android download section (`#android-apk`). The APK itself is hosted outside the repo (it is over GitHub's 100 MB file limit) and lives in Amazon S3. See `docs/apk-hosting.md` for how to publish a new version and keep the page details in sync.

## Brand

- Purple `#481172`, gold `#DFB73F`, cream `#FBF7EE`
- Typeface: Figtree (Noto Sans for Indian scripts)
- Logo files: `assets/brand/` (SVG recreations; swap in the official vector files when available)
- Favicon: `assets/favicon.svg`

## Before going live

All unfinished content is in `[square brackets]`. Search the HTML files for `[` to find it. Main items:

- Privacy Policy dates, retention periods and the final service-provider list
- In-app menu names in the delete-account steps and the support FAQ
- Final list of languages (home page)
- Real Google Play and App Store links (those two buttons on the home page currently point back to the page)
- Check the Download APK link works for signed-out visitors, and that only the APK (not the whole production bucket) is public; see `docs/apk-hosting.md`

The privacy policy is a draft and needs legal review before it is published.

## Known gaps

- The "Request deletion" form on `delete-account.html` is not connected to a backend yet. Wire it up, or rely on the email option on that page.
- The Support, Privacy Policy and Delete Account URLs must be reachable without signing in, because Google Play and the App Store check them.
