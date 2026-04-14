# Alegre Finals - Ansible Playbook

## What this does

- **Enterprise service**: installs and configures **PostgreSQL** on Debian and CentOS/RHEL hosts (group: `db_servers`).
- **Monitoring**: installs **Node Exporter** on all hosts, and installs **Prometheus** on a separate host (group: `monitoring_server`) which scrapes targets from `monitored_nodes`.
- **MOTD**: sets `/etc/motd` to `"Ansible Managed by Alegre"`.

## Inputs

- Config file: `config.yaml`
- Inventory file (structured): `inventory/hosts.yaml`

## How to run

From this folder:

- Install required Ansible collections:
  - `ansible-galaxy collection install -r collections/requirements.yml`

- Syntax check:
  - `ansible-playbook -i inventory/hosts.yaml site.yml --syntax-check`

- Run:
  - `ansible-playbook -i inventory/hosts.yaml site.yml`

## Notes

- For production secrets, use `ansible-vault` for `postgres.db_password`.
- Ensure your remote hosts allow sudo and are reachable via SSH.
