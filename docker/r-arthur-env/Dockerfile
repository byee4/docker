################## BASE IMAGE ######################

FROM brianyee/r-seurat

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="Creates an environment (R-Seurat + jupyter irkernel) to run Arthur's scRNA and bulk RNAseq alignment"
LABEL about.home="https://github.com/arthurhe"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN Rscript -e 'install.packages("matrixStats")'
RUN Rscript -e 'IRkernel::installspec(name = "R-arthur", displayname = "R-Arthur", user = FALSE)'
RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks, but curl wont install with it)
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN apt-get install -y libc6-dev