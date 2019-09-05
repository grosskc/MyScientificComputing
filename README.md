# My Scientific Computing and Publishing Setup


## Bash shell

* Add the following to `.inputrc`

```
"\e[A": history-search-backward
"\e[B": history-search-forward
```

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
python3 -m pip install --upgrade scikit-learn scikit-image matplotlib sympy pandas xarray cython tensorly pymc3 nose numexpr Pillow h5py netCDF4 cfunits wpca keras tensorflow pydot statsmodels constrNMPy spectral seaborn dask ipympl pyro-ppl torch torchvision pweave open3d-python trimesh[easy] pyntcloud
```

* Install `libspatialindex` for `trimesh`

```bash
brew install spatialindex
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

* Install conda

It is useful to install for all users as described [here](https://medium.com/@pjptech/installing-anaconda-for-multiple-users-650b2a6666c6). To do so, install Anaconda in `/usr/local/anaconda3`. Then do the following:

```bash
sudo adduser anaconda
sudo chown -R anaconda:anaconda /opt/anaconda
sudo chmod -R go-w /opt/anaconda
sudo chmod -R go+rX /opt/anaconda
su -c 'printf "# Add anaconda to path\nPATH=$PATH:/usr/local/anaconda3/bin/" >> /home/anaconda/.bashrc' anaconda
```

* Install dlib

Note there is no conda package

```bash
pip3 install dlib --verbose
```

* Install OpenCV

Found information [here](https://docs.opencv.org/4.1.1/d2/de6/tutorial_py_setup_in_ubuntu.html) and [here](https://www.pyimagesearch.com/2018/05/28/ubuntu-18-04-how-to-install-opencv/)

```bash
#!/bin/bash

# Save current working directory
cwd=$(pwd)

sudo apt -y update
sudo apt -y upgrade

sudo apt -y remove x264 libx264-dev
 
## Install dependencies
sudo apt -y install build-essential checkinstall cmake pkg-config yasm
sudo apt -y install git gfortran
sudo apt -y install libjpeg8-dev libpng-dev
sudo apt-get install libgtk-3-dev libboost-python-dev
 
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
sudo apt -y install mesa-common-dev libglbinding-dev
sudo apt -y install libgtk-3-dev libtbb-dev qt5-default
 
# Optional dependencies
sudo apt -y install libprotobuf-dev protobuf-compiler
sudo apt -y install libgoogle-glog-dev libgflags-dev
sudo apt -y install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen

sudo apt -y install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libdc1394-22-dev
sudo apt -y install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
sudo apt -y install libatlas-base-dev
sudo apt -y install libfaac-dev libmp3lame-dev libtheora-dev
sudo apt -y install libxvidcore-dev libx264-dev
sudo apt -y install libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt -y install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen x264 v4l-utils
sudo apt -y install libglu1-mesa-dev freeglut3-dev mesa-common-dev
sudo apt -y install libfltk1.3-dev libgtkglext1 libgtkglext1-dev python-gtkglext1

sudo apt -y install python3-dev python3-pip
sudo -H pip3 install -U pip numpy
sudo apt -y install python3-testresources

sudo apt-get install gtk2.0-examples libgail-doc libgtk2.0-0 libgail18 libgail-dev \
     libgtk2.0-common gtk2-engines-pixbuf libgail-common libgtk2.0-0 gtk2.0-examples \
     gtk2-engines-pixbuf libgtk2.0-doc libgtk2.0-bin libgtk2.0-0 \
     gir1.2-gtk-2.0 libgail18 libgtk2.0-dev
sudo apt-get install libgtkglext1 libgtkglext1-dev
sudo apt-get build-dep opencv
sudo apg-get install libqt5svg5 libqt5gui5 libqt5widgets5 libqt5opengl5 libqt5xml5 unixodbc-dev libsybdb5 libglew-dev freeglut3-dev libpng-dev libturbojpeg libjpeg-turbo8 libusb-1.0-0 curl libhidapi-dev libhidapi-libusb0 libopenblas-dev libv4l-0 unzip ttf-mscorefonts-installer

rm -rf build && mkdir build && cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local/opencv \
      -D EIGEN_INCLUDE_PATH=/usr/include/eigen3 \
      -D INSTALL_C_EXAMPLES=ON \
      -D INSTALL_PYTHON_EXAMPLES=ON \
      -D WITH_TBB=ON \
      -D WITH_V4L=ON \
      -D BUILD_TIFF=ON \
      -D BUILD_NEW_PYTHON_SUPPORT=ON \
      -D PYTHON3_EXECUTABLE=/usr/bin/python3 \
      -D PYTHON3_INCLUDE_DIR=/usr/include/python3.6m \
      -D PYTHON3_INCLUDE_DIR2=/usr/include/x86_64-linux-gnu/python3.6m \
      -D OPENCV_PYTHON3_INSTALL_PATH=/usr/local/lib/python3.6/dist-packages \
      -D WITH_QT=ON \
      -D WITH_GTK=OFF \
      -D WITH_OPENGL=ON \
      -D WITH_OPENCL=ON \
      -D WITH_CUDA=ON \
      -D ENABLE_FAST_MATH=1 \
      -D CUDA_FAST_MATH=1 \
      -D WITH_CUBLAS=1 \
      -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
      -D BUILD_EXAMPLES=ON ..

make -j10

sudo make install
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
