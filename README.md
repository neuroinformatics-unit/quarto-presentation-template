# quarto-presentation-template

## Prerequisites

You only need to do these once locally. 
* Install [Quarto](https://quarto.org/docs/get-started/)
* Install the [VS Code Quarto extension](https://quarto.org/docs/get-started/hello/vscode.html)

## Create a new presentation

* Click on "Use this template" -> "Create a new repository"
* Choose a repository name that ends with `-slides` (this should help as spot quarto presentation repositories at a glance, especially important if they proliferate)
* Clone the newly created repository and navigate to its root folder
* Create a conda environment with `conda create -n quarto python=3.11`
* Activate the environment with `conda activate quarto`
* `pip install -r requirements.txt`
* If you have additional requirements for your execution environment (e.g. your Python package) add them to `requirements.txt`
* Edit the `index.qmd` file to your liking, using the example slides as a guide.

## Build the presentation locally

You can either:
* Use the VS Code extension's GUI ("Render" button)
* Use the command line:
  * `quarto render index.qmd --to revealjs` for reveal.js slides
  * `quarto render index.qmd --to html` for a standalone HTML page with embedded resources.

## Deploy the presentation on GitHub Pages
* Make a new release on GitHub, tagged with a version number. Include some information on the date, location, event, etc. in the release notes.
* GitHub actions will take care of the rest (see example deployment [here](https://neuroinformatics-unit.github.io/quarto-presentation-template/#/title-slide))
