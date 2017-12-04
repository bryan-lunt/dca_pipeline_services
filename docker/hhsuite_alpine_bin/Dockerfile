FROM alpine:latest
MAINTAINER Bryan Lunt

#NEED python3

#Requirements hh-suite
#hh-suite needs pdbx CMake

#
# This installs hh-suite from source, but there is a package available at
# http://wwwuser.gwdg.de/%7Ecompbiol/data/hhsuite/releases/hhsuite-latest-linux-x86_64.tar.gz


#
# DATABASE
#
# We still need to download and install a database for searching (or create one, which is probably time-consuming)
#
# http://wwwuser.gwdg.de/%7Ecompbiol/data/hhsuite/databases/hhsuite_dbs/
#

#ENV HHPKG_URL http://wwwuser.gwdg.de/%7Ecompbiol/data/hhsuite/releases/hhsuite-latest-linux-x86_64.tar.gz
ENV HHPKG_URL http://wwwuser.gwdg.de/~compbiol/data/hhsuite/releases/all/hhsuite-2.0.16-linux-x86_64.tar.gz
#ENV HHPKG_URL https://github.com/soedinglab/hh-suite/releases/download/v3.0-beta.3/hhsuite-3.0-beta.3-Linux.tar.gz

ENV HHSUITE_BASE_DIR /opt/hhsuite/
ENV HHLIB /opt/hhsuite/
ENV HHDATA /opt/hhsuite/data/

ENV PATH ${PATH}:${HHSUITE_BASE_DIR}/bin

USER root
WORKDIR /root

RUN apk add --no-cache bash
#RUN apk add --no-cache g++ make cmake git


#RUN git clone https://github.com/soedinglab/pdbx.git && \
#	cd pdbx && \
#	mkdir build && \
#	cd build && \
#	cmake ../ && \
#	make install

RUN wget ${HHPKG_URL} && tar -zxvof $(basename ${HHPKG_URL}) && mkdir -p $(dirname ${HHSUITE_BASE_DIR}) && mv $(basename ${HHPKG_URL} .tar.gz) ${HHSUITE_BASE_DIR} && rm $(basename ${HHPKG_URL})
