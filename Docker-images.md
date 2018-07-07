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

        docker run -d --name <customer_iamge/container_name> -p <image>
        -The above container will be published to a  random port. since we havw used the -p paramter.
