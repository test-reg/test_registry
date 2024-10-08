FROM registry.renkulab.io/rok.roskar/vscode-example:0c10599 as code-server
FROM renku/renkulab-r:4.3.1-0.23.0 AS rstudio-server
FROM renku/renkulab-py:3.10-0.23.0 as jupyterlab
FROM code-server

COPY environment.yml* .devcontainer/noop.txt /tmp/conda-tmp/

RUN if [ -f "/tmp/conda-tmp/environment.yml" ]; then umask 0002 && \
    /opt/conda/bin/conda env create -n project -f /tmp/conda-tmp/environment.yml; fi && \
    conda init && \
    conda install -y -n project ipykernel && \
    /opt/conda/envs/project/bin/python -m ipykernel install --name project --display-name "Project environment" --user && \
    echo "conda activate project" >> $HOME/.bashrc
