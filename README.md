# Carine Ishimwe's website

This repository contains my personal Quarto website and DSCI 521 posts.
It includes computational analyses written in R and Python.

## Prerequisites

Install these tools before building. Versions used during development:

- Quarto 1.10.18
- uv 0.12.5
- R 4.6.1
- Git

Python 3.14 is selected by `.python-version`; development used Python 3.14.7.
uv installs the required Python version if it is unavailable.
The committed `.Rprofile` bootstraps renv.

## Build from a fresh clone

Run these commands in a terminal.
Choose a location where a folder named `milestone3-site` does not already exist.

```bash
git clone https://github.com/Carine-Ishimwe2025/carine-ishimwe2025.github.io.git milestone3-site
cd milestone3-site
uv sync --locked
Rscript -e 'renv::restore(prompt = FALSE)'
uv run quarto render
```

Run all environment and render commands from the repository root,
where `_quarto.yml` and `.Rprofile` are located.
The `Rscript` command runs R code from the terminal.

The completed website is written to `docs/`.

## View locally

After building, run from the repository root:

```bash
uv run python -m http.server 8000 --directory docs
```

Open <http://localhost:8000> in a browser.
Press Control+C in the terminal to stop the server.

## Data and network requirements

Both computational posts use the
[Palmer Penguins dataset](https://allisonhorst.github.io/palmerpenguins/),
provided under CC0.
The posts include attribution and a dataset reference.

The R and Python palmerpenguins packages include the data.
No separate data download, login, API key, or token is required at render time.
Internet access is needed initially to clone the repository, install tools,
bootstrap renv, and restore packages.

## Reproducible environments

Python dependencies are declared in `pyproject.toml` and locked in `uv.lock`.
R dependencies are recorded in `renv.lock`.
Commit these files and the environment activation files.
Installed libraries in `.venv/` and `renv/library/` are excluded from Git.

## Publishing

GitHub Pages serves the rendered files in `docs/`.
After editing, render from the repository root and commit the updated
source files and rendered website.
Keep `docs/.nojekyll` in the repository.

## AI assistance

I used OpenAI ChatGPT as a Socratic tutor through questions,
predictions, explanations, and feedback.
Each computational post also acknowledges AI assistance.