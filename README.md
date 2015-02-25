rsyslog
=======

This roles configures [rsyslog](http://www.rsyslog.com/).
It manages the general configuration file and several service-specific configuration files.

Usage
-----

In your role's meta, add a dependency to this role using the syntax described below.

```yaml
# my_role/meta/main.yml
dependencies:
  - role: aerisloud.rsyslog
    service_name: my_role
```

Variables
---------

If `logstash_forwarder` is set to the name of one of the machine in the inventory,
`rsyslog` will forward the logs to this machine.

Supported services
------------------

* [bash](./templates/bash.conf.j2)
* [couchbase](./templates/couchbase.conf.j2)
* [haproxy](./templates/haproxy.conf.j2)
* [marathon](./templates/marathon.conf.j2)
* [mongodb](./templates/mongodb.conf.j2)
* [xtradb](./templates/xtradb.conf.j2)
* [zookeeper](./templates/zookeeper.conf.j2)
