
# Ansible-Role-node_exporter

This Ansible Role will install the Prometheus' node_exporter as a systemd service on your Linux host(s).

More info on [node_exporter](https://github.com/prometheus/node_exporter) within the official repository.

## Requirements

None

## Role variables

You can change these variables within the 'defaults/main.yml' file.

    node_exporter_version: 1.3.1

The version of node_exporter to install.

    node_exporter_arch: "amd64"
    node_exporter_download_url: "https://github.com/prometheus/node_exporter/releases/download/v{{ node_exporter_version }}/node_exporter-{{ node_exporter_version }}.linux-{{ node_exporter_arch }}.tar.gz"

Replace the `node_exporter_arch` with the processor archetype your going to run the node_exporter on.


    node_exporter_bin_path: "/usr/local/bin/node_exporter"

The location where you place the node_exporter binary.

    node_exporter_collectors: ""

node_exporter comes with extra options when installing, to make more metric collectors available. More information can be found in the original repository [here](https://github.com/prometheus/node_exporter#collectors).

    firewalld_present: false

If you run firewalld as your firewall then you can change this to `True` open up port `9100` through this.

## Example Playbook

    - hosts: all
      roles:
        - role: node_exporter