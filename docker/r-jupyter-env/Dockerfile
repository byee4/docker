################## BASE IMAGE ######################

FROM brianyee/r-base

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-base with Jupyter and irkernel installed."
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update

RUN Rscript -e 'remove.packages(c("curl","httr"))'
ENV CURL_CA_BUNDLE /opt/conda/lib/R/lib/microsoft-r-cacert.pem
RUN Rscript -e 'devtools::install_github("IRkernel/IRkernel")'
RUN Rscript -e 'IRkernel::installspec(name = "R-3.5.1", displayname = "R-3.5.1", user = FALSE)'
