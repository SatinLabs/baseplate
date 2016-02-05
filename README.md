# baseplate
Satin Labs - Vagrant LAMP Baseplate
=================================

This repository contains our development virtual machine.

For an introduction for the technologies involved, check out these articles from
[the DigitalOcean Community](https://www.digitalocean.com/community/) as well as
the [upstream cloud-init documentation](https://cloudinit.readthedocs.org/en/latest/):

Starting
--------

Clone this repo and issue ```vagrant up --provision```

Contributing
------------

Scripts in this repository can be in one of two formats, shell scripts and
cloud-config files. In order to encourage simplicity and readability, it is
highly encouraged to use the declarative cloud-config file format when possible.

Each directory must contain a README.md file describing the scripts contained
within it, including the target platform and a description of any needed user
input. As these scripts are not interactive, please use the standardized
format of **`<%DESCRIPTIVE_NAME%>`** for variables that should be provided by
the user before running the script. (See the `examples/` directory.)

Feedback
--------

This project is an experiment, and it won't be successful without your feedback.
Let us know what you think by [opening an issue here on GitHub](https://github.com/satinlabs/baseplate/issues).