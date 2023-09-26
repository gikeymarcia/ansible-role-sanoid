gikeymarcia.sanoid
=========

Deploy [sanoid](https://github.com/jimsalterjrs/sanoid) for ZFS snapshot
management and Debian-based systems (Debian/Ubuntu/Proxmox)

WORK IN PROGRESS; STILL TESTING; NOT READY FOR USE!!

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

```yaml
# defaults
sanoid_version: "v2.2.0"
sanoid_run_each_x_minutes: 15
```

First variable is the version to pull from github

Second variable determies how regulary the systemd timer should run per hour.
For example, a value of 4 means to run every 4th minute of each hour. This
timer runs sanoid to check if snapshots need to be taken/pruned. When using
high 'frequently' values you should adjust this value down so more snapshots
can be taken.

Each of your snapshot templates are defined in the `sanoid_templates`
varialble. Below are a few example values but the `defaults/main.yaml` has all
of the templtes Jim Salter defines in the sample sanoid.conf file on github.

If you want to extend these values I recommend copying the default version of
the variable and adding/editing your own templates as playbook variables.

```
sanoid_templates:
  - name: docker
    frequently: 3
    hourly: 48
    daily: 30
    monthly: 6
  - name: archive
    daily: 5
    weekly: 6
    monthly: 12
    yearly: 3
sanoid_backup_modules:
  - name: zpoolname/datasetORzvol
    template: archive
    daily: 3
```

The 'sanoid_backup_modules' define which datasets/zvols are going to be managed
by sanoid and which template to use as a snapshot policy. You can define
multiple template by comma separating them. For example,  'docker,archive'
would process those templates in order and apply the end result.

You can also override any given value by passing as a key value pair. Above the
'zpoolname/datasetORzvol' dataset will have 3 daily snapshots.

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
