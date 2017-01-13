Role: nodejs
=========

This role is for MacOS Homebrew users that wish to install npm global packages without resorting to the use of sudo
When node is installed via Homebrew, and `npm install` is run with `-g` flag, it installs the requested packages in 
the default directory of `/usr/local/lib/node_modules`.  This directory requires root privileges for write and will
inevitably result in permissions being changed on files that will cause errors and conflict with Homebrew's semantics

This role will install Node via Homebrew without NPM, and install the latest NPM separately into a configurable 
directory (*defaults to the user's home*)

It will set up all environment variables for Node and Npm binarys so that things go neatly into this new home


Requirements
------------

* Ansible itself of course (*see the parent README*)
* Homebrew
* **No pre-existing Node or Npm installs (*this role assumes a clean environment*)**
* **Intended to be executed without sudo or as root**


Role Variables
--------------

### Defaults

* npm_dir: `"{{ home }}/.npm-packages"`

### Required

* action:
  * allowed values:
     * `install`
     * TODO: `remove`

Dependencies
------------

None

Example Playbook
----------------

    ---
    - hosts: all
      connection: local
   
      vars:
        action: install
    
      roles:
        - nodejs

License
-------

BSD

Author Information
------------------

@robogalactic