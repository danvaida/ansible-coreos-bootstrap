[![Build Status](https://travis-ci.org/danvaida/ansible-roles-coreos-bootstrap.svg?branch=master)](https://travis-ci.org/danvaida/ansible-roles-coreos-bootstrap)
[![Galaxy](http://img.shields.io/badge/galaxy-danvaida.coreos-bootstrap-blue.svg?style=flat-square)](https://galaxy.ansible.com/danvaida/coreos-bootstrap/)

# Ansible coreos-bootstrap role

In order to effectively run Ansible, the target machine needs to have a python interpreter. CoreOS machines are minimal and do not ship with any version of python. To get around this limitation we can install [pypy](http://pypy.org/), a lightweight python interpreter. The coreos-bootstrap role will install pypy and pip for us.

## Requirements

n/a

## Dependencies

n/a

## Role Variables

* __coreos_bootstrap_dir:__
  Dir path to where PyPy will be put.

* __coreos_bootstrap_bin_dir:__
  Dir path to other system binaries.

* __coreos_bootstrap_pypy_version:__
  What version of PyPy to download and install. Can be >= 5.3.0 or <= 5.6.0

* __coreos_bootstrap_pypy_download_dest:__
  Dir path to where the PyPy archive will be put.

* __coreos_bootstrap_pip_download_dest:__
  Dir path to where the pip installer will be put.

## Example playbook

    - hosts: coreos
      gather_facts: False
      remote_user: core
      become: True
      roles:
        - danvaida.coreos-bootstrap

## Testing

Currently there is only the default `--syntax-check` test running on Travis.

## To do

* Add idempotence tests (i.e. mock CoreOS in a Gentoo container, spawn an EC2/droplet somewhere; suggestions welcome)

## License

BSD
