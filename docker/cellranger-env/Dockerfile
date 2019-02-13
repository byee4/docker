################## BASE IMAGE ######################

FROM continuumio/miniconda:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="cellranger"
LABEL software.version="3.0.2"
LABEL about.summary=""
LABEL about.home="https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/installation"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

ENV NB_USER brian
ENV NB_UID 1000
ENV HOME /home/${NB_USER}

RUN adduser --disabled-password \
    --gecos "Default user" \
    --uid ${NB_UID} \
    ${NB_USER}

RUN apt-get update
RUN apt-get install -y build-essential
RUN apt-get install -y --no-install-recommends bsdtar # workaround for "Directory renamed before its status could be extracted"

RUN cd /opt && \
    wget https://s3-us-west-1.amazonaws.com/external-collaborator-data/public-software/cellranger-3.0.2.tar.gz
RUN cd /opt && \
    bsdtar -xzvf cellranger-3.0.2.tar.gz && \
    ln -s /opt/cellranger-3.0.2/cellranger /opt/conda/bin/
# ENV PATH="PATH=/opt/cellranger-3.0.2:$PATH"

# Make sure the contents of our repo are in ${HOME}
COPY . ${HOME}
USER root
RUN chown -R ${NB_UID} ${HOME}
RUN chown -R ${NB_USER}:${NB_UID} /opt/cellranger-3.0.2/
USER ${NB_USER}

# WORKDIR /home/${NB_USER}

CMD cellranger
