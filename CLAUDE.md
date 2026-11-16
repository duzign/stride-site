# CLAUDE.md

Public marketing site for Stride: plain HTML and CSS, no build step (see `README.md`). The app itself lives in `~/projects/duzign/stride`.

## New app screenshots

When the site needs new or updated screenshots of the app, run the app locally and capture them yourself:

1. **Backend**, from `~/projects/duzign/stride/backend`:
   `./mvnw spring-boot:run -Dspring-boot.run.profiles=development,local-auth`
   The `development` profile connects to the `stride_demo` database (Homebrew PostgreSQL 18, `localhost:5432`, role `stride`/`stride`), which holds fictional demo data only. Don't add the `seed` profile and never point it at production data. Run it in the background; ready when `http://localhost:8080/actuator/health` is UP.
2. **Frontend**, from `~/projects/duzign/stride/frontend`: `npm start` (background), serves `http://localhost:4200` and proxies `/api` to the backend.
3. **Capture** in mobile portrait: viewport 390×844 at device scale factor 2 (files are 780×1688), in **both light and dark mode**. Switch theme with `localStorage.setItem('stride-theme', 'light' | 'dark')` and reload (or emulate `prefers-color-scheme`).
   - Browser: drive the installed Firefox (`/Applications/Firefox.app`) headless with `puppeteer-core` (`browser: 'firefox'`, install with `PUPPETEER_SKIP_DOWNLOAD=1` in the scratchpad). There's no Chrome, and Playwright's Chromium download stalls. Wait for `load` plus a few seconds, not `networkidle` (the dev server's live-reload socket never settles), and inject `*{scrollbar-width:none}` before each shot.
   - Links in the app (passport share sheet) use `location.origin`. To show `https://dijc.strideapp.nl/...` instead of `localhost:4200`, run a small HTTPS proxy on 443 (self-signed cert) to `localhost:4200` with `Host: localhost:4200`, and launch Firefox with `acceptInsecureCerts: true` and pref `network.dns.localDomains: 'dijc.strideapp.nl'`.
   - Demo data can be shaped through the API (local-auth needs no token), e.g. passport consent/links (`PUT /api/passports/{id}/consent`, `PUT …/link`) or ratings (`POST /api/ratings`; the daily limit is off in development).
4. **Save** as WebP in `img/`: `name.webp` (light) and `name-dark.webp` (dark); reference in `index.html` with `src="img/name.webp"` and `data-dark="img/name-dark.webp"`.
5. **Stop backend and frontend** once the screenshots are taken: kill both processes (ports 8080 and 4200) and check that nothing is still listening.
