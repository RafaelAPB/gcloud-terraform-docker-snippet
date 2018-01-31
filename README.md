
# Description
This is a simple working example of how to deploy a container in google compute engine
using terraform and docker.

# Requirements 
* A google project with owner access rights.
* Docker engine.


# Before Start:
Create the credentials.json
 * Google Console -> "APIs & services -> Credentials"
 * Choose create- > "service account key" -> compute engine service account -> JSON (Download)

Build the docker image with: 
````
$ docker build -t gce_mgmt .
````

# Run 
Run the docker container, mapping the directory where the json was downloaded:

```
$ docker run --rm -v $(HOME)/downloads:/opt/downloads -it gce_mgmt
````

copy the json downloaded into the working directory of the container (credentials.json file):
```
$ sudo cp /opt/downloads/project-123141.json credentials.json
```

load the environment variables:
````
$ source load-credentials.sh
````

wait for the the gcp setup.

Initialize terraform:
````
terraform init
````

Deploy the example

````
$ terraform apply
````

Access the ip address shown at the terraform output and check if nginx is running. --profit.

Clean up the deployment
````
$ terraform destroy
````


# Notes
You can access gce instances with the alias: **sshgcp instance**




 


