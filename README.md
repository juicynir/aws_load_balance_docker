# Deploying Wordpress Amazon Web Service
In this repository you will find out how to deploy Wordpress in a containerized environment using Docker on Amazon Web Service (AWS).
Aiming to what has been introduced, it will be created two Elastic Compute Cloud (EC2) instances in different zones, both of them containerizing what is need to deploy and keeping on running Wordpress.
Besides that, on EC2, it will be created a Security Group (SG), to prevent the intances to connect to public IPs. So, the incoming traffic will be distributed by the Elastic Load Balancer (Load Balancer).
The database for Wordpress in both EC2 intances will be set up on Amazon Relational Database Service (Amazon RDS).

Before we start, it is recommended that one makes sure that can deploy Wordpress properly locally before doing it on the cloud, as working in the cloud may present many challenges ahead of the developer, specifically if one is stating his/her on DevSecOps. (Check the Bonus in the end of this README) [1]



# Bonus – Locally Deploying of Wordpress [1]

In this bonus topic, it is shown how to deploy locally Wordpress on docker-composer. 
First, check the version of docker-compose and remember that it is not installed by default with docker.

Install, use the command 

``` Bash
apt-get install -y docker-compose

```

Create a directory where you would like to have your docker-compose files.
Then, create using a files editor of your choice to create a file called  docker-compose.yml [2]

nano docker-compose.yml 

```bash 
version: '3.1'

services:

  wordpress:
    image: wordpress
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - wordpress:/var/www/html

  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - db:/var/lib/mysql

volumes:
  wordpress:
  db:

```


So, once the file is created in the very same directory, run the following command to run your docker-compose. 

```bash 

docker-compose up -d

```

Depending on your connection, it will take about 2 to 5 tminutes to complete the process. 
In my first attempt running the application, I encountered an error as port 8080:80 was busy with another application, so I edit the .yml to use another port, which was 8081:80.
Last, but not least, I typed on my browser the local hos; http://localhost:8081/ , it come up the Wordpress famous and welcoming installation page.

To stop and remove containers and network the application, one may use the following command: 

```bash 

docker-compose down

```

To remove associaed volumes and images, simply add -v to the above mentioned shell code. 




# References


Dockerhub. Wordpress. Available: wordpress - Official Image | Docker Hub [2]
