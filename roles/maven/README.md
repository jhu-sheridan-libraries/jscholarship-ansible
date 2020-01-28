Ansible Role: Maven
=========

Installs and configures the Apache Maven build tool.

Requirements
------------

JDK 1.7 or higher

Role Variables
--------------

TBD

Dependencies
------------

See requirements.

Example Playbook
----------------

    - hosts: app-server
      become: true

      roles:
      - { role: java, jdk: true }
      - { role: maven }

License
-------

CC0

Author Information
------------------

Drew Heles
