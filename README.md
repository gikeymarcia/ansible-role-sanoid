gikeymarcia.sanoid
=========

Deploy [sanoid](https://github.com/jimsalterjrs/sanoid) for ZFS snapshot
management and Debian-based systems (Debian/Ubuntu/Proxmox)

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

```yaml
sanoid_version: "v2.2.0"
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

GPLv3

Author Information
------------------

Find me on GitHub @ https://github.com/gikeymarcia
