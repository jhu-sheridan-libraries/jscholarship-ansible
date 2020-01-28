Ansible Role: PostgreSQL
=========

Installs and configures PostgreSQL database server

Requirements
------------

none

Role Variables
--------------
NOTE: defaults determined by environment. Centos7 has been tested the most, other environments may require adjustment.

    postgres_version_major:     0
    postgres_version_minor:     0
    postgres_version_patch:     0
    postgres_version:           "{{ postgres_version_major }}.{{ postgres_version_minor }}.{{ postgres_version_patch }}"
    postgres_debugging:         "{{ debugging | default(false) }}"
    postgres_data_directory:    "{{ postgres_default_data_directory }}"
    postgres_bindir:            "{{ postgres_default_bindir }}"
    postgres_setup:             "{{ postgres_default_setup }}"
    postgres_service:           "{{ postgres_default_service }}"
    postgres_legacy:            false # currently used to support Centos6
    postgres_admin_user:        "{{ db_admin_user   | default('postgres') }}"
    postgres_create_users:      "{{ db_create_users | default(false) }}"
    postgres_users:             "{{ db_users        | default(default_db_users) }}"
    default_db_users:
      - user:                   "example_user"
        pass:                   "don't_really_use_this"
        db:                     "you_can_omit_db"
        flags:                  "CREATEDB,NOSUPERUSER"

    postgres_default_encoding:  "UTF-8"

    postgres_create_databases:  "{{ db_create_databases | default(false) }}"
    postgres_databases:         "{{ db_databases        | default(default_databases) }}"
    default_databases:
      - name:                   "example_db"
        encoding:               "{{ postgres_default_encoding }}"
        owner:                  "example_user"

    # NOTE: if you template the hba config by setting a value for this variable,
    # you must either include all entries for all environments that will share the
    # database server in the template, or redundantly define them as postgres_hba_entries
    # in each environment's group vars (e.g. test and stage must include each other's
    # entries in their group vars). Otherwise, the template will overwrite any
    # existing entries, and the group's vars will only replace their own entries.
    # Therefore, by default, we are no longer templating a default config, and can
    # thereby allow each environment's group vars to only be responsible for its own entries
    postgres_hba_template:      ""
    postgres_hba_entries:
      - type:                   "local"
        database:               "all"
        user:                   "all"
        address:                ""
        method:                 "md5"

    postgres_listen_addresses:  "*"

    postgres_backup_args:
      - "format=custom"
      - "oids"
      - "no-owner"
      - "no-acl"

    postgres_extra_packages:  []
    postgres_extensions:      []

    postgres_upgrade_ok:      false
    postgres_upgrade_cleanup: false
    postgres_cleanup_scripts: []

Dependencies
------------

none

Example Playbook
----------------
NOTE: this role must be run with `become: true`

    - hosts: db
      roles:
      - { role: postgres, tags: ['postgres'], become: true }

License
-------

CC0

Author Information
------------------

Drew Heles
