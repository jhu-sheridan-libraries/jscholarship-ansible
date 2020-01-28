Ansible Role: DSpace 5
=========

Installs and configures DSpace 5.x


Requirements
------------

TBD


Role Variables
--------------

TBD


Dependencies
------------

Ansible roles (or other means) that provide the following:
  - Java JDK 7
    - e.g. https://github.com/dheles/java-ansible-role
  - Apache Maven 3.0.5+
    - e.g. https://github.com/dheles/maven-ansible-role
  - Apache Ant 1.8+
    - e.g. https://github.com/dheles/ant-ansible-role
  - Apache Tomcat 7+
    - e.g. https://github.com/dheles/tomcat-ansible-role
  - Apache HTTPD server
    - e.g. https://github.com/dheles/apache-ansible-role
  - postgres 9.0+
    - e.g. https://github.com/dheles/postgres-ansible-role  
    - Oracle is supported by DSpace, but not by this role


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: dspace-5 }


License
-------

CC0


Author Information
------------------

Drew Heles
