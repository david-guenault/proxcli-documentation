+++
archetype = "chapter"
title = "Installation"
weight = 1
slug = "installation"
+++

## python3 virtual environment


Proxcli is written in python. We must first create a virtual environment with the following commands.

```bash
mkdir proxcli
cd proxcli
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip wheel
```


## Install proxcli in the virtual environment

{{% notice style="info" %}}
You can choose a proxcli version from one released on the github repo (here 0.1.0-alpha.3).
{{% /notice %}}


```bash
 pip install https://github.com/david-guenault/proxcli/archive/refs/tags/0.1.0-alpha.3.tar.gz
  ```

## Initialize the configuration

You know have to initialize the proxcli configuration file. You only need three parameters:
- **hosts**: it is a comma separated list of proxmox cluster nodes. You can use fqdn and/or ip addresses (default port is the api port)
- **user**: at the moment proxcli only support pam authentication. It is up to you to create a dedicated user on your nodes.
- **password**: Do i realy have to explain ? :-)

```bash
proxcli config create --hosts "proxmox1,proxmox2,proxmox3" --user "root@pam" --password "*********"
```

## Test your proxcli installation

 You can test the installation by listing the existing virtual machines on your cluster

 ```bash
 proxcli --help
 ```
![](/images/proxcli_help.png)
