Ansible-Basic-Server-Setup
=========

This role performs a basic server setup:

* adds fancy `.bashrc` and `*.nanorc` files

* installs `atop`

* fixes `/etc/resolv.conf` for Google Cloud Platform VMs (there is a bug that you cannot get the internal DNS resolved on Ubuntu)
