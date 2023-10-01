+++
title = "Set virtual machine tags"
date = 2023-09-26T10:42:09.000Z
draft = false
weight = 1
slug = "set"
menuTitle = "Set"
+++

![](/images/proxcli_vms_tags_set_help.png)


## Options

|option|description|Allowed values|
|---|---|---|
|vm-tags|coma separated list of tags|string|
|filter-name|regex applied to match virtual machine names|string|

## Examples

- Set tags for all vms name matching the specified regex

```bash 
proxcli vms tags set --vm-tags "template,ubuntu" --filter-name "^ubuntu-cloud"
```
