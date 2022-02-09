# Overview

Snakemake is a **work flow engine** that provides a readable python-based workflow definition language and a powerful excecution environment that scales from single core work stations to compute clusters without modifying the workflow

## Getting started with snakemake

This workflow can be run on any of the operating systems, however, this work flow is for linux.

## Step 1: Install mambaforge

This is done on the terminal

`$ wget https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh`

`$ bash Mambaforge-Linux-x86_64.sh`

## Step 2: Prepare a working directory
You need to create a new working directory and name it *snakemake-tutorial*

`$ mkdir snakemake-tutorial`

`$ cd snakemake-tutorial`

## Step 3: Creating an environment with the required software

Be sure to activate the conda base environment with the following command

`$ conda activate base`

Please note that, the *environment.yaml* file that you have obtained with step (Step 2) can be used to install all required software into an isolated Conda environment with the name snakemake-tutorial via

`$ mamba env create --name snakemake-tutorial --file environment.yaml`


## Step 4: Activating the environment

To activate the snakemake-tutorial environment, execute the following command

`$ conda activate snakemake-tutorial`
