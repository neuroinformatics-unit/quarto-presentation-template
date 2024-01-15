# quarto-presentation-template

## Prerequisites

You only need to do these once locally. 
* Install [Quarto](https://quarto.org/docs/get-started/)
* Install the [VS Code Quarto extension](https://quarto.org/docs/get-started/hello/vscode.html)

## Create a new presentation

* Click on "Use this template" -> "Create a new repository"
* Choose a repository name that starts with `slides-` (this should help us spot quarto presentation repositories at a glance, especially important if they proliferate)
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
For the first deployment:
* Create an empty `gh-pages` branch:
  ```sh
  git checkout --orphan gh-pages
  git reset --hard
  git commit --allow-empty -m "fresh and empty gh-pages branch"
  git push origin gh-pages
  ```
* Review the repository Settings/Pages to ensure that deployment is enabled from the `gh-pages` branch.
* Make the first release on GitHub, tagged with a version number (see below for versioning schemes).

For all subsequent deployments:
* Simply make a new release tagged with the appropriate version number. For presentations, we prefer a date-based versioning scheme, e.g. `YY.MM` or `YY.MM.DD`. You are encouraged to include some additional information on location, event, etc. in the release notes. If the release is a work-in-progress, append `dev` to the version tag (`YY.MM.dev`) and tick the "Set as a pre-release" checkbox.
* GitHub actions will take care of the rest (see example deployment [here](https://neuroinformatics-unit.github.io/quarto-presentation-template/#/title-slide))
* Deployed presentations can be found at `https://{USER}.github.io/{REPOSITORY-NAME}/#/title-slide`. For repositories of the neuroinformatics-unit organisation, this redirects to `https://neuroinformatics.dev/{REPOSITORY-NAME}/#/title-slide`
