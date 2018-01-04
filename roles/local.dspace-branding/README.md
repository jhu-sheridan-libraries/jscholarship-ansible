Ansible Role: DSpace Branding
=========

Facilitates branding a DSpace instance.
Currently only tested on DSpace 5 with the Mirage2 theme applied to the XMLUI.

Requirements
------------

Intended to be used in an Ansible project that has itself installed and configured DSpace and applied the Mirage2 theme (or a compatible theme), or in conjunction with such a project.

Role Variables
--------------

TBD

Dependencies
------------

[dspace-5](https://github.com/dheles/dspace-5-ansible-role.git)

Example Playbook
----------------

    - hosts: app
      roles:
         - { role: local.dspace-branding }

License
-------

CC0

Author Information
------------------

Drew Heles
