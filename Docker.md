<span style="color: rgb(230, 126, 35);">Why do we need docker?</span>        -->when we try to replicate the local environment of one machine in another,many errors occur due to dependencies,versions,commands not working,etc."IT WORKS ON MY MACHINE".

Docker is an open platform for developers and sysadmins to <span style="color: rgb(45, 194, 107);">build, ship, and run distributed applications.</span>

<span style="color: rgb(185, 106, 217);">TAG<span style="color: rgb(0, 0, 0);">\-version or variant of the same docker image</span></span>

<span style="color: rgb(185, 106, 217);">Container</span>\->contains applications + dependencies(works on any system)-> <span style="color: rgb(45, 194, 107);">protable / lightweight</span>

2 applications ->different versions can be run

![c6227885f146e8dc3df349af14f82bd2.png](../_resources/c6227885f146e8dc3df349af14f82bd2.png)

we share the containers using docker image

![ac6df0afa50da3526c2c6fc59c1368cc.png](../_resources/ac6df0afa50da3526c2c6fc59c1368cc.png)

we can build multiple applications using different versions or dependencies using seperate containers.containers ensure a seperate environment isolated from the env of the host  or other containers.

![f2ac89225657334ad58cbb60c69749bf.png](../_resources/f2ac89225657334ad58cbb60c69749bf.png)

<span style="color: rgb(185, 106, 217);">Docker Image</span>(static snapshot)//(Class-Object relation):        Executable files(ins to build containers)->create multiple containers using 1 image

docker run -it ubuntu        (it->interactive mode)

docker hub->platform for deploying containers

*Hello from Docker!*  
*This message shows that your installation appears to be working correctly.*

*To generate this message, Docker took the following steps:*  
 *1\. The Docker <ins>client contacted</ins> the <ins>Docker daemon</ins>.*  
 *2\. The Docker <ins>daemon pulled</ins> the "hello-world" <ins>image</ins> from the <span style="color: rgb(248, 202, 198);">Docker Hub</span>.*  
    *(amd64)*  
 *3\. The Docker <ins>daemon created a new container</ins> from that image which runs the*  
    *executable that produces the output you are currently reading.*  
 *4\. The Docker <ins>daemon streamed</ins> that <ins>output to the Docker client</ins>, which sent it*  
    *to your terminal.*

*using `sudo` all the time:By default, Docker CLI talks to the Docker Engine (daemon), which requires **root access**. If your user isn’t in the special `docker` group, Docker is like “who even are you?” and blocks you.*

- *Add your user to the `docker` group:*
    
    <span style="color: rgb(53, 152, 219);">sudo usermod -aG docker $USER</span>
    
- *Refresh your session:*
    
    <span style="color: rgb(53, 152, 219);">newgrp docker</span>
    

&nbsp;

&nbsp;

<span style="color: rgb(224, 62, 45);">:        docker pull IMAGE_NAME</span>

<span style="color: rgb(224, 62, 45);">:        docker images</span>

<span style="color: rgb(224, 62, 45);">:        docker ps  -a        <span style="color: rgb(0, 0, 0);">(To check the no of containers)</span></span>

<span style="color: rgb(224, 62, 45);">:        docker ps        <span style="color: rgb(0, 0, 0);">(to check the running containers)</span></span>

<span style="color: rgb(224, 62, 45);">:         docker run IMAGE_NAME        <span style="color: rgb(0, 0, 0);">(creates a new container everytime we run the image)</span></span>

<span style="color: rgb(224, 62, 45);">:        docker run -it IMAGE_NAME</span>

<span style="color: rgb(224, 62, 45);">:        docker stop CONT_Name or CONT_ID</span>

<span style="color: rgb(224, 62, 45);">:        docker start CONT_NAME or CONT_ID        <span style="color: rgb(0, 0, 0);">(restarts the existing container)</span></span>

<span style="color: rgb(224, 62, 45);">:        docker rmi IMAGE_NAME        <span style="color: rgb(0, 0, 0);">(remove /destroy image)        ->(TO DELETE AN IMAGE WE MUST FIRST DELETE ALL ITS CONTAINERS)</span></span>

<span style="color: rgb(224, 62, 45);">:        docker rm CONT_NAME        <span style="color: rgb(0, 0, 0);">(remove /destroy cont)</span></span>

<ins>*<ins>versions in docker images:</ins>*</ins>

<span style="color: rgb(0, 0, 0);">layers in an image.</span>

<span style="color: rgb(224, 62, 45);">:        docker pull IMAGE_NAME:version</span>

<span style="color: rgb(224, 62, 45);">:        docker run -d IMAGE_NAME        <span style="color: rgb(0, 0, 0);">(detach mode->run in the background)</span></span>

<span style="color: rgb(224, 62, 45);">:        docker run --name CONT_NAME -d IMAGE_NAM        <span style="color: rgb(0, 0, 0);">(custom name )</span></span>

&nbsp;

<ins>*docker image-layers:*</ins>

![679996b4a05c78a851eb0bca99c7c4d1.png](../_resources/679996b4a05c78a851eb0bca99c7c4d1.png)

*<span style="color: rgb(0, 0, 0);">all the layers are read-only.only the container layer can be changed.</span>*

*<span style="color: rgb(0, 0, 0);">![6eb6b80ce86c2704ee686a2a84dcbccc.png](../_resources/6eb6b80ce86c2704ee686a2a84dcbccc.png)</span>*

&nbsp;

*<span style="color: rgb(0, 0, 0);">PORT BINDING:</span>*

*<span style="color: rgb(0, 0, 0);">every container has a separate virtual file system.ports are also seperate from that of host machine</span>*

*<span style="color: rgb(0, 0, 0);"><span style="color: rgb(224, 62, 45);">:        docker run -p800:3306 IMAGE_NAME</span>        (bind the host_port:with the container_port)</span>*

*<span style="color: rgb(0, 0, 0);">we cannot bind a host port with multiple container ports.</span>*

*<span style="color: rgb(0, 0, 0);">TROUBLESHOOT COMMANDS:</span>*

*<span style="color: rgb(0, 0, 0);"><span style="color: rgb(224, 62, 45);">:        docker logs CONT_ID</span>         (identify the root cause of the problem)</span>*

*<span style="color: rgb(0, 0, 0);">:        docker exec -it CONT_ID/bin/bash        (allows us to run additional commands to an already running containter)</span>*

:        docker exec -it CONT_ID/bin/sh\*\*

*<span style="color: rgb(0, 0, 0);">*Docker VS VM:*</span>*

![6e3cad75f816528f3b666a8e8c6d3193.png](../_resources/6e3cad75f816528f3b666a8e8c6d3193.png)

*<span style="color: rgb(0, 0, 0);">*Docker uses the host machine and only virtualise the application layer. compatible with linux (based images)(Docker desktop->contains small linux based VM which helps in running the images)*</span>*

*<span style="color: rgb(0, 0, 0);">*VM virtualises the host kernel & application layer. Compatible with all underlying OS.*</span>*

*<span style="color: rgb(0, 0, 0);">*Developing an application:*</span>*

*<span style="color: rgb(0, 0, 0);">*we want 2 containers to interact with each other without any port or limitations*</span>*

*<span style="color: rgb(0, 0, 0);">*solution:Docker Network*</span>*

:        docker network create\*\*

:        docker network ls\*\*

![64eee6f679cd1850cae08bf465bad106.png](../_resources/64eee6f679cd1850cae08bf465bad106.png)

&nbsp;

&nbsp;

to create a Docker image:

create a Dokcer file in your app folder and include the following FROM node RUN CMD COPY ENV save it logout and login into your docker desktop through the terminal

&nbsp;            docker build -t IMAGE_NAME

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;