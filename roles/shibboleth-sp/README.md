Ansible Role: Shibboleth Service Provider
========================================

Installs and configures a Shibboleth service provider from the Suse rpm repo

Requirements
------------
This role requires Apache to be installed, and installs from an rpm repo. The default apache configuration file is installed by the rpm.

Role Variables
--------------

No role variables at present

Dependencies
------------

NONE

Example Playbook
----------------

Simply use the role in a playbook

    - hosts: servers
      roles:
         - { role: shib }

License
-------

BSD

Author Information
------------------

Farooq Sadiq <fsadiq1@jhu.edu>
Drew Heles <dheles@jhu.edu>
Dazhi Jiao <djiao1@jhu.edu>
