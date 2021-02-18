Role Name : Victoriamertics single node tsdb
=========

Deploy and configure single-node victoria-metrics

Requirements
------------

ansible 2.10

Role Variables
--------------

Name | Default Value | Description
---|---|---
`victoriametrics_version` |  "1.54.1" | current version
`victoriametrics_system_user` | "victoriametrics" | 
`victoriametrics_system_group` | "victoriametrics" |
`victoriametrics_install_dir` | "/usr/local/bin" |
`victoriametrics_repo_dir` | "/var/tmp/archive" | vm files
`victoriametrics_checksum` | "{{ victoriametrics_repo_dir }}/checksums.txt" | sha256sum file
`victoriametrics_storageDataPath` | "/var/lib/vm" | storage directory
`victoriametrics_retentionPeriod` | "12" | 1 year retention

Read this [https://github.com/VictoriaMetrics/VictoriaMetrics#environment-variables](https://github.com/VictoriaMetrics/VictoriaMetrics#environment-variables) аnd set more vars, put it into `templates/victoriametrics.j2`

Copy vm files to `victoriametrics_repo_dir`:
```sh
cd /var/tmp/archive
https://github.com/VictoriaMetrics/VictoriaMetrics/releases/download/v1.54.1/victoria-metrics-amd64-v1.54.1.tar.gz
wget -o checksums.txt https://github.com/VictoriaMetrics/VictoriaMetrics/releases/download/v1.54.1/victoria-metrics-arm64-v1.54.1_checksums.txt
```

Example Playbook
----------------

```yaml
---
- hosts: vm
  gather_facts: true
  connection: ssh
  roles:
    - v98765_vm_single
```

License
-------

BSD
