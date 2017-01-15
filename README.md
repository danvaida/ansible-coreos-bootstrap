[![Build Status](https://travis-ci.org/danvaida/ansible-roles-coreos-bootstrap.svg?branch=master)](https://travis-ci.org/danvaida/ansible-roles-coreos-bootstrap)
[![Galaxy](https://img.shields.io/ansible/role/14882.svg)](https://galaxy.ansible.com/danvaida/coreos-bootstrap/)

# Ansible coreos-bootstrap role

In order to effectively run Ansible, the target machine needs to have a python interpreter. CoreOS machines are minimal and do not ship with any version of python. To get around this limitation we can install [pypy](http://pypy.org/), a lightweight python interpreter. The coreos-bootstrap role will install pypy and pip for us.

The recommended way of configuring your CoreOS boxes is through [Cloud-Config](https://coreos.com/os/docs/latest/cloud-config.html)

## Requirements

n/a

## Dependencies

n/a

## Role Variables

* __coreos_bootstrap_dir:__
  Dir path to where PyPy will be put.

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

If you need to override the Python interpreter that Ansible uses, and want to do so also for ad-hoc commands, one way of doing it is by adding the following block to your inventory file:

    [coreos:vars]
    ansible_user=core
    ansible_python_interpreter="/opt/bin/python"

Make sure the path to the interpreter is based on the `coreos_bootstrap_dir` var.

## Testing

Currently there is only the default `--syntax-check` test running on Travis.

## To do

* Add idempotence tests (i.e. mock CoreOS in a Gentoo container, spawn an EC2/droplet somewhere; suggestions welcome)

## License

BSD
