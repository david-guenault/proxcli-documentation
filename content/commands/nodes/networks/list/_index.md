---
title: "List nodes networks"
weight: 1
menuTitle: "List"
---


![](/images/proxcli_nodes_networks_list_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|proxmox-nodes|coma separated list of proxmox nodes from which we want to grab networks|string|
|output-format|format to display networks list (json, yaml or table)|string|

## Examples

- Show networks from a selected list of nodes

```bash
proxcli nodes nodes networks list --proxmox-nodes "pve1,pve2"
```
