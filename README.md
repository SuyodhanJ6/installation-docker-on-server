MySQL Setup Using Docker
This guide provides step-by-step instructions for setting up MySQL using Docker and accessing the MySQL database in your application.
Prerequisites

A server with Ubuntu or a compatible Linux distribution
Sudo privileges on the server

Step 1: Install Docker
If Docker is not already installed on your server, install it using the following commands:
bashCopysudo apt-get update
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker
Step 2: Pull the MySQL Docker Image
Pull the latest MySQL Docker image:
bashCopysudo docker pull mysql:latest
Step 3: Run the MySQL Docker Container
Start a new MySQL container with the following command:
bashCopysudo docker run --name mysql-server \
  -e MYSQL_ROOT_PASSWORD=<your_password> \
  -p 3306:3306 \
  -d mysql:latest
This command does the following:

--name mysql-server: Names the container mysql-server.
-e MYSQL_ROOT_PASSWORD=<your_password>: Sets the root password (replace <your_password> with your desired password).
-p 3306:3306: Maps port 3306 on the host to port 3306 in the container.
-d mysql:latest: Runs the MySQL container in detached mode using the latest MySQL image.

Step 4: Verify MySQL Container
Check if the MySQL container is running:
bashCopysudo docker ps
Step 5: Connect to MySQL
You can connect to MySQL using the mysql client:
bashCopysudo docker exec -it mysql-server mysql -uroot -p
Enter the password you set in Step 3 when prompted.
Step 6: Create a Database and User
Once connected to MySQL, create a database and user for your application:
sqlCopyCREATE DATABASE myapp;
CREATE USER 'myappuser'@'%' IDENTIFIED BY 'myapppassword';
GRANT ALL PRIVILEGES ON myapp.* TO 'myappuser'@'%';
FLUSH PRIVILEGES;
Step 7: Configure Your Application
Update your application's database configuration to use the following details:

Host: Your server's IP address or domain name
Port: 3306
Database: myapp
Username: myappuser
Password: myapppassword

Security Considerations

Always use strong passwords for your MySQL root and application users.
Consider using Docker volumes for persistent data storage.
Regularly update your Docker images and containers.
Implement proper firewall rules to restrict access to your MySQL port.

Troubleshooting
If you encounter any issues, check the Docker logs:
bashCopysudo docker logs mysql-server
For more detailed MySQL logs:
bashCopysudo docker exec mysql-server cat /var/log/mysql/error.log
Additional Resources

Docker Documentation
MySQL Docker Hub Page
MySQL Documentation
