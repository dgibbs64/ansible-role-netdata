# netdata

An [Ansible](https://www.ansible.com) role that installs and configures <a href="https://www.netdata.cloud">netdata</a> agent for standalone or cloud use.

<p align="center">
  <img src="https://github-production-user-asset-6210df.s3.amazonaws.com/4478206/248550959-b4dc7485-34bb-4915-94dc-25ec4df79a68.jpg" alt="Ansible Netdata"></a>
<br>
</p>
<p align="center">
<a href="https://app.codacy.com/gh/dgibbs64/ansible-role-netdata"><img src="https://img.shields.io/codacy/grade/1a892d499efd4dabb73beffa8d64ed01?logo=codacy&style=flat-square" alt="Codacy grade"></a>
<a href="https://github.com/dgibbs64/ansible-role-netdata/actions/workflows/molecule.yml"><img alt="GitHub Workflow Status" src="https://img.shields.io/github/actions/workflow/status/dgibbs64/ansible-role-netdata/molecule.yml?label=molecule&logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/netdata"><img alt="GitHub tag (latest by date)" src="https://img.shields.io/github/v/tag/dgibbs64/ansible-role-netdata?color=EE0000&label=release&logo=ansible&style=flat-square"></a>
<a href="https://github.com/dgibbs64/ansible-role-netdata/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/gameservermanagers/docker-steamcmd?style=flat-square" alt="MIT License"></a>
</p>

## About

<a href="https://www.netdata.cloud">Netdata</a> is a monitoring agent that can be installed on Linux systems to collect metrics and provide a web dashboard for viewing metrics. This role will install or remove netdata agent and can be configured to use the standalone dashboard or the cloud dashboard.

## Requirements

Requires a <a href="https://www.netdata.cloud">Netdata</a> account to use the cloud features.

### Supported Distros

- AlmaLinux >= 8
- AmazonLinux 2023
- CentOS >= 8
- Debian >= 10
- Fedora >= 29
- openSUSE >= 15.4
- OracleLinux >= 8
- Pop!\_OS >= 20.04
- Redhat Enterprise Linux >= 8
- Rocky Linux >= 8
- Ubuntu >= 20.04

## Role Variables

By default this role will setup netdata agent with the standalone dashboard enabled.

To enable cloud functionality change `netdata_cloud_enable` to `true` and set the `netdata_cloud_claim_token` and `netdata_cloud_claim_room_id` variables. See the [Netdata Cloud documentation](https://learn.netdata.cloud/docs/installing/install-with-a-cicd-provisioning-system/ansible#edit-the-varsmainyml-file) for more information.

To disable the standalone dashboard set `netdata_agent_web_enabled` to `false`. See the [Netdata documentation](https://learn.netdata.cloud/docs/configuring/securing-netdata-agents/) for more information on securing netdata.

```yaml
# Netdata cloud
# https://learn.netdata.cloud/docs/installing/install-with-a-cicd-provisioning-system/ansible#edit-the-varsmainyml-file
netdata_cloud_enable: false
netdata_cloud_claim_url: https://app.netdata.cloud
netdata_cloud_claim_token:
netdata_cloud_claim_room_id:
netdata_cloud_force_claim: false

# Netdata agent
# Channel stable|edge
netdata_agent_channel: stable

# Agent state present|absent
netdata_agent_state: present

# netdata.conf template location
netdata_agent_conf_template: netdata.conf.j2

## Netdata agent web dashboard
# https://learn.netdata.cloud/docs/configuring/securing-netdata-agents/
netdata_agent_web_enabled: true
netdata_agent_web_port: 19999
netdata_agent_web_bind_to:
netdata_agent_web_allow_from:
```

## Dependencies

```yaml
community.general
```

## Example Playbook

```yaml
---
- name: Netdata
  hosts: all
  roles:
    - dgibbs64.netdata
```

## License

MIT

## Author Information

- [Daniel Gibbs](https://danielgibbs.co.uk)
