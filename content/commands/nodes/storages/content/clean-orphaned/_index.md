+++
title = "List nodes storages content"
weight = 1
menuTitle = "List"
+++


![](/images/proxcli_nodes_storages_content_list_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|storage|the node storage name (local-lvm, isos, ...)|string|
|proxmox-node|proxmox node name|string|
|output-format|output format can be one of table, json, yaml (default to table)|string|
|content-type|filter by content column (iso, tzst, raw, qcow2 ....)|string|
|content-format|filter by content format. Can be one of iso,images,backup,vztmpl|string|
|filter-orphaned|can be YES (orphaned content), NO (no orphaned content), N/A (not applicable to orphaned content). This is a coma separated list. Default to YES,NO,N/A|string|


## Examples

- List specific node storage content

```bash
proxcli nodes storages content list --node pve1 --storage local-lvm
```

- List storage content filtered by images content-type in raw format

```bash
proxcli nodes storages content list --node pve1 --storage b4papp --content-type raw --content-format images 
```
