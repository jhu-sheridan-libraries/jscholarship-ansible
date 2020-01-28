Ansible Role: Tomcat
=========

Installs and configures the Apache Tomcat webserver.

Requirements
------------

Java - the current versions of Tomcat (7.0.x or 8.5.x) requires Java Runtime Environment (JRE) version 1.6 or higher (1.7 for websockets).

Role Variables
--------------

    tomcat_minimum_java_version:  1.7
    tomcat_major_version:         8
    tomcat_minor_version:         5
    tomcat_patch_version:         23
    tomcat_version:               "{{ tomcat_major_version }}.{{ tomcat_minor_version }}.{{ tomcat_patch_version }}"
    tomcat_install_dir:           "/usr/local"
    tomcat_download_dir:          "{{ ansible_env.HOME}}"
    tomcat_dir:                   "apache-tomcat-{{ tomcat_version }}"
    tomcat_download_file:         "{{ tomcat_dir }}.tar.gz"
    tomcat_url:                   "https://archive.apache.org/dist/tomcat/tomcat-{{ tomcat_major_version }}/v{{ tomcat_version }}/bin/{{ tomcat_download_file }}"
    tomcat_checksum_algo:         "sha1"
    tomcat_checksum_url:          "{{ tomcat_url }}.{{ tomcat_checksum_algo }}"
    tomcat_user:                  "tomcat"
    catalina_home:                "{{ tomcat_install_dir }}/tomcat"
    # TODO: review
    java_home:                    "/usr/lib/jvm/jre"
    tomcat_reinstall:             false
    java_opts:                    "-Djava.awt.headless=true -Dfile.encoding=UTF-8"
    catalina_opts:                "-server
                                  -Xms256m
                                  -Xmx512m
                                  -XX:+UseParallelGC"
    tomcat_manager_access:        true
    tomcat_roles:
      - "manager-gui"
    tomcat_users:
      - username: "admin"
        password: "changeme"
        roles:    "manager-gui"


Dependencies
------------

Any role (or other method) that will provide Java

Example Playbook
----------------

- hosts: tomcat
  roles:
     - { role: java }
     - { role: tomcat }

License
-------

CC0

Author Information
------------------

Drew Heles
