+++
title = "Set"
date = 2023-09-26T10:42:09.000Z
draft = false
weight = 3
slug = "set"
+++

## Set virtual machines parameters



### Arguments

|argument|description|Allowed values|
|---|---|---|
|vmid|The (unique) ID of the VM.|integer|
|vmname|Virtual Machine exact name|string|
|cores|The number of cores per socket.|integer|
|sockets|The number of CPU sockets.|integer|
|cpulimit|Limit of CPU usage. NOTE: If the computer has 2 CPUs, it has total of '2' CPU time. Value '0' indicates no CPU limit.|integer|
|memory|Amount of RAM for the VM in MiB. This is the maximum available memory when you use the balloon device.|integer|
|ipconfig|cloud-init: Specify IP addresses and gateways for the corresponding interface. IP addresses use CIDR notation, gateways are optional but need an IP of the same type specified. The special string 'dhcp' can be used for IP addresses to use DHCP, in which case no explicit gateway should be provided. For IPv6 the special string 'auto' can be used to use stateless autoconfiguration. This requires cloud-init 19.4 or newer. If cloud-init is enabled and neither an IPv4 nor an IPv6 address is specified, it defaults to using dhcp on IPv4.|string|
|cipassword|cloud-init: Password to assign the user. Using this is generally not recommended. Use ssh keys instead. Also note that older cloud-init versions do not support hashed passwords.|string|
|ciuser|cloud-init: User name to change ssh keys and password for instead of the image's configured default user.|string|
|citype|Specifies the cloud-init configuration format. The default depends on the configured operating system type `ostype`. We use the `nocloud` format for Linux, and `configdrive2` for windows.|string|
|boot|Specify guest boot order. Use the 'order=' sub-property as usage with no key or 'legacy=' is deprecated.|string|
|sshkey|cloud-init: Setup public SSH key|string|

{{% notice style="info" %}}
Set parameters is a small subset of what is available in the proxmox API. I (maybe) will had more parameters later. 
{{% /notice %}}


### Exemples

{{% notice style="info" %}}
assert we have already cloned a cloud init enabled ubuntu virtual machine with the following command:

```bash
proxcli vms clone --vmid 100 --full-clone --block --name ubuntu-cloud-init-clone --vm-description exemple_clone --target pve1 --storage b4papp
```

the cloned vm is not started yet
{{% /notice %}}

- cloud init configuration of a vm cloned from a cloud init enabled ubuntu virtual machine

```bash 
proxcli vms set --vmid 110 --ciuser myuser --cipassword mypassword --ipconfig "ip=dhcp" --sshkey "$(cat ~/.ssh/id_rsa.pub)"
```

- adjust resources of a cloned virtual machine

```bash
proxcli vms set --vmid 110 --cores 4 --memory 4096
```

