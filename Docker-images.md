## This tutorials will provides information about the images.

1. To run a docker images.

        docker run <image_name>
        
2. To run a docker image in interactive mode.

        docker run -it <image_name>
        
3. To run a docker image in interactive mode and want to specify the name of the image.

        doccker run -it --name <my_custome_image_name> <image_name>

4. To pull an images from private/public repo and store it on locally, we can use pull command to download that image and store it to
    local machine repo.
    
        docker pull <image_name>
        
5. To run a docker in detach mode.

        docker run -d <image_name>

6. To stop a container/image.

        docker stop <custom_image_name>
        
7. To delete an image.

        docker rmi <image>
        
8. If we want to publish the port of an image to external world, then we use -p parameter.

        docker run -d --name <customer_iamge/container_name> -p 80:<port_number> <image>
        -The above container will be published to a  random port. since we havw used the -p paramter.

9. We can also create our own image.
       
       - in order to create our own image, first we need a base image. just say like operating system. on top of it, we will
          be downloading various software.
        - Let's create an image using ubntu.
        - follow the below steps.
        
               docker search ubntu
               -list all the available ubuntu.
               docker pull ubuntu:latest
               -it will pull the latest version of ubntu.
               docker run -it --name mycontainer --rm ubuntu:latest
               - this will run the ubuntu image in intractive mode.
               - then will be dopwnloading and installing the list of softwares inorder to customize our image.
               - the rm flag will remove/delete the container on termination.
  
  
 **Concept  of Docker Hub**
 
        a.> when we lauch a container it's always refers to the master images.
        b.> so when we apply any changes on the images and we want this customized images will be available to other places,
            like in other docker engines, then we need to save this changes in some cloud.
        c.> docker Hub is a repository where we can save our customed images on docker cloud.     
        d.> we need to create our own repository on docker hub.
   [click here](https://hub.docker.com/) to create an account/ repository on docker.
   
   **steps to commit the changes in docker hub repository.**
        
        1. docker commit <container_id/container_name> <dockerhub_username>/<repository_name>:<tag>
        
        - here the tag is optional. if we don;t specify the tag it will just point to latest.
        - repository_name is the customed image name.
        e.g.: docker commit mycontainer ravi115ranjan/my_ubuntu:tag1
                        or
              docker commit hq243hkjfn12313 ravi115ranjan/my_ubuntu
                        or
              docker commit mycontainer ravi115ranjan/ubuntu:tag4.0  
         
        2. How to run the images just created above.
        
           docker run -it --name <some_name> <docker_hub_username>/<repository_name>:tag
           e.g.: docker run -it --name mynewcontainer ravi115ranjan/my_ubuntu
           
           
        3. how to push the created repository in docker hub cloud.
           - first login to docker hub on terminal using
             docker login
           - it will ask for few information, after providing the information it will successfully logged in.
        
        4. then use below docker command to push the repository.
            
           docker push <dockerhub_username>/<repository_name>
           e.g.: docker push ravi115ranjan/my_ubunutu.
          
           - here docker is enough smart while pushing the repositoy. docker already contains ubuntu. so it will only push the
           changes on top of it and re-construct the images on the cloud on our repository.
        

        
