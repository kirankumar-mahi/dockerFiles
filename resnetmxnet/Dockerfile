# Start with Ubuntu base image
FROM ubuntu:14.04
MAINTAINER Dong Meng <mengdong0427@gmail.com>

# Install build-essential, git, wget and other dependencies
RUN apt-get update && apt-get install -y \
  build-essential \
  git \
  libopenblas-dev \
  libopencv-dev \
  python-dev \
  python-setuptools \
  wget


RUN cd /root && wget https://bootstrap.pypa.io/get-pip.py && python get-pip.py && \
  pip install numpy flask opencv-python && git clone https://github.com/mengdong/ResnetMXnetFlask.git

# Clone MXNet repo and move into it
RUN cd /root && git clone --recursive https://github.com/dmlc/mxnet && cd mxnet && \
# Copy config.mk
  cp make/config.mk config.mk && \
# Set OpenBLAS
  sed -i 's/USE_BLAS = atlas/USE_BLAS = openblas/g' config.mk && \
# Make 
  make -j"$(nproc)"

# Install Python package
RUN cd /root/mxnet/python && python setup.py install

# Set ~/mxnet as working directory
WORKDIR /root/ResnetMXnetFlask
ENTRYPOINT ["python"]
CMD ["predict.py"]
