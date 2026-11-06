# Stride website

Public marketing site for [Stride](https://stride.duzign.nl), served by GitHub Pages from `main` (root). Plain HTML and CSS, no build step.

- Colours, radii and type follow the Stride design system (tokens in the app repo).
- Lexend is self-hosted (`fonts/`, SIL Open Font License 1.1), so the page makes no third-party requests.
- Custom domain: `CNAME`. DNS: `CNAME stride → duzign.github.io`.

Preview locally: `python3 -m http.server 8000`, then open http://localhost:8000.

Screenshots in `img/` come from a local Stride run against an empty database with fictional pupils, groups and trainer (never production data), in light (`name.webp`) and dark (`name-dark.webp`); the theme toggle swaps them.
