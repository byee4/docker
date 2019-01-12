################## BASE IMAGE ######################

FROM brianyee/r-jupyter:latest

################## METADATA ######################

LABEL base_image="brianyee/r-jupyter:latest"
LABEL version="1"
LABEL software="Seurat"
LABEL software.version="3.0"
LABEL about.summary="R-seurat with Jupyter and irkernel installed."
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN conda create -y -c r -c bioconda -c conda-forge \
    -n r-seurat python=2.7 jupyter r-irkernel libjpeg-turbo=1.5 zeromq=4.2.5 readline=6.2

ENV PATH /opt/conda/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
RUN apt-get install -y libhdf5-dev
RUN Rscript -e 'install.packages("Seurat", repos="https://cran.rstudio.com")'
ENV PATH /opt/conda/envs/r-seurat/bin:$PATH
RUN Rscript -e 'IRkernel::installspec(name = "R-seurat", displayname = "R-seurat", user = FALSE)'