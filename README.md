This vagrant setup is used to set up foreman/katello.

# Installation
Install Fedora libvirt virtualization and vagrant
```
dnf install virt-manager libvirt libvirt-python python-virtinst vagrant-libvirt
```

Install useful vagrant plugins
```
vagrant plugin install vagrant-hostmanager vagrant-hostsupdater
```

Stand up the vms
```
vagrant up
```
