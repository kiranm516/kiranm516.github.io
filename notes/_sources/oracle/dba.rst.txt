===
DBA
===

EZConnect Syntax
================

.. code:: sql
  
   CONN[ECT] username/password@[//]host[:port][/service_name]

Where:

- //            - Optional. Specify // for URL
- host          - Required. Specify the host name or IP address of the database server computer. The host name is domain-qualified if the local operating system configuration specifies a domain.
- port          - Optional. Specify the listening port. The default is 1521.
- service_name  - Optional. Specify the service name of the database. The default is the host of the database server computer. Note that this might not be the same value that you entered in the connect string for the host. For example, for the host emp, the service name might be emp.acme.com.

If the host does not match the database service name, then enter a valid service name value rather than accepting the default.

Notes
-----
When installing/re-installing oracle check if any home already exists. If any upgrade just use the old HOME or else new home will be created

Run host (windows) commands

host <host-command>

e.g., host cls


CREATE USER kiran IDENTIFIED BY passme

ALTER USER kiran IDENTIFIED BY passme

GRANT CONNECT TO kiran;

GRANT ALL PRIVILEGES TO kiran IDENTIFIED BY passme;