################## BASE IMAGE ######################

FROM brianyee/r-base

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="R"
LABEL software.version="3.5.1"
LABEL about.summary="R-VISION + jupyter irkernel"
LABEL about.home="https://github.com/byee4/docker"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>


RUN apt-get update
RUN Rscript -e 'remove.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
ENV CURL_CA_BUNDLE /opt/conda/envs/r-vision/lib/R/lib/microsoft-r-cacert.pem
RUN Rscript -e 'devtools::install_github("IRkernel/IRkernel")'
RUN apt-get remove -y libc6-dev # https://github.com/riscv/riscv-gnu-toolchain/issues/105 (the solution that sucks, but curl wont install with it)
RUN Rscript -e 'install.packages(c("curl","httr"))' # https://github.com/Microsoft/microsoft-r-open/issues/63
RUN Rscript -e 'devtools::install_version("pbmcapply", version = "1.3.1", repos="https://cran.rstudio.com")'
RUN Rscript -e 'devtools::install_github("YosefLab/VISION")'
# RUN Rscript -e 'install.packages("Biobase", repos="https://cran.rstudio.com")'
# RUN Rscript -e 'install.packages("BiocStyle", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("knitr", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("markdown", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("SumarizedExperiment", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("testthat", repos="https://cran.rstudio.com")'
RUN Rscript -e 'install.packages("ggplot2", repos="https://cran.rstudio.com")'
RUN Rscript -e 'devtools::install_github("hrbrmstr/gzmem")'
RUN Rscript -e 'IRkernel::installspec(name = "r-vision", displayname = "R-VISION", user = FALSE)'
