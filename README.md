Ansible Role: InfluxDB
======================

[![License: MPL 2.0](https://img.shields.io/badge/License-MPL%202.0-brightgreen.svg)](https://opensource.org/licenses/MPL-2.0)

Ansible role to deploy InfluxDB server on CentOS/RHEL systems


Requirements
------------

No special requirements.
Note this role requires root access; either run it in a playbook with a global `become: yes` or invoke the role in your playbook:

```yaml
- hosts: servers
  roles:
    - role: jwflory.influxdb
      become: yes
```


Role Variables
--------------

```yaml
db_fqdn: example.com
http:
  enabled: "true"
  bind_address: ":8086"
  auth_enabled: "true"
  https_enabled: "true"
  https_certificate: "/usr/lib/influxdb/tls/{{ db_fqdn }}/fullchain.pem"
  https_private_key: "/usr/lib/influxdb/tls/{{ db_fqdn }}/privkey.pem"
```

* **`db_fqdn`**: Hostname/FQDN of InfluxDB server
* **`http.enabled`**: Whether to enable HTTP gateway to InfluxDB server
  (default: `true`)
* **`http.bind_address`**: Specify bind address for host
  (default `:8086`, runs on `0.0.0.0`)
* **`http.auth_enabled`**: Is authentication required to connect to DB?
  You should have a good reason for turning this off if so.
  (default: `true`)
* **`http.https_certificate`**: Path to HTTPS certificate
* **`http.https_private_key`**: Path to HTTPS private key


Dependencies
------------

None.


Example Playbook
----------------

```yaml
- hosts: influx_server
  roles:
     - role: jwflory.influxdb
```


License
-------

[Mozilla Public License 2.0](https://www.mozilla.org/en-US/MPL/ "Mozilla Public License – Mozilla")

Author(s) accept changes made in `vars/` directory to be omitted in published derivative work.
Modifications to other aspects of the Ansible Role, that others could also benefit from, are expected to be open.


Author Information
------------------

This role was created in 2019 by [Justin W. Flory](https://justinwflory.com/).
Find him on [GitHub](https://github.com/jwflory "Check out other things I'm working on!") and [LinkedIn](https://www.linkedin.com/in/justinwflory/ "See what I'm doing out in the world…").
