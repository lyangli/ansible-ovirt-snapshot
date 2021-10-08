# oVirt snapsot

An ansible playbook to manage oVirt/Red Hat Virtualization(RHV) snaphot.

## Prerequisites

    1. Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).
    2. Install dependencies for oVirt Ansible Collection.
        ```sh
        dnf install ansible libcurl-devel libxml2-devel gcc python3-devel python3-passlib python3-netaddr
        pip3 install --user ovirt-engine-sdk-python
        ```
    3. Install oVirt Ansible Collection.
        ```sh
        ansible-galaxy collection install ovirt.ovirt
        ```

## Configuration

Use following files as reference and modify to replace variables with yours.

### 1. inventory_sample.yml
    - Define oVirt/RHV server to connect to.

### 2. group_vars/sample.yml
    - Email report configuration

### 3. host_vars/sample.yml
    - oVirt/RHV configuration
    - List of VM to snapshots

### 4. dev_create.yml
    - Playbook to create snapshot for VM in the list.
    - Created snapshot description format is `beforepatch_<yyyy-mm-dd>_by_Ansible`.

### 5. dev_delete.yml
    - Playbook to delete snapshot for VM in the list.
    - Default snapshot query string is `beforepatch_*_by_Ansible`.

### 6. dev_list_all.uml
    - Playbook to list all the snapshots for in the list.

### 7. ansiblevirtsvc.yml (Ansible Vault)
    - Store the oVirt/RHV ansible service account password in variable `ovirt_credential.password`

## How to run 

- To create snapshot
  ```sh
  ansible-playbook dev_create.yml --ask-vault-pass
  ``` 

- To delete snapshot
  ```sh
  ansible-playbook dev_delete.yml --ask-vault-pass
  ``` 

- To list all snapshot
  ```sh
  ansible-playbook dev_list_all.yml --ask-vault-pass
  ```

## Tested on

- ansible 2.9.25
- oVirt Ansible Collection 1.6.1

## Resources

[Ansible Playbook](http://docs.ansible.com/ansible/latest/playbooks.html)
[Download oVirt Ansible Collection](https://galaxy.ansible.com/ovirt/ovirt)
[oVirt Ansible Collection Documentation](https://docs.ansible.com/ansible/latest/collections/ovirt/ovirt/index.html)

## About the Author

This project was created by Loke Yangli.

