################## BASE IMAGE ######################

FROM continuumio/miniconda:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.2"
LABEL about.summary="R-base with Jupyter and irkernel installed."
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN apt-get install -y apt-utils build-essential gcc-multilib gfortran fort77 python-pip
RUN apt-get install -y liblzma-dev libblas-dev libreadline-dev libbz2-dev libpcre3 libpcre3-dev libopenblas-base
RUN apt-get install -y libzmq3-dev libcurl4-openssl-dev libssl-dev jupyter-core jupyter-client
RUN apt-get install -y default-jdk texlive-fonts-extra xorg-dev
RUN pip install --upgrade setuptools
RUN cd /opt && \
    wget https://cran.r-project.org/src/base/R-3/R-3.5.2.tar.gz && \
    tar --no-same-permissions --no-same-owner -xf R-3.5.2.tar.gz && \
    cd R-3.5.2 && \
    ./configure && \
    make && \
    make check && \
    make install