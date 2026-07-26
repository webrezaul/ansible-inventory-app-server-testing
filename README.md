# 🚀 Ansible Inventory & Playbook Setup – Stratos DC

Configured Ansible connectivity from a jump host to app servers in Stratos DC and validated playbook execution against them.

---

## 📦 Stack / Tech Used

| Technology   | Version  | Purpose                                      |
|--------------|----------|----------------------------------------------|
| Ansible      | `v2.9+`  | Configuration management and task automation |
| YAML         | `1.2`    | Playbook serialization format                |
| SSH          | `OpenSSH`| Secure communication channel to App Server 1 |

---

## 📁 Project Structure

```
.
├── inventory            # INI-style inventory file defining target hosts
├── playbook.yml         # Playbook targeting Stratos DC app servers
└── README.md            # Project documentation
```

---

## ✅ Prerequisites

Before running the playbook, make sure you have the following setup:
- **Ansible** installed on your control/jump host node.
- SSH access enabled from the control node to the Stratos DC hosts.

---

## 🔧 Configuration & Credentials

### Stratos DC App Server Credentials (Wiki)

| Hostname | Host Alias | Username | Password | Description |
|----------|------------|----------|----------|-------------|
| `stapp01`| `stapp01`  | `tony`   | `Ir0nM@n`| App Server 1|
| `stapp02`| `stapp02`  | `steve`  | `Am3ric@`| App Server 2|

#### Inventory File Format (`/home/thor/playbook/inventory`):
```ini
[stratos]
stapp01 ansible_host=stapp01 ansible_user=tony ansible_ssh_pass=Ir0nM@n ansible_connection=ssh ansible_ssh_common_args='-o StrictHostKeyChecking=no'
```

---

## 📋 Available Commands

| Command                                     | Description                                                    |
|---------------------------------------------|----------------------------------------------------------------|
| `ansible-playbook -i inventory playbook.yml`| Executes the playbook against hosts defined in the inventory  |
| `ansible-inventory -i inventory --list`     | Lists all parsed hosts and host variables                      |
| `ansible -i inventory stratos -m ping`      | Pings Stratos DC hosts to test connectivity                    |

---

## 🛠️ What Was Done

- **INI-style Inventory Configuration**: Created the `inventory` file on the jump host defining app server hosts with mandatory connection variables (`ansible_host`, `ansible_user`, `ansible_ssh_pass`, `ansible_connection`, `ansible_ssh_common_args`).
- **File Management Automations**: Wrote playbooks to automate tasks like creating empty files (`/tmp/file.txt`) on the target servers using the `ansible.builtin.file` module.
- **Service Configuration Automations**: Configured playbooks to automate the installation and startup of services like `httpd` on app servers, confirming successful completion.
- **Clean Execution**: Verified all playbooks run cleanly without requiring extra CLI flags.

---

## 🔍 Validation

- **Connection Auditing**: Confirmed target file creation via direct SSH audits.
- **Service Verification**: Audited package installations and ensured target services are active and running.
- **Idempotency Audits**: Verified playbook idempotency (`changed=0` on repeat runs).

---

## ✍️ Author

- **GitHub**: [webrezaul](https://github.com/webrezaul)
- **Website**: [mdrezaulkarim.com](https://mdrezaulkarim.com)
