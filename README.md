Ansible Role Common
=========

This role configures common system and security settings on Ubuntu 20.04+.

Requirements
------------

Operating System Support: Ubuntu 20.04 or later

Role Variables
--------------

## /system
### Hostname - Auto
```
common_system_hostname: "{{ inventory_hostname }}"
```

### DNS - Required
```
# common_system_dns_server_1: "8.8.8.8"
```
### Hosts - Optional
```
# common_system_custom_hosts_entries: []
```
### User Management - Required
```
# common_system_sudo_user_name: "admin"
# common_system_sudo_user_password: "admin"
# common_system_sudo_user_sshpubkey: "admin"
```

## /security
### UFW - Admin IPs Required
```
common_security_ufw_reset: false
#common_security_ufw_default_outgoing_policy: allow
#common_security_ufw_default_incoming_policy: deny
#common_security_ufw_default_route_policy: deny
common_security_ufw_status: disabled

common_security_admin_ip_addresses:
   - 0.0.0.0/0
```
### IPv6 - Optional
```
common_security_disable_ipv6: 1
```

Dependencies
------------

No dependency.

Example Playbook
----------------

Install
```
ansible-galaxy install cihanyilmazer.ansible_role_common
```

    - hosts: servers
      roles:
         - cihanyilmazer.ansible_role_common/system
         - cihanyilmazer.ansible_role_common/security


Run with Custom Tags (at least one tag must be provided)
- common
- common-system
- common-security
- dns_servers
- hostname
- sudo_users
- ipv4_forwards
- hosts
- ipv6
- sshd
- ufw

```
ansible-playbook -i hosts playbook.yml --tags initial --limit servers
```

License
-------

MIT

Author Information
------------------

Cihan Yilmazer<br />
https://www.cihanyilmazer.com<br />
https://www.github.com/cihanyilmazer<br />
https://galaxy.ansible.com/cihanyilmazer<br />