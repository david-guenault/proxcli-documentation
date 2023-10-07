---
title: "Save proxcli inventory file"
weight: 2 
menuTitle: "Create"
---


![](/images/proxcli_inventory_save_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|exclude-tags|a list of coma separated tags to be excluded from the ansible inventory file|string|
|filter-name|a regex applied on host names so only matching host names will be saved in the ansible inventory file|string|
|output-format|one of json or yaml|string|
|path|full path of the ansible inventory file|string|

## Examples

- save a proxmox inventory file in yaml format

```bash
proxcli inventory create --path ./inventory.yaml
```

- save a proxmox inventory file in yaml format with host names matching regex "^test"

```bash
proxcli inventory create --path ./inventory.yaml --filter-name "^test"
```
