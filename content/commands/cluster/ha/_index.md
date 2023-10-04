---
title = "High availibility"
menuTitle = "HA"
weight = 4
---

![](/images/proxcli_cluster_ha_help.png)

## Definition

High Availability ensures that a VM will stay running even if an individual node is shut down. This means that if the device is either powered off or has any sort of issue, the VM will automatically migrate to another node and start there. This will use all nodes to ensure the VMs configured will stay running as close to 100% of the time as possible.

source: [https://www.wundertech.net/how-to-set-up-a-cluster-in-proxmox/]()

Virtual machine HA in proxmox depend on two concepts: 
- groups 
- resources

An HA group is a logical configuration specifying on which nodes the vm can be migrated when a proxmox node fail. 
HA resouces is a virtual machine associated with an HA group. Several resources can be created and associated with a group.

![](/images/proxcli_cluster_ha_schema.png)


