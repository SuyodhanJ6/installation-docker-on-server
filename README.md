# installation-docker-on-server

# MySQL Setup Using Docker

This guide provides instructions for setting up MySQL using Docker and accessing the MySQL database in your application.

## Step 1: Install Docker

If Docker is not already installed on your server, install it using the following commands:

```bash
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker

## Step 2: Pull the MySQL Docker Image

```bash
sudo docker pull mysql:latest


## Step 3: Run the MySQL Docker Container
```bash
sudo docker run --name mysql-server \
  -e MYSQL_ROOT_PASSWORD=<your_password> \
  -p 3306:3306 \
  -d mysql:latest


this command does the following:

--name mysql-server: Names the container mysql-server.
-e MYSQL_ROOT_PASSWORD=<your_password>: Sets the root password (replace <your_password> with your desired password).
-p 3306:3306: Maps port 3306 on the server to port 3306 in the container.
-d mysql:latest: Runs the MySQL container in detached mode using the latest MySQL image.
