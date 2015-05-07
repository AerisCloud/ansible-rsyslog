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
    role_name: my_role
```

You role must contain a template file named `rsyslog.j2` which will be copied on the server.

Variables
---------

If `logstash_forwarder` is set to the name of one of the machine in the inventory,
`rsyslog` will forward the logs to this machine.

