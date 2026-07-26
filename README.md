# Ansible Inventory & Playbook Setup – Stratos DC

Configured Ansible connectivity from a jump host to app servers in Stratos DC and validated playbook execution against them.

## What was done
- Created INI-style Ansible inventory files (`inventory`) defining app server hosts (e.g. `stapp01`, `stapp02`) with the required connection variables (`ansible_host`, `ansible_user`, `ansible_ssh_pass`, `ansible_connection`, `ansible_ssh_common_args`).
- Wrote a playbook to create an empty file (`/tmp/file.txt`) on a target app server using the `ansible.builtin.file` module.
- Ran an existing playbook to install and start the `httpd` service on an app server, confirming successful execution (`failed=0`).
- Verified all playbooks run cleanly with `ansible-playbook -i inventory playbook.yml`, requiring no extra CLI arguments.

## Validation
- Confirmed target file creation via direct SSH check.
- Confirmed `httpd` package install and active service status.
- Re-ran playbooks to verify idempotency (`changed=0` on repeat runs).

**Stack:** Ansible, SSH, Linux (RHEL/CentOS-based app servers)
