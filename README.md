# [earlyoom](#earlyoom)

Install and configure Early Out Of Memory Killer on your system.

|Travis|GitHub|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-earlyoom.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-earlyoom)|[![github](https://github.com/robertdebock/ansible-role-earlyoom/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-earlyoom/actions)|[![quality](https://img.shields.io/ansible/quality/40792)](https://galaxy.ansible.com/robertdebock/earlyoom)|[![downloads](https://img.shields.io/ansible/role/d/40792)](https://galaxy.ansible.com/robertdebock/earlyoom)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-earlyoom.svg)](https://github.com/robertdebock/ansible-role-earlyoom/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.earlyoom
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.buildtools
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for earlyoom

earlyoom_version: v1.6
earlyoom_clone_destination: /tmp/earlyoom
earlyoom_installation_destination: /usr/bin

earlyoom_minimum_memory_percent: 10
earlyoom_minimum_swap_percent: 5
earlyoom_memory_report_interval: 60  # in seconds
```

## [Requirements](#requirements)

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

## [Status of requirements](#status-of-requirements)

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |
| [robertdebock.buildtools](https://galaxy.ansible.com/robertdebock/buildtools) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-buildtools.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-buildtools) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-buildtools/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-buildtools/actions) |
| [robertdebock.service](https://galaxy.ansible.com/robertdebock/service) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-service.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-service) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-service/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-service/actions) |

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/earlyoom.png "Dependency")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|el|7, 8|
|debian|buster, bullseye|
|fedora|all|
|opensuse|all|
|ubuntu|focal, bionic, xenial|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.

## [Exceptions](#exceptions)

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| Alpine | Not idempotent |

## [Included version(s)](#included-versions)

This role [refers to a version](https://github.com/robertdebock/ansible-role-earlyoom/blob/master/defaults/main.yml) released by rfjakob on GitHub. Check the released version(s) here:
- [earlyoom](https://github.com/rfjakob/earlyoom/releases).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.
## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-earlyoom) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-earlyoom/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0

## [Contributors](#contributors)

I'd like to thank everybody that made contributions to this repository. It motivates me, improves the code and is just fun to collaborate.


## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
