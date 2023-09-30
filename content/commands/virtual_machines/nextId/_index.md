+++
title = "Display the next available vm id"
date = 2023-09-26T10:42:09.000Z
weight = 7
slug = "nextid"
keywords = "proxcli"
description = "Display the next available vm id"
menuTitle = "NextId"
+++



## Options

|option|description|Allowed values|
|---|---|---|


## Examples

- Display the next available virtual machine id

```bash
proxcli vms nextId
```

- migrate multiples virtual machines by selecting the with a regex filter on their name

```bash
proxcli vms migrate --filter-name "^b4p" --target-node pve2
```
