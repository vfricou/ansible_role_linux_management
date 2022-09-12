# Ansible Role: linux_management

# Disclaimer

I couldn't be responsible with any production issues if you use this role without any prior tests.  
This role is designed for my proper environment and possibly not correspond to your.

The master branch is development branch. Use only release/* branches for production.

# Introduction

This role is designed to perform postinstallation on GNU/Linux servers and to performs systems updates.  
It's structured and do tasks according to my own postinstallation and production needs.  
Feel free to fork and update this according to your requirements.

# Supported OS

**Debian** :
- buster (10)
- bullseye (11)

**Ubuntu** :
- Bionic Beaver (18.04)
- Focal Fossa (20.04)
- Jammy Jellyfish (22.04)

**Rocky** :
- 8

**AlmaLinux** :
- 8

**RHEL** :
- 8

# Requirements

## On target OS

You need to have python3 package installed on remote OS to use this role.

# Actions

- Perform full system update
- Install required packages (see [packagelist](#package-list))

# Package List

| Collection | OS             | Package             |
| ---------- | -------------  |---------------------|
| Disk       | All            | iotop               |
| Disk       | All            | ncdu                |
| Disk       | Debian (based) | gdisk               |
| Disk       | RHEL (based)   | gdisk               |
| Editor     | Debian (based) | vim                 |
| Editor     | OpenSUSE       | vim                 |
| Editor     | RHEL (based)   | vim-enhanded        |
| Network    | All            | iftop               |
| Network    | All            | nmap                |
| Network    | All            | mtr                 |
| Network    | All            | tcpdump             |
| Network    | Debian (based) | nicstat             |
| Security   | All            | iptables            |
| Security   | Debian (based) | auditd              |
| Security   | OpenSUSE       | audit               |
| Security   | RHEL (based)   | audit               |
| Shell      | All            | zsh                 |
| System     | All            | htop                |
| System     | All            | strace              | 
| System     | All            | git                 |
| System     | All            | ca-certificates     |
| System     | All            | tree                |
| System     | Debian (based) | alien               |
| System     | Debian (based) | pastebinit          | 
| System     | Debian (based) | apt-transport-https |
| System     | OpenSUSE       | snapper             |

# Changelog

To clearest and updated changelog, I encourage you to see pull requests with flags "feature".

# Roadmap

You could refer to milestones to full current roadmap.

### v1.0.0

- Hability to perform postinstall and updates process on following OS :
  - Debian 10
  - Debian 11
  - RHEL 8
  - Rocky 8
  - Ubuntu 18.04
  - Ubuntu 20.04
  - Ubuntu 21.04
- Capacity of users packages locking/exclusions during update process

### v2.0.0

- OpenSUSE 15 support
- Hability to add users packages into install process

# Tests

Initials tests was done through molecule.  
Role fully tested on virtual machines vanilla installed.

## Normal fails on molecule tests

According to container environments, handlers executions fails at molecule converge/idempotence.  
Actually, auditd wasn't supported to run into container environments.
