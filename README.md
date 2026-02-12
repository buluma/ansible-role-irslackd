# [Ansible role irslackd](#ansible-role-irslackd)

Install and configure irslackd on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-irslackd/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-irslackd/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-irslackd/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-irslackd)|[![downloads](https://img.shields.io/ansible/role/d/buluma/irslackd)](https://galaxy.ansible.com/buluma/irslackd)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-irslackd.svg)](https://github.com/buluma/ansible-role-irslackd/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-irslackd/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  pre_tasks:
    - name: Update apt cache.
      apt: update_cache=true cache_valid_time=600
      when: ansible_os_family == 'Debian'

  roles:
    - role: buluma.git
    - role: buluma.ca_certificates
    - role: buluma.npm
    - role: buluma.irslackd
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-irslackd/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: false
  become: true

  roles:
    - role: buluma.bootstrap
    - role: buluma.epel
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-irslackd/blob/master/defaults/main.yml):

```yaml
---
# defaults file for irslackd

# The tcp port that irslackd should listen on.
irslackd_port: 6697

# The address that irslackd should bind to.
irslackd_address: "0.0.0.0"

# Where to install irslackd.
irslackd_dest: /opt/irslackd

# The version of irslackd to install.
irslackd_version: b8ab630c877819d8b4bac9ab808b408e06cdb350

# These settings are used for the SSL certificate.
irslackd_country: KE
irslackd_state: Nairobi
irslackd_location: Nairobi
irslackd_organization: Very little
irslackd_organizational_unit: IT Department
irslackd_common_name: "{{ ansible_fqdn }}"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-irslackd/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.ca_certificates](https://galaxy.ansible.com/buluma/ca_certificates)|[![Build Status GitHub](https://github.com/buluma/ansible-role-ca_certificates/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-ca_certificates/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-ca_certificates/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-ca_certificates)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Build Status GitHub](https://github.com/buluma/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-epel/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-epel/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-epel)|
|[buluma.git](https://galaxy.ansible.com/buluma/git)|[![Build Status GitHub](https://github.com/buluma/ansible-role-git/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-git/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-git/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-git)|
|[buluma.npm](https://galaxy.ansible.com/buluma/npm)|[![Build Status GitHub](https://github.com/buluma/ansible-role-npm/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-npm/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-npm/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-npm)|
|[buluma.service](https://galaxy.ansible.com/buluma/service)|[![Build Status GitHub](https://github.com/buluma/ansible-role-service/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-service/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-service/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-service)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-irslackd/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-irslackd/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-irslackd/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

