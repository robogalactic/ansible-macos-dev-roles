# Ansible roles for various development environments on Mac OS

## Synopsis

This repo contains a collection of Ansible roles for automating the setup of various development environments on a Mac

More info and details about what they do are included in the respective README for each role.

## Why Ansible?

Compared to other configuration management solutions, Ansible is currently the easiest to setup, use, maintain.  It has 
nice orchestration and deployment features, and was designed with a focus on modularity.

## Quick setup for installing Ansible

Before continuing please make sure that you have Commandline Tools for XCode and [Homebrew](http://brew.sh) installed

### Bash profile setup

#### 64 bits user's package installations
OS X 10.8 *Mountain Lion* and up are 64-bit.

Create or edit a `~/.bashrc` file and include the following to configure our environment to ensure that installed 
packages result in 64 bit binaries:

```
echo 'ARCHFLAGS="-arch x86_64"' >> ~/.bashrc
```

#### Load .bashrc if it exists
`.bashrc` is for non-interactive shells but we can simply load it for login shells:

```
echo 'test -f ~/.bashrc && source ~/.bashrc' >> ~/.bash_profile
```

### Install Homebrew Python

OS X ships with Python and `setup_tools`, however this is heavily patched version and not updated frequently.
Plus OSX upgrades can wipe out any global Python packages requiring a manual re-installation - not fun.

Homebrew Python comes with the Pip installer which will install global packages in 
`/usr/local/lib/python<version>/site-packages` and binary executables into `/usr/local/bin/`

A better solution is to use Homebrew's Python which is continually maintained and will be more current.

Use the following command to install to install the latest stable version of Python via Homebrew:

`brew install python`

### Install Ansible

Now we're ready to install Ansible via Pip.

` pip install ansible`

## Using the provided roles

### See the `site.yml` for an example of including these roles in a playbook

If you use the site.yml as-is then all of the listed roles will be installed

#### Command example

`ansible-playbook -i inventory site.yml`
