# Scout Docs
This repo contains the documentation for Wild Me's Scout. Documentation is published with every accepted PR.

## Planned changes
The documentation will eventually support:
- internationalization
- versioning

## Local Setup
1. Install the prereqs:
- install sphinx
- install [sphinx-book-theme](https://sphinx-book-theme.readthedocs.io/en/stable/tutorials/get-started.html): `pip install sphinx-book-theme`
- install [myst-parser](https://www.sphinx-doc.org/en/master/usage/markdown.html) (used by sphinx markdown extension): `pip install myst-parser`
2. Clone the `scout-docs` repo: `git clone https://github.com/WildMeOrg/scout-docs.git`

## Build locally
To build:
1. `cd` to the `docs` directory:
2. Run the following commands:
    ```
    python -m venv .venv
    source .venv/bin/activate
    make html
    ```
3. Files will be in `docs/_build/html/`

If you aren't seeing your changes, try `make clean html` to force a complete rebuild.

To see files as they will appear online, including url paths:
1. In a new terminal, `cd` to `docs/_build/html/`
2. `python -m SimpleHTTPServer` or `python3 -m http.server`
3. Open `http://localhost:8000` in your browser

## Contribute to docs
TBD