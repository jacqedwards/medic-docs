# Install

## Intro

This document should help you quickly install the necessary tools to download and run the Medic Mobile public docker image.

## Download Docker

Mac OSX:
` Docker for Mac` : 
[Docker for Mac](https://download.docker.com/mac/stable/Docker.dmg)

Windows:
` Docker for Windows` :
[Docker for Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)

Open the installation and follow the instructions

Launch Docker. 

Performance Settings that can be changed:
Memory: 4 GiB
CPUs: 2

## Download Medic Mobile Image:

Open your terminal and run this command:

```
docker pull medicmobile/medic-os
```

## Usage

To run the docker container, simply enter this command:

```
docker run -t -p 5988:5988 -p 80:80 -p 443:443 medicmobile/medic-os
```

If you wish to run multiple projects, you will need to change the above ports:

```
docker run -t -p 5989:5988 -p 81:80 -p 444:443 medicmobile/medic-os
```

Note the `New CouchDB Administrative User` and `New CouchDB Administrative Password` in the output terminal. These are the login credentials to use in the next step.


If you have any **port conflicts**, substitute with an unused local port. For reference, the port forwarding syntax is as follows `<forwarded-port>:<port-from-docker>`

To find out which service is using a conflicting port:

On Linux
```
sudo netstat -plnt | grep ':<port>'
```

On Mac (10.10 and above)
```
sudo lsof -iTCP -sTCP:LISTEN -n -P | grep ':<port>'
```

After bootstrap, visit: https://localhost and accept the self-signed SSL certificate warning.
(Use the login credentials shown in the terminal output when the docker container was launched).
## Helpful Docker commands

```
# list running containers
docker ps

# ssh into container/application
docker exec -it <container_name> /bin/bash


# View container stderr/stdout logs:
docker logs <container_name>
```

## Clean Up

```
# list running containers
docker ps

# list all available docker containers with their status
sudo docker ps -a

# stop container
docker stop <container ID>

# start container
docker start <container ID>

# list all stoped containers 
docker ps -f "status=exited"

```
