# netdata

An [Ansible](https://www.ansible.com) role that installs and configures netdata agent for local or cloud use.

<p align="center">
  <img src="https://user-images.githubusercontent.com/4478206/202930662-130cf21e-8d0c-4b4d-a9af-82c61b0b62d.png" alt="Ansible Netdata"></a>

<br>
</p>
<p align="center">
<a href="https://app.codacy.com/gh/dgibbs64/ansible-role-netdata"><img src="https://img.shields.io/codacy/grade/1a892d499efd4dabb73beffa8d64ed01?logo=codacy&style=flat-square" alt="Codacy grade"></a>
<a href="https://github.com/dgibbs64/ansible-role-netdata/actions/workflows/molecule.yml"><img alt="GitHub Workflow Status" src="https://img.shields.io/github/actions/workflow/status/dgibbs64/ansible-role-netdata/molecule.yml?label=molecule&logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/netdata"><img alt="Ansible Quality Score" src="https://img.shields.io/ansible/quality/60605?logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/netdata"><img alt="Ansible Role" src="https://img.shields.io/ansible/role/d/60605?color=EE0000&logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/netdata"><img alt="GitHub tag (latest by date)" src="https://img.shields.io/github/v/tag/dgibbs64/ansible-role-netdata?color=EE0000&label=release&logo=ansible&style=flat-square"></a>
<a href="https://github.com/dgibbs64/ansible-role-netdata/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/gameservermanagers/docker-steamcmd?style=flat-square" alt="MIT License"></a>
</p>

## Requirements

Requires a <a href="https://www.netdata.cloud">Netdata</a> account to use the cloud features.

## Role Variables

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

```
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
