+++
title = "Create an HA cluster group"
date = 2023-09-26T10:42:09.000Z
weight = 2
slug = "create"
keywords = "proxcli"
description = "Create an HA cluster group"
menuTitle = "Create"
+++


![](/images/proxcli_cluster_ha_groups_create_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|group|Cluster ha group name to be created|string|
|proxmox-nodes|On which proxmox nodes the group should apply|string|
|restricted|The CRM tries to run services on the node with the highest priority. If a node with higher priority comes online, the CRM migrates the service to that node. Enabling nofailback prevents that behavior.|N/A|
|nofailback|Resources bound to restricted groups may only run on nodes defined by the group. The resource will be placed in the stopped state if no group node member is online. Resources on unrestricted groups may run on any cluster node if all group members are offline, but they will migrate back as soon as a group member comes online. One can implement a preferred node behavior using an unrestricted group with only one member.|N/A|


## Examples

- create an HA group for application powerdns. the group will use proxmox nodes pve1 and pve2 and make sure the group resources will stay on those 2 nodes

```bash
proxcli cluster ha groups create --group powerdns --nofailback --proxmox-nodes "pve1,pve2"
```

