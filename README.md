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

If `logstash_syslog_port` is set, rsyslog will send to the `logstash_forwarder` on that port.
The default port is `514`. This is useful if logstash is not running as root and cannot listen on ports 0-1024.

If you are not using a centralized log forwarding service and would like to have rsyslog on each server to
send logs directly to [Papertrail](https://papertrailapp.com/), set the following:
  - set `use_papertrail` to `true`. Default is false.
  - set `papertrail_host` to the [Papertrail log destination](https://papertrailapp.com/account/destinations). An
    account is required.
  - set `papertrail_port` to the [Papertrail port](https://papertrailapp.com/account/destinations) given.
  - `logstash_forwarder` defaults to an empty string, `''`. If it is defined, `rsyslog` will forward the logs to this machine.
  - set `papertrail_pem` to the full path of the papertrail-bundle.pem file. Default: `/etc/papertrail-bundle.pem`.
