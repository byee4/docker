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
RUN Rscript -e 'devtools::install_version("stringr", version = "1.2.0")'
RUN Rscript -e 'install.packages("https://cran.r-project.org/src/contrib/Archive/VGAM/VGAM_1.0-6.tar.gz",repos=NULL, method="libcurl")'
# RUN Rscript -e 'devtools::install_version("VGAM", version = "1.0-6")'
RUN Rscript -e 'devtools::install_github("cole-trapnell-lab/monocle-release@master")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/S4Vectors_0.20.1.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/IRanges_2.16.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.r-project.org/src/contrib/futile.options_1.0.1.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.r-project.org/src/contrib/formatR_1.5.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.r-project.org/src/contrib/lambda.r_1.2.3.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.r-project.org/src/contrib/futile.logger_1.4.3.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.r-project.org/src/contrib/snow_0.4-3.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/BiocGenerics_0.28.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/BiocParallel_1.16.6.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/DelayedArray_0.8.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/Rhdf5lib_1.4.2.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/rhdf5_2.26.2.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/HDF5Array_1.10.1.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/DelayedMatrixStats_1.4.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.rstudio.com/src/contrib/DBI_1.0.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.rstudio.com/src/contrib/blob_1.1.1.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://cran.rstudio.com/src/contrib/RSQLite_2.1.1.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/AnnotationDbi_1.44.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/data/annotation/src/contrib/org.Hs.eg.db_3.7.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/data/annotation/src/contrib/org.Mm.eg.db_3.7.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'install.packages("https://bioconductor.org/packages/release/bioc/src/contrib/Biobase_2.42.0.tar.gz",dependencies=TRUE,repos=NULL, method="libcurl")'
RUN Rscript -e 'devtools::install_github("cole-trapnell-lab/garnett")'
RUN Rscript -e 'source("http://bioconductor.org/biocLite.R");'
RUN Rscript -e 'remove.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN Rscript -e 'IRkernel::installspec(name = "R-garnett", displayname = "R-garnett", user = FALSE)'
