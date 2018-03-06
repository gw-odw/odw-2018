# What is docker?

Docker is an open platform for developing, sharing, and running applications.  It allows you to run applications in a loosely isolated environment called a *container*.  If you're familiar with virtual machines, containers are similar in spirit, but lighter weight and run directly in the host machine's kernel, making performance comparable to native applications.  

There are community and enterprise editions of docker with support for multiple OS's.  For more details and installation instructions see the [docker docs](https://docs.docker.com/engine/docker-overview/).

# Images and containers

We will be using docker to avoid having to separately install package dependencies, setup local environments, etc.  Applications are shared in *images*, read-only templates for creating a docker *container*.  [Docker hub](https://hub.docker.com/) is an image hosting service, and the default location that docker looks for images in.

Containers are created from images; they can be created, started, stopped, moved, and deleted.  They're relatively isolated from other containers and the rest of your machine.

# Example: minimal Jupyter notebook environment

Assuming you've installed docker and have the daemon running on your machine, let's work on setting up a minimal Jupyter notebook enironment as a use case.

## Pulling the image

The image we'll be using is the [Jupyter project](https://hub.docker.com/u/jupyter/)'s [minimal notebook](https://hub.docker.com/r/jupyter/minimal-notebook/).

Download the image with a `docker pull`:

```bash
docker pull jupyter/minimal-notebook
```

This pulls the image from Docker Hub, but you won't see it in your working directory.  Docker has default locations on your file system for storing things, and their content is rather opaque to users; you're intended to manage images and containers entirely through `docker` commands.

To see the images on your machine, run `docker images`.  You should see `jupyter/minimal-notebook` there.

## Starting a container

Now let's start a container from this image:

```bash
docker run -it -p 8888:8888 --name test_notebook jupyter/minimal-notebook
```

This will create and start a new container based on the `jupyter/minimal-notebook` image, where `-i` indicates we want the container to be run interactively and `-t` attached to our terminal, and `--name` gives our container a name for easily referring to the container later.  `-p 8888:8888` exposes our containers port 8888 (which the jupyter notebook uses by default) and forwards to our machine's port 8888.  If you're local port 8888 is already in use, you can forward to a different port, e.g. `-p 8890:8888`.

This will start a container, and based on the instruction in the image, will automatically launch a jupyter notebook and print a link to it.  If you didn't map to a different local port, just follow the link, otherwise cut and paste the link and change the port to the port you're forwarding to.

**note**: If you are using an older OS (without Hyper-V support) where it was necessary to use docker toolbox, you may need to replace `localhost` with the IP address returned by `docker-machine ip`.

## Installing things within the container

Now that Juptyer is up and running, you can create and interact with a notebook as you normally would.  Since this is a minimal notebook, it only comes with the software necessary for launching jupyter notebooks.  Let's say you want to install `numpy` now.  This can be done with `pip` as usual, either in a jupyter notebook with `!pip install numpy`, or by launching a terminal session from jupyter and running the pip command there.

## Managing containers

If you open a new (local) terminal, you can see what containers are currently running with `docker ps`, and see all containers (including stopped containers) with `docker ps -a`.

To stop the container you can `ctrl-c` from the terminal running the container, or run `docker stop test_notebook` from another terminal.  To delete the container once it has been stopped use `docker rm test_notebook`.

To start an existing (stopped) container (e.g., listed by `docker ps -a`):

```bash
docker start -ai test_notebook
```

where `-a` attaches `STDOUT`/`STDERR` and `-i` makes it an interactive session by connecting `STDIN`.

## File transfers

To copy files in from your local filesystem use `docker cp`, e.g.:
```bash
echo "this is a test" > test.txt
docker cp test.txt test_notebook:/home/jovyan
```

If you will be doing a lot of file movement, you can mount a local volume in a container at the time of creation with `-v`, e.g.:
```bash
mkdir test_data
touch test_data/test.1
touch test_data/test.2
docker run -it -p 8888:8888 --name test_notebook -v $PWD/test_data:/home/jovyan/test_data jupyter/minimal-notebook
```

This will expose the contents of the local director to the container, and any changes made in the container to the directory's contents will be reflected in the local directory.
