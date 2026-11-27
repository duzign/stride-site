# CLAUDE.md

Public marketing site for Stride: plain HTML and CSS, no build step (see `README.md`). The app itself lives in `~/projects/duzign/stride`.

## New app screenshots

Screenshots come from the screenshot tool in `~/projects/duzign/stride-tools/screenshots` (see its README). Add or change screens in its `shots.mjs` and the demo data in `data.mjs`, rather than capturing by hand.

1. **Backend**, from `~/projects/duzign/stride/backend`:
   `STRIDE_DB_URL=jdbc:postgresql://localhost:5432/stride_demo ./mvnw spring-boot:run -Dspring-boot.run.profiles=development,local-auth`
   The `development` profile on its own connects to the `stride` database, so always set `STRIDE_DB_URL` to `stride_demo` (Homebrew PostgreSQL 18, `localhost:5432`, role `stride`/`stride`). That database holds fictional demo data only. Don't add the `seed` profile, and never point it at production data (`stride_prod`). Run it in the background; it's ready when `http://localhost:8080/actuator/health` is UP.
2. **Frontend**, from `~/projects/duzign/stride/frontend`: `npm start` (background). It serves `http://localhost:4200` and proxies `/api` to the backend.
3. **Capture**, from the tool folder: `npm run build`, or `node shoot.mjs <name>...` for only some screens. It writes `img/name.webp` (light) and `img/name-dark.webp` (dark) at 780×1688. Reference them in `index.html` with `src="img/name.webp"` and `data-dark="img/name-dark.webp"`.
4. **Stop the backend and frontend** once the screenshots are taken: kill both processes (ports 8080 and 4200) and check that nothing is still listening.
