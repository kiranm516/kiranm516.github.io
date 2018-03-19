===
DBA
===

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