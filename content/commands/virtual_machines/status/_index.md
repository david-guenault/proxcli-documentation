+++
title = "Set virtual machine status"
date = 2023-09-26T10:42:09.000Z
draft = false
weight = 11
slug = "status"
menuTitle = "Status"
+++

## Description

Virtual machine status commands use the same options interface for every desired status. The following options table apply to all status commands such as start, stop, suspend or reset. 

## Options

|option|description|Allowed values|
|---|---|---|
|vmid|the virtual machine id you want to delete|string|
|filter-name|a regex applied on virtual machine name |string|


## Examples

- Start virtual machine

```bash
proxcli vms start --vmid 101
```

- Stop virtual machine

```bash
proxcli vms stop --vmid 101
```

- Suspend all virtual machines with name matching specified regex

```bash
proxcli vms suspend --filter-name "^b4p"
```

- Reset virtual machine

```bash
proxcli vms reset --vmid 101
```
