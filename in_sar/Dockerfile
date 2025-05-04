FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# System packages
RUN apt-get update && apt-get install -y \
    wget curl git \
    python3 python3-pip python3-dev python3-setuptools \
    gfortran build-essential \
    libgdal-dev gdal-bin \
    libhdf5-dev \
    libnetcdf-dev \
    && rm -rf /var/lib/apt/lists/*

# MintPy requirements
COPY requirements.txt /opt/requirements.txt
RUN pip3 install --upgrade pip && \
    pip3 install --no-cache-dir -r /opt/requirements.txt

# Clone MintPy and install in editable mode
RUN git clone https://github.com/insarlab/MintPy.git /opt/MintPy && \
    pip3 install -e /opt/MintPy

# Set default workdir
WORKDIR /app

CMD ["/bin/bash"]
