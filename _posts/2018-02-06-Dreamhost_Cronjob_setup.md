---
layout: post
title:  "Creating a Cron Job on Dreamhost"
date:   2018-02-06
excerpt: ""
categories: dev
tags: [dreamhost, git, cron, virtualenv, python, rsync, bash]
comments: true
---

## Pre-requisite
The task I wanted to run is a Bash script that runs a bit of Python code, rsync the newly generated data to a github project folder, then do a `Git Push`

Dreamhost already has `virtualenv` installed on their `ssh` shell. And [here][1] is a great resource on how to use it for installed the required python packages.

### Setting up `virtualenv`
```sh
$ cd project_dir                      # first goes to the project folder
$ virtualenv _myenv                   # this creates the _myenv environment in project_dir
$ source _myenv/bin/activate          # this activate _myenv
$ pip install -r requirement.txt      # this install the py packages you need in _myenv
$ deactivate                          # this deactivate _myenv
$ rm -rf _myenv                       # this delete the virtual environment _myenv
```

### The other pieces
`git`, `python`, `rsync`, and `bash` are all already available on Dreamhost's `ssh` shell.

I just had to do a `git clone` and run the python code in my project using the `_myenv` (created above).

## Cron Job on Dreamhost
Just follow [this awesome article][2]

But to config the Cron Job I need to know what time Dreamhost knows. So in the SSH shell just do `$ date`. And it seems the server's on Pacific Standard Time.


[1]: http://docs.python-guide.org/en/latest/dev/virtualenvs/
[2]: https://help.dreamhost.com/hc/en-us/articles/215088668-How-do-I-create-a-cron-job-
