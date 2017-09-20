FROM jupyter/minimal-notebook
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

ENV HHSUITE_BASE_DIR /opt/hhsuite/
ENV HHLIB /opt/hhsuite/
ENV HHDATA /opt/hhsuite/data/

ENV PATH ${PATH}:${HHSUITE_BASE_DIR}/bin

USER root

RUN apt-get update && apt-get install -y \
	less \
	cmake \
	&& rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/soedinglab/pdbx.git && \
	cd pdbx && \
	mkdir build && \
	cd build && \
	cmake ../ && \
	make install

RUN git clone https://github.com/soedinglab/hh-suite.git && \
	cd hh-suite && \
	git pull && \
	git submodule deinit . && git submodule init && git submodule update && \
	mkdir build && \
	cd build && \
	cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -G "Unix Makefiles" -DCMAKE_INSTALL_PREFIX=${HHSUITE_BASE_DIR} .. && \
	make && make install

USER jovyan
