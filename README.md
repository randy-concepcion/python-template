[![Python 3.12.0](https://img.shields.io/badge/python-3.12.0-blue.svg)](https://www.python.org/downloads/release/python-3120/) [![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

# python-template
This repo is a template for Python applications

## How-to
### Python Virtual Environment

* `pyenv update`
* `pyenv install <python version number>`
* `pyenv virtualenv <python version number> <virtual environment name>`
* `pyenv activate <virtual environment name>`
* `pyenv deactivate`
* `pyenv local <python version number>/envs/<virtual environment name>` to create `.python-version`
* Use `.python-version` containing your virtual environment name to automatically load your python virtual environment

### Poetry

* Install packages from `pyproject.toml`: `poetry install --no-root`
* Add new packages: `poetry add <python package>`
  * Use `--group dev` config to add to dev group
* Update to latest packages: `poetry update`

### SonarCloud

* Uncomment `sonar-project.properties`
* Adjust config values for your repo
* Make sure `SONAR_TOKEN` environment variable is set
* Make sure `docker-compose.yaml` file contains the correct paths to the code
  * Run sonar-scanner docker image locally: `docker-compose run sonar-scanner-cloud`
* The `./bin/sonar` script will run the `sonar-scanner` tool locally

### pre-commit config

* Install pre-commit hooks: `pre-commit install --hook-type pre-commit --hook-type pre-push`
* Make any updates to `.pre-commit-config.yaml`
  * Make sure the `INSTALL_PYTHON` variable is correct which contains the path to your python virtual environment
  * Run `pre-commit autoupdate` to update all the package library versions

### pytest

* Update `bin/test` for running tests and report generation
  * Especially the workaround for resolving report paths for sonar-scanner docker image
* Alternatively, run reports manually
  * HTML report: `pytest -v --cov=. --cov-branch --cov-report html ./tests`
  * XML report (for SonarCloud): `pytest -v cov=. --cov-branch=xml:coverage/coverage.xml ./tests`
* If no unit tests are found, _pytest_ will return an exit code status of `5`
  * Use `--no-verify` if pushing changes and we have no unit tests to run yet

### Dependabot

* Make sure paths in `.github/dependabot.yml` are correct
* Check config in repo settings

### Github Workflow

* Update `.github/workflows/build.yaml` as needed
* You can also disable the workflow in the Actions tab
