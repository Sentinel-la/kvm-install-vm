## kvm-install-vm

A bash wrapper around virt-install to build virtual machines on a local KVM
hypervisor.  Tested on Fedora 25.

Fork of https://github.com/giovtorres/kvm-install-vm
Thank you Giovanni!

### Usage

```
kvm-install-vm [OPTIONS] [-n vmname] [-r vmname]

OPTIONS
  -c          Number of vCPUs                             (default: 1)
  -m          Memory Size (MB)                            (default: 1024)
  -d          Disk Size (GB)                              (default: 10)
  -t          Linux Distribution                          (default: centos7)
  -l          Location of Images                          (default: /root/virt/images)
  -k          SSH Public Key                              (default: /root/.ssh/id_rsa.pub)
  -b          Primary Bridge                              (default: virbr0)
  -N          Additional Networks (comma separated list)  (default: '')
  -B          Additional Bridges (comma separated list)   (default: '')
  -h          Display help
  -i          Custom QCOW2 Image
  -n vmname   Name of VM to create
  -r vmname   Name of VM to delete

DISTRIBUTIONS
 - centos7
 - centos6
 - rhel7
 - ubuntu8

EXAMPLES

Create VM with default params:
  kvm-install-vm -n foo

Create VM with custom params:
  kvm-install-vm -c 2 -m 2048 -d 20 -n foo

Create VM in bridge virbr0, adding network mynet:
  kvm-install-vm -c 2 -m 2048 -d 20 -b virbr0 -N mynet -n foo

Remove (destroy and undefine) a VM:
  kvm-install-vm -r foo
```

### Notes

- This will download a cloud image from the CentOS site if the default QCOW2
  image doesn't exist.

### Use Cases

If you don't need to use Docker or Vagrant, don't want to make changes to a
production machine, and just want to spin up one or more VMs locally to test
things like:

- high availability
- clustering
- package installs
- preparing for exams
- checking for system defaults
- anything else you would do with a VM

...then this wrapper could be useful for you.
