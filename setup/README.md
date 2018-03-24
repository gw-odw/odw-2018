
# Setup Hints

Here are some hints to help you run excercises for the workshop.

## What software do you need?

Many of these excercises use Jupyter notebooks with python
kernals.  Where possible, the excercises are designed to work using
python 2 or 3.  They should all work with python 2.

The included notebook [check_setup.ipynb](check_setup.ipynb) can be
used to see some of the required python packages, and to check if they
are installed.

## What's python?!

If you have never worked with Python before, we strongly encourage you to practice some before the workshop:
 * The official [Python for Beginner's page](https://www.python.org/about/gettingstarted/) provides links to a variety of tutorials and examples
 * We like [Google's Python Class](https://developers.google.com/edu/python/) as a way to learn the basics (try the lecture videos)

## How to work with Jupyter Notebooks

If you've never used a Jupyter Notebook before, you can see a short video here:
https://labcit.ligo.caltech.edu/~jkanner/losc/online_tutorial_demo.mov

## How to access the software you will need

### Option 1

Use a Docker Container:

This option will allow you to install a complete software enviornment
on you laptop.  This is a great option and should work well on
nearly any operating system.  However, it requires around
6 GB of harddrive space.  

 * For setup instructions specific to this workshop, see [docker_workshop.md](./docker_workshop.md) in this directory.
 * For a short introduction to Docker, see [docker.md](./docker.md) in this
 directory.

### Option 2 (No software installation required!)

Run the tutorials remotely using Microsoft Azure:
 * https://notebooks.azure.com/losc/libraries/odw-2018 (Requires sign-in with a free Microsoft account)
 * To run these notebooks
   * sign up for a free account
   * click the "clone" button in the above link to make a copy of the notebooks that you are free to edit, run, and are persistant.
   * You should be brought to your fork of the tutorials and you can open them up and run directly in the browser.

### Option 3

Run the tutorials remotely using mybinder:
 * https://mybinder.org/v2/gh/gw-odw/odw-2018/master

### Option 4

Install the software you need:
 * Suggestions for python installations at https://losc.ligo.org/tutorial00/
 
 * These tutorials will require a number of specialized python
   packages.  For details, see the packages and pip commands listed in 
   [check_setup.ipynb](./check_setup.ipynb)

