Ubuntu 16 GSA Benchmark [![CircleCI](https://circleci.com/gh/GSA/ansible-os-ubuntu-16.svg?style=shield)](https://circleci.com/gh/GSA/ansible-os-ubuntu-16)
====================

This ansible content will configure Ubuntu 16 machine to be GSA compliant.

This role **will make changes to the system** that could break things. This is not an auditing tool but rather a remediation tool to be used after an audit has been conducted. For compliance auditing, use a tool such as [nessus](https://www.tenable.com/products/nessus-vulnerability-scanner) or [CIS-CAT](https://learn.cisecurity.org/cis-cat-landing-page)

## IMPORTANT INSTALL STEP

This code is based on the GSA Ubuntu 16 v1.0 and the [CIS Ubuntu 16 Benchmark v2.0.0 ](https://www.cisecurity.org/cis-benchmarks/).

Requirements
------------

You should carefully read through the tasks to make sure these changes will not break your systems before running this playbook.

Role Variables
--------------
There are many role variables defined in defaults/main.yml.

By default, many of the variables are turned off. Please review and adjust to meet your organizational requirements.

Note, a subset of controls were removed due to operational impact or organizational dependent variables. Those are listed [here](https://docs.google.com/spreadsheets/d/1hHbPDnm5WspzGt6F67_Dw2GgLA1E0-NCAsIGeHJLK7s/edit#gid=0) *Note: Must have a GSA account to access.*

Dependencies
------------

Ansible > 2.4

Example Playbook
-------------------------

```yaml
---
- name: Harden Server
  hosts: all
  become: yes

  roles:
    - gsa_hardening
```

How to test locally
--------------------------
```
ansible-playbook playbook.yml --connection=local
```

CircleCI Intergration
--------------
This repository has been updated to optionally utilize Continuous Intergration with CircleCI and tests the ansbile tasks against a privledged Ubuntu-16 Container.  A low number of tasks are incompatiable when ran against a container vs a vm or bare-metal and have been tagged with no_test for error handling purposes.

##### Using CircleCI:
* Fork this repository or create a branch
* Sign up for an account and follow the getting started guide at https://circleci.com/docs/2.0/first-steps/#section=getting-started
* Add the repository to your projects and click start building. https://circleci.com/docs/2.0/project-build/#section=getting-started
* New Commits will trigger the CircleCI build and run the playbook.yml and the result will pass or fail.

License
-------

MIT
