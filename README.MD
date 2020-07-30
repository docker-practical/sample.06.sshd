# Overview

The following Dockerfile sets up an SSHd service in a container that you can use to connect to and inspect other container’s volumes, or to get quick access to a test container

https://docs.docker.com/engine/examples/running_ssh_service/

# Note

## Replace your password
RUN echo 'root:admin@123' | chpasswd


## Build image
$ docker build -t hg_sshd_image .

## Run a container test, random port
$ docker run -d -p 22 --name hg_sshd_container hg_sshd_image

## Check port running
$ docker port hg_sshd_container
Example: 22/tcp -> 0.0.0.0:32768


## Inspect on Docker daemon's host
$ ssh root@192.168.1.2 -p 32768
or $ ssh root@localhost -p 32768


# Clean up
$ docker container stop hg_sshd_container
$ docker container rm hg_sshd_container
$ docker image rm hg_sshd_image