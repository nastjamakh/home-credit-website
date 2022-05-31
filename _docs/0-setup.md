---
layout: doc
title: A (Very Quick)  Development Setup
date: 2022-05-22
post_image: assets/images/service-icon3.png
tags: [Profile]
toc: true
custom_links:
- text: Homebrew
  url: https://brew.sh/
- text: GitHub
  url: https://github.com/
- text: Docker
  url: https://docs.docker.com/engine/install/
- text: Amazon Web Services
  url: https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
---

Before starting to explore the data and code, let's make sure we have all the necessary tools to build this project. At the very least, you will need a package manager to, well, install packages. As well as a version control tool like git to keep track of your code.

Later on you will also need a container manager like Docker to package your Machine Learning application; and a command-tool to work withA mazon Web Services.

I am working on MacOS with Apple Silicon (M1) chip.


### TL:DR

{% include doc-note.html %}
You can simply install all the prerequsites by navigating to a `start-here` branch in the project repo and running `dev-setup.sh` script. It will install all necessary tools for you:

* brew
* Git CLI tools
* pyenv and python version 3.10.4 as a virtual environment
* Docker
* AWS CLI tools

You will still have to configure your accounts though, as well as add SSH keys for your git account.

### Package Manager

Although there is no default packages manager on MacOs like `yum` or `apt` on Linux, `Homebrew` tends to be the go-to solution. It is the most painless way to install anything on MacOs (even apps from AppStore). In my quest to automate setting up a new laptop, work or personal, I have gotten pretty used to installing all my utlities and software with brew via bash scripts. Much more convinient than googling every packages and scrollng around on many many websites. f you are are familiar with teh command line or want to be, you should definitely get used to brew.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

And now you have the power to easily add and remove command-line utilities and even full-blown apps from your command line with 

```bash
# install a cli utility
brew install <your-package-name>

# install an app
brew install --cask <your-package-name>

# remove a cli utility
brew uninstall <your-package-name>

# remove an app
brew uninstall --cask <your-package-name>
```

You can also list your installed packages with
```bash
brew install list
```

...

### Python Virtual Environment

If you done any Python project, you are probably familiar with virtual environments.  Why are they so popular? The short answer is that Python is not good at dependency managemnt, and different porjcets may ask for different (conflicting) dependencies. Creating isolated environments with different version of python and its packages installed mitigates this issue.
You can read more about Python virtual environments [here](https://realpython.com/python-virtual-environments-a-primer/).

There are several solutions available, but my favourote one by far is `pyenv` together woth `pyenv-virtualenv`.

##### Installing

First, let's install with our package manager:
```bash
brew install pyenv pyenv-virtualenv
```

Next we need to add teh following lines to our shell config (either `bashrc` or `.zshrc`):

{% include codeHeader.html %}
```bash
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

...

### Version Control

* Installation
* Configure multiple account with SSH

...

### Packaging Your Application

We are going to use Docker to package our code in a container.

```bash

# install with brew cask
brew install --cask docker

# verify it's working
docker --version

# run an example
docker run hello-world
```

<br>
If you are new to Docker, take a look at this awesome [guide](https://runnable.com/docker/python/dockerize-your-python-application) to help you get started. It walks you through packaging a Python application for the first time (which we are also going to do later on), as well as provides a useful portion of commands to use on containers and images.

### Cloud Services (AWS)

...


### Configuring your shell with zsh (Optional)

...

<br>
Note that thsse tools are the basic prerequisites to follow through the project. My dev setup is, however, quite more complex and has a lot more command-line tools installed for a convinient workflow, such as ...
If you want to see what extra tools and shell plugins I am using, you can check it out [here]() .