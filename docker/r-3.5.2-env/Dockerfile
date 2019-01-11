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
RUN apt-get install -y apt-utils  build-essential gcc-multilib gfortran fort77
RUN apt-get install -y liblzma-dev libblas-dev libreadline-dev libbz2-dev libpcre3 libpcre3-dev libcurl4-openssl-dev libopenblas-base libssl-dev
RUN apt-get install -y default-jdk texlive-fonts-extra xorg-dev

RUN cd /opt && \
    wget https://cran.r-project.org/src/base/R-3/R-3.5.2.tar.gz && \
    tar --no-same-permissions --no-same-owner -xf R-3.5.2.tar.gz && \
    cd R-3.5.2 && \
    ./configure && \
    make && \
    make check && \
    make install

RUN conda create -y -c r -c bioconda -c conda-forge \
    -n r-3.5.2 python=2.7 jupyter r-irkernel libjpeg-turbo=1.5 zeromq=4.2.5 readline=6.2

RUN Rscript -e 'install.packages("devtools", repos="https://cran.rstudio.com")'
RUN Rscript -e 'devtools::install_github("IRkernel/IRkernel")'
