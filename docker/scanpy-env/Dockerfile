################## BASE IMAGE ######################

FROM continuumio/miniconda3:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="scanpy"
LABEL software.version="1.4.1"
LABEL about.summary=""
LABEL about.home=""
LABEL about.documentation="https://github.com/theislab/scanpy"
LABEL about.license_file="https://github.com/theislab/scanpy/blob/master/LICENSE"
LABEL about.license="BSD-3"
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN conda update conda;
RUN conda install -c conda-forge -c bioconda python=3.6 python-igraph jupyter ipykernel && \
    pip install scanpy==1.4.1 && \
    python3 -m ipykernel install --name scanpy141 --display-name "scanpy-1.4.1"

CMD ["python"]

