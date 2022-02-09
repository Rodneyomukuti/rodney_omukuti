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

# Important notes

### Introduction

Large-scale data analyses in bioinformatics involve the chained execution of many command line applications. Workflow engines help to automate these pipelines and ensure reproducibility. These engines include Biopipe, Taverna, Galaxy, among others.
workflows can be edited without a graphical environment (e.g. directly on a remote server); and developers can collaborate on them through source code management tools. Similar to Pwrake and GXP Make, Snakemake is inspired by the build system GNU Make. They all infer the actual workflow (dependencies, parallelization) from a set of rules with input and output files. Snakemake complements these prior works with a syntax close to pseudocode, in the spirit of the Python language.

### Snakemake language

A workflow is defined in a ‘Snakefile’ through a domain-specific language that is close to standard Python syntax. It consists of rules that denote how to create output files from input files. The workflow is implied by dependencies between the rules that arise from one rule needing an output file of another as an input file.

Generally, a rule definition specifies:
1. a name
2. any number of input and output files
3. either a shell command or a python code that creates the output from the input

### Snakemake engine

Upon invocation, Snakemake creates a directed acyclic graph (DAG) that represents a plan of rule executions. The nodes of the DAG are jobs (the execution of a rule), a directed edge between job A and B means that the rule underlying job B needs the output of job A as an input file. 

A path in the DAG represents a sequence of jobs that have to be executed serially. Importantly, two disjoint paths in the DAG can be executed independently from each other, i.e. in parallel. Since individual jobs can use multiple threads themselves, Snakemake can be instructed to solve a 0/1-knapsack problem to optimize the usage of CPUs, given a threshold of available cores. This mechanism allows to scale Snakemake to environments with a hard limit of used CPU cores, e.g. a shared compute server. Furthermore, using only as many threads as there are cores available can be beneficial for performance since it reduces the amount of context switching.
