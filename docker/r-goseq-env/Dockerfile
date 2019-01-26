################## BASE IMAGE ######################

FROM brianyee/r-deseq2

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-deseq2 + R-goseq + jupyter irkernel"
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation="http://bioconductor.org/packages/release/bioc/html/goseq.html"
LABEL about.license_file=""
LABEL about.license="LGPL (>= 2)"
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("goseq", version = "3.8")'
RUN Rscript -e 'IRkernel::installspec(name = "R-goseq", displayname = "R-goseq", user = FALSE)'
