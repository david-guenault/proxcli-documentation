---
title: Wait for virtual machine status
weight: 13
menuTitle: "Wait status"
---

![](/images/proxcli_vms_wait_for_status_help.png)

## Description

wait for virtual machines to reach the desired status (stopped, running ...)

## Options

|option|description|Allowed values|
|---|---|---|
|vmid|the virtual machine id you want to wait for reaching the desired status|string|
|name|the virtual machine name you want to wait for reaching the desired status|string|
|filter-name|a regex applied on virtual machine name you want to wait for reaching the desired status|string|
|status|the desired status|string|

{{% notice style="info" %}}
vmid, name and filter-name are mutualy exclusive
{{% /notice %}}

## Examples

- wait for every virtual machine with name start with test to be stopped

```bash
proxcli vms wait_for_status --filter-name "^test" --status "stopped"
```
