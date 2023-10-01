---
title: Delete cluster ha resource
menuTitle: Delete
date: {}
categories: []
description: ""
keywords: ""
weight: 2
---

![](/images/proxcli_cluster_ha_resources_delete_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|vmid|the virtual machine id you want to remove from resources|string|
|filter-name|A regex applied on virtual machine name used to select matching virtual machines to remove from resources|string|

## Examples

- Delete a single cluster ha resource by virtual machine id

```bash
proxcli cluster ha resources delete --vmid 105
```

- Delete all cluster ha resources (not recomended)

```bash
proxcli cluster ha resources delete --filter-name "^.*$"
```
