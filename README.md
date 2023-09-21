# RHEL CIS

Configure RHEL machine to be [CIS](https://www.cisecurity.org/cis-benchmarks/) compliant


## Caution(s)

This role **will make changes to the system** which may have unintended consequences. This is not an auditing tool but rather a remediation tool to be used after an audit has been conducted.

This role was developed against a clean install of the Operating System. If you are implementing to an existing system please review this role for any site specific changes that are needed.

### Running level1 or level2 only

While the defaults/main.yml has the options this is used for auditing purposes.
In order to run level(1|2)-server level(1|2)-workstation  This is carried out via tags.

e.g.

``` shell
ansible-playbook -l test-server -i test_inv site.yml -t level1-server

```

## Requirements

RHEL 7 8 9 - Other versions are not supported.

## Dependencies

- Python3
- Ansible 2.9+
- python-def
- libselinux-python

## Role Variables

This role is designed that the end user should not have to edit the tasks themselves. All customizing should be done via the defaults/main.yml file or with extra vars within the project, job, workflow, etc.

## Tags

There are many tags available for added control precision. Each control has it's own set of tags noting what level, if it's scored/notscored, what OS element it relates to, if it's a patch or audit, and the rule number.

Below is an example of the tag section from a control within this role. Using this example if you set your run to skip all controls with the tag services, this task will be skipped. The opposite can also happen where you run only controls tagged with services.

```txt
      tags:
      - level1-server
      - level1-workstation
      - scored
      - avahi
      - services
      - patch
      - rule_2.2.4
```