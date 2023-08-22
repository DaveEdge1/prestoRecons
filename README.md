[![DOI](https://zenodo.org/badge/665741281.svg)](https://zenodo.org/badge/latestdoi/665741281)


# Guide for contributors

This repo is intended to serve PReSto contributors. The parameter input standards for presto reconstructions (presto_input_standards) and an example (Holocene_DA_parameters.yml) live here. There are also containerization instructions (containerization_instructions.md) and you will find links to the repositories for two example reconstructions, including Dockerfiles.

## Step 1 - Formatting your input paramters
all parameters for your reconstruction will need to be applied by a single yaml file

the yaml file will need to conform to the standards outlined in presto_input_standards.md

completed examples can be found in the holocene_da or temp12kComposites folders as configs.yml

## Step 2 - Formatting your outputs
need to complete this section

## Step 3 - Containerizing your code
containerizing you code with Docker removes any concern of changing dependencies and variability across operating systems

* if you do not have Docker on your local machine, you will first need to download and install it: [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* gather all files necessary for your reconstruction in one place (remember, data should be pulled from a repository when the container is run, so it will not be included here)
* write a Dockerfile
*   see an example in R here:
*   see an example in Python here:
* test your new container by building and running it locally
* after debugging, push this directory to GitHub  

If you use PReSto, please cite it as:

Dave Edge, Michael Erb, Nicholas McKay, Feng Zhu, Deborah Khider, Julien Emile-Geay, & Cody Routson. (2023). The Paleoclimate Reconstruction Storehouse (PReSto) platform (alpha-release). Zenodo. https://doi.org/10.5281/zenodo.8274756
