# jupyterlab_ydata-profiling

## Explanation of the Dockerfile

 * FROM jupyter/scipy-notebook:latest: This line starts with the official jupyter/scipy-notebook Docker image, which already includes JupyterLab and many common scientific libraries (like pandas, numpy, matplotlib). This saves you a lot of setup.
 * RUN pip install ydata-profiling: This command installs the ydata-profiling library using pip within the Docker image.
 * WORKDIR /home/jovyan/work: This sets the working directory inside the container to /home/jovyan/work. This is where your notebooks and data will typically be stored.
 * EXPOSE 8888: This line declares that the container will listen on port 8888, which is the default port for JupyterLab.
 * CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]: This is the command that will be executed when the Docker container starts. It launches JupyterLab with the following options:
 * --ip=0.0.0.0: Allows access to JupyterLab from outside the container.
 * --port=8888: Specifies the port JupyterLab will run on.
 * --no-browser: Prevents JupyterLab from trying to open a browser inside the container (since there isn't one).
 * --allow-root: Allows JupyterLab to run as the root user inside the container (generally okay for personal use in Docker).

## How to Use This - as Infrastructure as Code (IaC)
1. **Install Docker and Docker Compose**: Make sure you have Docker installed on your machine.
2. Open your terminal or command prompt, navigate to the directory containing your docker-compose.yml file, and run the following command:

```Bash
docker-compose up -d
```
docker-compose up: This command creates and starts the services defined in your docker-compose.yml file.
-d: This flag runs the containers in detached mode (in the background), so your terminal isn't blocked.
3. Docker Compose will now:

 - Build the Docker image using your Dockerfile (if it hasn't been built before or if the Dockerfile has changed).
 - Create and start a container named (by default, something like your_directory_name_jupyterlab_1) based on the built image.
 - Set up the port mapping so you can access JupyterLab on http://localhost:8888.
 - Mount the notebooks directory to the container.
4. Access JupyterLab:

Just like before, open your web browser and navigate to http://localhost:8888. You might be prompted for a token, which you can find in the output of the docker-compose up command or by checking the logs of the container using docker-compose logs jupyterlab.