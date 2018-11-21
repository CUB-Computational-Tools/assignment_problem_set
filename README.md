# Problem Set Template

This repo contains problem set templates for R and python and the [binder](https://mybinder.readthedocs.io) settings to respectively run them in RStudio and Jupyter Lab (alghouth you *could* run both R and python in either IDE). Once ready for student usage, make sure to cleanup unused files and adjust the binder settings as described below.

## Cleanup

Generally, it is good to clean up the repo once ready for student usage by deleting unused files in the main and subdirectories. This also prevents your binder environment from installing more than is necessary. Key files to **keep** for R/python, respectively (keep both if you want to run both) in addition to your problem set notebook files:

### R
 - `binder/runtime.txt`
 - `binder/install.R`
 - `scripts/functions.R` (if any functions)

## Python
 - `binder/requirements.yml`
 - `binder/postBuild`
 - `scripts/functions.py` (if any functions)
 - `scripts/__init__.py` (if any functions)

## Binder Setup

Once ready for student use, make sure to modify the files in the `binder` sub-directory depending on which language the students should use for this problem set (`R` or `Python` or both). Binder will dockerize your repository the first time it is run with a new configuration but will re-use the docker image on subsequent launches. This means that the first time you launch binder for the latest version of your repo, it may take some time to launch but will be fast for everyone else aftewards. This means that you should always test-run your repository on binder before giving out the link to students. Switching between `RStudio` vs. `Jupyter Lab` as the IDE is done easily by changing the binder link as described below.

## R
 - modify the `binder/runtime.txt` file to specify which R date snapshot should be used (the [MRAN](https://mran.microsoft.com/documents/rro/reproducibility) network keeps a daily snapshot)
 - modify the `binder/install.R` file to make sure all dependencies are specified. Dependencies can be from CRAN, bioconductor or GitHub. Since GitHub hosted libraries are not part of the MRAN snapshot, it is best to specify a commit or release tag to ensure that a compatible version of the package is installed in the binder.

## Python

 - modify the `binder/requirements.yml` file to specify the dependencies. The file is a standard conda config file and thus supports conda packages as well as pip installations.
 - modify the `binder/postBuild` file for any JupyterLab extensions as well as an explicit `pip install` command for the dependencies in case you want to run `R` and `python` in the same binder (i.e. if you have a `binder/install.R` file present, in which case your `requirements.yml` will be ignored)

## Link

### RStudio

Modify the following link to launch your repo in an RStudio binder (`USER`, `REPO`, `BRANCH`): `http://beta.mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=rstudio`

> Example (for this repo): `http://beta.mybinder.org/v2/gh/2018-Computational-Tools/assignment_problem_set/master?urlpath=rstudio`

Modify the following markdown code to create a launch badge: `[![Binder](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=rstudio)`

> Example (click on it to launch binder for this repo): [![Binder](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/2018-Computational-Tools/assignment_problem_set/master?urlpath=rstudio)
 
### Jupyter Lab

Modify the following link to launch your repo in an RStudio binder (`USER`, `REPO`, `BRANCH`): `http://beta.mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=lab`

> Example (for this repo): `http://beta.mybinder.org/v2/gh/2018-Computational-Tools/assignment_problem_set/master?urlpath=lab`

Modify the following markdown code to create a launch badge: `[![Binder](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=lab)`

> Example (click on it to launch binder for this repo): [![Binder](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/2018-Computational-Tools/assignment_problem_set/master?urlpath=lab)