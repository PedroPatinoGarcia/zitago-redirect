# zitago-redirect

Sends `zitago.es` and `www.zitago.es` to `https://app.zitago.es`, keeping the path.

Served by GitHub Pages, which gives the custom domain a free HTTPS certificate.
`404.html` is a copy of `index.html` so that any path also redirects.
Pages can't send a real 301, so the redirect is done with JavaScript, with a
meta refresh to the home page as fallback.

DNS and setup steps: `docs/despliegue-render.md` in the main repository.
