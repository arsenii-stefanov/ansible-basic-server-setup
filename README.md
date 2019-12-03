Ansible-Basic-Server-Setup
=========

This role performs a basic server setup:

* adds fancy `.bashrc` and `*.nanorc` files

* installs `atop`

* fixes `/etc/resolv.conf` for Google Cloud Platform VMs (there is a bug that you cannot get the internal DNS resolved on Ubuntu)

### Configurable options

> Default values are set in `defaults/main.yml`

* `server_basic_packages` - a list of packages to install on your server

```
# Example
server_basic_packages: [ some_package_1, some_package_2 ]
```

* `server_basic_config_templates` - a list of templates to copy to your server, the templates are located in the `./templates/` directory

```
# Example
server_basic_config_templates: [ 
  {
    src: "<name of your Jinja2 template in the templates directory (some_file_1.conf.j2)>",
    dest: "<absolute path to the destination file to copy your template to (/var/lib/some_dir_1/some_file_1.conf)>",
    owner: "<owner user (root)>",
    group: "<owner group (root)>",
    mode: "<file mode (0600, 0644)>"
  }
]
```

* `server_basic_config_files` - a list of files to copy to your server, the files are located in the `./files/` directory

server_basic_config_files: [
  {
    src: "<name of your file in the files directory (some_file_2.conf)>",
    dest: "<absolute path to the destination file to copy your file to (/var/lib/some_dir_2/some_file_2.conf)>",
    owner: "<owner user (root)>",
    group: "<owner group> (root)",
    mode: "<file mode (0600, 0644)>"
  }
]

* `server_basic_atop_config` - if you decide to install `atop` (it is present in `server_basic_packages` by default)

```
# Example
server_basic_atop_config:
  scan_interval: <integer value, seconds>
  log_keepdays: <integer value, days>
```

* `server_basic_fix_resolv_conf` - whether to fix the symlink `/etc/resolv.conf` symlink on GCE instances running Ubuntu or not (the default symlink points to `/run/systemd/resolve/stub-resolv.conf` which is unable to resolve internal DNS names); disabled by default

```
# Example
server_basic_fix_resolv_conf: false
```
