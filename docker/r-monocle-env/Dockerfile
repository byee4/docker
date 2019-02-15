################## BASE IMAGE ######################

FROM brianyee/r-jupyter

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="monocle"
LABEL software.version="2.4"
LABEL about.summary="R-monocle + jupyter irkernel"
LABEL about.home="http://cole-trapnell-lab.github.io/monocle-release"
LABEL about.documentation="http://cole-trapnell-lab.github.io/monocle-release"
LABEL about.license_file=""
LABEL about.license="GPL 3.0"
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>
RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks, but curl wont install with it)
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN apt-get install -y libc6-dev
RUN apt-get install -y libhdf5-dev && Rscript -e 'install.packages("hdf5r")'
RUN Rscript -e 'source("http://bioconductor.org/biocLite.R");biocLite("monocle")'
RUN Rscript -e 'remove.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN Rscript -e 'IRkernel::installspec(name = "R-monocle", displayname = "R-monocle", user = FALSE)'
