# Ansible role sshguard

[![CircleCI](https://circleci.com/gh/nephosolutions/ansible-role-sshguard.svg?style=shield)](https://circleci.com/gh/nephosolutions/ansible-role-sshguard)

This Ansible role installs and configures sshguard on Debian and RHEL/CentOS based systems.

## Requirements

For RHEL/CentOS based systems, this role depends on [geerlingguy.repo-epel]
to install and configure the EPEL (Extra Packages for Enterprise Linux) repository.

Other than that, only Ansible >= 2.2 is required.

### Tested on

* Debian 9 and 10
* Ubuntu 16.04 and 18.04
* REHL/CentOS 7 and 9

## Role Variables

The following role variables are relevant:

* `sshguard_block_time`: Block attackers for initially BLOCK_TIME seconds after exceeding THRESHOLD.
    Subsequent blocks increase by a factor of `1.5`; default `120`.
* `sshguard_detection_time`: Remember potential attackers for up to DETECTION_TIME seconds before resetting
    their score; default `1800`
* `sshguard_threshold`: Block attackers when their cumulative attack score exceeds THRESHOLD.
    Most attacks have a score of `10`; default `30`.
* `sshguard_whitelist`: A list of whitelist entries. IP addresses listed in the WHITELIST are considered to be
    friendlies and will never be blocked.
    * `comment`: A comment / description (optional)
    * `address`: A single IPv4 and IPv6 address / address blocks in CIDR notation / hostnames

## Example Playbook

```yaml
---
- name: test-playbook | Test sshguard role
  hosts: all
  become: yes
  become_user: root
  vars:
    - sshguard_whitelist:
        - comment: IPv4 localhost
          address: 127.0.0.0/8
        - address: 127.0.0.1/32
        - comment: IPv6 localhost
          address: ::1
  roles:
    - nephosolutions.sshguard
```

## License

This Ansible role is distributed under the Apache-2.0 License.  See the [LICENSE](LICENSE) file for more details.

[geerlingguy.repo-epel]: https://galaxy.ansible.com/geerlingguy/repo-epel/
