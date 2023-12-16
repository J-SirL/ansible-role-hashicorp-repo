# HashiCorp Repository Setup Ansible Role

## Overview

This Ansible role sets up the HashiCorp repository and installs Packer and Vagrant specifically for AlmaLinux 9.

## Prerequisites

- Ansible installed on the control node.
- Target hosts must be running AlmaLinux 9.

## Role Structure

```
JsirL.hashicorp_repo/
├── LICENSE
├── meta
│   └── main.yml
├── README.md
├── tasks
│   └── main.yml
└── tests
    ├── inventory
    └── test.yml
```

## Instructions
 You can either clone the repository or create an requirements.yml to add repo in your own project
 ### Clone the repository 

   ```bash
   git clone git@github.com:J-SirL/ansible-role-hashicorp-repo.git
   ```
 ### Create an requirements.yml to add repo in your own project
  
  ```bash
   #Create requirements.yml in your git repository
   cd your-git-repo
   mkdir -p roles # if you do not have a roles folder
   vi roles/requirements.yml
   ```
   #### Paste in the below in roles/requirements.yml
   ```bash
   ---
   roles:

     - name: JsirL.hashicorp_repo
       src: git@github.com:J-SirL/ansible-role-hashicorp-repo.git
       scm: git
       version: main
   ```
   #### Install the role with ansible-galaxy using your newly created requirements.yml
   ```bash
   ansible-galaxy install -r roles/requirements.yml
   ```

   ### Create an Ansible playbook

   Create a playbook to use the `hashicorp_repo` role.

   ```yaml
   ---
   - name: Install and configure HashiCorp tools packer and vagrant on AlmaLinux 9
     hosts: almalinux_servers
     gather_facts: yes
     become: true
     tasks:
       - name: Include the hashicorp_repo role
         ansible.builtin.include_role:
           name: JsirL.hashicorp_repo
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

## Author Information
```
Created by Johan Sörell 16 December 2023

```

