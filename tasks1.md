problem1
• Run the container hello-world
• Check the container status
• Start the stopped container
• Remove the container
• Remove the image

```
$docker run hello-world
$docker ps -a
$docker images
$docker rm a3abacde9c0b
$docker rmi feb5d9fea6a5
```
Problem 2
• Run container centos or ubuntu in an interactive 
mode
• Run the following command in the container 
“echo docker ”
• Open a bash shell in the container and touch a 
file named hello-docker
• Stop the container and remove it. Write your 
comment about the file hello-docker :•	comment : the file deleted because no valume 
• Remove all stopped containers

```
	$docker run -it --name=my-ubuntu1 ubuntu:focal
	$echo docker
	$touch hello-docker
	$exit
        $docker rm 8f57d173cb68
        $docker container prune
  ```
  Problem 3
•  Run a container httpd with name apache and 
attach a volume to the container
• Volume for containing static html file
• Remove the container
• Run a new container with the following:
• Attach the volume that was attached to the 
previous container
• Map port 80 to port 9898 on you host machine
• Access the html files from your browser
```
$mkdir /docker
$docker run -d --name apache -v /docker:/usr/local/apache2/htdocs httpd
$docker stop 7bc270cd4949
$docker rm 7bc270cd4949
$docker run -d --name apache -v /docker:/usr/local/apache2/htdocs -p 9898:80  httpd
```
problem4
• Run the image httpd again without attaching any 
volumes
• Add html static files to the container and make 
sure they are accessible
• Commit the container with image name my 
apache
• Create a dockerfile for ngnix and build the 
image from this dockerfile
```
$docker run -d --name apache1  httpd
$docker exec -it 7d5dd48c62a5 bash
$apt-get update
$apt-get install vim
$vim htdocs/index.html
$exit
$ curl http://172.17.0.2:80
