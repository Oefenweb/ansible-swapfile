## swapfile

[![Build Status](https://travis-ci.org/Oefenweb/ansible-swapfile.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-swapfile) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-swapfile-blue.svg)](https://galaxy.ansible.com/list#/roles/1350)

Ansible role to manage a swap file in Debian-like systems.

#### Requirements

* `fallocate`

## Variables

* `swapfile_size` [default: `1G`]: the size of the swap file to create in the format that `fallocate` expects:

  The length and offset arguments may be followed by binary (2^N) suffixes KiB, MiB, GiB, TiB, PiB and EiB (the "iB" is optional, e.g. "K" has the same meaning as "KiB") or decimal (10^N) suffixes KB, MB, GB, PB and EB.

### Optional

The following variables are set to `False` by default and will not have any effect on your hosts. Setting them to any value other than `False` will update your hosts' `sysctl.conf` file.

* `swapfile_swappiness` [default: `False`]: the swappiness percentage (`vm.swappiness`) -- the lower it is, the less your system swaps memory pages

* `swapfile_vfs_cache_pressure` [default: `False`]: "this percentage value controls the tendency of the kernel to reclaim the memory which is used for caching of directory and inode objects."

## Dependencies

None

#### Example

```yaml
- hosts: all
  roles:
    - { role: tersmitten.swapfile }
```

or:

```yaml
- hosts: all
  roles:
    - { role: tersmitten.swapfile, swapfile_size: 1GB, swapfile_swappiness: 10 }
```

You can also set the variables described above in `group_vars` or `host_vars` (see `defaults/main.yml`).

#### License

MIT

#### Author Information

Mischa ter Smitten (based on work of kamaln7)

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-swapfile/issues)!
