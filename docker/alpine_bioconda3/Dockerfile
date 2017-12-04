FROM frolvlad/alpine-miniconda3

MAINTAINER Bryan Lunt


RUN conda install -y biopython

RUN (conda config --add channels r) && \
conda config --add channels defaults && \
conda config --add channels conda-forge && \
conda config --add channels bioconda
