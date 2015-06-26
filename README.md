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

In addition to setting `logstash_forward`, if `private_ip` is set, `rsyslog` will forward 
to this IP address. Default is the `ansible_ssh_host` of the `logstash_forwarder`. This is
useful when the `logstash_forwarder` have multiple IPs, such as global and private IPs.
