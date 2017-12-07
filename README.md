# rhidm_install_application

## Description:

Install Red Hat Identity Management (IPA) on a system

_Note: Still work in progress_

## Behaviour:

**Feature:** Install Red Hat Identity Management on a system
- **Given** a VM of capable size and power is available
- **Given** the connection details to the VM are known
- **Given** the hostname has been set and configured properly
- **Given** there is working DNS and NTP available
- **Given** the host is using a valid Red Hat subscription
- **When** A new RHEL-system has been installed
- **Then** 
- **Then** Update all packages
- **Then** Install rng-tools for faster random number generators
- **Then** Install ipa-server
- **Then** Ensuring that hosts-file looks proper lines with unwanted occurrences of ListenAddress
- **Then** Add host to /etc/hosts
- **Then** Start rngd
- **Then** Check if swapfile exists
- **Then** Create swapfile
- **Then** Check if IPA-server is already installed
- **Then** Install ipa-server
- **Then** Add firewalld rules

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **rhidm_default_password** | Default Password for IDM | rhidm_default_password=redhat123 |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Install RH IDM
  include_role:
    name: rhidm_install_application
  vars:
    rhidm_default_password: redhat123
```
