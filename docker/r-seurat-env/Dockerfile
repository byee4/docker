################## BASE IMAGE ######################

FROM brianyee/r-jupyter

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-Seurat + jupyter irkernel"
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>
RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks, but curl wont install with it)
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN apt-get install -y libc6-dev
RUN apt-get install -y libhdf5-dev && Rscript -e 'install.packages("hdf5r")'
RUN Rscript -e 'devtools::install_github(repo = "satijalab/seurat", ref = "release/3.0")'
RUN Rscript -e 'remove.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN Rscript -e 'IRkernel::installspec(name = "R-Seurat", displayname = "R-Seurat", user = FALSE)'
RUN Rscript -e 'install.packages("reticulate")'
RUN Rscript -e 'library("reticulate");py_install("umap-learn", pip = T, pip_ignore_installed = T)'
RUN Rscripe -e 'install.packages("umap")'
# RUN conda install -y -c bioconda umap-learn;
# RUN Rscript -e 'install.packages("https://cran.r-project.org/src/contrib/umap_0.2.0.0.tar.gz",repos=NULL)'
RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks, but curl wont ins$
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN apt-get install -y libc6-dev
