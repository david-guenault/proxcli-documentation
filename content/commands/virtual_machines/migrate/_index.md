+++
title = "Migrate a virtual machine"
date = 2023-09-26T10:42:09.000Z
weight = 7
slug = "migrate"
keywords = "proxcli"
description = "Migrate a virtual machine"
menuTitle = "Migrate"
+++


![](/images/proxcli_vms_migrate_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|vmid|The virtual machine id to migrate|integer|
|filter-name|A regex string to select multiple virtual machines to be migrated|string regex|
|target-node|the proxmox target node name|string|

{{% notice style="info" %}}
vmid and filter-name are mutualy exclusive
{{% /notice %}}


## Examples

{{% notice style="note" %}}
You can't migrate a running virtual machine. The only way to do live migration is through cluster ha resource migrate.
See [cluster ha section](/commands/cluster/ha)
{{% /notice %}}

- migrate a virtual machine from one proxmox node to other

```bash
proxcli vms migrate --vmid 111 --target-node pve2 
```

- migrate multiples virtual machines by selecting the with a regex filter on their name

```bash
proxcli vms migrate --filter-name "^b4p" --target-node pve2
```
