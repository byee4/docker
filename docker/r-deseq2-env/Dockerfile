
################## BASE IMAGE ######################

FROM brianyee/r-jupyter

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-leafcutter + jupyter irkernel"
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("DESeq2", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("vsn", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("tximport", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("tximportData", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("pasilla", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("airway", version = "3.8")'
RUN Rscript -e 'install.packages("pheatmap")'
RUN Rscript -e 'install.packages("readr")'
RUN Rscript -e 'IRkernel::installspec(name = "R-deseq2", displayname = "R-DESeq2", user = FALSE)'
