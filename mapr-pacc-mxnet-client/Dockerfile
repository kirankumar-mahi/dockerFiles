# Start with mapr 5.2 image
FROM maprtech/pacc:5.2.2_3.0.1_ubuntu16_yarn_fuse_streams 
MAINTAINER Dong Meng <mengdong0427@gmail.com>

RUN unlink /etc/localtime && ln -s /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
# Install build-essential, git, wget and other dependencies
RUN bin/bash && sudo rm -r /etc/apt/sources.list.d && \
    sudo apt-get update -y && \
    sudo apt-get install -y build-essential git && \
    sudo apt-get install -y libopenblas-dev liblapack-dev && \
    sudo apt-get install -y libopencv-dev && \
    git clone --recursive https://github.com/dmlc/mxnet && \
    cd mxnet && \
    make -j $(nproc) USE_OPENCV=1 USE_BLAS=openblas && \
    sudo apt-get install -y python-dev python-setuptools python-numpy python-pip && \
    cd python && \
    sudo pip install --upgrade pip && \
    sudo pip install opencv-python && \
    sudo apt-get -y install graphviz && \
    sudo pip install graphviz && \
    sudo pip install -e . 
