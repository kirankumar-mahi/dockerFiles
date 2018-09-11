FROM ubuntu:18.10
MAINTAINER Dong Meng <mengdong0427@gmail.com> 

# Install build-essential, git, wget and other dependencies
RUN unlink /etc/localtime && \
    ln -s /usr/share/zoneinfo/America/Los_Angeles /etc/localtime && \
    apt-get update && apt-get install -y \
    build-essential \
    git \
    curl \
    libfreetype6-dev \
    libopenblas-dev \
    libopencv-dev \
    liblapack-dev \
    python3 \
    python3-dev \
    python3-pip \
    python3-setuptools \
    python3-numpy \
    graphviz \
    python3-setuptools \
    wget \
    screen \
    rsync \
    unzip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py && \
    rm get-pip.py

COPY requirements.txt /tmp/.
WORKDIR /tmp
RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 6006 8888

WORKDIR "/root"
CMD ["/bin/bash"]
