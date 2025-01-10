# CANARI Sprint DOCUMENTATION
====================

This project represents the documentation for the CANARI Sprint.

It was assembled based on the mkdocs package.

## Installation

1. Create a Python 3 virtual environment and activate it:

   ```bash
   pyenv virtualenv imfe-documentation
   ```

2. Clone the project and install it:

   ```bash
   git clone git@github.com:CANARI-sprint/docs.git
   cd docs
   pip install -r requirements.txt
   ```

## Information about MkDocs

The central file of the documentation is `docs/index.md`.

All images should be stored in the `docs/assets` folder.

MkDocs uses Markdown language. Therefore, you can easily import your README files from GitHub/GitLab to include in the documentation.

In the `mkdocs.yml` file, you can define the main navigation bar of your project. For example, below, I am indicating that only `index.md` and `about.md` will be present in the navbar:

```yaml
nav:
  - 'index.md'
  - 'about.md'
```

If you do not include the `nav` option, all your .md files in the `docs` folder will be items in your navbar.

The titles in the navbar will be the same of the first tag `#` on your md files.

## Running the Server Locally

If the configuration was done correctly, you can run the following command to launch the documentation:

```bash
mkdocs serve
```

This will run the app in development mode. Open [http://localhost:8000](http://localhost:8000) in your browser to access it. The page will automatically reload when you make edits.

## Deploy on gh-pages

Project Pages sites are simpler as the site files get deployed to a branch within the project repository (gh-pages by default). After you checkout the primary working branch (usually master) of the git repository where you maintain the source documentation for your project, run the following command:

```bash
mkdocs gh-deploy
```

That's it! Behind the scenes, MkDocs will build your docs and use the ghp-import tool to commit them to the gh-pages branch and push the gh-pages branch to GitHub.

Use `mkdocs gh-deploy --help` to get a full list of options available for the gh-deploy command.

Be aware that you will not be able to review the built site before it is pushed to GitHub. Therefore, you may want to verify any changes you make to the docs beforehand by using the build or serve commands and reviewing the built files locally.

## Running the Server as a Docker Compose

First, build the Docker Compose:

```bash
docker build mkdocs .
```

Now, start the containers:

```bash
docker run -d -p 8084:8000 --rm mkdocs
```

This will run the app in development mode. Open [http://localhost:8084](http://localhost:8084) in your browser to access it.
