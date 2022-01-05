# faveo-dev-apache2

Usage:

Download the docker-compose.yml file. Create 2 directories html and mysql repectively. Upload the faveo files in html directory.

Run the below command to spin apache and mysql containers

```sh 
docker-compose up -d
```
Obtain the IP address of faveoapp container.

```sh
docker inspect faveoapp
```
Edit hosts file and map the IP to faveo.localhost. The container is configured with Self Signed SSL certificates for the domainname faveo.localhost. This cannot be changed.

You can visit the site in browser using the URL https://faveo.localhost

The database details are mentioned in the docker-compose file as Environment variable. Either use the deault credentials or you can modify the docker-compose accordingly. For Database Host you can use the container name "mysql". 

To enter inside the container

```sh
docker exec -ti faveoapp bash
```
To stop containers

```sh
docker-compose down
```
