# My Scientific Computing and Publishing Setup

* Install [Brew](https://brew.sh) package manager for MacOS

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

* Remove old versions of Python

```bash
sudo rm -rf /Library/Frameworks/Python.framework
rm -rf ./Library/Python/
```

* Install fresh [Python 3](https://www.python.org/downloads/mac-osx/) and upgrade `pip`

```bash
python3 -m pip install --upgrade pip
```

* Install univeral Python 3 packages

```bash
python3 -m pip install --upgrade ipython jupyterlab ipywidgets nbconvert ipykernel autopep8 black yapf isort pipreqs pylint python-language-server[all] genson pipreqs cookiecutter python-dotenv sphinx sphinx-autobuild jsonmerge jupytext pandoc-eqnos pandoc-fignos pandoc-tabnos
```

* Install [pandoc](https://pandoc.org/installing.html) and related useful stuff

```bash
brew update
brew install pandoc-citeproc
brew install pandoc-crossref
brew install librsvg
```

* Install [Node.js](https://nodejs.org/en/) and NPM

```bash
brew install node
```

* Install [MathJax](https://www.mathjax.org)

```bash
npm install -g mathjax-node
npm install -g mathjax-node-cli
npm install -g mathjax-pandoc-filter
```

* Make virtual environment for scipy

```bash
python3 -m venv --system-site-packages ./venv/scipy
source venv/scipy/bin/activate
```

* Install scientific packages into the virtual environment

```bash
python3 -m pip install --upgrade scikit-learn scikit-image matplotlib sympy pandas xarray cython tensorly pymc3 nose numexpr Pillow h5py netCDF4 cfunits wpca keras tensorflow pydot statsmodels constrNMPy spectral seaborn dask ipympl pyro-ppl torch torchvision pweave
```

* Inspect currently-installed packages

```bash
pip freeze > requirements.txt
```

* Need to install the atmos python package manually and it depends on udunits2

```bash
brew install udunits
git clone https://github.com/atmos-python/atmos.git

```

* Install graphviz -- a dependency for Keras

```bash
brew install graphviz
```

* For Markdown to HTML with LaTeX maths

```bash
git clone https://github.com/humenda/GladTeX.git; cd GladTeX; python setup.py install
```

* Jupyter stuff

```bash
jupyter labextension install @jupyter-widgets/jupyterlab-manager
jupyter labextension install jupyter-matplotlib
jupyter labextension install @jupyterlab/toc
jupyter nbextension enable --py widgetsnbextension
jupyter labextension install jupyterlab-jupytext
```

* Now deactivate the current virtual environment

```bash
deactivate
```

## Tips and Tricks

* Launch a terminal and connect to existing Jupiter environment

```bash
jupyter console --existing
```

* Trick for Atom

```json
{"Python2": "import matplotlib as matplotlib_import_only\nmatplotlib_import_only.use('Agg')\n%matplotlib inline\n%config InlineBackend.figure_format = 'retina'\npython=None"}
```

* Trick for VSCode

```json
"python.terminal.launchArgs": [
   "-m",
   "IPython",
   "--no-autoindent",
]
```

* Use this for new data analysis projects

```bash
cookiecutter https://github.com/drivendata/cookiecutter-data-science
```
