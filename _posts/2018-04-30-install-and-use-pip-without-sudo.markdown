---
layout: post
title: Install and use pip without sudo
tags:
- osx
- programming
date: '2018-04-30 15:58:00'
---
I'm used to installing and running my Ruby gems in user space with the help of [`rbenv`](https://github.com/rbenv/rbenv). I wasn't aware of a similar setup for Python, until today.

[This Gist by Matthew](https://gist.github.com/haircut/14705555d58432a5f01f9188006a04ed) guides you through all the steps you need to take. It's quite simple, really.

``` bash
# Uninstall sudo-requiring pip (only if pip is already installed)
sudo pip uninstall pip

# Download pip
curl https://bootstrap.pypa.io/get-pip.py -o ~/Downloads/get-pip.py

# Install pip with the --user argument 
python ~/Downloads/get-pip.py --user

# Add Python's bin folder in ~/Library to your PATH environment variable
echo 'export PATH="$HOME/Library/Python/2.7/bin:$PATH"' >> ~/.bashrc

# Reload your config
source ~/.bashrc
```

Matthew mentions to remember to append `--user` when installing modules:
``` bash
$ pip install <package_name> --user
```
