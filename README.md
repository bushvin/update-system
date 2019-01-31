# update-system
This git project gathers a bunch of roles, modules, playbooks to keep (Linux) systems up-to date.

## Authors
This ansible project was created by [William Leemans](https://github.com/bushvin)

## Roles
The following roles are available, and detail what goes in, and what comes out, if any.

### check-storage
This roles will check existing mountpoint for available free space and return a list of mountpoint which do not confirm.
#### Usage

    - role: check-storage
      role_check_storage_free:
      - mount: '/'
        free: 1g
      - mount: '/boot'
        free: 10%
      
**Arguments**

- **role_check_storage_free:** *mandatory*, a list defining the requirements per mountpoint. Required keys per element: mount (mountpoint), free (the required diskspace, in human readable format, or percentages)

**Returns**
- **role_check_storage_failed:** a list of dicts containing each mountpoint which does not meet the requirements of *role_check_storage_free*, derived from the *ansible_mounts* format.

