FROM ubuntu:18.04

LABEL maintainer="Paul Schlueter <paul@paulschlueter.com>"

ENV DEBIAN_FRONTEND=noninteractive 

# Add CRAN repository to enable R 3.6
RUN apt-get -y update && apt-get install -y --install-recommends \
    apt-transport-https \
    software-properties-common \
    dirmngr \
    gpg-agent && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9 && \
    add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/'

RUN apt-get -y update && apt-get install -y --no-install-recommends \
    wget \
    r-base \
    r-base-dev \
    ca-certificates

RUN R -e "install.packages(c('mda', 'plumber'), repos='https://cloud.r-project.org')"

COPY algorithm /opt/program

ENTRYPOINT ["/usr/bin/Rscript", "/opt/program/mars.R", "--no-save"]
