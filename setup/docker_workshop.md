# Notes to use Docker for Open Data Workshop 1

## Requirements

Docker should work on a wide range of operating systems, including
Mac OS, Windows, and Linux.  It will require around 15 GB of hard-drive
space, and may have problems on operating systems more than a few years old.
If you find Docker does not work well on your computer, you might instead
try [running with either Azure or mybinder](./README.md).

## Installing Docker

First, install Docker Community Eddition.  This is a free download from
the "Docker Store": https://www.docker.com/community-edition

### Video Help

For a video guide, see the 
[Docker Video Example](https://labcit.ligo.caltech.edu/~jkanner/losc/docker-odw-2018.mov).

If working on Windows, an intro to [Docker on Windows](https://youtu.be/S7NVloq0EBc) could also help.

### Create and start the Docker container

The pycbc Docker image includes most of the software needed for
these tutorials.  To run this on your laptop, you will need to:

 * Pull an image of a machine loaded with pycbc and parts of LALSuite (6 GB download!)
 * Start the docker container
 * Install gwpy using pip
 * Clone the tutorials for the workshop
 * Start a Jupyter Notebook server

To do this, copy and paste each of the following commands into a terminal
window:
```
docker pull pycbc/pycbc-el7:v1.9.2  
docker run -it -p 8888:8888 --name pycbc_odw pycbc/pycbc-el7:v1.9.2 /bin/bash -l
pip install gwpy
git clone https://github.com/gw-odw/odw-2018.git
jupyter notebook --ip 0.0.0.0
```

If you are prompted to "Accepting one-time-token-authenticated connection from 127.0.0.1",
you will need to type `A` for "Always", and then `Q` for Quit

```
A
Q
```
Then, copy and paste the displayed URL into your browswer to access the notebook server.


### Stop the Docker container

If you want to shutdown the notebook server, type control-C in the terminal window.

Then, you can "stop" the Docker containter by typing `exit`.

### Where did my files go?!?

Any files you saved in the Docker container are still there - inside the
Docker container.

To see a list of exisiting containers, use the command:

```
docker ps -a
```

You should see your container listed as `pycbc_odw`.  To start the container,
type into the terminal window:

```
docker start -ai pycbc_odw
jupyter notebook --ip 0.0.0.0
```

Any files you saved in the container should still be there.


### More information

For more notes on using Docker, including instructions for copying files
from the container onto your laptop, see [docker.md](./docker.md) in this directory.

