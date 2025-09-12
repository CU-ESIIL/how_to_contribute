# Creating a GitHub Pages website from this repo
This is a base repository that has all the files necessary for building a GitHub Pages site. GitHub Pages render Markdown ``.md`` files that you will provide as the content for the website. The MkDocs package is used as the framework that builds the overall website. The entire site is configured with a single `mkdocs.yml` file.

## Forking
 In order to build your GitHub Pages site from here you must first fork this repository and create your own repository. When you are creating the fork, make sure you are selecting the correct owner. If you want this to be a CU-ESIIL owned site, for example, make sure to make CU-ESIIL the owner instead of your personal GitHub account.

## Updating necessary files
There are several files that you will need to update with your site's information. Each of the lines that need changing are marked with a TODO comment, which makes it easy to search each file for lines that need changing.

**If you would like to see a working example of each of the files for an active GitHub pages site, go to https://github.com/CU-ESIIL/data-library**

### mkdocs.yml
This is the configuration file that MkDocs uses to build your site. In it there are several lines that you need to change in order to get your site to build correctly. Each of these lines is commented out and includes a TODO:. Search for 'TODO:' within the file, and update the line according to the comment.

### .github/workflows/gh-pages.yml
This file is what is executed by GitHub once you push changes to the main branch. It sets up the runtime and tells MkDocs to start building the site. This file should not require any real changes, just that you uncomment the code under the TODO.

### .gitignore
MkDocs generates the finished site in a local `site/` directory. Add `site/` to your `.gitignore` so these build artifacts are not committed to version control.

### docs/
This folder is where you will add Markdown files for each section of your site's pages. There should be a folder for each section and a subfolder for each subsection. For example you may have `education/non-profits/non-profits.md` and `education/nces/nces.md` files.

### docs/index.md
By convention this is the Markdown file for your site's home page. Customize it however you would like.

### docs/ESIIL_logo.png
This is used as the site logo in the `mkdocs.yml` file. If you would like to use a different logo, add a new `.png` file to the `docs` folder and update the `theme: logo` line in the `mkdocs.yml` file.

### docs/favicon.ico
This is the site's favicon. If you would like to use a different one, add a new `favicon.ico` file to `docs/` that replaces the existing one.
