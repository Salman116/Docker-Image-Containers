
# Docker-Image-Containers

This repository demonstrates basic Docker commands and concepts related to images and containers.

## Requirements

1. You should have a Docker Hub account.
2. Docker Desktop should be installed.
3. Verify the installation by running:
   ```bash
   docker --version
   ```

## Let's Start

1. Create a new folder and create a `Dockerfile` inside this folder.
2. Add the following code in the `Dockerfile`:

    ```Dockerfile
    FROM python:3.6

    RUN apt-get update && apt-get install -y --no-install-recommends \
            python3-setuptools \
            python3-pip \
            python3-dev \
            python3-venv \
            git \
            && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/*

    EXPOSE 8000

    CMD python -c "print('Hello world dev, Have a great day!')"
    ```

### Understanding the Dockerfile:
- **FROM**: Specifies the base image. Here, we're using the official Python 3.6 image.
- **RUN**: Executes shell commands to update the system and install necessary packages (e.g., `python3`, `git`).
- **EXPOSE**: Exposes port 8000, which is commonly used for web applications like Django.
- **CMD**: Specifies the default command to run when the container starts. In this case, it prints a friendly message.

---

## Docker Image

1. **Build the Docker image**:
    ```bash
    docker build -t hello-world -f Dockerfile .
    ```
    - This command builds the Docker image using the `Dockerfile` and tags it as `hello-world`.
    - The process may take a few minutes as it downloads the base image and installs packages.

2. **Run a container from the image**:
    ```bash
    docker run -it hello-world
    ```
    - This command creates and runs a container from the `hello-world` image.

3. **Stop the running container**:
    ```bash
    docker stop <Container-ID>
    ```
    - Replace `<Container-ID>` with the actual ID of the container (you can get this using `docker ps`).

4. **Remove the stopped container**:
    ```bash
    docker rm <Container-ID>
    ```
    - This command removes the stopped container.

5. **Access the container's bash shell**:
    ```bash
    docker run -it hello-world /bin/bash
    ```
    - This command starts the container and gives you access to the bash shell within the container.

---

### Additional Notes:
- Make sure to check the Docker logs if the build or run steps produce any unexpected errors.
- Use `docker ps` to view the running containers and `docker images` to see the images you've built.
