################## BASE IMAGE ######################

FROM brianyee/r-jupyter

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="diffbind"
LABEL software.version="2.10.0"
LABEL about.summary="R-diffbind + jupyter irkernel"
LABEL about.home="http://bioconductor.org/packages/release/bioc/vignettes/DiffBind/inst/doc/DiffBind.pdf"
LABEL about.documentation="http://bioconductor.org/packages/release/bioc/vignettes/DiffBind/inst/doc/DiffBind.pdf"
LABEL about.license_file=""
LABEL about.license="Artistic-2.0"
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>
RUN apt-get update
RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks)
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN apt-get install -y libc6-dev
RUN apt-get install -y libhdf5-dev && Rscript -e 'install.packages("hdf5r")'
RUN Rscript -e 'devtools::install_version("stringr", version = "1.2.0")'
RUN conda install -y -c conda-forge zlib && export LDFLAGS="-L/opt/conda/lib/" && Rscript -e 'install.packages("BiocManager");BiocManager::install("ShortRead")'
RUN Rscript -e 'devtools::install_version("amap", version ="0.8-16")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("DiffBind")'
RUN Rscript -e 'remove.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN Rscript -e 'IRkernel::installspec(name = "R-DiffBind", displayname = "R-DiffBind", user = FALSE)'
