## This Tutorials will explains the DockerFile.

1. when we build our own image then it more convienient way to use a DockerFile.
2. A DockerFile is a text file which has a series of instruction on how to build our images.

**_DockerFile_** : 
  - it is set of instruction to create a docker image.
  - DockerFile is a text file that contains all the commands that would normally needs to be executed manually in order to build
    a docker image.
  - DockerFile is always aligned on any base images.
  - Docker daemon build docker images automatically by reading the instructions from the DockerFile.
  
**DockerFile Build Process** :
  - To build a docker file we use below command.
        
            docker build <some_arguments> <.>
  - The above command will be ran by docker deamon,not by the CLI.
  - The build process first sends the entire context to the docker deamon, context means the available files inside the directory. that's why it is advisable to place a dockerfile which requires to be build shuold be placed in a sperate directory.
  - **Dockerfile** is standard naming convention to create a docker file.
  - when we build the dockerfile then we need to run the docker build command inside the directory where the dockerfile is present else we need to use **-f** to specify the dockerfile location explicitly.
    
        docker build DockerFile .
  - so the docker daemon will look for the DockerFile in the current directory and build the docker images in the current directory.
    
        docker build -f /path/to/a/dockerfile .
  - so in the above case, the deamon will search for the docker file in the specified path and build the docker image in the current directory.
  - if we want to tag the docker images the use **-t** flag while building.
  
          docker build -t <repository_name>/<image_name>:<tag_name> .
  - if we want to build the same images in multiple tags then we ccan specify the muiltple **-t** flag and build the images.
      
          docker build -t <repository_name>/<image_name>:<tag_name> -t <repository_name><image_name>:<tag_name> .
         
          e.g.: 
          docker build -t ravi115ranjan/myubuntu:0.1.ravi -t ravi115ranjan/myubuntu:latest .
  - Dockerfile syntax will be validated by docker deamon before it starts building the docker images.
  - The Docker daemon runs the instructions in the Dockerfile one-by-one, committing the result of each instruction to a new image if necessary, before finally outputting the ID of your new image. The Docker daemon will automatically clean up the context you sent.
  -  
### DockerFile Instructions: 
  
   - **.dockerignore**
            
        a. Before the docker CLI sends the context to the docker daemon, it looks for a file named .dockerignore in the root directory of the context.
        b. If this file exists, the CLI modifies the context to exclude files and directories that match patterns in it.
        c.  This helps to avoid unnecessarily sending large or sensitive files and directories to the daemon and potentially adding them to images using ADD or COPY.
        d. exmaple: create a .dockerignore file and place the below contents.
                # comment
                */temp*
                */*/temp*
                temp?
       docker-cli will skip all the files specifed at above pattern while serving files to docker deamon.              
   
   - **FROM** : defines the base image to start the build process.
                syntax: 
                      
                        FROM <image> [AS <name>]
                        or
                        FROM <image>[:<tag>] [AS <name>]
                        or
                        FROM <image>[@<digest>] [AS <name>]
                                                  
   
   - **MAINTAINER** : declares the author who has generated this image.
   
   - **ENV** : sets environment variable.
              
                      ENV <key> <value>
                      ENV <key>=<value> ...
   
   - **RUN** : executes any commands in a new layer on top of the current image and commits the result.
               commands like, shell command or if we want to install something then we use the command to execute something then
               we specify those commands by with RUN.
               This RUN command is used to build/customized the images. that's why it runs during the contianer build process.
               e.g.: RUN apt-get update && apt-get install java8
               so basically RUN has two forms: 
                                    
                    RUN <command> 
                    (shell form, the command is run in a shell, which by default is /bin/sh -c on Linux or cmd /S /C on Windows)
                    
                    RUN ["executable", "param1", "param2"] (exec form) like RUN date || RUN echo "hello from docker"
         
       we use backslash(\) in shell to run a single line instruction on to next line. same can be used with RUN command too.
                e.g.: 
                  
                        RUN set -eux; \
                                 { \
                                      echo 'Package: php*'; \
                                      echo 'Pin: release *'; \
                                      echo 'Pin-Priority: -1'; \
                                  } > /etc/apt/preferences.d/no-debian-php

   - **CMD** : provides default for executing container.
               This is also a kind of command only but it is an executable command.
               the specified command here executes after container is completely built and during container initialization.
               like if you want to specify to print something or any just executable command.
               e.g.: CMD echo "hello from container";
                     CMD date;                                
    
              CMD ["executable","param1","param2"] (exec form, this is the preferred form)
              CMD ["param1","param2"] (as default parameters to ENTRYPOINT)
              CMD command param1 param2 (shell form)

   - **LABEL** :
                The LABEL instruction adds metadata to an image. A LABEL is a key-value pair. To include spaces within a LABEL value, use quotes and backslashes as you would in command-line parsing. 
                A few usage examples:
  
                      LABEL "com.example.vendor"="ACME Incorporated"
                      LABEL com.example.label-with-value="foo"
                      LABEL version="1.0"
                      LABEL description="This text illustrates \
                      that label-values can span multiple lines."
  
        Define the multiple LABEL in single line: 
        
          LABEL multi.label1="value1" multi.label2="value2" other="value3"
          or
          LABEL multi.label1="value1" \
                    multi.label2="value2" \
                    other="value3"
   we can label as below :
   
                  "Labels": {
                                  "com.example.vendor": "ACME Incorporated"
                                  "com.example.label-with-value": "foo",
                                  "version": "1.0",
                                  "description": "This text illustrates that label-values can span multiple lines.",
                                  "multi.label1": "value1",
                                  "multi.label2": "value2",
                                  "other": "value3"
                              },

   - **ENTRYPOINT** : configures a container that will run as an executables.
                      basically this the first command which get executed after container is built completely.
                      this overrides the CMD command.
                      like if we want to execute any file or want to run any process as soon as the container is ready then
                      we can specify those commands here.
                      
                      ENTRYPOINT has two forms: 
                      
                      
                             ENTRYPOINT ["executable", "param1", "param2"] (exec form, preferred)
                             ENTRYPOINT command param1 param2 (shell form)

   
   - **ADD** : copies new files or directory or remote file to container.
               prefered to use _CPOY_ instead of _ADD_.
               ADD [source_file_directory] [destination file directroy]
               ADD /my_files_on_host_machine/my_folder_on_container's_own_directory.
               ADD has two forms: 
               
                  
                    ADD [--chown=<user>:<group>] <src>... <dest>
                    ADD [--chown=<user>:<group>] ["<src>",... "<dest>"] (this form is required for paths containing whitespace)

   - **COPY** : copies new files or directories to container.
                COPY has two forms: 
                  
                  
                   COPY [--chown=<user>:<group>] <src>... <dest>
                   COPY [--chown=<user>:<group>] ["<src>",... "<dest>"] (this form is required for paths containing whitespace)

   - **EXPOSE** : used to associate a specific port to enable networking between the running process inside container and host.
                  in simple word, the port on which container will listen for any networking activity.
                  You can specify whether the port listens on TCP or UDP, and the default is TCP if the protocol is not specified.


                  
                  Syntax: 
                  
                  EXPOSE <port> [<port>/<protocol>...]
                 
                  e.g.: 
                  EXPOSE 80/tcp
                  EXPOSE 80/udp
   
   - **VOLUME** : used to mount the volume specified on host machone or can be used the existing volume avaibale on host machine.
   
                  VOLUME ["/data"]
        
   - **USER** : sets the username for the following RUN/CMD/ENTRYPOINT commands.
                Syntax: 
                The USER has two forms: 
                
                 USER <user>[:<group>] or
                 USER <UID>[:<GID>]
       the USER instruction sets the user name (or UID) and optionally the user group (or GID) to use when running the image and for any RUN, CMD and ENTRYPOINT instructions that follow it in the Dockerfile.
       
   - **WORKDIR** : sets the working directory.
   
   - **_#_** : used to specify a comment.
   
 
 Samples: 
 
 # Nginx
#
# VERSION               0.0.1

FROM      ubuntu
LABEL Description="This image is used to start the foobar executable" Vendor="ACME Products" Version="1.0"
RUN apt-get update && apt-get install -y inotify-tools nginx apache2 openssh-server

   
   
