========================
Red Hat Enterprise Linux
========================

Prompt
======
$ means that you are logged in as normal user
# means that you are logged in as root user

CTRL + L    Clear Screen
CTRL + V    Logout/Exit

ssh <username>@<remote-server>

command <option>

option type
short e.g., ls -a
long e.g., ls --all


RHEL Docker Config
------------------
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux_atomic_host/7/html-single/getting_started_with_containers/index#getting_docker_in_rhel_7

https://access.redhat.com/solutions/253273

Red Hat Subscription Manager Firewall and Proxy
-----------------------------------------------

https://access.redhat.com/solutions/65300

Add user and set password

.. code:: shell
   
   [root@109c05bcda00 /]# useradd kiran
   [root@109c05bcda00 /]# passwd kiran
   Changing password for user kiran.
   New password:
   Changing password for user kiran.
   New password:
   Retype new password:

Switch user:
su - <username>

Install Packages
================

-y is yes for all

Network related tools
yum install -y ip-utils

yum install -y network-tools

For service command
yum install -y initscripts