FROM julia
MAINTAINER Bryan Lunt

ENV PATH ${PATH}:${HHSUITE_BASE_DIR}/bin

USER root

RUN apt-get update && apt-get install -y \
	less \
	cmake \
	git \
	&& rm -rf /var/lib/apt/lists/*



RUN git clone https://github.com/pagnani/PlmDCA.git
RUN git clone https://github.com/carlobaldassi/GaussDCA.jl.git
RUN git clone https://github.com/JuliaOpt/NLopt.jl.git
