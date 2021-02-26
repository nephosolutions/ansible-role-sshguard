# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

## [1.0.2] - 2021-02-26

* Fixed vars for RHEL 7 to work out of the box

## [1.0.1] - 2021-01-14

Changed order of tasks to prevent systemd from triggering a service
start failure due to too many service restarts in a short period of
time on RHEL.

## [1.0.0] - 2020-04-02

Initial release

[Unreleased]: https://github.com/nephosolutions/ansible-role-sshguard/compare/1.0.2...HEAD
[1.0.2]: https://github.com/nephosolutions/ansible-role-sshguard/compare/1.0.1...1.0.2
[1.0.1]: https://github.com/nephosolutions/ansible-role-sshguard/compare/1.0.0...1.0.1
[1.0.0]: https://github.com/nephosolutions/ansible-role-sshguard/releases/tag/1.0.0
