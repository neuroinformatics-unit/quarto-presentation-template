# quarto-presentation-template

## Prerequisites

You only need to do these once locally. 
* Install [Quarto](https://quarto.org/docs/get-started/)
* Install the [VS Code Quarto extension](https://quarto.org/docs/get-started/hello/vscode.html)
* Install [uv](https://docs.astral.sh/uv/) to manage your Python environments (recommended if you want to execute code in your presentation)

## Create a new presentation

### Step 1: Create a new repository from this template
* Click on "Use this template" -> "Create a new repository"
* Choose a repository name that starts with `slides-` (this should help us spot quarto presentation repositories at a glance, especially important if they proliferate)
* Clone the newly created repository and navigate to its root folder

### Step 2: Set up your Python environment

> [!note]
> You can skip this step if you don't require any code execution in your presentation.

If you have additional requirements for your execution environment (e.g. your Python package) append them to `requirements.txt`.

We recommend using [uv](https://uv.sh/) to manage your Python environment:
* Create a new environment with `uv venv --python=3.13`. Make sure the Python version matches the one used in your GitHub Actions workflow.
* Activate the environment with `source .venv/bin/activate` 
* Install the required packages with `uv pip install -r requirements.txt`

> [!warning]
> Make sure Quarto is using the correct Python environment 
> by setting the `QUARTO_PYTHON` environment variable.
> 
> An easy way to do this once you have activated the environment is:
> ```sh
> export QUARTO_PYTHON=$(which python)
> ```

### Step 3: Edit and preview the presentation

* Edit the `index.qmd` file to your liking, using the example slides as a guide. Additional images should be placed in the `img/` folder whereas references should be added to the `references.bib` file in BibTeX format.
* To build the presentation locally, you can either use the VS Code extension's GUI ("Render" button) or run `quarto render index.qmd` in the terminal.
* The rendered presentation will be available as `build/index.html` in the root folder. Note that the `build/` folder is included in `.gitignore` to avoid committing generated files to the repository.

> [!tip]
> If you want to preview the rendered slides as you're editing them, you can type `quarto preview index.qmd` in the terminal.

### Step 4: Deploy the presentation on GitHub Pages

For the first deployment:

* Create an empty `gh-pages` branch:
  ```sh
  git checkout --orphan gh-pages
  git reset --hard # make sure all changes are committed before running this!
  git commit --allow-empty -m "Initialising gh-pages branch"
  git push origin gh-pages
  ```
* Review the repository Settings/Pages to ensure that deployment is enabled from the `gh-pages` branch.
* Make the first release on GitHub, tagged with a version number (see below for versioning schemes).

For all subsequent deployments:
* Simply make a new release tagged with the appropriate version number. For presentations, we prefer a date-based versioning scheme, e.g. `YY.MM` or `YY.MM.DD`. You are encouraged to include some additional information on location, event, etc. in the release notes. If the release is a work-in-progress, append `dev` to the version tag (`YY.MM.dev`) and tick the "Set as a pre-release" checkbox.
* GitHub actions will take care of the rest (see example deployment [here](https://neuroinformatics-unit.github.io/quarto-presentation-template/#/title-slide))
* Deployed presentations can be found at `https://{USER}.github.io/{REPOSITORY-NAME}/#/title-slide`. For repositories of the neuroinformatics-unit organisation, this redirects to `https://neuroinformatics.dev/{REPOSITORY-NAME}/#/title-slide`
