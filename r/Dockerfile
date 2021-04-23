FROM jupyter/minimal-notebook:latest

RUN conda config --append channels conda-forge && \
    conda install --yes -c conda-forge r-base libv8
RUN R -e "install.packages('rstan',repos='https://cloud.r-project.org/', dependencies = TRUE)" && \
R -e "install.packages(c('coda','mvtnorm','devtools','dagitty', 'ellipse', 'ape', 'IRkernel'), dependencies=TRUE, repos='http://cran.rstudio.com/')" && \
R -e "IRkernel::installspec()" && \
R -e "library(devtools)" && \
R -e "devtools::install_github('rmcelreath/rethinking')"
RUN fix-permissions $CONDA_DIR && fix-permissions /home/$NB_USER
