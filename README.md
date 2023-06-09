# SmartScope Docs

This is the official repository for the SmartScope documentation website. To contribute to the documentation and be able to use the development server, you must first install a few dependencies.

The docs website is generated with: 

* [mkdocs](https://www.mkdocs.org/)
* [mkdocs-material](https://squidfunk.github.io/mkdocs-material/)

## Setup with Anaconda/Miniconda

```shell-session
conda create -n Smartscope-docs python==3.10

conda activate SmartScope-docs
git clone 
cd SmartScope-docs
pip install -r requirements.txt
```

## Start the dev server

The dev server allows to vizualize the changes locally.
```shell-session
cd SmartScope-docs
mkdocs serve
```
