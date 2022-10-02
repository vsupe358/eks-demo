Things to complete
- This repository hosts a Laravel 9 application which needs to be dockerized.
- The public folder is /public
- There are 2 routes defined in the application /container1 and /container2
  - Both these routes should be working on separate container
  - so if I access /container1 it should be routed to container 1 and same thing for container 2
- storage folder should be available even after the containers are destroyed and recreated

-------------------------------------------------------------------------------------

Resolution:

- Need to build docker image and push it to dockerhub .
- Execute cmds 
	
    docker build -t eks . 
    
	docker tag eks:latest <dockerhub_username>/<repo_name>:<tag>
	
    docker push <dockerhub_username>/<repo_name>:<tag>


- Created terraform folder which includes creation of infrastructue for EKS.
- Execute cmds terraform initialize, terraform plan, terraform apply
- Created Kubernetes folder which includes yaml scripts for pod deployment.
- Created Persistent Volume and attached its claim to pods so we will not loose data.
- ingress.yml having path based routing for different containers. We have to create nginx-ingress controller to access application outside cluster.
