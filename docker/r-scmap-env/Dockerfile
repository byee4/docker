################## BASE IMAGE ######################

FROM continuumio/miniconda:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-scmap + jupyter irkernel"
LABEL about.home="https://github.com/hemberg-lab/scmap"
LABEL about.documentation="http://bioconductor.org/packages/release/bioc/html/scmap.html"
LABEL about.license_file=""
LABEL about.license="GPL-3"
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN apt-get install -y apt-utils  build-essential gcc-multilib gfortran fort77
RUN apt-get install -y liblzma-dev libblas-dev libreadline-dev libbz2-dev libpcre3 libpcre3-dev libcurl4-openssl-dev libopenblas-base libssl-dev
RUN apt-get install -y default-jdk texlive-fonts-extra xorg-dev
RUN apt-get install -y libssh2-1-dev
RUN conda create -y -c r -c bioconda -c conda-forge \
    -n r-scmap python=2.7 jupyter r=3.5.1 r-irkernel libjpeg-turbo=1.5 zeromq=4.2.5 readline=6.2
ENV PATH /opt/conda/envs/r-scmap/bin:$PATH

RUN Rscript -e 'install.packages("devtools", repos="https://cran.rstudio.com")'
RUN Rscript -e 'remove.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
ENV CURL_CA_BUNDLE /opt/conda/envs/r-scmap/lib/R/lib/microsoft-r-cacert.pem
RUN Rscript -e 'devtools::install_github("IRkernel/IRkernel")'
RUN Rscript -e 'devtools::install_github("hemberg-lab/scmap")'
RUN Rscript -e 'IRkernel::installspec(name = "R-scmap", displayname = "R-scmap", user = FALSE)'
RUN Rscript -e 'install.packages("optparse", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("DT", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("ggrepel", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("ggplot2", repos="https://cran.rstudio.com")'

