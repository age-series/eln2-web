# eln2-web

This is the eln2 website, hosted at [eln2.org](https://eln2.org)

PR's accepted ONLY for the `master` repository. Don't propose changes to `gh-pages`.

# Development

All the webpages are located in the `docs` folder.

The page navigation bar config is located in `mkdocs.yml` under `nav:`

You will need to have mkdocs and mkdocs-bootswatch installed:

```
pip install mkdocs mkdocs-bootswatch
```

# Testing

This allows you to test the website in a browser (live)

```bash
mkdocs serve
```

Then go to [127.0.0.1:8000](http://127.0.0.1:8000/) in your favorite browser.

# Deploying

Run these two:

```bash
mkdocs build
mkdocs gh-pages
```
