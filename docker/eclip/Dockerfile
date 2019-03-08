################## BASE IMAGE ######################

FROM brianyee/perl

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="eclip"
LABEL software.version="0.2.2"
LABEL about.summary="eCLIP processing pipeline environment + cwl implementation of the eCLIP workflow"
LABEL about.home="https://github.com/yeolab/eclip"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN apt-get install -y zip build-essential

RUN conda install -y -c bioconda -c r -c conda-forge \
  python=2.7 \
  samtools=1.7 \
  bedtools=2.25.0 \
  pysam=0.14.1 \
  pybedtools=0.8.0 \
  pybigwig=0.3.13 \
  fastqc=0.11.5 \
  star=2.4.0 \
  cutadapt=1.14 \
  rna-seqc=1.1.8 \
  picard=2.18.27 \
  r=3.5.1 \
  fastq-tools=0.8 \
  umi_tools \
  ucsc-bedgraphtobigwig=357 \
  ucsc-bedsort=357 \
  seaborn=0.9.0 \
  cython=0.29.6 \
  scikit-learn=0.18 \
  pycrypto=2.6.1 \
  pytest=4.3.0 \
  pandas=0.24.1 \
  numpy=1.16.2 \
  zlib=1.2 \
  nodejs=10.13;

RUN cd /opt && \
  wget https://github.com/YeoLab/eclip/archive/0.2.1a.zip && \
  unzip 0.2.1a.zip -d /opt/

RUN conda install -y -c https://conda.anaconda.org/toms umi_tools;

RUN pip install --ignore-installed six && \
  pip install cwlref-runner && \
  pip install cwltool==1.0.20180306140409 && \
  pip install cwltest==1.0.20180413145017 && \
  pip install galaxy-lib==17.9.3;
  
RUN cd /opt && \
  git clone https://github.com/byee4/toil && \
  cd toil && \
  /opt/conda/bin/python setup.py install;

RUN cd /opt && \
  git clone https://github.com/byee4/eclipdemux
  
RUN cd /opt && \
  git clone https://github.com/YeoLab/clipper && \
  cd clipper && \
  /opt/conda/bin/python setup.py install;
  
RUN cd /opt && \
  git clone https://github.com/YeoLab/makebigwigfiles && \
  cd makebigwigfiles &&\
  /opt/conda/bin/python setup.py install;

RUN cd /opt/conda/lib && \
  rm libstdc++.so libstdc++.so.6 && \
  ln -s libstdc++.so.6.0.25 ./libstdc++.so && \
  ln -s libstdc++.so.6.0.25 ./libstdc++.so.6

ENV PATH /opt/eclipdemux/bin:/opt/eclip-0.2.1a/cwl:/opt/eclip-0.2.1a/wf:/opt/eclip-0.2.1a/bin:/opt/eclip-0.2.1a/bin/perl:$PATH

CMD cwltool /opt/eclip-0.2.1a/cwl/wf_get_peaks_scatter_pe.cwl $@
