# Nengo running on a Jupyter Notebook with Scientific Python Stack

## What it gives you 

* Scientific Python Stack
* Nengo 2.3.1

# Basic Use
The following command starts a restartable container with a Jupyter notebook 
server listening for HTTP connections on port 8888 and capable of running
Nengo models.


```
    docker run -it -restart=always -p 8888:8888 jjaguayo/nengo-scipy-jupyter
```

This [link](https://github.com/jupyter/docker-stacks/tree/master/scipy-notebook)
gives more information on the Scientific Python Stack (provided by Jupyter) used
as a base for this Docker image.

This [link](https://pythonhosted.org/nengo/index.html) gives more information on
Nengo, a Python library for building and simulating large-scale brain models.
