# Understanding the $PATH Variable

## Introduction

The $PATH variable specifies a list of directories that impacts your computing platform's functionality in a critical way. This is because the $PATH is the list of directories in which the system searches for executable programs, scripts, or files.

## Using bash_profile to Set your PATH

When the $PATH variable is set in the current shell only, without persisting the change, it is prone to being lost when a new shell is opened. Therefore, it is a good practice to set your $PATH permanently. This is achieved through:

### 1. Modifying the path variable in the bash profile file

If the bash profile is located at ` /home/<user>/.bash_profile` , and I want to add a new directory `/home/tomahawk/tools/jdk1.8.0_92/bin` to my PATH, whatever the directory contains, I can add it to my path and make the programs that this bin directory contains accessible from the command line by running the following command at the end of the file `~/.bash_profile`

`export PATH="$PATH:/home/tomahawk/tools/jdk1.8.0_92/bin"`

### 2. Editing the file

The file can be edited using `nano` or any other text editor such as `vi`, `vim` or `emacs`. You can use the command: `sudo <editor> ~/.bash_profile`, and enter your admin password when prompted, then add that line to the end and save the file.

### 3. Activating the changes

To activate the changes in the current shell, you have to "source" the updated bash_profile file. This can be achieved by running the following command:

`source ~/.bash_profile`

This step imports the file's settings into the current shell. Now every time you open your shell, your `bash_profile` will automatically be "sourced" and you won't need to run this command every time.

## Using .bashrc to Set your PATH

Instead of setting the PATH in `~/.bash_profile`, we can alternatively add the directories we want to the PATH in `~/.bashrc`. Setting the PATH in bashrc looks identical to how we set it in `bash_profile`.

For example, to include the directory `/home/tomahawk/.rbenv/bin` in our path, we edit or create the file `/home/tomahawk/.bashrc`, and add the following line:

`export PATH="$PATH:/home/tomahawk/.rbenv/bin"`

This ensures that we preserve the current value of PATH, and just add any additional directories on to the PATH, after the $PATH variable. If you do not do this, you will overwrite the PATH variable entirely, and miss critical directories the system needs to be on the PATH. As a result, your system can become unusable.

*Note*

*The difference between using `bashrc` and `bash_profile` is that `bash_profile` is used for login shells. These run when you login via the console, or log in using `ssh`. In contrast, once you are logged in, and you open a command shell or run the bash command, the `bashrc` file will run. Your PATH settings from `bashrc` will then be available.*

## Using a Profile File to Set your PATH

We can also set the PATH permanently using a user's profile file. This is different from `~/.bash_profile` in that it is set not for shells only, but for **all programs.**

To set my PATH to include everything already in $PATH, as well as a new directory `/home/tomahawk/.exenv/bin`, we edit the file at `~/.profile` and set the PATH as follows:

`export PATH="$PATH:/home/tomahawk/.exenv/bin"`

As previously discussed, we will need to source these changes to make them active for the current shell, but subsequent logins will persist the changes.




