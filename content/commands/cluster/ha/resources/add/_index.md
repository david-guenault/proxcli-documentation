---
title: Add cluster ha resource
menuTitle: Add
date: {}
categories: []
description: ""
keywords: ""
weight: 1
---

![](/images/proxcli_cluster_ha_resources_add_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|group|the cluster ha group this resource belong to|string|
|vmid|the virtual machine id you want to assign to the resource |string|
|name|the cluster ha resource name|string|
|comment|additional information for this resource|N/A|
|state|Requested resource state. The CRM reads this state and acts accordingly. Please note that enabled is just an alias for started. (disabled | enabled | ignored | started | stopped)|string|
|max-relocate|Maximal number of service relocate tries when a service failes to start|integrer|
|max-restart|Maximal number of tries to restart the service on a node after its start failed.|integer|

## Examples

- create a cluster ha resource with minimal informations

```bash
proxcli cluster ha resources add --group gitlab --name gitlab --vmid 105
```
