################## BASE IMAGE ######################

FROM brianyee/r-seurat:245d72b5f7c3ae75b185f2ae2d3a5b4c67c61e9a

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL base_image="brianyee/r-base:3.5.1"
LABEL base_image="brianyee/r-jupyter:r3.5.1_jupyterlab4.4.0_py3.6"
LABEL base_image="brianyee/r-seurat:245d72b5f7c3ae75b185f2ae2d3a5b4c67c61e9a"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-Seurat (develop) + immunogenomics/harmony (develop) + RUVnormalize (1.16.0) + jupyter irkernel"
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN Rscript -e 'devtools::install_github(repo = "immunogenomics/harmony", ref = "818123eff65eca65bd96ee8ad2b56d58002ab290")'
RUN Rscript -e 'install.packages("BiocManager");BiocManager::install("RUVnormalize")'

RUN Rscript -e 'remove.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN Rscript -e 'IRkernel::installspec(name = "R-Seurat-develop_harmony-develop_RUVnormalize-1.16.0", displayname = "R-Seurat-develop+harmony-develop+RUVnormalize-1.16.0", user = FALSE)'

RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks, but curl wont ins$
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN apt-get update && apt-get install -y libc6-dev
