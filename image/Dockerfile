FROM --platform=amd64 jupyter/r-notebook:python-3.10

# Most springtime dependencies can be added from conda channels
COPY --chown=${NB_UID}:${NB_GID} environment.yml /tmp/
RUN mamba env update --name base --file /tmp/environment.yml &&\
    mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

# Additional R dependencies not available on conda channels
RUN Rscript -e 'devtools::install_github("bluegreen-labs/phenor", upgrade="never")'
RUN Rscript -e 'devtools::install_github("ropensci/rppo", upgrade="never")'
RUN Rscript -e 'install.packages(c("AeRobiology", "chillR", "daymetr", "MODISTools", "phenocamr", "rnpn"), repos = "http://cran.us.r-project.org")'

EXPOSE 8888
