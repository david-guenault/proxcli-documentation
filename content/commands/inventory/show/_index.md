---
title: Show computed proxcli inventory
menuTitle: Show
weight: 1
---

![](/images/proxcli_inventory_show_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|filter-name|filter inventory by a regex applyed on virtual machines names|string|
|exclude-tag|exclude tags from inventory. Comma separated list of tags|string|
|output-format|output format is one of (table, json, yaml)|string|

## Examples

- show computed inventory

```bash
proxcli inventory show
```

- show computed inventory with only virtual machine names starting by test

```bash
proxcli inventory show --filter-name "^test"
```

- show computed inventory with only virtual machine names starting by test and exclude production tag

```bash
proxcli inventory show --filter-name "^test" --exclude-tag "production"
```
