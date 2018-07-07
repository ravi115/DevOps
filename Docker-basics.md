## This Docker tutorials provides information about how to get most out of docker using terminal.
**what is Container and images?**
  - An **_image_** is an executable package that includes everything needed to run an application.
    the code, a runtime, libraries, environment variables, and configuration files.
  - A **_container_** is a runtime instance of an image--what the image becomes in memory when executed 
    (that is, an image with state, or a user process). You can see a list of your running containers with the command, docker ps, 
    just as you would in Linux.
    
**Docker**
  1. basically docker toolset consists of three main parts: 
    - docker deamon
    - docker client
    - docker hub
  
  2. when we work with docker client, the commands are being sent to the docker deamon which interprets the command and execute.
  3. To list out all the commands supported by Docker.
    
          docker help
  4. To get the list of available command inside any command use below syntax.
  
         docker <command> --help
         
         e.g.: Docker images --help
  5. To check the Docker version.
      
          docker --version
        
  6. To get the Docker info.
  
          docker info

  7. To get the list of available images on docker hub, jsut run below commands.
  
          docker search <image_name>
          e.g.: docker search hello-word.
          - it will list all the images which names contains the 'hello-word' string and display it in descending order from
            top to bottom based on the number of people have downloaded the images.
  
  8. To tun a docker images in interactive mode, basically want to login to that images.
  
          docker run -i -t <image_name>
          e.g.: docker run -i -t nginx
          - what will happen when above command run.
          - docker first look for that specified image in local repository/directorty. if it unable to finds it thenit will
            pull from the internet and then start the images basically start the running continer and we can access the nginx.
          
          - we can also combined the -i  and -t together.
            docker run -it <image_name>
          
  9. we can multiple tags or version of any images, then how do we specify it to download.
      
          docker run-it <image_name>:<tag>
          -if we don;t specify the tag, it will download the default tag images i.e. latest.
          -the above command gets resolved into docker run -it <image_name>:latest
          
   
  10. we can also specify the command how we want to launch the container.
  
          docker run -it --name <container name> <image_name> <COMMAND>
          
          e.g.: docker run -it --name redis1 redis sh
          - after running above command a redis1 named container will be launched for redis image and open in a shell mode.
          
            
