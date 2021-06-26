# Overview
This role installs and configures packages needed on all hosts.
This role requires root permissions. It must be called as root. This needs to be managed at the ansible or playbook level.

On RedHat based systems, EPEL is enabled as it provides htop.
On Debian systems, `resolvconf` is replaced by `openresolv` for compatibility with cloud-init.

# Variables

| Name  | Type | Required | Default Value | Description |
| ----- | ---- | -------- | ------------- | ----------- |
| use_debian_backports | boolean | no | `false` | Should the backports repo be enabled on debian |
| journal_forward_to_syslog | string | no | "no" | Accepted values are "yes" and "no" |

# Installed Packages

| RedHat | Debian |
| ------ | ------ |
| htop | htop |
| zsh | zsh |
| zsh-syntax-highlighting | zsh-syntax-highlighting |
| vim | vim |
| redhat-lsb | acl |
|  | openresolv |
|  | apt-transport-https |
|  | python*-apt |
|  | ssl-cert |

# Uninstalled Packages

| RedHat | Debian |
| ------ | ------ |
|  | resolvconf |

# Automatique Testing

This role is tested using Molecule against:
- Python 3.7 and 3.8
- CentOS 7/8
- Debian 9/10