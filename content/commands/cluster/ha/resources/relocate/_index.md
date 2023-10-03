---
title: Relocate cluster ha resource
menuTitle: Relocate
date: {}
categories: []
description: ""
keywords: ""
weight: 5
---

![](/images/proxcli_cluster_ha_resources_relocate_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|vmid|The virtual machine id to be relocated|integer|
|filter-name|a regex on virtual machines name used to select multiples virtual machines to be relocated|string|
|proxmox-node|the target node to relocate the virtual machines to|string|
|block|wait for each resources to finish relocation before starting another one (sequential mode)|string|

{{% notice style="note" %}}
vmid and filter-name are mutualy exclusive
{{% /notice %}}

## Examples

- relocate a cluster ha resource to another node

```bash 
proxcli cluster ha resources relocate --vmid 125 --proxmox-node pve1
```

- relocate multiple cluster ha resources to another node

```bash
proxcli cluster ha resources relocate --filter-name "^b4p-powerdns" --proxmox-node pve1
```
- relocate multiple cluster ha resources to another node waiting for each resource to finish relocation

```bash
proxcli cluster ha resources relocate --filter-name "^b4p-powerdns" --proxmox-node pve1 --block
```