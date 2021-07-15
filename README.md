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
`victoriametrics_version` |  "1.63.0" | current version
`victoriametrics_system_user` | "victoriametrics" | 
`victoriametrics_system_group` | "victoriametrics" |
`victoriametrics_install_dir` | "/usr/local/bin" |
`victoriametrics_repo_dir` | "/var/tmp/archive" | vm files
`victoriametrics_storageDataPath` | "/var/lib/vm" | storage directory
`victoriametrics_retentionPeriod` | "12" | 1 year retention

Read this [https://docs.victoriametrics.com/#environment-variables](https://docs.victoriametrics.com/#environment-variables) аnd set more vars, put it into `templates/victoriametrics.j2`

Copy vm files to `victoriametrics_repo_dir`:
```sh
mkdir -p /var/tmp/archive
cd /var/tmp/archive
wget https://github.com/VictoriaMetrics/VictoriaMetrics/releases/download/v1.63.0/victoria-metrics-amd64-v1.63.0.tar.gz
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
