## This Tutorials will explains the DockerFile.

1. when we build our own image then it more convienient way to use a DockerFile.
2. A DockerFile is a text file which has a series of instruction on how to build our images.

**_DockerFile_** : 
  - it is set of instruction to create a docker image.
  - DockerFile is a text file that contains all the commands that would normally needs to be executed manually in order to build
    a docker image.
  - DockerFile is always aligned on any base images.
  - Docker daemon build docker images automatically by reading the instructions from the DockerFile.
  
### DockerFile Instructions: 
  
   - **.dockerignore** : 
   
   - **FROM** : defines the base image to start the build process.
   
   - **MAINTAINER** : declares the author who has generated this image.
   
   - **ENV** : sets environment variable.
   
   - **RUN** : executes any commands in a new layer on top of the current image and commits the result.
               commands like, shell command or if we want to install something then we use the command to execute something then
               we specify those commands by with RUN.
               This RUN command is used to build/customized the images. that's why it runs during the contianer build process.
               e.g.: RUN apt-get update && apt-get install java8
               
   - **CMD** : provides default for executing container.
               This is also a kind of command only but it is an executable command.
               the specified command here executes after container is completely built and during container initialization.
               like if you want to specify to print something or any just executable command.
               e.g.: CMD echo "hello from container";
                     CMD date;
                    
   - **ENTRYPOINT** : configures a container that will run as an executables.
                      basically this the first command which get executed after container is built completely.
                      this overrides the CMD command.
                      like if we want to execute any file or want to run any process as soon as the container is ready then
                      we can specify those commands here.
   
   - **ADD** : copies new files or directory or remote file to container.
               prefered to use _CPOY_ instead of _ADD_.
               ADD [source_file_directory] [destination file directroy]
               ADD /my_files_on_host_machine/my_folder_on_container's_own_directory.
               
   - **COPY** : copies new files or directories to container.
                  
   - **EXPOSE** : used to associate a specific port to enable networking between the running process inside container and host.
                  in simple word, the port on which container will listen for any networking activity.
                  
   
   - **VOLUME** : used to mount the volume specified on host machone or can be used the existing volume avaibale on host machine.
   
   - **USER** : sets the username for the following RUN/CMD/ENTRYPOINT commands.
   
   - **WORKDIR** : sets the working directory.
   
   - **#** : used to specify a comment.
   
   
   
   
