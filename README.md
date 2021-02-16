Rancher Node Cordon
=========

Ansible role to manage Kubernetes node cordoning via the Rancher API.

Pre-Requisites
------------

API keys are required for authentication to Rancher.

https://rancher.com/docs/rancher/v2.x/en/api/

Role Variables
--------------

`rancher_host: rancher.derby.ac.uk`

`rancher_node_name: "{{ inventory_hostname }}"`

`rancher_node_cordon: uncordoned / cordoned / drained`

`rancher_user: token-fffff`

`rancher_password: api_secret_key`

Example Playbook
----------------

```
---
- hosts: rancher_nodes
  gather_facts: false
  connection: local

  vars:
    rancher_host: rancher.derby.ac.uk
    rancher_node_name: "{{ inventory_hostname }}"
    rancher_node_cordon: cordoned

  roles:
    - rancher-node-cordon

```

Usage
-----------------
Add 'rancher_node_cordon' as a host var with the desired state, or declare within a playbook (By default 'uncordoned' is the desired state)

Example ansible-playbook command:

`ansible-playbook -i ../../inventory.yml --limit k8s-tst-wn01 -e@credential.yml playbook.yml --ask-vault-pass`

Authors
------------------

* Luke Williams - Initial Work