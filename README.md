# Ansible Role: sshguard

## Description

Manage sshguard protects hosts from brute-force attacks against SSH and other services.

## Requirements

None

## Dependencies

None

## OS Platforms

- CentOS-7
- Ubuntu-20.04
- Ubuntu-22.04

## Example Playbook

```
- hosts: all
  roles:
    - sshguard
```

## Role Variables

### sshguard_package_ensure: (string)

```
sshguard_package_ensure: "present"
```

### sshguard_service_ensure: (string)

```
sshguard_service_ensure: "started"
```

### sshguard_service_enable: (bool)

```
sshguard_service_enable: true
```

### sshguard_config_options: (dict)

```
sshguard_config_options: {}
```

### sshguard_config_whitelist: (dict)

```
sshguard_config_whitelist: {}
```

## Example vars

```
sshguard_config_options:
  BACKEND: "/usr/libexec/sshguard/sshg-fw-nft-sets"
  LOGREADER: "LANG=C journalctl -afb -p info -n1 -t sshd -o cat"
  THRESHOLD: 30
  BLOCK_TIME: 120
  DETECTION_TIME: 1800
  WHITELIST_FILE: /etc/sshguard/whitelist

sshguard_config_whitelist:
  - "127.0.0.0/8"
  - "::1/128"
```
