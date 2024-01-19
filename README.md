# Tracer
# GemOS Docker Instance Setup

## 1. Installation

Install Docker on your system by following the instructions for your operating system:

- [Ubuntu Installation](https://docs.docker.com/engine/install/ubuntu/)
- [Mac Installation](https://docs.docker.com/docker-for-mac/install/)
- [Windows Installation](https://docs.docker.com/docker-for-windows/install/)

## 2. Download Docker Image

Download the GemOS Docker image from the following link:
[cs330-gemos.tar.gz](https://cse.iitk.ac.in/users/deba/cs330/cs330-gemos.tar.gz)

## 3. Steps to Create the Docker Container on Unix/Linux

Run the following commands in the terminal (use `sudo` in Linux machines):

```bash
$ docker import cs330-gemos.tar.gz
$ docker image ls  # It will show the newly created image; get its ID (say <image-id>)
$ docker image tag <image-id> cs330
$ docker run -it -p 2020:22 <image-id> /bin/bash  # This should take you to a shell

# In another terminal, type the following command (and exit the shell)
$ docker ps  # Note down container ID using command "docker ps" (say <container-id>)
$ docker container rename <container-id> NameYouWantToUse
```
4. Using the Docker Container

Run the following commands in the terminal:
```bash
$ docker start NameYouWantToUse  # Starts the container
$ ssh -p 2020 osws@localhost  # Should take you to ssh prompt; use password ’cs330’
$ docker stop NameYouWantToUse  # Stops the container
```
Check `docker --help` for more Docker commands.

5. Executing GemOS

Start the container and login. After login, run the following commands in the Docker container terminal:

```bash
$ cd gem5
$ ./run.sh /home/osws/gemOS/src/gemOS.kernel
```
Open another terminal and ssh to the container, then run the following command:
```bash
$ telnet localhost 3456  # Will show you the GemOS console
```
Feel free to explore more about GemOS and its functionalities.

Note: Make sure to replace placeholders such as `<image-id>` and `<container-id>` with the actual values obtained during the setup.
