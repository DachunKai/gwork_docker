FROM pytorch/pytorch:1.10.0-cuda11.3-cudnn8-runtime

RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list && \
    APT_INSTALL="apt-get install -y --no-install-recommends" && \
    PIP_INSTALL="python -m pip --no-cache-dir install --upgrade" && \
    GIT_CLONE="git clone --depth 10" && \
    CONDA_INSTALL="conda install -y" && \
    rm -rf /var/lib/apt/lists/* \
           /etc/apt/sources.list.d/cuda.list \
           /etc/apt/sources.list.d/nvidia-ml.list && \
    apt-get update && \
    pip config set global.index-url https://mirrors.ustc.edu.cn/pypi/web/simple && \
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/  && \
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/  && \
    conda config --set show_channel_urls yes && \
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/ && \
    sed -i '5d' ~/.condarc && \
    conda config --set channel_priority flexible && \
    conda update conda && \
# ==================================================================
# tools
# ------------------------------------------------------------------
    DEBIAN_FRONTEND=noninteractive $APT_INSTALL \
        apt-utils \
        build-essential \
        ca-certificates \
        cmake \
        wget \
        git \
        vim \
        htop \
        tmux \
        openssh-client \
        openssh-server \
        libboost-dev \
        libboost-thread-dev \
        libboost-filesystem-dev \
        libglib2.0-0 \
        libsm6 \
        libxext6 \
        libxrender-dev \
        libgl1-mesa-glx \
        ninja-build \
        libturbojpeg \
        && \
# ==================================================================
# pip
# ------------------------------------------------------------------
    pip install --upgrade pip && \
    $PIP_INSTALL \
        opencv-python-headless \
        tensorboardX \
	matplotlib \
	imageio \
        visdom \
        numpy \
        pandas \
        scikit-image \
	scikit-learn \
        Pillow \
        argparse \
	tqdm \
	pandas \
        h5py\
	tb-nightly \
	PyYAML \
	easydict \
	lmdb \
	scipy \
        && \
# ==================================================================
# config & cleanup
# ------------------------------------------------------------------
    ldconfig && \
    apt-get clean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* ~/*
EXPOSE 6006
