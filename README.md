# BPR Vagrant Machine

Vagrant development machine to mimic the Yahoo Small Business host and provide a consistent environment between development and production.

This machine involves both CentOS 6.10 and PHP 5.3.29.

Ensure you get the OS disk image from the [CentOS](#CentOS) portion of the [Requirements section](#Requirements). 

## Requirements

### CentOS

Download the [CentOS 6.10 x86-64 Minimal ISO](https://vault.centos.org/6.10/isos/x86_64/CentOS-6.10-x86_64-minimal.iso) and place it in the `images` directory.

This is the minimal installation disk image for the OS. The Vagrantfile references this for quicker provisioning.

### VirtualBox

Ensure you have the latest version of [VirtualBox](https://www.virtualbox.org/wiki/Downloads) installed.

## Scripts and Aliases

### Nix-based Systems

On a nix-based system, you can add the following aliases to your `.bashrc` file for ease of operation:

```
BPR_VAGRANT="/path/to/bpr-vagrant"
alias bpr-vagrant="cd ${BPR_VAGRANT}"
alias bpr-init="pushd ${BPR_VAGRANT} && ./add-vbox-guest-additions.sh && ./start-vms.sh && popd"
alias bpr-start="pushd ${BPR_VAGRANT} && ./start-vms.sh && popd"
alias bpr-stop="pushd ${BPR_VAGRANT} && ./stop-vms.sh && popd"
alias bpr-restart="bpr-stop && bpr-start"
```

Ensure you `chmod +x *.sh` the scripts for execution permissions.

The `bpr-init` alias should be executed for the first run of the machine to add the VirtualBox Guest Additions and then start the machine. Subsequent starts can simply use the `bpr-start` alias instead.

### Windows Systems

The `start-vms.bat` and `stop-vms.bat` scripts perform the same tasks as `start-vms.sh` and `stop-vms.sh`. They simply start and stop the machine, respectively.

Ensure you run `add-vbox-guest-additions.bat` prior to running `start-vms.bat` for the first time.
