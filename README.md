Ubuntu 16 GSA Benchmark
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

## Testing

### with Molecule
```
pip install pipenv
sudo pipenv install
pipenv run test
```

### with Packer
To test the role against a bare AWS AMI:

1. Install [Packer](https://www.packer.io/).
1. [Specify your AWS credentials as environment variables.](https://www.packer.io/docs/builders/amazon.html#automatic-lookup)
1. Build an AMI using the role.

    ```sh
    cd test
    packer build packer.json
    ```

License
-------

MIT
