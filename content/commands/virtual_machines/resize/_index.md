---
title: Resize virtual machine disk
menuTitle: Resize
date: {}
categories: []
description: ""
keywords: ""
weight: 4
---

![](/images/proxcli_vms_resize_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|vmid|the virtual machine id from which you want to resize the disk|string|
|vmname|the virtual machine name from which you want to resize the disk |string|
|filter-name|regex selector applied on virtual machines names you want to resize the disk|string|
|disk|the disk name in virtual machine config (usualy the one associated with bootdisk)|string|
|size|The desired size of the disk (Ex: 50G)|string|

{{% notice style="info" %}}
vmid, vmname and filter-name are mutualy exclusive
{{% /notice %}}

## Examples

- resize the boot disk

```bash
proxcli vms resize --vmid 111 --disk virtio0 --size "60G"
```
