################## BASE IMAGE ######################

FROM brianyee/r-jupyter:latest

################## METADATA ######################

LABEL base_image="brianyee/r-jupyter:latest"
LABEL version="1"
LABEL software="leafcutter"
LABEL software.version="3.5.2"
LABEL about.summary="R-leafcutter with Jupyter and irkernel installed."
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN conda create -y -c r -c bioconda -c conda-forge \
    -n r-leafcutter python=2.7 jupyter r-irkernel libjpeg-turbo=1.5 zeromq=4.2.5 readline=6.2

ENV PATH /opt/conda/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
RUN Rscript -e 'devtools::install_github("davidaknowles/leafcutter/leafcutter")'
ENV PATH /opt/conda/envs/r-leafcutter/bin:$PATH
RUN Rscript -e 'IRkernel::installspec(name = "R-leafcutter", displayname = "R-leafcutter", user = FALSE)'