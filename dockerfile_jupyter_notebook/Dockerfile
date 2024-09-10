# Use the latest jupyter/scipy-notebook image
FROM jupyter/scipy-notebook:latest

USER root

# Install Python dependencies
COPY requirements.txt /tmp/
RUN pip install --upgrade pip && \
    pip install --requirement /tmp/requirements.txt && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER && \
    apt update && \
    apt-get install -y curl && \
    export NODE_OPTIONS=--max-old-space-size=4096 && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Plotly and related packages using pip
RUN pip install plotly jupyter-dash jupyterlab "ipywidgets>=7.6"

# Set environment variables
ENV PYTHONPATH="/home/jovyan/work/q_pack:${PYTHONPATH}"
ENV JUPYTER_ENABLE_LAB="yes"

# Build JupyterLab (if needed, but not installing extensions this way)
RUN jupyter lab build

# Run JupyterLab
CMD ["jupyter", "lab", "--no-browser", "--NotebookApp.token=''", "--NotebookApp.password=''", "--allow-root"]
