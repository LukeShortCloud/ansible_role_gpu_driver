# ansible-role-gpu-driver

This role aims to make it easy for installing proprietary graphics card drivers on any Linux or Windows operating system. This is especially helpful for Linux where the steps are completely different to install the driver between the operating system variants. This role also focuses on utilizing system packages to maintain the updates of the Nvidia driver.

Currently supported platforms:

* Arch Linux
* Fedora >= 28
* Windows

## Requirements

* Ansible >= 2.6

## Role Variables

* nvidia_install = Set to "true" to install the Nvidia graphics drivers.
* nvidia_use_bumblebee = Set this to "true" if Nvidia will be installed on an [Nvidia Optimus laptop](https://www.geforce.com/hardware/technology/optimus/supported-gpus). On some operating systems, such as Fedora, this is shipped as different binary packages.

## Dependencies

Fedora requires the [RPM Fusion (nonfree) repository](https://rpmfusion.org/).

```
$ sudo ansible-galaxy install -r requirements.yml
```

## Compatibility

Only Nvidia is supported right now. AMD is switching to a new AMDGPU-PRO driver for Linux that that is still young and is replacing the old Catalyst driver. Windows also does not have a Chocolatey package for any of the AMD drivers.

## Example Playbook

Create a Playbook to run the `ansible-role-gpu-driver` role on the local computer.

```
$ vim site.yml
---
- hosts: localhost
  roles:
   - ansible-role-gpu-driver
```

Run the Playbook to install the Nvidia driver.

```
$ sudo ansible-playbook --extra-vars "nvidia_install=true" site.yml
```

Alternatively, a laptop with Nvidia Optimus support should install the Nvidia Bumblebee drivers.

```
$ sudo ansible-playbook --extra-vars "nvidia_install=true nvidia_use_bumblebee=true" site.yml
```

## License

GPLv3
