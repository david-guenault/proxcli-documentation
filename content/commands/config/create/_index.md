---
title: "Create proxcli config file"
weight: 1 
menuTitle: "Create"
---


![](/images/proxcli_config_create_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|hosts|coma separated list of proxmox nodes ip addresses / host names|string|
|user|administrator username (only pam at the moment)|string|
|password|password|string|

## Examples

- Create a proxmox config file

```bash
proxcli config create --hosts "pve1,pve2,pve3" --user root@pam --password rootpassword
```

