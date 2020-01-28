Ansible Role: Apache
=========

Installs and configures the [Apache HTTP Server](https://httpd.apache.org/)

* Currently, only CentOS7 is supported

Requirements
------------

None

Role Variables
--------------

    apache_https:                   false
    apache_remove_welcome:          false
    apache_hostname:                "{{ hostname | default('myapp') }}"
    apache_domainname:              "{{ domainname | default('test.test') }}"
    apache_log_path:                "/var/log/{{ apache_service }}"
    apache_log_level:               "warn"
    apache_debugging:               "{{ debugging | default(false) }}"
    apache_trace_enabled:           false
    apache_config_file:             "/etc/{{ apache_service }}/conf.d/01_{{ apache_hostname }}.conf"
    apache_config_template:         "default.conf.j2"
    apache_http_redirect_marker:    "http redirect"
    apache_http_logging_marker:     "http logging"
    apache_https_logging_marker:    "https logging"
    apache_ssl_config_marker:       "ssl config"
    apache_header_mod_marker:       "header modification"
    apache_trace_marker:            "trace config"

    # SSL vars
    # NOTE: self-signed and provided cert booleans are mutually exclusive
    # ...either or both can be false, but both cannot be true
    ssl_self_sign_cert:             false
    ssl_provided_cert:              false
    ssl_certificate_file:           "{{ apache_fqdn | replace('.', '_') }}.crt"
    ssl_certificate_key_file:       "{{ apache_fqdn | replace('.', '_') }}.key"
    ssl_certificate_chain_file:     false
    ssl_certificate_path:           "/etc/pki/tls/certs"
    ssl_certificate_key_path:       "/etc/pki/tls/private"
    ssl_certificate_subj:           "/CN={{ apache_fqdn }}"
    ssl_support_legacy_clients:     true
    # NOTE: expect the cert and the key (and possibly the chain cert) content
    # to be passed in, if ssl_provided_cert is true
    ssl_certificate_content:        ""
    ssl_certificate_key_content:    ""
    ssl_certificate_chain_content:  ""

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: apache }

License
-------

CC0

Author Information
------------------

Drew Heles
Farooq Sadiq
