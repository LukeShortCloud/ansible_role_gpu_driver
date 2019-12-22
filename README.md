# GPU Driver (Ansible Role)

This role aims to make it easy for installing proprietary graphics card drivers on any Linux or Windows operating system. This is especially helpful for Linux where the steps are completely different to install the driver between the operating system variants. This role also focuses on utilizing system packages to maintain the updates of the Nvidia driver.

Currently supported platforms:

* AMD
    * Arch Linux
    * Fedora >= 28
* Nvidia
    * Arch Linux
    * Fedora >= 28
    * Windows

## Requirements

* Ansible >= 2.6

## Role Variables

* gpu_driver_vendor = Set to `amd` or `nvidia`.
* gpu_driver_nvidia_use_bumblebee = Set this to `True` if Nvidia will be installed on an [Nvidia Optimus laptop](https://www.geforce.com/hardware/technology/optimus/supported-gpus).
* gpu_driver_nvidia_bumblebee_user = A user that should be allowed to run programs using Bumblebee.

## Example Playbook

Create a Playbook to run the `ansible_role_gpu_driver` role on the local computer.

```
$ vim site.yml
---
- hosts: localhost
  roles:
    - ansible_role_gpu_driver
```

Run the Playbook to install the Nvidia driver.

```
$ sudo ansible-playbook --extra-vars "gpu_driver_nvidia_install=true" site.yml
```

Alternatively, a laptop with Nvidia Optimus support should install the Nvidia Bumblebee drivers.

```
$ sudo ansible-playbook --extra-vars "gpu_driver_nvidia_install=true gpu_driver_nvidia_use_bumblebee=true gpu_driver_nvidia_bumblebee_user=exampleuser" site.yml
```

## License

GPLv3
