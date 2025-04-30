FROM jupyter/scipy-notebook:latest

# Install ydata-profiling and clean up pip cache
RUN pip install ydata-profiling black isort jupyterlab_code_formatter && pip cache purge

# Set the working directory inside the container
WORKDIR /home/jovyan/work

# Expose the JupyterLab port
EXPOSE 8888

# Start JupyterLab when the container runs
# Potentialy get token from environment variable in future
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root", "--NotebookApp.token=your-token"]]