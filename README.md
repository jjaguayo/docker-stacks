# Nengo running on a Jupyter Notebook with Scientific Python Stack

## What it gives you 

* Scientific Python Stack
* Nengo 2.3.1

# Basic Usage

After installing Docker, the following command downloads an image from DockerHub and starts a container using the image `jjaguayo/nengo-scipy-jupyter`. The image has a Jupyter notebook server, listening for HTTP connections on port 8888, capable of 
running Nengo models.

```
    docker run -it --restart=always -p 8888:8888 jjaguayo/nengo-scipy-jupyter
```

This [link](https://github.com/jupyter/docker-stacks/tree/master/scipy-notebook)
gives more information on the Scientific Python Stack (provided by Jupyter) used
as a base for this Docker image.

This [link](https://pythonhosted.org/nengo/index.html) gives more information on
Nengo, a Python library for building and simulating large-scale brain models.

# Building a local image

If you do not care to download the image from DockerHub, clone this repository
and run the following from the directory containing the file `Dockerfile`.

```
    docker build -t <your_local_build_name> .
    docker run -it --restart=always -p 8888:8888 <your_local_build_name>
```

This builds an image called `<your_local_build_name` and runs it in a 
restartable container. 

# Installing Docker

If you have not installed Docker, the following links provide instructions for
installing on

* [Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/) (14.04 or later)
* [Mac OS X](https://docs.docker.com/docker-for-mac/install/) (Hardware releases 2010 or later)
* [Windows 10](https://docs.docker.com/docker-for-windows/install/)

Note that there are minimum requirements for each platform so check the 
[Docker documentation](https://docs.docker.com/engine/installation/) for more
information on what is supported.
