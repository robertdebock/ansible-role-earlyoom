earlyoom
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-earlyoom"><img src="https://travis-ci.org/robertdebock/ansible-role-earlyoom.svg?branch=master" alt="Build status" align="left"/></a>

Install and configure Early Out Of Memory Killer on your system.

<img src="https://img.shields.io/ansible/role/d/40792"/>
<img src="https://img.shields.io/ansible/quality/40792"/>

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.earlyoom
```

The machine you are running this on, may need to be prepared.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - robertdebock.bootstrap
    - robertdebock.buildtools
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for earlyoom

earlyoom_version: v1.3
earlyoom_clone_destination: /tmp/earlyoom
earlyoom_installation_destination: /usr/bin

earlyoom_minimum_memory_percent: 10
earlyoom_minimum_swap_percent: 5
```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.buildtools
- robertdebock.service

```

This role uses the following modules:
```yaml
---
- copy
- git
- import_role
- make
- meta
- package
- service
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/earlyoom.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.7|ansible 2.8|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|no|yes|yes*|
|alpine-latest|no|yes|yes*|
|archlinux|no|yes|yes*|
|centos-7|no|no|no*|
|centos-latest|no|yes|yes*|
|debian-stable|no|yes|yes*|
|debian-unstable*|no|yes|yes*|
|fedora-latest|no|yes|yes*|
|fedora-rawhide*|no|yes|yes*|
|opensuse-leap|no|yes|yes*|
|ubuntu-devel*|no|yes|yes*|
|ubuntu-latest|no|yes|yes*|
|ubuntu-rolling|no|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.


Included version(s)
-------------------

This role [refers to a version](https://github.com/robertdebock/ansible-role-earlyoom/blob/master/defaults/main.yml) released by rfjakob on GitHub. Check the released version(s) here:
- [earlyoom](https://github.com/rfjakob/earlyoom/releases).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-earlyoom) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-earlyoom/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
