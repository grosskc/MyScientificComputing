# My Scientific Computing and Publishing Setup

## MacOS

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
sudo -H python3 -m pip install --upgrade ipython jupyterlab ipywidgets nbconvert ipykernel autopep8 black yapf isort pipreqs pylint python-language-server[all] genson pipreqs cookiecutter python-dotenv sphinx sphinx-autobuild jsonmerge jupytext pandoc-eqnos pandoc-fignos pandoc-tablenos
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

## Linux

* Install Ubuntu 18.04.2 LTS

* Install developer tools

```bash
sudo apt-get update
sudo apt-get install build-essential cmake unzip pkg-config
sudo apt install python3-pip libssl-dev libffi-dev python3-dev python3-venv
sudo apt-get install git git-gui git-doc
```

* Install OpenCV

Found information [here](https://docs.opencv.org/4.1.1/d2/de6/tutorial_py_setup_in_ubuntu.html) and [here](https://www.pyimagesearch.com/2018/05/28/ubuntu-18-04-how-to-install-opencv/)

Install dependencies

```bash
sudo apt -y remove x264 libx264-dev
 
## Install dependencies
sudo apt -y install build-essential checkinstall cmake pkg-config yasm
sudo apt -y install git gfortran
sudo apt -y install libjpeg8-dev libpng-dev
 
sudo apt -y install software-properties-common
sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
sudo apt -y update
 
sudo apt -y install libjasper1
sudo apt -y install libtiff-dev
 
sudo apt -y install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
sudo apt -y install libxine2-dev libv4l-dev
cd /usr/include/linux
sudo ln -s -f ../libv4l1-videodev.h videodev.h
cd "$cwd"
 
sudo apt -y install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
sudo apt -y install libgtk2.0-dev libtbb-dev qt5-default
sudo apt -y install libatlas-base-dev
sudo apt -y install libfaac-dev libmp3lame-dev libtheora-dev
sudo apt -y install libvorbis-dev libxvidcore-dev
sudo apt -y install libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt -y install libavresample-dev
sudo apt -y install x264 v4l-utils
 
# Optional dependencies
sudo apt -y install libprotobuf-dev protobuf-compiler
sudo apt -y install libgoogle-glog-dev libgflags-dev
sudo apt -y install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen

```

```bash
sudo apt-get install cmake python-dev python-numpy gcc g++  libpng-dev libtiff-dev libwebp-dev libjpeg-dev libpng-dev libjpeg-dev libpng-dev libtiff-dev libxvidcore-dev libx264-dev libgtk-3-dev libatlas-base-dev gfortran
```

Could not install these libraries per the first link: `gtk2-dev ffmpeg-dev gstreamer-plugins-base-dev libjpeg-turbo-dev jasper-dev openexr-dev`


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
