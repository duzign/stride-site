# CLAUDE.md

Public marketing site for Stride: plain HTML and CSS, no build step (see `README.md`). The app itself lives in `~/projects/duzign/stride`.

## New app screenshots

Never make screenshots by hand. Use the tool in the app repo, which gives the same result every run:

```bash
~/projects/duzign/stride/tools/site-screenshots/run.sh              # all shots
~/projects/duzign/stride/tools/site-screenshots/run.sh paspoort     # only these
```

It restores a fixed demo database (`fixture.sql`, fictional data) into `stride_screenshots`, starts backend and frontend, captures every shot in mobile portrait (390×844 at 2×) in light and dark, writes `img/<name>.webp` and `img/<name>-dark.webp`, then stops backend and frontend again. Ports 8080, 4200 and 443 must be free, so stop a running backend/frontend first.

- A new screen: add it to `SHOTS` in `shoot.mjs`, then reference it in `index.html` with `src="img/name.webp"` and `data-dark="img/name-dark.webp"`.
- Different data: change `fixture.sql` as described in the tool's `README.md`. Never use production data.
- The tool lives in the private app repo on purpose: this repo is public and GitHub Pages serves every file in it.
