# Docker

## Introduction 

Docker is an open source containerization platform that enables developers to package applications into containers—standardized executable components combining application source code with the operating system libraries and dependencies required to run that code in any environment.

**Publish your container in the Docker Hub to share it with other people using the following steps**

### 1. Create an account 
Create an account in the [Docker website](https://www.google.com/search?q=hub.docker.com+web+site&oq=hub.docker.com+web+site&aqs=chrome.0.69i59j0i13i30.1020j0j7&sourceid=chrome&ie=UTF-8). Then from your shell terminal run the following command, entering the user name and password you specified registering in the Hub:

`docker login`

### 2. Tag the image with your Docker user name account:

`docker tag my-image rodney/my-image`

### 3. Push it to the Docker Hub:

`docker push rodney/my-image`

After that anyone will be able to download it for their own use

# Running nextflow from GitHub

Nextflow allows the execution of a pipeline project directly from a GitHub repository for easier sharing.

You can run a project by specifying the project name as shown below, by running the command:

`nextflow run nextflow-io/rnaseq-nf -with-docker`

Which automatically downloads the container and stores it in the `HOME/.nextflow folder`.

To check the project information, run the following command:

`nextflow info nextflow-io/rnaseq-nf`

Nextflow allows the execution of a specific revision of your project by using the -r command line option:

`nextflow run nextflow-io/rnaseq-nf -r dev`

Revision are defined by using Git tags or branches defined in the project repository.This allows a precise control of the changes in your project files and dependencies over time.

# Singularity

Singularity is container runtime designed to work in HPC data center, where the usage of Docker is generally not allowed due to security constraints.

## Creating singularity images

### 1. Create a singularity file
```
Bootstrap: docker
From: debian:stretch-slim

%environment
export PATH=$PATH:/usr/games/

%labels
AUTHOR <your name>

%post

apt-get update && apt-get install -y locales-all curl cowsay
curl -sSL https://github.com/COMBINE-lab/salmon/releases/download/v1.0.0/salmon-1.0.0_linux_x86_64.tar.gz | tar xz \
 && mv /salmon-*/bin/* /usr/bin/ \
 && mv /salmon-*/lib/* /usr/lib/
 ```
 ### 2. Create an image from the file
 
 `sudo singularity build my-image.sif Singularity`
 
 ## Run the container
 
 `singularity exec my-image.sif cowsay 'Hello Singularity'`
 
 ## Start working in the container
 
 `singularity shell my-image.sif`
 `touch hello.txt
   ls -la`
   
  ## Import a Docker Image
  
  `singularity pull docker://debian:stretch-slim`
  
  ## Run a nextflow script using a singularity container
  
  `nextflow run script7.nf -with-singularity nextflow/rnaseq-nf`
 

