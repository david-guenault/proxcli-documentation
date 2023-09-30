+++
title = "Clone a virtual machine template"
date = 2023-09-26T10:42:09.000Z
weight = 2
slug = "clone"
keywords = "proxcli"
description = "Clone a virtual machine template"
menuTitle = "Clone"
+++


![](/images/proxcli_vms_clone_help.png)

## Options

|option|description|Allowed values|
|---|---|---|
|vmid|virtual machine template id to be cloned|integer|
|name|virtual machine clone name|regex string|
|vm-description|virtual machine clone description|string|
|full-clone|A full clone VM is a complete copy and is fully independant to the original VM or VM Template, but requires the same disk space as the original.|N/A|
|storage|storage name (local or remote) where the virtual machine disk image will be cloned|string|
|target|the target proxmox node name where the cloned virtual machine will be assigned|string|
|block|will the clone process will block until it end ? It make sense on slow remote storage (like on NAS), we wait for the clone task to finish before doing the next clone. This prevent IO saturation on storage|N/A|
|duplicate|how many duplicate do we need ? each duplicate will get his name suffixed by an index.|integer|

{{% notice style="info" %}}
vmid and name are mutualy exclusive
{{% /notice %}}


## Examples

- Clone a virtual machine template

```bash
proxcli vms clone --vmid 111 --name test --description test --full-clone --block --target pve2 --storage b4papp 
```

- Clone a virtual machine template with cloud enabled template

This is the same command as for a normal clone but you need additional steps to set user, password, ssh public key and network configuration. Try the following commands after cloning finishes. 

```bash
proxcli vms set --vmid 112 --ciuser myuser --cipassword mypassword --ipconfig "ip=dhcp" --sshkey "$(cat ~/.ssh/id_rsa.pub)"
proxcli vms set --vmid 112 --cores 4 --memory 4096
proxcli vms resize 
```

{{% notice style="info" %}}
Make sure you already have a cloud init enabled template on your proxmox nodes. You can find in the next section an example of creating an ubuntu server cloud init enabled image. 
{{% /notice %}}

{{% notice style="tip" title="Customize the cloudimg with embeded qemu-guest-agent"%}}
you will need **virt-customize** tool on your proxmox nodes in order to install qemu-guest-agent (install it with **apt install libguestfs-tools**)
you also need an ubuntu cloud-init enabled image. You can find one [here](https://cloud-images.ubuntu.com/lunar/current/lunar-server-cloudimg-amd64.img)

```bash
virt-customize -a lunar-server-cloudimg-amd64.img --install qemu-guest-agent 
virt-customize -a lunar-server-cloudimg-amd64.img --run-command "echo -n > /etc/machine-id"
```
{{% /notice %}}


{{% notice style="tip" title="Create a cloud init enabled template on selected proxmox nodes"%}}


Those commands will help you create an ubuntu cloud init enabled virtual machine template. Adjust the variables at the begining of the script so it match your needs. 

```bash
vmid=$(pvesh get /cluster/nextid)
isopath="/mnt/pve/isos/template/iso/lunar-server-cloudimg-amd64.img"
storage="b4papp"
scsihw="virtio-scsi-pci"
devname="virtio"
disksize="5G"
qm create $vmid  --memory 4096 --name lunar-server-cloudinit --net0 virtio,bridge=vmbr0
qm set $vmid --agent enabled=1
qm importdisk $vmid $isopath $storage
qm set $vmid --scsihw $scsihw --${devname}0 ${storage}:${vmid}/vm-${vmid}-disk-0.raw
qm set $vmid --ide2 ${storage}:cloudinit
qm set $vmid --boot c --bootdisk ${devname}0
qm resize $vmid ${devname}0 ${disksize}    
qm set ${vmid} --serial0 socket --vga serial0  
qm template ${vmid}
```
{{% /notice %}}

{{% notice style="note" %}}
On some shared storages (like Synology NFS share), you may encounter the following error with qm template command: 

```
/usr/bin/chattr: Operation not supported while reading flags on /mnt/pve/b4papp/images/111/base-111-disk-0.raw
```

You don't have to do anything, it is just a limitation in synology hardening. But it does not affect the creation of a template.
{{% /notice %}}

