<!--
Copyright (C) 2017 Jordi Blasco
Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.3
or any later version published by the Free Software Foundation;
with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.
A copy of the license is included in the section entitled "GNU
Free Documentation License".

HPCNow!, hereby disclaims all copyright interest in this document
`hpcnow-labs' written by Jordi Blasco.
-->
# Hands-On 01: Getting access to the cluster

In this hands-on, we are going to setup the required software in order to be able to access the High Performance Computing cluster.

*Estimated time : 15 minutes*

## Requirements
Cluster account.
Laptop with SSH client.

## ToDo

### Install a SSH client

* Windows: download and install [MobaXterm Home Edition](http://mobaxterm.mobatek.net/download-home-edition.html)
* MacOSX: download and install [iTerm2](https://www.iterm2.com/downloads.html)
* Linux: install one of the following programs: Konsole (KDE), Gnome-Terminal (Gnome), Guake, Yakuake
* Multiplatform: [Terminus](https://eugeny.github.io/terminus/)

### Create a SSH key

```
ssh-keygen -t rsa
```

### Transfer the SSH key to the cluster


```
ssh-copy-id -i ~/.ssh/id_rsa username@delta-login1.pfizer.com
```

:heavy_exclamation_mark: The server delta-login1.pfizer.com is only accesible from Pfizer network.

:heavy_exclamation_mark: Replace the ```username``` with the user provided by the trainer.

:heavy_exclamation_mark: The default SSH key is located in the following path ```~/.ssh/id_rsa```. If you have created a different one, replace the path to the SSH key.

### Connect to the login node

```
ssh username@delta-login1.pfizer.com -X
```

The login node is meant to be a simple but very secure node to provide access to the files and to manage the batch jobs. It is not suitable for running CPU intensive codes or compile your code. In order to test the code and interact with the command line, you can use the ```interactive``` command line which is explained in hands-on 03.

### Setup alias
The previous command is quite long and easy to forget. You can create an alias for the previous command following these two simple steps in a shell session in your laptop:

```
echo "alias delta='ssh username@delta-login1.pfizer.com -X'" >> ~/.bashrc
source ~/.bashrc
```
:heavy_exclamation_mark: If you are using mobaxterm, use ```~/.bash_profile``` instead of ```~/.bashrc```

### Download the training material into your home directory:

```
git clone --recursive https://github.com/PfizerRD/hpcnow-labs
```
