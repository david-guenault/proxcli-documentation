---
title: "Provision K3S cluster"
menuTitle: "Provision K3S cluster"
weight: 2
---

## Configure proxcli playbooks to provision cluster

Edit the **playbooks/blobal_vars/defaults/main.yml** file and add the following to the **provision_instances** section:

```yaml
  k3s-dev-01:
    ha_groups:
      master:
      node:
    instances:
      master:
        desc: "control plane"
        count: 3
        ha_group: "master"
        memory: 4096
        cores: 4
        disk_storage: "b4pstorage"
        tags:
          - "k3s"
          - "master"
          - "k3s_cluster"
      node:
        desc: "node"
        count: 4
        ha_group: "node"
        memory: 4096
        cores: 4
        disk_storage: "b4papp"
        tags:
          - "k3s"
          - "node"
          - "k3s_cluster"    
```

## Launch cluster provisionning

```bash
pcreate k3s-dev-01
```

After a few minutes you will have the vm spreaded over your nodes and available. 


## Deploy the k3s cluster

We will use the following playbook provided on k3s.io github repositories: https://github.com/k3s-io/k3s-ansible

```bash
git clone https://github.com/k3s-io/k3s-ansible
cd k3s-ansible
cp -a inventory/sample inventory/k3s-dev-01
proxcli inventory save --filter-name "^k3s-dev-01" --output-format yaml --path ./inventory/k3s-dev-01/inventory.yaml
ansible-playbook -i inventory/k3s-dev-01/inventory.yaml --extra-vars="ansible_user=system" site.yml
```
