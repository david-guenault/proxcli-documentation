---
title: "Show cluster nodes tasks"
weight: 4
menuTitle: "Tasks"
---


![](/images/proxcli_nodes_tasks_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|proxmox-nodes|coma separated list of proxmox nodes from which we want to grab tasks|string|

## Examples

- Show tasks on a list of proxmox nodes

```bash
proxcli nodes tasks --proxmox-nodes "pve1,pve2"
```
