# Portfolio

Source for my personal site: research on ML evaluation and robustness, publications, and shipped code.

**Live:** https://rickygole.github.io/portfolio/

Static HTML and CSS in a single file. No build step, no dependencies, no framework.
GitHub Pages serves `index.html` directly.

## Structure

```
index.html                  the entire site (markup + styles inline)
assets/Ricky_Gole_CV.pdf    CV, linked from the header
.nojekyll                   tells Pages to skip Jekyll processing
```

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying

Pushing to `main` publishes automatically once Pages is enabled
(Settings, Pages, Source: `main` / root).

## Maintenance

Publication statuses are dated on the page ("current as of ..."). Update them when
decisions land, and refresh that date. A stale "under review" label on a venue whose
decisions are already out is worse than no label.
