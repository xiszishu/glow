# for CPU env
FROM ubuntu:18.04

LABEL version="0.1"

# Install Glow dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        wget \
        clang-8 \
        llvm-8 \
        llvm-8-dev \
        libpng-dev \
        python-dev \
        ninja-build \
        libgoogle-glog-dev \
        opencl-headers \
        graphviz \
# onnx dependencies
        protobuf-compiler \
        libprotoc-dev \
        && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

RUN wget --no-check-certificate https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py && \
    rm get-pip.py

# Redirect clang
RUN ln -s /usr/bin/clang-8 /usr/bin/clang
RUN ln -s /usr/bin/clang++-8 /usr/bin/clang++

# Install ninja and (newest version of) cmake through pip
RUN pip --no-cache-dir install \
        ninja \
        cmake \
        lit
