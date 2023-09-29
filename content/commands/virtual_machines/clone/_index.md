+++
title = "Clone"
date = 2023-09-26T10:42:09.000Z
draft = "2023-09-29T16:41:46.369Z"
weight = 2
slug = "clone"
+++

## Clone a virtual machine template

![](/images/proxcli_vms_clone_help.png)

### Arguments

|argument|description|Allowed values|
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

Exemples

### Clone a virtual machine template

- First we clone the exisiting template

```bash
proxcli vms clone --vmid 101 --name test --description test --full --block --target pve2 --storage b4papp 
```

### Clone a virtual machine template with cloud enabled template

{{% notice style="info" %}}
Make sure you already have a cloud init enabled template on your proxmox nodes. You can find in the next section an example of creating an ubuntu server cloud init enabled image. 
{{% /notice %}}

### How to create a cloud init enabled ubuntu template

#### Customize the cloudimg with embeded qemu-guest-agent

{{% notice style="tip" %}}
you will need **virt-customize** tool in order to install qemu-guest-agent
you also need an ubuntu cloud-init enabled image. You can find one [here](https://cloud-images.ubuntu.com/lunar/current/lunar-server-cloudimg-amd64.img)
{{% /notice %}}

```bash
virt-customize -a lunar-server-cloudimg-amd64.img --install qemu-guest-agent 
virt-customize -a lunar-server-cloudimg-amd64.img --run-command "echo -n > /etc/machine-id"
```

#### Create a cloud init template on selected proxmox nodes

```bash
qm create $(pvesh get )  --memory {{terraform.qemu_cloud_init_template.memory}} --name ubuntu-cloud --net0 {{terraform.qemu_cloud_init_template.net}}
qm set {{next_vmid.stdout}} --agent enabled=1
qm importdisk {{next_vmid.stdout}} {{terraform.qemu_cloud_init_template.isopath}}/{{terraform.qemu_cloud_init_template.imagename}} {{terraform.qemu_cloud_init_template.storage}}
qm set {{next_vmid.stdout}} --scsihw {{terraform.qemu_cloud_init_template.scsihw}} --{{terraform.qemu_cloud_init_template.devname}}0 {{terraform.qemu_cloud_init_template.storage}}:{{next_vmid.stdout}}/vm-{{next_vmid.stdout}}-disk-0.raw
qm set {{next_vmid.stdout}} --ide2 {{terraform.qemu_cloud_init_template.storage}}:cloudinit
qm set {{next_vmid.stdout}} --boot c --bootdisk {{terraform.qemu_cloud_init_template.devname}}0
qm resize {{next_vmid.stdout}} virtio0 {{terraform.qemu_cloud_init_template.disk_size}}    
qm set {{next_vmid.stdout}} --serial0 socket --vga serial0  
qm template {{next_vmid.stdout}}
```