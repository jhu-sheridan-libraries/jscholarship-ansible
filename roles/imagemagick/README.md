Ansible Role: ImageMagick
=========

Installs the ImageMagick image manipulation tool

WIP Notice
----------

This role is a Work-In-Progress. It will improve when I have a project that justifies the additional effort, when I have time to burn on it, or someone contributes a pull-request. It is limited in the following ways:

* This could not be much more basic.
* Installs only from the OS package manager
* Only tested against a very limited set of OSes/versions
* As of this writing, recent security issues in ImageMagick appear to have been addressed. Therefore, this role does not currently provide a means of altering ImageMagick's policies

Requirements
------------

None; Installs ghostscript (does not rely on another role to do so).

Role Variables
--------------

None

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: imagemagick }

License
-------

CC0

Author Information
------------------

Drew Heles
