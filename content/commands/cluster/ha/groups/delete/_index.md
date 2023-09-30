+++
title = "Delete an HA cluster group"
date = 2023-09-26T10:42:09.000Z
weight = 3
slug = "delete"
keywords = "proxcli"
description = "Delete an HA cluster group"
menuTitle = "Delete"
+++


![](/images/proxcli_cluster_ha_groups_delete_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|group|Cluster ha group name to be deleted|string|


{{% notice style="note" %}}
It is impossible to delete a group with associated resources. You must first delete resources from group and then delete the group
{{% /notice %}}


## Examples

- delete a cluster HA group

```bash
proxcli cluster ha groups delete --group powerdns
```

