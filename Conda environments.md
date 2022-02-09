## Introduction 

Conda allows you to: create, export, list, remove, and update and share environments that have different versions of packages installed in them. Switching or moving between environments is called activating the environment. To interact with conda, you use the terminal

## Creating an environment

To create an environment, run the following command

`$ conda create --name rodney` 

conda will ask you to proceed.

Type `y` 

This creates the rodney environment in /envs/. 

## Creating an environment from an environment.yml file

To create the environment from the environment.yml file, run the following command

`$ conda env create -f environment.yml`

 ## Installing packages 
 
 To install any package eg python version 3.7:
 
 `$ conda install python=3.7 codecov`
 
## Activating the environment  

Activate the new environment: 

`$ conda activate myenv`

Verify that the new environment was installed correctly:

`$ conda env `

## Updating an environment

`$ conda env update --prefix ./env --file environment.yml  --prune`

## Cloning an environment

`$ conda create --name myclone --clone myenv`

## Activating an environment 

To activate an environment: 

`$ conda activate myenv`

## Determining your current environment

`(myenv) $`

## Viewing a list of your environments
To see a list of all of your environments, in your terminal window, run:

`$ conda info --envs`

## Viewing a list of the packages

`$ conda list`

## Sharing an environment
You may want to share your environment with someone else in case they want to reproduce your work. It is good to share with them a copy of the generated .yml file.

### Exporting the environment.yml file

Export your active environment to a new file:

`$ conda env export > environment.yml`

*Email or copy the exported environment.yml file to the other person.*




