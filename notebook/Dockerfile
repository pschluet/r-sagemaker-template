FROM r-base

RUN apt-get -y update && apt-get install -y --no-install-recommends \
    python3.6-dev \
    python3-distutils \
    && cd /usr/local/bin \
    && ln -s /usr/bin/python3.6 python \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://bootstrap.pypa.io/get-pip.py && \
        python get-pip.py && \
        pip install jupyterlab

RUN R -e "install.packages(c('repr', 'IRdisplay', 'IRkernel'), type = 'source')"
RUN R -e "IRkernel::installspec(user = FALSE)"

ENV SHELL=/bin/bash

ENTRYPOINT ["jupyter-lab", "--ip=0.0.0.0", "--allow-root", "--no-browser"]
