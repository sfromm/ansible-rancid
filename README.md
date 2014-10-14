Role Name
=========

Role configures [RANCID](http://www.shrubbery.net/rancid/), the *Really
Awesome New Cisco config Differ*.

Requirements
------------

No external dependencies.

At this time, this role does not create the *cloginrc* file required by
RANCID.  It is left to the user to install this after the role has
completed its tasks.

Role Variables
--------------

The RANCID role has the following variables:

- **rancid_conf**: */etc/rancid/rancid.conf*  This is the path to where
  *rancid.conf* is installed.
- **rancid_home**: */home/rancid*  This is both the home directory for
  RANCID and the base directory where RANCID stores device
  configurations.
- **rancid_shell**: */bin/bash*  Shell for RANCID user.
- **rancid_logdir**: */var/log/rancid* Where RANCID stores its logs
- **rancid_password** and **rancid_encrypted_password**:  *rancid*  The
  password for the RANCID user.  You are strongly encouraged to set this
  to something different.
- **rancid_rcsys**: *svn*  Set to VCS system used by RANCID.
- **rancid_groups**: A list of groups used for RANCID runs.  This
  defaults to *routers*, but you are encouraged to override.
- **netmon**: A dictionary meant to be used among several roles that
  describes monitored devices.

Dependencies
------------

Requires the EPEL repository.  There are several roles that accomplish
this, including *[sfromm.epel](https://github.com/sfromm/ansible-epel)*.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: netmon
      roles:
         - { role: sfromm.rancid, rancid_encrypted_password: "{{my_rancid_encrypted_pass}}", rancid_password: "{{my_rancid_pass}}" }

      tasks:
         - name: deploy cloginrc
           copy: src=cloginrc dest={{rancid_home}}/.cloginrc mode=0600


License
-------

GPLv2

Author Information
------------------

See https://github.com/sfromm
