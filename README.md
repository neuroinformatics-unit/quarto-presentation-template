# quarto-presentation-template

To use this template
* install [Quarto](https://quarto.org/docs/get-started/)
* install the [VS Code Quarto extension](https://quarto.org/docs/get-started/hello/vscode.html)
* Create a conda environment with `conda create -n quarto python=3.11`
* Activate the environment with `conda activate quarto`
* `pip install -r requirements.txt`
* If you have additional requirements for you execution environment (e.g. your Python package) add them to `requirements.txt`
* Edit the `index.qmd` file to your liking, using the example slides as a guide.

To build the presentation locally, you can eiter:
* Use the VS Code extension's GUI ("Render" button)
* Use the commandline:
  * `quarto render index.qmd --to revealjs` for reveal.js slides
  * `quarto render index.qmd --to html` for a standalone HTML page with embedded resources.

To deploy the presentation on GitHub Pages:
* Make a new release on GitHub, tagged with a version number. Include some information on the date, location, event, etc. in the release notes.
* GitHub actions will take care of the rest (see example deployment [here](https://neuroinformatics-unit.github.io/quarto-presentation-template/#/title-slide))