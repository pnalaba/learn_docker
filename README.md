# Docker exercises
The demo has a collection of dockerfiles that I built in the past. Nothing complicated here. These have been retained for quick reference.

The docker projects were all built on top of CentOS7 images and mostly install basic tools needed on a CentoS system. Following is a description of this repository's contents

* docker_commands.ipynb
A jupyter notebook showing few of the commands that I normally use. I keep forgetting commands, and this notebook acts as a quick reference

* CentosSpark 
This dockerfile sets up an image based on Centos7, installs Java, Spark, Scala and ElasticSearch. It was used to try out an web-application that accepted csv files and could run the data through an ML model and show results like prediction accuracy etc.

* dsmodernization_code
This dockerfile was written to create a container that pulls an appication (called DeployDemo) from github and runs it. 

* python-example
This I believe is an example that I borrowed from Docker's documentation, or from some other source ( can't find the source now). It has a python web-application and show how to build a docker container that can serve the web application

