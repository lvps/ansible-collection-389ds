# 389DS Ansible Collection

The `lvps.ds389` collection packages the following upstream roles:

- `lvps.ds389.server` — installs and configures a 389 Directory Server.
- `lvps.ds389.replication` — configures replication between existing 389DS instances.

The roles remain maintained in their upstream repositories. This repository pins released role revisions as Git submodules so collection builds are reproducible.

## Installation

```yaml
---
- name: Install 389DS
  hosts: ldap_servers
  become: true
  roles:
    - role: lvps.ds389.server
      dirsrv_rootdn_password: "{{ vault_dirsrv_rootdn_password }}"
```

Install the collection from Ansible Galaxy with `ansible-galaxy collection install lvps.ds389`.

The collection depends on `community.general`, which Ansible Galaxy installs automatically.

Replication requires a running 389DS server. Apply the server role before the replication role and store all passwords in Ansible Vault or an external secret manager.

## Development

Clone the repository with its roles:

    git clone --recurse-submodules https://github.com/lvps/ansible-collection-389ds.git

For an existing checkout, initialise the submodules with `git submodule update --init --recursive`.

Run the same checks as CI by installing `requirements.txt`, then running `yamllint`, `ansible-lint`, and `ansible-galaxy collection build --force`.

Role updates must use released upstream tags. Update the submodule pointer, change the collection version in `galaxy.yml`, update `CHANGELOG.md`, and verify the generated archive before creating a GitHub release.

## Licences

The server role is Apache-2.0 licensed and the replication role is MIT licensed. Their licence files are included with the respective role sources.