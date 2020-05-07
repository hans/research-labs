# Modified from the jupyter/datascience-notebook Dockerfile
# (added a few R + Python dependencies, and removed Julia)
# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/scipy-notebook
FROM $BASE_CONTAINER

USER root

# R pre-requisites
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    fonts-dejavu \
    gfortran \
    gcc && \
    rm -rf /var/lib/apt/lists/*

USER $NB_UID

# R packages including IRKernel which gets installed globally.
RUN conda install --quiet --yes \
    'r-base=3.6.3' \
    'r-caret=6.0*' \
    'r-crayon=1.3*' \
    'r-devtools=2.3*' \
    'r-hexbin=1.28*' \
    'r-htmltools=0.4*' \
    'r-htmlwidgets=1.5*' \
    'r-irkernel=1.1*' \
    'r-plyr=1.8*' \
    'r-randomforest=4.6*' \
    'r-rcurl=1.98*' \
    'r-reshape2=1.4*' \
    'r-rmarkdown=2.1*' \
    'r-rsqlite=2.2*' \
    'r-shiny=1.4*' \
    'r-tidyverse=1.3*' \
    'rpy2=3.1*' \
    && \
    conda install -qy -c conda-forge r-brms && \
    pip install 'tensorflow==2.1.0' nltk spacy regex && \
    jupyter labextension install @jupyterlab/toc && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER
