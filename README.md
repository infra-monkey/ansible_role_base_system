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
| debian_fallback_to_testing | boolean | no | `false` | Should the debian fallback to the testing repo when a package is not available in the stable repo. |
| debian_fallback_to_unstable | boolean | no | `false` | Should the debian fallback to the unstable repo when a package is not available in the stable repo. (example of freeipa-client in bullseye) |

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
- Python 3.7, 3.8 and 3.8
- CentOS 7/8/9
- Debian 9/10/11