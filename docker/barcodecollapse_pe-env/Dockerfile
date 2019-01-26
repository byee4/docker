################## BASE IMAGE ######################

FROM continuumio/miniconda:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="barcodecollapsepe.py"
LABEL software.version="0.0.1"
LABEL about.summary="barcodecollapsepe.py will take eCLIP paired-end reads and perform PCR-deduplication based on randomers in the name of each read."
LABEL about.home="https://github.com/YeoLab/eclip"
LABEL about.documentation="https://github.com/YeoLab/eclip/README.md"
LABEL about.license_file="https://github.com/YeoLab/eclip/blob/master/LICENSE"
LABEL about.license="BSD-3"
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN conda install -c bioconda samtools=1.5 htslib=1.5 python=2.7 cryptography=1 pysam=0.12.0.1
RUN cd /opt/conda/bin/ && \
  wget https://raw.githubusercontent.com/YeoLab/eclip/master/bin/barcodecollapsepe.py && \
  chmod +x barcodecollapsepe.py
ENV LD_LIBRARY_PATH /opt/conda/lib:$LD_LIBRARY_PATH

CMD ["barcodecollapsepe.py"]
