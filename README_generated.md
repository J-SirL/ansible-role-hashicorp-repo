# HashiCorp Repository Setup Ansible Role

## Overview

This Ansible role sets up the HashiCorp repository and installs Packer and Vagrant with KVM support specifically for AlmaLinux 9.

## Prerequisites

- Ansible installed on the control node.
- Target hosts must be running AlmaLinux 9.

## Role Structure

```
hashicorp_repo/
├── tasks/
│   └── main.yml
├── handlers/
│   └── main.yml
└── README.md
```

## Instructions

1. **Clone the repository:**

   ```bash
   git clone git@github.com:J-SirL/ansible-role-hashicorp-repo.git
   ```

2. **Create an Ansible playbook:**

   Create a playbook to use the `hashicorp_repo` role.

   ```yaml
   ---
   - name: Install and configure HashiCorp tools on AlmaLinux 9
     hosts: almalinux_servers
     gather_facts: yes
     become: true
     tasks:
       - name: Include the hashicorp_repo role
         ansible.builtin.include_role:
           name: hashicorp_repo
   ```

3. **Execute the playbook:**

   Run the playbook using the following command:

   ```bash
   ansible-playbook -i inventory_file <playbook_name>.yml
   ```

   Replace `<playbook_name>` with your playbook filename and `inventory_file` with your host inventory.

## Notes

- This role is specifically designed for AlmaLinux 9 and might need adjustments for other distributions.
- Ensure proper network connectivity for downloading HashiCorp repository keys and packages.

## License

This project is licensed under the [GPL-3.0](LICENSE).
```

Feel free to adjust and customize this README.md according to your preferences and any additional information you want to provide regarding the usage or configuration of the role.