---
title: Delete virtual machine
menuTitle: Delete
date: {}
categories: []
description: ""
keywords: ""
weight: 5
---

![](/images/proxcli_vms_delete_help.png)

# Options

|option|description|Allowed values|
|---|---|---|
|vmid|the virtual machine id you want to delete|string|
|filter-name|a regex applied on virtual machine name |string|
|confirm|does not ask for confirmation|N/A|
|block|block the command until it finished|N/A|

## Examples

- delete a virtual machine by its id

```bash
proxcli vms delete --vmid 111
```

- delete all virtual machines matching the specified regex

```bash
proxcli vms delete --filter-name "^b4p"
```

- delete all virtual machines matching the specified regex without any confirmation and wait for all deletion to be finished before exiting

```bash
proxcli vms delete --filter-name "^b4p" --confirm --block
```
