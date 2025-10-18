Ansible role: Prometheus Exporter - Systemd
===========================================

Install and configure Systemd Exporter for Prometheus.

Requirements
------------

This role depends on the [base prometheus exporter role](https://github.com/wandansible/prometheus_exporter).

Role Variables
--------------

```
ENTRY POINT: *main* - Install and configure Systemd Exporter for Prometheus

Options (= indicates it is required):

- systemd_exporter_arch_map  Mapping of the possible values of
                              ansible_architecture to the exporter
                              package architectures
          default: null
          type: dict

- systemd_exporter_archive_urls  Override the list of exporter
                                  archive urls for different platforms
                                  and architectures
          default: null
          elements: str
          type: list

- systemd_exporter_bin_dir  Directory for the exporter executable
          default: null
          type: str

- systemd_exporter_binary  Filename for the exporter executable
          default: null
          type: str

- systemd_exporter_checksum_type  The exporter package checksum type
          default: null
          type: str

- systemd_exporter_checksum_url  Override the URL for the exporter
                                  checksum file
          default: null
          type: str

- systemd_exporter_checksums  Override exporter archive checksums
                               file contents
          default: null
          type: str

- systemd_exporter_clean_src_dir  Remove old downloaded archive files
                                   from exporter src directory
          default: true
          type: bool

- systemd_exporter_configure_caddy  If true, configure caddy to add a
                                     TLS endpoint for the exporter
          default: false
          type: bool

- systemd_exporter_description  Description for the exporter systemd
                                 service
          default: null
          type: str

- systemd_exporter_disabled_collectors  List of collectors to disable
          choices: [restart-count, ip-accounting, resolved]
          default: null
          elements: str
          type: list

- systemd_exporter_enabled_collectors  List of collectors to enable
          choices: [restart-count, ip-accounting, resolved]
          default: null
          elements: str
          type: list

- systemd_exporter_exclude_units  Regexp of systemd units to exclude
          default: null
          type: str

- systemd_exporter_extra_flags  Extra flags to run exporter with
          default: null
          type: dict

- systemd_exporter_file_sd_dir  Directory, on scrape servers, for the
                                 file service discovery target
          default: /etc/prometheus/file_sd/systemd_exporter
          type: str

- systemd_exporter_flags  List of flags to run exporter with, as
                           string or list
          default: null
          type: raw

- systemd_exporter_github_checksum_filename  Filename for the
                                              exporter package
                                              checksums file on github
          default: null
          type: str

- systemd_exporter_github_org  Name of organisation for exporter
                                github repository
          default: prometheus
          type: str

- systemd_exporter_github_repo  Name of exporter github repository
          default: null
          type: str

- systemd_exporter_github_token  Optional bearer token to use to
                                  authenticate with api.github.com
          default: ''
          type: str

- systemd_exporter_group  Name of the exporter unix group
          default: null
          type: str

- systemd_exporter_groups  Unix groups added to exporter unix user
          default: null
          elements: str
          type: list

- systemd_exporter_handler  Name of the exporter handler to notify
          default: null
          type: str

- systemd_exporter_include_units  Regexp of systemd units to include
          default: null
          type: str

- systemd_exporter_install  If true, install exporter
          default: true
          type: bool

- systemd_exporter_labels  Labels added to exporter metrics,
                            overrides prometheus_labels
          default: null
          type: dict

- systemd_exporter_listen_addresses  List of addresses and ports to
                                      listen on
          default: ['localhost:9558']
          elements: str
          type: list

- systemd_exporter_log_format  Output format of log messages
          choices: [logfmt, json]
          default: logfmt
          type: str

- systemd_exporter_log_level  Only log messages with the given
                               severity or above
          choices: [debug, info, warn, error]
          default: warn
          type: str

- systemd_exporter_manage_user  If true, add exporter unix user and
                                 group
          default: true
          type: bool

- systemd_exporter_port  Listen port
          default: 9558
          type: int

- systemd_exporter_private_connection  If true, establish a private,
                                        direct connection to systemd
                                        without dbus. Or empty string
                                        to not specify
          default: ''
          type: raw

- systemd_exporter_register  If true, register the exporter with the
                              scrape servers
          default: false
          type: bool

- systemd_exporter_scrape_servers  List of servers that scrape
                                    exporter metrics from the host,
                                    overrides
                                    prometheus_scrape_servers
          default: null
          elements: str
          type: list

- systemd_exporter_service  Name of the exporter systemd service
          default: null
          type: str

- systemd_exporter_service_unit_file  Contents of the systemd unit
                                       file for the exporter
          default: null
          type: str

- systemd_exporter_src_dir  Directory for the downloaded exporter src
                             archive
          default: null
          type: str

- systemd_exporter_strip_components  Strip NUMBER leading components
                                      from file names on extraction
          default: 1
          type: int

- systemd_exporter_target  Scrape target hostname and port
          default: null
          type: str

- systemd_exporter_telemetry_path  Path under which to expose metrics
          default: /metrics
          type: str

- systemd_exporter_user  Name of the exporter unix user
          default: null
          type: str

- systemd_exporter_user_instance  If true, connect to the user
                                   systemd instance. Or empty string
                                   to not specify
          default: ''
          type: raw

- systemd_exporter_version  Version to install (use "latest" for the
                             latest version)
          default: latest
          type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter,main,wandansible.prometheus_exporter
    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter.systemd,main,wandansible.prometheus_exporter.systemd
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.prometheus_exporter
      src: https://github.com/wandansible/prometheus_exporter
    - name: wandansible.prometheus_exporter.systemd
      src: https://github.com/wandansible/prometheus_exporter.systemd

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: all
      roles:
         - role: wandansible.prometheus_exporter.systemd
           become: true
