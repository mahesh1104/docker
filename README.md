# docker

Points:-
1) Dockerfile
      Image creation with Dockerfile
      Image & Containers(FROM,COPY and CMD)
      Dockerfile Instructions(ENTRYPOINT,ENV and WORKDIR)
      Difference between CMD & ENTRYPOINT
      Dockerfile Instructions(RUN and USER)
      .dockerigore usage
      Dockerfile instructions (ADD,COPY and ARG)
     
2) Docker Compose
      Docker Compose(SCALE,CONFIG,UP,DOWN)
3) Manage Data with Docker
4) Docker Volume(Create,Inspect,Prune,Mount)
      Docker Bind Mount to persist container data on Host machine
      Docker Volume Versus Bind Mount
      Volumes - How to Create Backup, Restore or Migrate.
5) Docker Swarm -Swarm Manager, Worker, Swarm Mode, Swarm nodes
      How to create Swarm Cluster with 2 Managers and 2 Workers
      How to create Swarm Services on Swarm Cluster 
      Service Update,Rollback,Scale&Replicas
      
 ----------------------------------------------------------------     
      
      A) Dockerfile
      Image creation with Dockerfile
      Image & Containers(FROM,COPY and CMD)
      Dockerfile Instructions(ENTRYPOINT,ENV and WORKDIR)
      Difference between CMD & ENTRYPOINT
      Dockerfile Instructions(RUN and USER)
      .dockerigore usage
      Dockerfile instructions (ADD,COPY and ARG)
     
B) Docker Compose
          This part covers
1. What is Docker Compose -> is a command line tool for defining and running muti-container docker applications.
2. Docker-compose.yml -> is used to define an application's services and includes various configuation options.
         Docker-compose.yml
                 version: "3.7" => Based on the Docker engine release compose version
                 
                 services:
                   web:
                     image: nginx
                   database:
                     image: postgres
   docker-compose -v
   docker-compose --help
   docker-compose config
   docker-compose up
   docker ps
   docker-compose down
   
3. Docker-compose config command to verify docker-compose.yml file syntax
4. docker-compose up to create services with multiple containers
5. docker-compose down to shutdown all containers

      Docker Compose(SCALE,CONFIG,UP,DOWN)
      
1. How to scale up services (containers) with docker-compose scale
2. Docker-compose.yml with depends_on to include dependency from one container to another
3. Docker-compose.yml to expose ports for containers
    
    docker-compose up -d
    docker-compose up -d --scale web=4
    docker ps
    
                 version: "3.7" 
                 
                 services:
                   web:
                     image: nginx
                     depends_on:
                       - database
                   database:
                     image: postgres
   docker-compose config
   docker-compose up -d
   
   
                 version: "3.7" 
                 
                 services:
                   web:
                     image: nginx
                     depends_on:
                       - database
                     ports:
                       - "8975:80"
                   database:
                     image: postgres
    
    docker-compose up -d
   
   
    


C) Manage Data with Docker
          By default Docker does not persist data
          To persist Data,Docker Provides 3 options
             Volume, BindMounts and tmpfs(linux only)
             
             docker run -it -v d:/data:/data alpine /bin/sh
1. How docker manage data
2. what all options docker provide to persist data
3. Default behavior of container layer
4. what is container layer
5. how container data can be stored in host machine

D) Docker Volume(Create,Inspect,Prune,Mount)

1. How to create volume with docker
2. How to mount docker volume to container with option -v & --mount
3. HOw to persist container data on to docker volume permanently
4. How to inspect any volume
5. How to list down volumes
6. Brief about volume prune & remove commands to free up the space by unused volumes
7. How to share container data with another containers
      docker volume --help
      docker volume ls
      docker create vol-demo-test
      docker volume ls
      docker run -it -v vol-demo-test:/data alpine /bin/sh
      docker stop container number
      docker rm container number
      docker run -it -v vol-demo-test:/data alpine /bin/sh
      
      docker run -it -v vol-demo-test:/data busybox /bin/sh
      
      docker run -it --mount source=vol-demo-test,destination=/data busybox /bin/sh
      
      docker run -it --mount source=vol-demo-test,destination=/data alpine /bin/sh
      
      docker volume inspect vol-demo-test
      
      Docker Bind Mount to persist container data on Host machine
      Docker Volume Versus Bind Mount
      Volumes - How to Create Backup, Restore or Migrate.
E) Docker Swarm-Swarm Manager, Worker, Swarm Mode, Swarm nodes
      How to create Swarm Cluster with 2 Managers and 2 Workers
      How to create Swarm Services on Swarm Cluster 
      Service Update,Rollback,Scale&Replicas
