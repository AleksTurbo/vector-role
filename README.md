Role Name
=========

Vector service role for ansible

Requirements
------------

CentOS 7-8

Role Variables
--------------

vector_version: "0.25.1"
clickhouse_host: 192.168.153.118
clickhouse_user: logger
clickhouse_password: logger
vector_packages:
  - vector-server
nginx_user: nginx

Dependencies
------------

- python
- ansible


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Assert VECTOR role
      hosts: vector
      roles:
        - vector_role

License
-------

BSD

Author Information
------------------

AleksTurbo for NENOLOGY Labs - HW 8.4
