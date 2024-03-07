[![Python 3.12.0](https://img.shields.io/badge/python-3.12.0-blue.svg)](https://www.python.org/downloads/release/python-3120/) [![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

# python-template
This repo is a template for Python applications

## How-to
### Python Virtual Environment

* `pyenv update`
* `pyenv install <python version number>`
* `pyenv virtualenv <virtual environment name> <python version number>`
* `pyenv activate <virtual environment name>`
* `pyenv deactivate`
* Use `.python-version` containing your virtual environment name to automatically load your python virtual environment

### Poetry

* Install packages from `pyproject.toml`: `poetry install`
* Add new packages: `poetry add <python package>`
  * Use `--group dev` config to add to dev group
* Update to latest packages: `poetry update`

### SonarCloud

* Uncomment `sonar-project.properties`
* Adjust config values for your repo

### pre-commit config

* Make any updates to `.pre-commit-config.yaml`
* Install pre-commit hooks: `pre-commit install`

### pytest

* Update `bin/test` for running tests and report generation
  * Especially the workaround for resolving report paths for sonar-scanner docker image
* Alternatively, run reports manually
  * HTML report: pytest -v --cov=. --cov-branch --cov-report html ./tests
  * XML report (for SonarCloud): pytest -v cov=. --cov-branch=xml:coverage/coverage.xml ./tests
