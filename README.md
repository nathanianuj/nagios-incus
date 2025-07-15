#list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------
- name: Configure SNMPv3 on Incus containers and test Nagios SNMP checks
  hosts: all
  become: yes
  gather_facts: yes
  roles:
    - nagios-incus


Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).



Role Name
=========

**nagios-incus**

This Ansible role configures SNMPv3 on Incus containers or virtual machines and sets up a test communication between `vm1` and `vm2`. It's specifically designed for use with a Nagios monitoring setup.

Requirements
------------

- Ansible 2.9+
- Ubuntu/Debian-based systems (tested on Ubuntu 22.04)
- Passwordless SSH access to `vm1` and `vm2`
- `snmpd` and `net-snmp` tools installed
- The `snmpwalk` and `net-snmp-config` utilities must be present
- Target machines (`vm1` and `vm2`) must be reachable via private IPs

Role Variables
--------------

These variables can be customized in your inventory, playbook, or included in `defaults/main.yml` or `vars/main.yml`.

```yaml
snmp_user: authPrivUser        # SNMPv3 username
auth_pass: myAuthPass123       # Authentication password (SHA)
priv_pass: myPrivPass456       # Encryption password (AES)


Dependencies
------------

None. This role is self-contained and does not rely on other Galaxy roles.

Example Playbook
----------------
- name: Configure SNMPv3 on Incus containers and test Nagios SNMP checks
  hosts: all
  become: yes
  gather_facts: yes
  roles:
    - nagios-incus


Author Information
----------------
Anuj Nathani

Master's in ICT & Internet Engineering, Rome, Italy

DevOps | Cloud | Monitoring Enthusiast

GitHub: https://github.com/anujnathani


Troubleshooting
----------------
If SNMP service fails to start, check if the snmpd daemon is installed and configured correctly.

Ensure firewall (UFW) allows SNMP ports (usually 161/udp).

Verify SNMPv3 credentials match on client and server.

Use snmpwalk command manually to verify SNMP response.


How to install this role from GitHub
------------------------------------
ansible-galaxy install git+https://github.com/anujnathani/nagios-incus.git


Or clone directly

git clone https://github.com/anujnathani/nagios-incus.git
cd nagios-incus
ansible-playbook playbook.yml


Tested Platforms
----------------
Ubuntu 22.04 LTS

Debian 11

CentOS 8	
