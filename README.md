# Docker for Faveo development
A pretty simplified Docker Compose workflow that sets up a network of containers for local Laravel development.

## Usage:
___
To get started, make sure you have Docker and docker-compose installed on your system, and then clone this repository.

Next, navigate in your terminal to the directory you cloned this, and create 2 directories html and mysql respectively. Upload the faveo files in the HTML directory. Spin up the containers for the webserver by running docker-compose up -d

Run the below command to spin apache and MySQL containers

```sh 
docker-compose up -d
```
The above command will spin up 2 containers apache and MySQL and this will mount the directories that you created before i.e, html and mysql respectively for persistent storage. Whatever changes you make in the HTML directory like create, delete or edit files will be reflected inside the containers as well.

To visit the Faveo in the browser you have to find the IP address for the apache container.

Run the below command to obtain the IP address of faveoapp container.

```sh
docker inspect faveoapp
```
Copy the IP Address and edit the hosts file of the OS and map the IP to faveo.localhost domain name. The container is configured with Self Signed SSL certificates for the domainname faveo.localhost. This cannot be changed.

Now you can visit the site in the browser using the URL https://faveo.localhost

The database details are mentioned in the docker-compose file as the Environment variable. Either use the default credentials or you can modify the docker-compose accordingly. For Database Host, you can use the container name "mysql" which is the DNS name of MySQL container the docker daemon will resolve to its IP Address.

The Apache container (faveoapp) is configured with all the required development tools like composer, npm, git etc. If you want to execute any commands you should enter into the container’s shell for that execute the below command.


To enter inside the container

```sh
docker exec -ti faveoapp bash
```
The above command will execute the bash shell of the apache container. To come out of the container type "exit".

To stop all containers run

```sh
docker-compose down
```
Bringing down the containers will not lead to loss of data as html and mysql directories are configured for persistent storage.
