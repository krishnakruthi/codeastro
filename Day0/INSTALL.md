# Installation

If you are using a Windows machine, first check out the setup instructions 
[here](https://github.com/semaphoreP/codeastro/blob/main/Day0/INSTALL_WINDOWS.md). If you are using a Mac, first check out the instructions [at the bottom of this page](https://github.com/semaphoreP/codeastro/blob/main/Day0/INSTALL.md#apple-specific-instructions). Once you've
followed those instructions, come back and continue here.

At the end of the Python installation section, you will run a series of tests that will give you a secret code that indicates Python has been installed successfully! 

### Video Walkthough and Advice on Managing Python Installations ###

Watch this [setup video](https://youtu.be/vpMbZdMeRAs) (23 min) to guide you through the setup process. It gives a short walkthrough of part of the setup process, discusses some details on how conda/pip work, and offers some best practices for managing your Python environment. Note that we are using Discord instead of Slack, so replace all mentions of Slack with Discord. You can also [view the slides here](https://docs.google.com/presentation/d/10PZgGP7SENmOKb6Xji4BX9POtVZcOpIYhaCsWUh-Qco/edit?usp=sharing). 

[![Setup Video](http://img.youtube.com/vi/vpMbZdMeRAs/0.jpg)](https://youtu.be/vpMbZdMeRAs "Setup Video")

### Git ###
If you don't have `git` installed, [install git](https://git-scm.com/downloads). (Windows users can use the `git` installed from WSL)

Then, clone this repository to your machine. It will create a folder called codeastro. 

    git clone https://github.com/semaphoreP/codeastro.git

### Python ###
We recommend you use an Anaconda Python installation. If you don't have such an installation already, use miniconda to install Python and necessary packages. You can download and install
miniconda [here](https://docs.conda.io/en/latest/miniconda.html) (https://docs.conda.io/en/latest/miniconda.html).


---
**Note**

1. When installing miniconda be sure to follow the prompts and say `yes` to running `conda init` at the last prompt! If you don't your terminal may not be able to recognize the `conda` command. If you miss it you can run it manually with:
```
/[conda install directory]/bin/conda init
```

2. Be sure to restart your terminal after installing conda and running `conda init` to apply the changes! Otherwise you will still be left with the unrecognized `conda` command error. 

---

For all Python users, we strongly recommend that you use conda environments to manage multiple Python versions for multiple projects, especially if you already have python installed for other projects. This prevents projects having conflicting dependencies as each project can have its own Python. Let's create an environment for Code/Astro that uses Python 3.10, which is the most up-to-date version of Python.

    conda create -n codeastro python=3.10

Then, any time you want to use this version of Python from the command line, run the following line of code to set Python to point to this version:

    conda activate codeastro

 To verify your installation, run the following line, which will list the path to your python installation. The path should include miniconda/anaconda and codeastro:

    which python

Now that we have a Python environment for this workshop, let's install packages that we need. First we want to install `numpy` through conda so that it is compiled with MKL/BLAS so that we can parallelize linear algebra operations. We'll also install `cython` and `jupyter` notebooks this way if they are not already installed (use `conda list` to check what is already installed in a given conda environment). We're installing cython here because we will need it installed ahead of time for some packages in requirements.txt. 

    conda install numpy cython jupyter pip

We can install the rest of the Python packages listed in our 
[requirements.txt](https://github.com/semaphoreP/codeastro/blob/main/requirements.txt) file through the regular `pip` package manager.
Assuming you followed the instructions above to clone this repository, `cd` into the codeastro folder and run the command:

    pip install -r requirements.txt

You can also install the packages one-by-one by typing, for example:

    pip install matplotlib

Once you've installed all of the requirements, clone the `orbitize!` repository to your machine and run the test suite to make sure everything is working properly. You can use the command sequence below to do this:

    git clone https://github.com/sblunt/orbitize.git
    cd orbitize
    pip install -r requirements.txt
    pip install -e . --upgrade
    pytest --mode codeastro

You may get some warnings, but you should see 0 errors and a secret code at the end of the output. We will ask you for the secret code to check your python installation is all working. 

If you run into any issues, contact us on discord or piazza. We will hold a "virtual office hours" session for 
technical setup questions.


## Visual Studio Code

In this workshop, we are recommending you use Visual Studio Code (VS Code) to develop and test your code. 
As part of the workshop, we will cover skills such as debugging and demonstrate how to do them using VS Code, so it will be easiest to also use it and follow along.
You can download VS Code for free from its official webpage: https://code.visualstudio.com/.

This video (25 mins; last 5 are optional) will take you through setting up your VS Code installation and learning about some of its features:

[![VS Code Video](http://img.youtube.com/vi/yl60qAmmOMM/0.jpg)](https://youtu.be/yl60qAmmOMM "VS Code Video")

The instructions in the video are adapted from the official [Getting Started with Python in VS Code](https://code.visualstudio.com/docs/python/python-tutorial) guide, which you should feel free to use as a reference. That guide is long, and not everything will be needed, so feel free to peruse the documentation, but do not worry if you do not understand certain parts of it (it can get quite advanced!). 

> For Windows users using WSL, install the `Remote - WSL` extension from the Marketplace so you can connect VS Code with WSL. Check the [Windows install guide](https://github.com/semaphoreP/codeastro/blob/main/Day0/INSTALL_WINDOWS.md) again for a few more details then come back here. If you cannot find where the Marketplace is to install this extension, check out the section in the video above about installing the Python extension, and adapt it for `Remote - WSL`. 

# Finished?

When you have finished everything above, fill out [this form](https://docs.google.com/forms/d/e/1FAIpQLSfyDVKjrxclGEtyh4PEpK9GdvHJSlMBTbtI_kRn615wKrXKew/viewform?usp=sharing&ouid=108007517358444486795) with the secret code so we know you are ready for the workshop!

# Apple-specific Instructions

If you are using a Mac you will need to install Xcode and the associated command line utilities in order to compile code. Some Python packages include portions of C or fortran code and must be compiled to run optimally. 

First, install the Xcode application using the App Store. 

Once Xcode is finished installing open a terminal and type:
    
    xcode-select --install

Accept the user agreement and follow the onscreen prompts. 
