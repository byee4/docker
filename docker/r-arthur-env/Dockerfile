################## BASE IMAGE ######################

FROM brianyee/r-seurat

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="Environment for running Arthurs lightbulb package"
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN Rscript -e 'install.packages("matrixStats")'
RUN Rscript -e 'install.packages("gplots")'
RUN Rscript -e 'install.packages("mixtools")'
RUN Rscript -e 'install.packages("fastcluster")'
RUN Rscript -e 'install.packages("RANN")'
RUN Rscript -e 'install.packages("igraph")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("GenomicRanges", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("impute", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("GO.db", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("AnnotationDbi", version = "3.8")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("preprocessCore", version = "3.8")'
RUN Rscript -e 'install.packages("WGCNA")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("rsvd", version = "3.8")'
RUN Rscript -e 'devtools::install_version(package = "Seurat", version = package_version("2.3.4"))'
RUN Rscript -e 'devtools::install_github("Arthurhe/Lightbulb")'
RUN Rscript -e 'IRkernel::installspec(name = "R-arthur", displayname = "R-arthur", user = FALSE)'
