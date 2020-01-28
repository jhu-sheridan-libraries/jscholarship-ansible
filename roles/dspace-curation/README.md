Ansible Role: DSpace Curation
=========

Deploys and configures DSpace curation tasks

Requirements
------------

Relies upon its containing playbook to include a "restart tomcat" handler

Role Variables
--------------

    dspace_major_version:         5
    # user vars
    dspace_user:                  "{{ app_user      | default('dspace') }}"
    dspace_group:                 "{{ app_group     | default(dspace_user) }}"
    dspace_user_uid:              "{{ app_user_uid  | default(omit) }}"
    dspace_group_gid:             "{{ app_group_gid | default(omit) }}"

    # dspace deployment vars
    dspace_install_dir:           "/opt"
    dspace_install:               "{{ dspace_install_dir }}/dspace"
    dspace_user_home:             "/home/{{ dspace_user }}"
    dspace_lib:                   "{{ dspace_install }}/lib"
    dspace_xmlui_lib:             "{{ dspace_install }}/webapps/xmlui/WEB-INF/lib"

    # curation vars
    dspace_curation_cfg_template: "curate.cfg.lessthan6.j2"
    dspace_curation_source_dir:   "ctask"
    dspace_curation_source:       "{{ dspace_user_home }}/{{ dspace_curation_source_dir }}"
    dspace_curation_repo:         "https://github.com/dheles/ctask.git"
    dspace_curation_branch:       "fixity"
    dspace_curation_module:       "fixity"
    dspace_curation_tasks:
      - shortname:                "fixity"
        ui_taskname:              "Check Fixity"
        classname:                "org.dspace.ctask.fixity.CheckFixity"
        bundle:                   "fixity-1.0-SNAPSHOT.jar"
        state:                    "present"

Dependencies
------------

None

Example Playbook
----------------
---
  - name: deploy and configure curation tasks
    hosts: app

    tasks:
    - name: include tomcat role to get its "restart tomcat" handler
      include_role:
        name: tomcat
        tasks_from: dolittle

    - include_role:
        name: dspace-curation

License
-------

CC0

Author Information
------------------

Drew Heles
