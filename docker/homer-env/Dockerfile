################## BASE IMAGE ######################

FROM continuumio/miniconda3:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="homer"
LABEL software.version="4.9.1"
LABEL about.summary="HOMER (Hypergeometric Optimization of Motif EnRichment) is a suite of tools for Motif Discovery and ChIP-Seq analysis."
LABEL about.home="http://homer.ucsd.edu/homer/"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license="GPLv3"
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
RUN apt-get install -y gcc g++ perl bsdmainutils zip unzip
RUN conda update conda;
RUN conda install -y -c conda-forge -c bioconda -c r \
    samtools r-essentials bioconductor-deseq2 bioconductor-edger homer=4.9.1

# Make sure the contents of our repo are in ${HOME}
COPY . ${HOME}
USER root
RUN chown -R ${NB_UID} ${HOME}
RUN chown -R ${NB_USER}:${NB_UID} /opt/conda/
USER ${NB_USER}

WORKDIR /home/${NB_USER}

CMD ["homer"]

