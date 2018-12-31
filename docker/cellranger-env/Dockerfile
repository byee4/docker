################## BASE IMAGE ######################

FROM continuumio/miniconda:latest

################## METADATA ######################

LABEL base_image="continuumio/miniconda:latest"
LABEL version="1"
LABEL software="cellranger"
LABEL software.version="3.0.1"
LABEL about.summary=""
LABEL about.home="https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/installation"
LABEL about.documentation=""
LABEL about.license_file=""
LABEL about.license=""
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Brian Yee <brian.alan.yee@gmail.com>

RUN apt-get update
RUN apt-get install -y build-essential

RUN cd /opt && \
    wget -O cellranger-3.0.1.tar.gz "http://cf.10xgenomics.com/releases/cell-exp/cellranger-3.0.1.tar.gz?Expires=1546250924&Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cDovL2NmLjEweGdlbm9taWNzLmNvbS9yZWxlYXNlcy9jZWxsLWV4cC9jZWxscmFuZ2VyLTMuMC4xLnRhci5neiIsIkNvbmRpdGlvbiI6eyJEYXRlTGVzc1RoYW4iOnsiQVdTOkVwb2NoVGltZSI6MTU0NjI1MDkyNH19fV19&Signature=fo5Uk0qTSK~VbAp6EJDUM7BWJFlpjBuE5ikiKpylyQlZkIb8aPM5D8AACggVpZ23DE2MzYVU1igPkrWz1p~JAv4qLEdPDcx8He5Jy5Buufj8U9iFYXeH~p3GYdjhdWUDbXdmpnFq35EiR-ArfWDzpj45DGiexOsMu-xNrAPH9oN-NAY37OvBb8aOr7Ozzkj~t4Q11reClvpURKP7iu-IN4Q9w8W5CLAsU81EcsNPv4pRPGCk3YdaR5C9XM-TtIkFW9CGbyQFV0vL1pT5ZRSBINdcV2OJnNPo~Lv43h3vJoL0SA8tzr~Oa4HMaN4snhs4TVZR0~ZKfHXzreAyyy49ig__&Key-Pair-Id=APKAI7S6A5RYOXBWRPDA" && \
    tar -xzvf cellranger-3.0.1.tar.gz

RUN cd /opt && \
    wget http://cf.10xgenomics.com/supp/cell-exp/refdata-cellranger-GRCh38-3.0.0.tar.gz && \
    tar -xzvf refdata-cellranger-GRCh38-3.0.0.tar.gz

ENV PATH="PATH=/opt/cellranger-3.0.1:$PATH"

CMD ["cellranger"]
