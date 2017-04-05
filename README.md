# Nengo running on a Jupyter Notebook with Scientific Python Stack

## What it gives you 

* Jupyter Notebook 4.3
* Scientific Python Stack
* Python 3
* Python 2
* Nengo 2.3.1

# Basic Usage

After installing Docker, the following command downloads an image from DockerHub 
and starts a container using the image `jjaguayo/nengo-scipy-jupyter`. The image 
has a Jupyter notebook server, listening for HTTP connections on port 8888, 
capable of running Nengo models.

```
    docker run -it --restart=always -p 8888:8888 jjaguayo/nengo-scipy-jupyter
```

This [link](https://github.com/jupyter/docker-stacks/tree/master/scipy-notebook)
gives more information on the Scientific Python Stack (provided by Jupyter) used
as a base for this Docker image.

This [link](https://pythonhosted.org/nengo/index.html) gives more information on
Nengo, a Python library for building and simulating large-scale brain models.

## Stopping a running container

The command above starts a restartable container that restarts if the application
exits.

If you want to stop a running container, two commands can be used, ```docker ps```
and ```docker stop```. The first command gives you a list of running containers
and their ids.  The second command stops the running container given the 
container id. For example, the following helps you find the id of the running 
container you want to stop (using ```docker ps```) and the second command stops 
the running container.

```
    docker ps
    docker stop <container_id>
```

## Running a non-restartable container

The option ```--restart=always``` indicates to Docker that the container should be
restarted if the container is stopped or if the application exits.

If the user wants to change this behavior having the container simply exit and not
restart, replace the ```--restart``` option with ```--rm```. For example,
the following will run a container and not restart it if the application ends or
the container is stopped.

```
    docker run -it --rm -v /home/myhomedir/nbwork:/home/jovyan/work -p 8890:88888 jjaguayo/nengo-scipy-jupyter
```

## Sharing a filesystem between host and container

Data stored in the jupyter notebook can be shared with a directory in your host
using the -v option. For example, the following shares the data stored in the
jupyter notebook with the directory ```/home/myhomedir/nbwork``` on my machine
hosting the container.

```
    docker run -it --restart=always -v /home/myhomedir/nbwork:/home/jovyan/work -p 8888:88888 jjaguayo/nengo-scipy-jupyter
```

Remember to replace ```/home/myhomedir/nbwork``` with the absolute path to the
directory you want to share with the container.

## Using a non-default port

It is possible that port 8888 on your host machine is being used. If so, 
a different host port can be used by changing the first number in the 
```-p``` option. For example, the following uses host port 8890 mapping it to 
port 8888 in the container.

```
    docker run -it --restart=always -v /home/myhomedir/nbwork:/home/jovyan/work -p 8890:88888 jjaguayo/nengo-scipy-jupyter
```

# Building a local image

If you do not care to download the image from DockerHub, clone this repository
and run the following from the directory containing the file `Dockerfile`.

```
    docker build -t <your_local_build_name> .
    docker run -it --restart=always -p 8888:8888 <your_local_build_name>
```

The first command builds an image called `<your_local_build_name>` and the second command runs it in a 
restartable container. 

# Connecting to Jupyter hub

When starting the hub, a URL is provided by the container app. Copy and paste the URL into a browser to connect to the hub.

# Installing Docker

If you have not installed Docker, the following links provide instructions for
installing on

* [Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/) (14.04 or later)
* [Mac OS X](https://docs.docker.com/docker-for-mac/install/) (Hardware releases 2010 or later)
* [Windows 10](https://docs.docker.com/docker-for-windows/install/)

Note that there are minimum requirements for each platform so check the 
[Docker documentation](https://docs.docker.com/engine/installation/) for more
information on what is supported.
