# Deploying Wordpress Amazon Web Service
In this repository you will find out how to deploy Wordpress in a containerized environment using Docker on Amazon Web Service (AWS).
Aiming to what has been introduced, it will be created two Elastic Compute Cloud (EC2) instances in different zones, both of them containerizing what is need to deploy and keeping on running Wordpress.
Besides that, on EC2, it will be created a Security Group (SG), to prevent the intances to connect to public IPs. So, the incoming traffic will be distributed by the Elastic Load Balancer (Load Balancer).
The database for Wordpress in both EC2 intances will be set up on Amazon Relational Database Service (Amazon RDS).

 Before we start, it is recommended that one makes sure that can deploy Wordpress properly locally before doing it on the cloud, as working in the cloud may present many challenges ahead of the developer, specifically if one is stating his/her on DevSecOps.





# References
