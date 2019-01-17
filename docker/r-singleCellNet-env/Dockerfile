################## BASE IMAGE ######################

FROM brianyee/r-jupyter

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-singleCellNet with Jupyter and irkernel installed."
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update

RUN Rscript -e 'devtools::install_github("thomasp85/patchwork")'
RUN Rscript -e 'devtools::install_github("ctlab/fgsea")'
RUN Rscript -e 'devtools::install_github("pcahan1/singleCellNet", ref="v0.2.0")'
RUN apt-get install -y libhdf5-dev
RUN Rscript -e 'devtools::install_github("hhoeflin/hdf5r")'
RUN Rscript -e 'devtools::install_github("mojaveazure/loomR", ref = "develop")'
RUN Rscript -e 'IRkernel::installspec(name = "R-singleCellNet", displayname = "R-singleCellNet", user = FALSE)'
RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks, but curl wont install with it)
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN apt-get install -y libc6-dev
