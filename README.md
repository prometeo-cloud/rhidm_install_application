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
- **Then** Update all packages
- **Then** yum - Install rng-tools for faster random number generators
- **Then** yum - Install ipa-server
- **Then** Remove host from /etc/hosts
- **Then** Add host to /etc/hosts
- **Then** Start rngd
- **Then** Check if swapfile exists
- **Then** Setup swap
- **Then** Check if IPA is already installed
- **Then** Install ipa-server
- **Then** Check if firewalld is in use
- **Then** Add firewalld rules


## Configuration:

Common variables used by this role:

| Variable  | Required | Description  | Example  | 
|---|---|---|---|
| **rhidm_default_password** | yes | Default Password for IDM | rhidm_default_password=redhat123 |
| **rhidm_firewall_ports**   | no  | Firewall ports to open if firewalld is installed | rhidm_firewall_ports="[{"port":80,"proto":"tcp"},{"port":443,"proto":"tcp"}]" |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Install RH IDM
  include_role:
    name: rhidm_install_application
  vars:
    rhidm_default_password: redhat123
    rhidm_firewall_ports:
      - {port: 80, proto: tcp}
      - {port: 443, proto: tcp}
      - {port: 389, proto: tcp}
      - {port: 88, proto: tcp}
      - {port: 464, proto: tcp}
      - {port: 53, proto: tcp}
      - {port: 53, proto: udp}
      - {port: 88, proto: udp}
      - {port: 464, proto: udp}
      - {port: 123, proto: udp}
```
