# 🚀 Ansible Inventory for Stratos DC App Server 1

An Ansible inventory configuration to manage and test connection to **App Server 1 (stapp01)** in **Stratos DC** infrastructure.

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
├── inventory            # Ansible inventory file targeting stapp01
├── playbook.yml         # Playbook to test connection
└── README.md            # Documentation
```

---

## ✅ Credentials (Stratos DC Wiki)

| Server | Hostname | Username | Password |
|--------|----------|----------|----------|
| App Server 1 | `stapp01` | `tony` | `Ir0nM@n` |

---

## 🔧 Inventory Configuration

The `/home/thor/playbook/inventory` file is formatted as:
```ini
[stratos]
stapp01 ansible_host=stapp01 ansible_user=tony ansible_ssh_pass=Ir0nM@n ansible_connection=ssh ansible_ssh_common_args='-o StrictHostKeyChecking=no'
```

---

## 🚀 Usage

Verify connectivity using:
```bash
ansible stratos -i inventory -m ping
```

Run the playbook:
```bash
ansible-playbook -i inventory playbook.yml
```
