---
title: Cluster log
menuTitle: Log
weight: 2
---

![](/images/proxcli_cluster_log_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|output-format|format the output to one of table, json or yaml|string|
|max-items|max number of log lines we grab from nodes|integer|
|proxmox-nodes|comma separated list of nodes issuing the log lines|string|
|severities|filter logs by severities. this option is a coma separated list of severities labels (panic,alert,critical,error,warning,notice,info,debug)|string|

## Examples

- Show cluster log

```bash
proxcli cluster log
```
- Show errors searching in the last 1000 logs lines

```bash
proxcli cluster log --severities critical,error,warning --max-items 1000
```
