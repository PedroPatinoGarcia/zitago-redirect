# zitago-redirect

The site at `zitago.es` and `www.zitago.es`, served by GitHub Pages, which gives
the custom domain a free HTTPS certificate. GitHub sends `www` to `zitago.es`.

- `index.html` is a static landing page: what ZitaGo is, a button to the app and
  links to the privacy policy, the terms and the legal notice. It is the brand's
  home page in Google Auth Platform, which needs a page it can read without
  JavaScript (`app.zitago.es` is a single-page app). No scripts, no cookies, no
  third parties: a `Content-Security-Policy` meta tag keeps it that way.
- `404.html` sends every other path to `https://app.zitago.es`, keeping the path
  (`zitago.es/privacidad` → `app.zitago.es/privacidad`). Pages can't send a real
  301, so it redirects with JavaScript, with a meta refresh to the app's home
  page as fallback.
- `fonts/` holds Inter 400, 600 and 700, subset to Latin and converted to WOFF2
  (licence in `fonts/OFL.txt`). Colours and type follow `mobile/src/theme.ts`
  in the main repository. To rebuild a weight, from the main repository's
  `mobile/` with `pip install fonttools brotli`:

  ```bash
  pyftsubset node_modules/@expo-google-fonts/inter/700Bold/Inter_700Bold.ttf \
    --unicodes="U+0000-00FF,U+0131,U+0152-0153,U+02C6,U+02DA,U+02DC,U+2013-2014,U+2018-201A,U+201C-201E,U+2022,U+2026,U+2030,U+2039-203A,U+20AC,U+2122,U+2190-2193,U+2212" \
    --layout-features="kern,liga,calt,tnum,case" --flavor=woff2 --no-hinting --desubroutinize \
    --output-file=../../zitago-redirect/fonts/inter-700.woff2
  ```

- `favicon.svg`, `favicon.png`, `apple-touch-icon.png` and `og-image.png` are
  copies of `mobile/assets/brand/zitago-icon.svg`, `mobile/assets/images/favicon.png`,
  `mobile/store/icon-512.png` and `mobile/store/feature-graphic-1024x500.png`
  (made by `node scripts/brand-assets.mjs` in the main repository).

Preview locally with `npx serve .` and open `http://localhost:3000`.

DNS and setup steps: `docs/despliegue-render.md` in the main repository.
