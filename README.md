# System Security (`system-security`)

Master:
[![Build Status](https://semaphoreci.com/api/v1/bas-ansible-roles-collection/system-security/branches/master/badge.svg)](https://semaphoreci.com/bas-ansible-roles-collection/system-security)

Develop:
[![Build Status](https://semaphoreci.com/api/v1/bas-ansible-roles-collection/system-security/branches/develop/badge.svg)](https://semaphoreci.com/bas-ansible-roles-collection/system-security)


Meta role for including roles related to system security

**Part of the BAS Ansible Role Collection (BARC)**

## Overview

* Meta-role for including roles related to system security

## Quality Assurance

This role uses manual and automated testing to ensure the features offered by this role work as advertised. 
See `tests/README.md` for more information.

## Dependencies

* [**bas-ansible-roles-collection.system-ssh**](https://galaxy.ansible.com/bas-ansible-roles-collection/system-ssh/)
  * Minimum version: *0.2.0*

### Pinning dependencies

All dependencies of this role will use the latest role version. In many cases this will be unsuitable and so versions
should be 'pinned' to a specific version to ensure breaking changes for example are introduced. This issue becomes
increasingly important the longer a project is not updated.

A method developed for BAS projects uses a `roles.yml` file to specify all roles, including dependencies of roles, 
and their version. This does require you to resolve dependencies for roles manually, however dependencies are listed in
each role's `meta/main.yml` and `README.md` file.

Note: BAS projects **SHOULD** always pin role versions, except in exceptional circumstances.

### Avoiding dependencies

All dependencies of this role are tagged as *BARC_ROLE_DEPENDENCY*. Skipping this tag when executing a playbook that
includes this role will prevent role dependencies from being installed.

E.g.

```shell
$ ansible-playbook playbook.yml --skip-tags "BARC_ROLE_DEPENDENCY"
```

Note: This 'dependency' tag is shared across all BARC roles, and skipping it will therefore exclude all dependencies,
from all BARC roles. There is currently no supported method to exclude only this roles dependencies.

Note: Using this role without its dependencies is **NOT** supported, and may lead to incomplete results or errors.

## Requirements

* None

## Limitations

* None

## Usage

### BARC manifest

By default, BARC roles will record that they have been applied to a system. This is recorded using a set of 
[Ansible local facts](http://docs.ansible.com/ansible/playbooks_variables.html#local-facts-facts-d), specifically:

* `ansible_local.barc-system-security.general.role_applied` - to indicate that this role has been applied
* `ansible_local.barc-system-security.general.role_version` - to indicate the applied version of this role

Note: You **SHOULD** use this feature to determine whether this role has been applied to a system.

If you do not want these facts to be set by this role, you **MUST** skip the **BARC_SET_MANIFEST** tag. No support is 
offered in this case, as other roles or use-cases may rely on this feature. Therefore you **SHOULD NOT** disable this
feature.

### What are meta-roles?

Meta-roles are a concept with the BARC for roles which group other roles together through role dependencies.

They are used to simplify specifying sets of roles. These include groupings by purpose (such as 'system security'), or 
for a particular stack (such as 'nginx, php, php-fpm, postgresql server and php-pgsql'). Using these meta-roles means
you don't need to list all of roles within a set manually, or to necessarily know the roles that make up a set.

For example, a playbook such:

```yaml
---

- name: setup web-servers
  hosts: all
  become: yes
  vars: []
  roles:
    - bas-ansible-roles-collection.nginx
    - bas-ansible-roles-collection.php
    - bas-ansible-roles-collection.php-fpm
    - bas-ansible-roles-collection.php-pgsql
    - bas-ansible-roles-collection.postgresql
```

Might become:

```yaml
  roles:
    - bas-ansible-roles-collection.LEPP
```

Note: The roles above are not necessarily real BARC roles.

### Typical playbook

```yaml
---

- name: configure system security
  hosts: all
  become: yes
  vars: []
  roles:
    - bas-ansible-roles-collection.system-security
```

### Tags

BARC roles use standardised tags to control which aspects of an environment are changed by roles. Where relevant, tags
will be applied at a role, or task(s) level, as indicated below.

This role uses the following tags:

* [**BARC_SET_MANIFEST**](https://antarctica.hackpad.com/BARC-Standardised-Tags-AviQxxiBa3y#:h=BARC_SET_MANIFEST)

### Variables

#### *system_security_barc_role_name*

* **MUST NOT** be specified
* Specifies the name of this role within the BAS Ansible Roles Collection (BARC) used for setting local facts
* See the *BARC roles manifest* section for more information
* Example: system-security

#### *system_security_barc_role_version*

* **MUST NOT** be specified
* Specifies the name of this role within the BAS Ansible Roles Collection (BARC) used for setting local facts
* See the *BARC roles manifest* section for more information
* Example: 2.0.0

## Developing

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the 
[BAS Ansible Roles Collection](https://jira.ceh.ac.uk/projects/BARC) (BARC) project on Jira.

This service is currently only available to BAS or NERC staff, although external collaborators can be added on request.
See our contributing policy for more information.

### Source code

All changes should be committed, via pull request, to the canonical repository, which for this project is:

`ssh://git@stash.ceh.ac.uk:7999/barc/system-security.git`

A mirror of this repository is maintained on GitHub. Changes are automatically pushed from the canonical repository to
this mirror, in a one-way process.

`git@github.com:bas-ansible-roles-collection/system-security.git`

Note: The canonical repository is only accessible within the NERC firewall. External collaborators, please make pull 
requests against the mirrored GitHub repository and these will be merged as appropriate.

### Contributing policy

This project welcomes contributions, see `CONTRIBUTING.md` for our general policy.

The [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow/) 
workflow is used to manage the development of this project:

* Discrete changes should be made within feature branches, created from and merged back into develop 
(where small changes may be made directly)
* When ready to release a set of features/changes, create a release branch from develop, update documentation as 
required and merge into master with a tagged, semantic version (e.g. v1.2.3)
* After each release, the master branch should be merged with develop to restart the process
* High impact bugs can be addressed in hotfix branches, created from and merged into master (then develop) directly

### Release procedure

See [here](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Release-procedures) for general 
release procedures for BARC roles.

## Licence

Copyright 2015 NERC BAS.

Unless stated otherwise, all documentation is licensed under the Open Government License - version 3. All code is
licensed under the MIT license.

Copies of these licenses are included within this role.
