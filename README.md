# Qloapps custom docker

This is a fork of official bloated docker that carry with PHP, MYSQL, OPENSSH

https://hub.docker.com/r/webkul/qloapps_docker

Without all that bloat, just Apache, PHP and Certbot, wich im using on a 1gb instances on Oracle Free Tier.

## How to build that image to your custom repo

docker build -t qloapps_apache_php .
docker tag qloapps_apache_php:latest andrescabrera/qloapps_apache_php:latest

## My own public repo
docker pull andrescabrera/qloapps_apache_php

## WHAT IS QLOAPPS

Qloapps is an open source, free and customizable online reservation system. You can launch a userfriendly site and can manage online as well as offline bookings. Using this you can easily launch your hotel booking website and even manage your offline booking too. This package is developed on top of Prestashop 1.6.

## DOCKERIZING QLOAPPS

Docker is an open-source project that can be integrated with almost all the applications allowing scope of isolation and flexibility. It can be integrated with  Qloapps.

## PREREQUISITES

> Install lastest avaiable Docker version and its dependencies according to your OS version. Refer to link https://docs.docker.com/install/linux/docker-ce/ubuntu/#prerequisites. 

> Check if your user has access privileges to run docker commands.


## DOCKERIZING QLOAPPS

In the dockerized Qloapps architecture, we are using:

> Ubuntu 18.04

> PHP 7.2

To begin with:

1. Pull qloapps docker image from docker hub by running command "docker pull webkul/qloapps:latest".

2. After pulling the image, run your qloapps container by specifying ports and arguments as: 

> docker run -v qloapps_data:/home/qloapps/www/QloApps -d --restart unless-stopped -p 80:80 -p 443:443 -name qloappsv161 -e USER_PASSWORD=REPLACE andrescabrera/qloapps_apache_php:latest

3. In the above command, your Host port 80 is linked with the docker port 80 running apache, you can change the ports of your Host as per your requirements. Please ensure that no other services are running on these host ports.

4. Mention your mysql root password, database name, 'qloapps' user password in arguments MYSQL_ROOT_PASSWORD, MYSQL_DATABASE and 
USER_PASSWORD respectively.

5. Check your running container using command *docker ps*. It will display you a container running with name qloappsv150.

6. Now go to your browser and hit your IP or domain name and start qloapps installation process

7. After qloapps installation, remove "install" directory from server root directory inside the container. Run command:

> docker exec -i qloappsv150 rm -rf /home/qloapps/www/hotelcommerce/install .

8. On clicking on backoffice URL, you will be promped to rename your backoffice URL. Go to running docker container and change the name of admin directory as mentioned.

9. To access your qloapps files and directories, you can SSH in your docker container as:

> docker exec -it qloappsv161 bash

Note -: If you are running any other services on your host at port 80 then you have to mention other ports in step 2.

## GETTING SUPPORT

If you have any issues, contact us at support@qloapps.com or raise ticket at https://webkul.uvdesk.com/


Thank you.
