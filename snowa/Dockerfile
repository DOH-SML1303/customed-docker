FROM ubuntu:22.04 AS app

ENV DEBIAN_FRONTEND=noninteractive

LABEL base.image="ubuntu:22.04"
LABEL dockerfile.version="1.0"
LABEL software="wastewater"
LABEL description="This container is made for running analyes of wastewater surveillance data for Washington state"
LABEL maintainer="Steph M Lunn, MPH, MS"
LABEL maintainer.email="stephanie.lunn@doh.wa.gov"

ARG PYTHON_VER=3.10
ARG PANDAS_VER=2.3.3
ARG NUMPY_VER=2.2.6
ARG MATPLOTLIB_VER=3.10.7
ARG SEABORN_VER=0.13.2
ARG GEOPANDAS_VER=1.1.1
# Added Altair version argument here
ARG ALTAIR_VER=5.5.0

RUN apt update -y && apt upgrade -y

# Crucial step: Install repository tools so Ubuntu can find python3.10 explicitly
RUN apt install -y software-properties-common && add-apt-repository -y ppa:deadsnakes/ppa && apt update -y

RUN apt install -y python${PYTHON_VER}
# Added python-is-python3 package here
RUN apt install -y python-is-python3
RUN apt install -y python3-pip

# Changed to -sf so the build doesn't crash if the symlink already exists
RUN ln -sf /usr/bin/python3 /usr/bin/python

# Added altair to the pip installation block
RUN pip install pandas==${PANDAS_VER} \
 numpy==${NUMPY_VER} \
 matplotlib==${MATPLOTLIB_VER} \
 seaborn==${SEABORN_VER} \
 geopandas==${GEOPANDAS_VER} \
 altair==${ALTAIR_VER}

RUN apt autoclean

