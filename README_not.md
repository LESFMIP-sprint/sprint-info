# CANARI Sprint DOCUMENTATION
This project represents the documentation for the CANARI Sprint.


## Information about MkDocs

This docmentation was assembled based on the mkdocs package.

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

## Edting the easy way

You can edit this page directly on github. Click on the file you want to edit and then click on the pencil icon in the top right corner. Make the changes you need to make and click on the green "Commit Changes" button near the top right of the screen. Your changes will then automatically update on the webpage, but this can take a couple of minutes to appear. 

## Editing the hard way

If you want to do more complex edits or test the rendered web page on your computer before it is pushed then you can install and run mkdocs on your computer.

### Installating mkdocs

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


### Running the Server Locally

If the configuration was done correctly, you can run the following command to launch the documentation:

```bash
mkdocs serve
```

This will run the app in development mode. Open [http://localhost:8000](http://localhost:8000) in your browser to access it. The page will automatically reload when you make edits.

### Deploy on gh-pages

Project Pages sites are simpler as the site files get deployed to a branch within the project repository (gh-pages by default). After you checkout the primary working branch (usually master) of the git repository where you maintain the source documentation for your project, run the following command:

```bash
mkdocs gh-deploy
```

That's it! Behind the scenes, MkDocs will build your docs and use the ghp-import tool to commit them to the gh-pages branch and push the gh-pages branch to GitHub.

Use `mkdocs gh-deploy --help` to get a full list of options available for the gh-deploy command.

Be aware that you will not be able to review the built site before it is pushed to GitHub. Therefore, you may want to verify any changes you make to the docs beforehand by using the build or serve commands and reviewing the built files locally.

### Running the Server as a Docker Compose

First, build the Docker Compose:

```bash
docker build mkdocs .
```

Now, start the containers:

```bash
docker run -d -p 8084:8000 --rm mkdocs
```

This will run the app in development mode. Open [http://localhost:8084](http://localhost:8084) in your browser to access it.
