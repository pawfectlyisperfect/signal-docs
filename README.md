# signal-docs

Documentation site for Signal, a Fabric mod for group/squad coordination in Minecraft.

Built with [MkDocs](https://www.mkdocs.org/) and the Material theme, deployed to GitHub Pages on every push to `main`.

## Local preview

```
pip install -r requirements.txt
mkdocs serve
```

Then open `http://127.0.0.1:8000`.

## Structure

Everything under `docs/` is a page, `mkdocs.yml` controls the nav and theme. Deployment is handled by `.github/workflows/deploy.yml`, no manual build step needed, just push to `main`.
