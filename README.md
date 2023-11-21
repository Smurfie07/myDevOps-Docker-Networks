# myDevOps-Docker-Networks
## Part 1 Docker Networking

●	Create a new Docker network named "my_network" using the bridge driver. (2 marks)
G:\Git\docker-networking>docker network create -d bridge my_network
d304072bf8d0429fc03b5593b85f8686b4a28b7983a2b2ebffed9d42f6129b9d

G:\Git\docker-networking>docker network ls
NETWORK ID     NAME         DRIVER    SCOPE
ec91ce3ae91c   bridge       bridge    local
f09ae83f5f5f   host         host      local
d304072bf8d0   my_network   bridge    local
24538f1158e9   none         null      local

●	Create a new Docker container using the "nginx" image and connect it to the "my_network" network. Name the container "nginx_container". (4 marks)
G:\Git\docker-networking>docker run --name nginxContainer -d --network my_network --publish 8080:80 nginx:latest
608c99fb3aac9c87b560a0e4376ea6e6f244e589d8e3ed36a57e691e96408ca2

●	Verify that the "nginx" default page is accessible on your host machine at http://localhost:8080. (2 marks)
![image](https://github.com/Smurfie07/myDevOps-Docker-Networks/assets/42376819/ebba5317-da18-4f1b-b186-38e2760b85cd)

●	Create a new Docker container using the "httpd" image and connect it to the "my_network" network. Name the container "httpd_container". (4 marks)
G:\Git\docker-networking>docker run --name httpdContainer -d --network my_network --publish 8081:80 httpd:latest
294e80394d22e8c57c96c2af193b94c979c54b365eef954f7cc4762ad8a5012d

●	Verify that the "httpd" default page is accessible on your host machine at http://localhost:8081. (2 marks)
![image](https://github.com/Smurfie07/myDevOps-Docker-Networks/assets/42376819/2cca8811-2e75-4781-accd-cb079b69ad19)

●	Use the "docker network inspect" command to display information about the "my_network" network. Document your findings in the README.md file. (4 marks)
G:\Git\docker-networking>docker network inspect my_network
[
    {
        "Name": "my_network",
        "Id": "d304072bf8d0429fc03b5593b85f8686b4a28b7983a2b2ebffed9d42f6129b9d",
        "Created": "2023-11-21T09:34:09.3786586Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "294e80394d22e8c57c96c2af193b94c979c54b365eef954f7cc4762ad8a5012d": {
                "Name": "httpdContainer",
                "EndpointID": "f504dce7787b7f6118aa2eeeecbb906d580d812a68afe47615313749ce8c2e76",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            },
            "608c99fb3aac9c87b560a0e4376ea6e6f244e589d8e3ed36a57e691e96408ca2": {
                "Name": "nginxContainer",
                "EndpointID": "988f41369d71fd6caed32f27ed8e7b23f370c1552542bfd1449aedab58651ebb",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]

●	Stop and remove the "nginx_container" container. (2 marks)
G:\Git\docker-networking>docker stop 608c99fb3aac
608c99fb3aac

G:\Git\docker-networking>docker rm 608c99fb3aac
608c99fb3aac

●	Create a new Docker container using the "nginx" image and connect it to the "my_network" network. Name the container "nginx_container_2". (4 marks)
G:\Git\docker-networking>docker run --name nginxContainer2 -d --network my_network --publish 8082:80 nginx:latest
da61c7f7ecc9273615144c85016a398c5b679d0caad1106f507968352b1457df

●	Verify that the "nginx" default page is accessible on your host machine at http://localhost:8082. (2 marks)
![image](https://github.com/Smurfie07/myDevOps-Docker-Networks/assets/42376819/0eb13721-d31d-4d5f-ad5e-a92e096c683c)

●	Use the "docker container ls" command to display information about all running containers. Document your findings in the README.md file. (4 marks)
G:\Git\docker-networking>docker container ls
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                  NAMES
da61c7f7ecc9   nginx:latest   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8082->80/tcp   nginxContainer2
294e80394d22   httpd:latest   "httpd-foreground"       4 minutes ago        Up 4 minutes        0.0.0.0:8081->80/tcp   httpdContainer

●	Stop and remove all containers. (2 marks)
G:\Git\docker-networking>docker stop nginxContainer2
nginxContainer2

G:\Git\docker-networking>docker rm nginxContainer2
nginxContainer2

G:\Git\docker-networking>docker stop httpdContainer
httpdContainer

G:\Git\docker-networking>docker rm httpdContainer
httpdContainer

●	Cleanup: Remove the "my_network" network. (2 marks)

G:\Git\docker-networking>docker network rm my_network
my_network

G:\Git\docker-networking>docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
23e22fc4a8c5   bridge    bridge    local
f09ae83f5f5f   host      host      local
24538f1158e9   none      null      local


●	Create a README.md file and document your findings for each command. For each command, provide a brief description of what it does, followed by the output and logs generated by the command. Ensure that the README.md file is well-organized, easy to read, and contains all necessary information. (18 marks)

> This is the same README.md file

●	Push the codebase for the sample application to your GitHub repository (create a new one for this part)
https://github.com/Smurfie07/myDevOps-Docker-Networks.git
