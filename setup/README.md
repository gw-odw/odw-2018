
# Setup Hints

Here are some hints to help you run excercises for the workshop.

## What software do you need?

Many of these excercises use Jupyter notebooks with python
kernals.  The notebooks are designed to work in python 3, using the
[IGWN Conda Distribution](https://computing.docs.ligo.org/conda/)

## What's python?!

If you have never worked with Python before, we strongly encourage you to practice some before the workshop:
 * The official [Python for Beginner's page](https://www.python.org/about/gettingstarted/) provides links to a variety of tutorials and examples
 * We like [Google's Python Class](https://developers.google.com/edu/python/) as a way to learn the basics (try the lecture videos)

## How to work with Jupyter Notebooks

If you've never used a Jupyter Notebook before, you can see a short video here:
https://labcit.ligo.caltech.edu/~jkanner/losc/online_tutorial_demo.mov

## How to access the software you will need

### Option 1 (Requires software installation, Linux or Mac OS)

Use the conda IGWN distribution, following instructions on the [IGWN Conda distribution page](https://computing.docs.ligo.org/conda/)


### Option 2 (No software installation required!  Any OS!)

Run the tutorials remotely using Google co-lab

 * Navigate to https://colab.research.google.com
 * Select the "github" option
 * Search for "gw-odw/gw-2018"
 * Click on the notebook of choice to open
 * In the first cell of each notebook, remove the comment (remove the `#`) from the line that begins `#! pip install`
 * Run the first cell to install the software, then restart the runtime and run all cells using the menu bar at the top

### Option 3 (No software installation required! Any OS!)

Run the tutorials remotely using mybinder, by clicking the badge.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/gw-odw/odw-2018/master)

### Option 4

Install the software you need:
 * Suggestions for python installations at https://losc.ligo.org/tutorial00/
 
 * These tutorials will require a number of specialized python
   packages.  For details, see the packages and pip commands listed in 
   [check_setup.ipynb](./check_setup.ipynb)

