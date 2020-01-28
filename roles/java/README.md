Ansible Role - Java
=========

Installs Java, using [OpenJDK](https://openjdk.java.net) on CentOS/RHEL or Debian/Ubuntu - super bare-bones; only-what-I-need.

TODO
----

update alternatives, to handle version changes

Requirements
------------

none

Role Variables
--------------

Available variables (with current defaults)...

Uses colloquial versions (e.g. 8)
translated (e.g. java-1.8.0), as appropriate.
Valid values: 8, 7, and (probably) 6

    java_version: 8

By default, installs just the Java Runtime Environment (JRE). If you need the Java Development Kit (JDK) for developing with Java or to utilize a component that requires it, override by setting jdk to true

    jdk: false

Dependencies
------------

none

Example Playbook
----------------

Minimal:

    - hosts: servers
      roles:
         - { role: dheles.java }

With options (in this case, same as the current defaults):

    - hosts: servers
      roles:
         - { role: dheles.java, java_version: 8, jdk: false}

License
-------

[CC0](http://creativecommons.org/publicdomain/zero/1.0/)

Author Information
------------------

[Drew Heles](https://github.com/dheles), late 2016

Acknowledgement
---------------

My process of learning how to do this Ansible stuff was greatly accelerated by reading [Jeff Geerling's](http://www.jeffgeerling.com/) excellent book, [Ansible for DevOps](https://www.ansiblefordevops.com/).
