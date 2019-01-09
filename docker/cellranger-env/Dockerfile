################## BASE IMAGE ######################

FROM continuumio/miniconda:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="cellranger"
LABEL software.version="3.0.1"
LABEL about.summary=""
LABEL about.home="https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/installation"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN apt-get install -y build-essential

RUN cd /opt && \
    wget https://s3-us-west-1.amazonaws.com/external-collaborator-data/public-software/cellranger-3.0.1.tar.gz && \
    tar -xzvf cellranger-3.0.1.tar.gz

ENV PATH="PATH=/opt/cellranger-3.0.1:$PATH"

CMD ["cellranger"]
