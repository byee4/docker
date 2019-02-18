################## BASE IMAGE ######################

FROM continuumio/miniconda:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-base 3.5.1 and python2.7 from anaconda and devtools"
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation="https://anaconda.org/r/r-base"
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN apt-get install -y apt-utils  build-essential gcc-multilib gfortran fort77
RUN apt-get install -y liblzma-dev libblas-dev libreadline-dev libbz2-dev libpcre3 libpcre3-dev libcurl4-openssl-dev libopenblas-base libssl-dev
RUN apt-get install -y default-jdk texlive-fonts-extra xorg-dev
RUN apt-get install -y libssh2-1-dev
RUN conda install -y -c r -c bioconda -c conda-forge \
    python=2.7 jupyter jupyterlab r=3.5.1 r-irkernel libjpeg-turbo=1.5 zeromq=4.2.5 readline=6.2
ENV PATH /opt/conda/bin:$PATH

RUN Rscript -e 'install.packages("devtools", repos="https://cran.rstudio.com")'
