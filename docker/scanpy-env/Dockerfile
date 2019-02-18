################## BASE IMAGE ######################

FROM continuumio/miniconda3:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="scanpy"
LABEL software.version="1.4"
LABEL about.summary=""
LABEL about.home=""
LABEL about.documentation="https://github.com/theislab/scanpy"
LABEL about.license_file="https://github.com/theislab/scanpy/blob/master/LICENSE"
LABEL about.license="BSD-3"
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
RUN conda update conda;
RUN conda install -c conda-forge -c bioconda python=3.6 scanpy jupyter ipykernel && \
    python3 -m ipykernel install --name scanpy --display-name "scanpy"

# Make sure the contents of our repo are in ${HOME}
COPY . ${HOME}
USER root
RUN chown -R ${NB_UID} ${HOME}
RUN chown -R ${NB_USER}:${NB_UID} /opt/conda/
USER ${NB_USER}

WORKDIR /home/${NB_USER}

CMD ["python"]

