
# Networking Using Docker

Docker Networking allows you to create a Network of Docker Containers managed by a master node called the manager. Containers inside the Docker Network can talk to each other by sharing packets of information. In this article, we will discuss some basic commands that would help you get started with Docker Networking.

# Types of Network Drivers

1. bridge: If you build a container without specifying the kind of driver, the container will only be created in the bridge network, which is the default network. 
2. host: Containers will not have any IP address they will be directly created in the system network which will remove isolation between the docker host and containers. 
3. none: IP addresses won’t be assigned to containers. These containments are not accessible to us from the outside or from any other container.
4. overlay: overlay network will enable the connection between multiple Docker demons and make different Docker swarm services communicate with each other.
5. ipvlan: Users have complete control over both IPv4 and IPv6 addressing by using the IPvlan driver.
macvlan: macvlan driver makes it possible to assign MAC addresses to a container. 






## Documentation

[Docker](https://linktodocumentation)

[Docker Network](https://linktodocumentation)

[Networking](https://www.geeksforgeeks.org/basics-computer-networking/)




## Installation

First of all we will Check that Docker is installed in ths system and also Docker hub and Docker desktop Should be Sign in

```bash
  docker network ls
```
    
Launch a Container on the Default Network :

1. Understanding the Docker Network Command

```bash
sudo docker network
```

2. Using Docker Network Create command

```bash
docker network create --driver bridge --subnet 172.20.0.0/16 --ip-range 172.20.240.0/20 net-bridge
```

3. Using the Docker Network Connect command

```bash
sudo docker network connect <network-name> <container-name or id>
```

4. Using the Docker Network Inspect command

```bash
sudo docker network inspect <network-name>
```
5. This command runs a Redis container in detached mode (-d), interactively (-it), using a specified bridge network (--net=net-bridge), and names the container cont_database.

```bash
docker run -itd --net=net-bridge --name=cont_database redis

```

6. This command retrieves and displays the IP address of the Docker container named cont_database2 by inspecting its network settings.

```bash
docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' cont_database2

```

7. This command runs a BusyBox container in detached mode (-d), interactively (-it), using a specified bridge network (--net=net-bridge), and names the container server-A.

```bash
docker run -itd --net=net-bridge --name=server-A busybox

```

8. This command inspects the Docker network named net-bridge, retrieves information about its containers in JSON format, and then formats that JSON output for better readability using Python's `json.tool`.

```bash
docker inspect --format='{{json .Containers}}' net-bridge | python -m json.tool

```

9. This command inspects the Docker container named server-B, retrieves its network settings in JSON format, and then formats that JSON output for better readability using Python's `json.tool` .

```bash
docker inspect --format='{{json .NetworkSettings}}' server-B | python -m json.tool 
```

10. This command executes a Bash shell inside the running Docker container with the ID <CONTAINER_ID> allowing you to interact with the container's filesystem and processes in an interactive terminal (-it).

```bash
docker container exec -it <CONTAINER ID> bash

```

11. To get update we can update it..

```bash
apt-get update

```

12. This command installs the `iputils-ping` package on a Debian-based Linux system (like Ubuntu), which provides the `ping` utility used to test network connectivity by sending ICMP echo requests to a specified host.

```bash
apt-get install iputils-ping
```
Now we will ping the network using this..

Thank you...
