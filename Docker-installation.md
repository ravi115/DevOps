## Getting Started with Docker --------------->

**install docker on ubntu operating system or any linux based operating system**
  1. First need to uninstall the docker from the machine if any instance of docker is installed.

          sudo apt-get remove docker docker-engine docker.io
          
  2. it's always preffered to install the docker using repository.
      - first update the packages.
          
            sudo apt-get update
            
      - Install packages to allow _apt_ to use a repository over _HTTPS_.
            
            sudo apt-get install \
                    apt-transport-https \
                    ca-certificates \
                    curl \
                    software-properties-common
      
      - Add Docker’s official GPG key.
      
            curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add
      
      - verify the key. basically search for last 8 characters string in fingerprint.
          
            sudo apt-get fingerprint
            
           this will return some information which will also have fingerprint key like below.
           9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
           Then take the last 8 character key and verify the key with below command.
           
            sudo apt-get fingerprint 0EBFCD88
      
      -  set up the stable repository.
          
             sudo add-apt-repository \
                "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
                 $(lsb_release -cs) \
                 stable"
           
       - after all the above mandatory steps, it is advisable to update the packages and then install the docker CE.
            
              sudo apt-get update
            
              sudo apt-get install docker-ce
       
       - to verify that docker is installed succesfully, just pull a _hello-world_ images.
       
              sudo docker run hello-world
  
  3. if we want to install any specific version of docker, then we should use below command after setting up the docker repository 
  using the above procedure.
  
        - to list the available repo version.
              
                sudo apt-cache madison docker-ce
                
        - then choose a specific version and install it.
                
                sudo apt-get install docker-ce=<VERSION>

            
