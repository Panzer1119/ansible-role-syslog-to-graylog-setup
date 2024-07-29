# Ansible Role: Syslog to Graylog Setup

This Ansible role installs and configures rsylog or rsyslog-ng to send logs to Graylog.

## Installation

```bash
ansible-galaxy role install Panzer1119.syslog-to-graylog-setup
```

## Variables

- `preferred_syslog_daemon`: Preferred syslog daemon (default: `"rsyslog"`, options: `"rsyslog"`, `"syslog-ng"`)
- `install_syslog_daemon_if_missing`: Whether to install syslog daemon if missing (default: `true`)

- `graylog_protocol`: Protocol for Graylog (default: `"udp"`, options: `"tcp"`, `"udp"`)
- `graylog_host`: Hostname for Graylog (default: `"graylog"`)
- `graylog_port`: Port for Graylog (default: `1514`)

## Example Playbook

```yaml
- hosts: all
  become: yes
  vars:
    preferred_syslog_daemon: "rsyslog"
    install_syslog_daemon_if_missing: true
    graylog_protocol: "udp"
    graylog_host: "graylog"
    graylog_port: "1514"
  roles:
    - ansible-role-syslog-to-graylog-setup
```

Test it with the following command:

```bash
ansible-playbook -i inventory playbook.yml -CD
```
