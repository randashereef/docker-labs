problem:

 Create your bridge network, two containers from ubuntu image with different 
names and try to ping each other using NAME 

```
$docker create myNetwork
$docker run -it --name ubuntu2 --network myNetwork  myubuntu:focal
$docker run -it --name ubuntu1 --network myNetwork  myubuntu:focal
$ping ubuntu1
$ping ubuntu2
```
another solution by using docker compose:

```
$vim docker-compose.yml
```
```
version: "3.8"
services:
   container1:
      container_name: ubuntu1
      image: myubuntu:focal
      networks:
       - mynetwork
      command: sleep infinity
   container2:
     container_name: ubuntu2
     image: myubuntu:focal
     networks:
      - mynetwork
     command: sleep infinity
networks:
mynetwork:
```
 ```
 $docker compose up -d
 $docker exec -it 2127bce8e6ca bash
 $ping ubuntu1
 $docker exec -it 67a43691660a bash
 $ping ubuntu2
 ```
