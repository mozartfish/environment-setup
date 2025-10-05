# environment-setup

## Overview
This repo containts a conda and uv environment setup for machine learning and python engineering projects. I use the conda setup for my coursework at KTH but after learning about [uv](https://docs.astral.sh/uv/) and [marimo](https://marimo.io/) I am migrating toward using a uv based setup for personal projects.

If you are interested in supporting `oss` and `science`, please [read this](https://www.theregister.com/2024/08/08/anaconda_puts_the_squeeze_on/) and consider switching to `uv` if your work and teams allow for it. 

**Special Thanks**: [Jakob Johnson](https://jakobj.dev/), [Ryan Stutsman](https://rstutsman.github.io/), [Matthew Flatt](https://users.cs.utah.edu/~mflatt/), [Varun Shankar](https://users.cs.utah.edu/~shankar/), [Jeff Phillips](), [Travis Oliphant](https://www.nature.com/articles/d41586-025-02903-1), [Marimo Development Team](https://marimo.io/) for sharing all their knowledge about how systems work, development tools and how to setup workflows and environments for data projects. 

## Why this project 
[Google Colab](https://colab.research.google.com/) is a fantastic tool for prototyping and teaching but it abstracts all installation which becomes a problem when your assignments and projects require specific versions that are no exactly backward compatible with colab. This project seeks to provide a way for running and developing data and python projects locally.

## Notes 
1. `If you are doing deep learning` - use the python version that is supported by pytorch and torchvision. Currently this is `python 3.11`. If you don't have this installed locally or cannot install it due to work requirements I strongly recommend using the `uv setup` since it's easier than dealing with pyenv.  

2. `Setting up pyenv` - My friend Jakob Johnson wrote this fantastic article [Python Management with Pyenv](https://jakobj.dev/posts/pyenv/) for setting up and managing python versions with pyenv.  If you follow the `conda setup` read this article for before following the installation steps. 

## Conda 
1. Install [miniconda](https://www.anaconda.com/docs/getting-started/miniconda/main)
2. **Create environment** - `conda env create -f workbench.yaml` 
3. **Activate environment** - `conda activate workbench`
4. **Update packages** - `conda updatge --all`
5. **Clean up packages** - `conda clean --all`
6. **Uninstall environment** - `conda remove --name workbench --all`

## UV 
1. Install [uv](https://docs.astral.sh/uv/)
### new projects 
2. Inside your project directory **run** - `uv python pin 3.11`
3. **Run** `uv init` 
4. Add python packages you need using `uv add[package-name]`. To separate development and production dependencies use `uv add --dev [package-name]` to make it easier for people to understand wht packages are for development and what is for production. I usually add tools like `pytest, ruff, marimo, ipython, jupyter-lab` for dev because they are more for engineering and data exploration. 
5. **Run** `cat pyproject.toml` to ensure you have installed the packages you need. 
6. **Run** `uv sync`
7. **Run** `uv lock`
8. **Run** `uv run main.py` to ensure the environment is set up correctly. The main.py file will be the driver file for your project. 
8. **Now you are set up for development!**

### ml-environment-setup 
If you want to start with my default setup you can use my **ml-environment-setup** and rename it - but still run the following steps for making sure the packages meet your needs. 

2. Inside the ml-environment-setup directory **run** - `uv lock --upgrade` to ensure all the packages are up to date. 
3. **Run** `uv sync` to ensure all packages are synced followed by `uv lock` to freeze the versions to work with your project. 
4. **Run** `uv run main.py` to ensure the environment is set up correctly. After running this **run** `uv run marimo edit notebook.py` which will open the marimo notebook. 
5. **Run** the marimo notebook cells to make sure all the packages are installed properly followed by the gpu cell. The gpu cell is really important for developing deep learning and machine learning models and knowing what device you are using for training your models. 
6. **Now you are set up for development!**  