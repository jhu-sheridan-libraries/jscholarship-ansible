Role Name
=========

Installs and configures Psi Probe, the manager and monitor for Apache Tomcat.

WIP Notice
----------

This role is a Work-In-Progress. It will improve when I have a project that justifies the additional effort, when I have time to burn on it, or someone contributes a pull-request. It is limited in the following ways:

* Only tested against a limited set of prereqs (see Reqiurements).
* Overwrites CATALINA_OPTS. This is a limitation of how systemd sets environment vars (or my understanding of it). If anyone has an approach that will allow one to add to it instead, I'd love to hear it. In the meantime, the best approach is probably to set {{ catalina_opts }} in the ansible project that contains the tomcat and psi-probe roles.

Requirements
------------

* Apache Tomcat >= 6
* Java >= 7

Note, Psi Probe has this much latitude in the prerequisite versions it can support.
This role, in its current state, has only been tested against my current requirements,
(Centos 7, Apache 8.5, OpenJDK 1.8). These are reflected in the defaults.
Presumably it will work under other conditions, but the further one goes from
this starting point, the more likely it is that further effort will be required.


Role Variables
--------------

TBD

Dependencies
------------

I am using the following roles, which are hosted alongside this one on GitHub
(not yet on Ansible Galaxy):

* ansible-role-java
* ansible-role-tomcat

Example Playbook
----------------

    - hosts: app-server
      become: true

      roles:
      - { role: java }
      - { role: tomcat }
      - { role: psi-probe }

License
-------

CC0

Author Information
------------------

Drew Heles
