## This Tutorials will display the information about docker contianer.

1. To work with docker container, always start your command with docker container <sub_commands_supported_by_docker_container>

2. To list out all the docker container command, use help.
 
        docker contianer --help
3. docker ps command display all the process/ containers.
  
        docker ps
        - it list all the running containers.
        docker ps --all
        - it list all the containers.
        
4. when we run docker ps command then we see,
    
    - CONTAINER_ID : A unique Id given to every container.
    - IMAGE: The name of the image for which the container was running.
    - COMMAND: important point, while launching the continer we specify some command how we want to run the container.
    - CREATED: when the container was created.
    - STATUS : running, exited, etc.
    - NAME : name of the contianer.
    
5. we can start/relaunch the stopped container, use start command.

          docker start <container_id>
          e.g.: docker start dba9538dd901
    
6. we can start/relaunch the container with in interactive mode by specifying the command the -i.

          docker start -i <container_id>
          
7. we can attach a container with _attach_ command.

          docker attach <container_id>
          
8. To stop a container.

          docker stop <container_id>
         
9. To delete a contianer.

         docker rm <container_id>/<container_name>
         
10. To restart a container.
  
         docker restart <container_name>
         - to go inside the container after restarting the container using above command, we have to execute one more command.
         docker attach <container_name>
         - after this, it will take us inside the container.
          
 
 **Linking Containers**
 
     1. if want to link containers for some  reason the we should go for this concept. 
     2. the official way of linking the docker containers is Docker Compose.
     3. why container linking?
        - A simple answer is like we have web pages running where the database is on  different machine, even some other         resources are on different machine and how they communicate each other by means of some connection medium.
        - same concept we want to implement incase of docker contianers. 
     4. if we want to run a container for redis database and want to use this redis server in other container then we should link
        the containers and provide a connection medium between them.
        
        a.> first launch the redis container.
        
            docker run -d --name redis1 redis
        
        b.> the command to link a new container to existing container.
        
           docker run -it --link <running_container>:<alias_name_of_the_running_container_to_this_container> --name <container_name> <image_name>
           
           e.g.: docker run -it redis1:redis --name redisclient ubuntu
       
      5. we can go to the redisclient ubuntu container and open /etc/hosts and see the redis port menstioned here.
      6. we can even open environment variable into the redisclient ubuntu container to see the redis env variables.
     
     
        
