# ACA-Py Plugins Documentation

The documentation site for the ACA-Py plugins can be found at: [https://hyperledger.github.io/aries-acapy-plugins](https://hyperledger.github.io/aries-acapy-plugins).

## Managing the Documentation Site

The documentation site is sourced from this repo and generated by the `publish-docs` GitHub Action. That action:

- Checkouts out the repo at `main`
- Installs [Mkdocs Material]
- Runs the script in the repo `setupDocs.sh`, which
    - Creates the `docs` folder
    - Populates the `docs` with all of the root level Markdown files
    - Creates a folder for each plugin and copies it's `README.md`
    - Generates a complete `mkdocs.yml` file with navigation
- Runs the `mkdocs` `mike` extension to generate the site to thwe `gh-pages` branch for deployment with GitHub pages

[Mkdocs Material]: https://squidfunk.github.io/mkdocs-material/

If you want to change how the doc site looks, edit the `setupDocs.sh` file and
the `mkdocs.yml` portion of the script for both look and feel and navigation.
Most of the script is just redirect plain text into the `mkdocs.yml` file,
although there is a little bash script to, for example, generate the navigation
for all of the plugins. If you want to edit the content displayed on the site,
edit the markdown files in this repo.

## Testing the Documentation Site

To test the documentation site locally, follow the instructions on the [Mkdocs
Material] to install `mkdocs` locally and run it.  When you are ready, run:

```bash
./setupDocs.sh
mkdocs
```

You should have the site up at `http://localhost:8000/`.

The `/docs` folder and `mkdocs.yml` file are `.gitignore`d in this repo, but if
you want to get rid of them, you can use the following to clean them up.

```bash
./setupDocs.sh clean
```