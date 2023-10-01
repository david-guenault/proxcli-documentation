---
title: Migrate cluster ha resource
menuTitle: Migrate
date: {}
categories: []
description: ""
keywords: ""
weight: 3
---

![](/images/proxcli_cluster_ha_resources_migrate_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|--vmid|The virtual machine id to migrate|integer|
|--filter-name|a regex on virtual machines name used to select multiples virtual machines to be migrated|string|
|--node|the target node to migrate the virtual machines to|string|

{{% notice style="note" %}}
vmid and filter-name are mutualy exclusive
{{% /notice %}}

## Examples

- migrate a cluster ha resource to another node

```bash 
proxcli cluster ha resources migrate --vmid 125 --node pve1
```

- migrate multiple cluster ha resources to another node

```bash
proxcli cluster ha resources migrate --filter-name "^b4p-powerdns" --node pve1
```