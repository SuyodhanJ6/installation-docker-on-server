# Installation of Docker on Server

## Step 1: Install Docker

To install Docker on your server, use the following commands:

```bash
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

## Step 2: Pull the MySQL Docker Image
```bash
sudo docker pull mysql:latest
```

## Step 3: Run the MySQL Docker Container
```bash
sudo docker run --name mysql-server \
  -e MYSQL_ROOT_PASSWORD=<your_password> \
  -p 3306:3306 \
  -d mysql:latest
```

* --name mysql-server: Names the container mysql-server.
* -e MYSQL_ROOT_PASSWORD=<your_password>: Sets the MySQL root password (replace <your_password> with the actual password you want).
* -p 3306:3306: Maps port 3306 on the server to port 3306 inside the container.
* -p 3306:3306: Maps port 3306 on the server to port 3306 inside the container.
* -d mysql:latest: Runs the MySQL container in detached mode using the latest MySQL image.
