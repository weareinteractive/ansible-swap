# Ansible Swap Role

[![Build Status](https://img.shields.io/travis/weareinteractive/ansible-swap.svg)](https://travis-ci.org/weareinteractive/ansible-swap)
[![Galaxy](http://img.shields.io/badge/galaxy-franklinkim.swap-blue.svg)](https://galaxy.ansible.com/list#/roles/)
[![GitHub Tags](https://img.shields.io/github/tag/weareinteractive/ansible-swap.svg)](https://github.com/weareinteractive/ansible-swap)
[![GitHub Stars](https://img.shields.io/github/stars/weareinteractive/ansible-swap.svg)](https://github.com/weareinteractive/ansible-swap)

> `swap` is an [ansible](http://www.ansible.com) role which:
>
> * installs swap file
> * configures swap
>
> Used i.e. with [digital ocean droplets](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04).
>
> NOTE: Travis currently fails due to permission errors as you can't create swap files.

## Installation

Using `ansible-galaxy`:

```
$ ansible-galaxy install franklinkim.swap
```

Using `requirements.yml`:

```
- src: franklinkim.swap
```

Using `git`:

```
$ git clone https://github.com/weareinteractive/ansible-swap.git franklinkim.swap
```

## Dependencies

* Ansible >= 1.9

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```
# swap file path
swap_file_path: /swapfile
# swap file size in bytes
swap_file_size: "{{ 512 * 1024 * 1024 }}" # 512MB
# Configures how often your system swaps data out of RAM to the
# swap space. This is a value between 0 and 100 that represents a percentage
swap_swappiness: 10
# This setting configures how much the system will
# choose to cache inode and dentry information over other data
swap_vfs_scache_pressure: 50
```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

* `restart swap`

## Example playbook

```
- hosts: all
  roles:
    - franklinkim.swap
  vars:
    swap_file_size: "{{ 128 * 1024 * 1024 }}" # 128MB

- hosts: all
  roles:
    - franklinkim.swap
  vars:
    swap_file_size: "{{ 256 * 1024 * 1024 }}" # 256MB
```

## Testing

```
$ git clone https://github.com/weareinteractive/ansible-swap.git
$ cd ansible-swap
$ vagrant up
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) We Are Interactive under the MIT license.
