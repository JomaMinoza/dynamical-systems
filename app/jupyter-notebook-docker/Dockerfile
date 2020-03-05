FROM jupyter/scipy-notebook

# For Python Kernel
RUN conda install --quiet --yes \
    'mlflow=1.0.0' \
    'psycopg2' 

RUN pip install plotdf


USER root


# For R Kernel 

# R pre-requisites
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    fonts-dejavu \
    unixodbc \
    unixodbc-dev \
    r-cran-rodbc \
    gfortran \
    gcc && \
    rm -rf /var/lib/apt/lists/*

RUN ln -s /bin/tar /bin/gtar

USER $NB_UID

# R packages
RUN conda install --quiet --yes \
    'r-base=3.6.2' \
    'r-caret=6.0*' \
    'r-crayon=1.3*' \
    'r-devtools=2.2*' \
    'r-forecast=8.11*' \
    'r-hexbin=1.28*' \
    'r-htmltools=0.4*' \
    'r-htmlwidgets=1.5*' \
    'r-irkernel=1.1*' \
    'r-nycflights13=1.0*' \
    'r-plyr=1.8*' \
    'r-randomforest=4.6*' \
    'r-rcurl=1.98*' \
    'r-reshape2=1.4*' \
    'r-rmarkdown=2.1*' \
    'r-rodbc=1.3*' \
    'r-rsqlite=2.1*' \
    'r-shiny=1.4*' \
    'r-tidyverse=1.3*' \
    'unixodbc=2.3.*' \
    && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR

# Install e1071 R package (dependency of the caret R package)
RUN conda install --quiet --yes r-e1071