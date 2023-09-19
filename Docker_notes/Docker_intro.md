# Docker intro

is a popular containerization platform that allows you to package, distribute, and run applications and their dependencies in lightweight containers. Containers are portable, efficient, and provide a consistent environment for your applications across different environments. Let's get started with the basics of Docker:

**1. Installation**:

First, you need to install Docker on your system. Docker provides installers for various operating systems, including Windows, macOS, and Linux. You can find installation instructions specific to your OS on the Docker website: [Docker Installation](https://docs.docker.com/get-docker/).

**2. Docker Concepts**:

Before diving into Docker commands, it's essential to understand a few key concepts:

- **Image**: An image is a read-only blueprint or template used to create containers. It contains the application code, runtime, libraries, and environment variables needed for your application.

- **Container**: A container is a runnable instance of an image. It is isolated from the host system and other containers, ensuring that your application runs consistently regardless of the environment.

**3. Docker Commands**:

Here are some fundamental Docker commands to get you started:

- **Pull an Image**: To fetch a Docker image from a repository (e.g., Docker Hub), use the `docker pull` command. For example, to pull the official Ubuntu image, you can run:
  ```
  docker pull ubuntu
  ```

- **Run a Container**: To create and run a container from an image, use the `docker run` command. For example, to start an interactive Ubuntu container, use:
  ```
  docker run -it ubuntu
  ```

  - `-it`: This option allows you to interact with the container's terminal.

- **List Running Containers**: To view a list of running containers, execute:
  ```
  docker ps
  ```

- **List All Containers**: To list all containers, including stopped ones, use:
  ```
  docker ps -a
  ```

- **Stop and Remove a Container**: You can stop and remove a container using its ID or name. For example:
  ```
  docker stop <container_id_or_name>
  docker rm <container_id_or_name>
  ```

- **Build an Image**: To create a custom Docker image, you can write a Dockerfile, which contains instructions for building an image. Once you have a Dockerfile, use the `docker build` command. For example:
  ```
  docker build -t my-custom-image .
  ```

- **Push an Image**: If you want to share your custom image with others, you can push it to a container registry (like Docker Hub) using the `docker push` command.

- **Cleanup**: Docker can accumulate unused images and containers over time. To clean up unused resources, you can use the following commands:
  ```
  docker system prune  # Removes stopped containers, unused networks, and dangling images.
  docker volume prune  # Removes unused volumes.
  ```

**4. Dockerfile**:

To create custom images, you'll often use a Dockerfile. It's a plain-text file that defines the image's contents and configuration. Here's a simple example:

```Dockerfile
# Use an existing image as a base
FROM ubuntu:20.04

# Set environment variables
ENV MY_VAR=my_value

# Run commands to install software
RUN apt-get update && apt-get install -y my-package

# Specify the default command to run when the container starts
CMD ["my-command"]
```

You can then build this Dockerfile into an image using `docker build`.

**5. Docker Compose**:

For more complex applications that consist of multiple containers, you can use Docker Compose. Docker Compose allows you to define and manage multi-container applications with a single `docker-compose.yml` file. It simplifies orchestration and service dependencies.

**6. Networking and Volumes**:

Docker provides networking and volume features to connect containers together and manage data persistence.

- **Networking**: Docker containers can communicate with each other by default. You can also create custom networks for better isolation.

- **Volumes**: Volumes allow you to persist data outside of containers, making it accessible even after a container is removed.

**7. Docker Hub**:

Docker Hub is a cloud-based repository for Docker images. It's a central place to find and share Docker images, including official images and user-created ones. You can publish your custom images to Docker Hub or pull images from it.

**8. Documentation and Community**:

Docker has extensive documentation available on its website, including tutorials, reference guides, and best practices. The Docker community is also active, with forums and community-contributed resources available for support.

# "Hello World"

Here's a simple example of how to create a Docker container running a Python script on Ubuntu 22.04.3:

**Step 1: Install Docker** (if not already installed):

**Step 2: Create a Python Script**

Create a simple Python script (e.g., `hello.py`) that prints a message. For example:

```python
# hello.py
print("Hello, Docker!")
```

**Step 3: Create a Dockerfile**

Create a Dockerfile in the same directory as your Python script. This Dockerfile defines how to build your Docker image. Here's a minimal Dockerfile:

```Dockerfile
# Use the official Python image as a base image
FROM python:3.9-slim

# Copy your Python script into the container
COPY hello.py /

# Run the Python script when the container starts
CMD ["python", "hello.py"]
```

**Step 4: Build the Docker Image**

Open your terminal and navigate to the directory containing the Dockerfile and the Python script. Then, run the following command to build the Docker image:

```bash
docker build -t my-python-app .
```

- `-t my-python-app`: This option tags the image with the name `my-python-app`. You can choose any name you like.

**Step 5: Run the Docker Container**

Now that you've built the Docker image, you can run a container based on that image:

```bash
docker run my-python-app
```

You should see the output "Hello, Docker!" printed in your terminal, indicating that the Python script inside the container has executed.

**Step 6: Cleanup (Optional)**

After you're done with the container, you can stop and remove it to clean up resources:

```bash
docker stop <container_id_or_name>
docker rm <container_id_or_name>
```

That's it! You've successfully created a Docker container running a Python script on Ubuntu. This simple example demonstrates how to use Docker to package and run applications in isolated containers. It can be built on this foundation to create more complex Dockerized applications as needed.