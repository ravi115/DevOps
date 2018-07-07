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
    - IAMGE: The name of the image for which the container was running.
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
