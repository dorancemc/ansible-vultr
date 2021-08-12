dorancemc.ansible-vultr
=========

Role to deploy servers in Vultr.com cloud provider   


Requirements
------------

You should to ensure the ngine_io.vultr collections are installed https://galaxy.ansible.com/ngine_io/vultr  


Role Variables
--------------

* api_key  
You need to create the api key from your vultr account, and update it in the vault.yml file on defaults/main path, variable `vultr_api_key`  

* ssh_keys definition  
The ssh keys should be defined in the `vultr_sshkeys` variable, each ssh_key have three parameters, two required, one optional
```yaml
vultr_sshkeys:
  - name: ssh_key_name #required
    ssh_key: ssh_key #required
    state: #optional: present (default) / absent (do delete it)
```

* servers definition
The servers should be defined in the `vultr_servers` variable, each server have  parameters, one required, others are optional defined by defaults values  

```yaml
vultr_servers:
  name: server_name #required, should be unique
  auto_backup_enabled: #optional, default: vultr_auto_backup_enabled
  force: # reboot on changes when is required, default: vultr_force
  hostname: #server hostname, default: server.name
  ipv6_enabled: # default vultr_ipv6_enabled
  notify_activate: #send notifications on creation, default: vultr_notify_activate
  os: #operative system, default vultr_osid
  plan: #virtualvps plan, default vultr_planid
  private_network_enabled: #enable local network interface, default vultr_private_network_enabled
  region: #region or datacenter to deploy, default: vultr_region
  state: #desired state, default: present, to delete a server modify to absent
  snapshot: #to recover a host from snapshot, put the snapshot id here
  ssh_keys: #put here the ssh_keys names to use in the server (as a list), should be exist as a name in vultr, default: vultr_sshkeysid
  tag: #
```

More details about variables required you could find in the defaults/main folder.  

Use the Vultr API to get the values for os, plan and region if you need update them.  

Currently the ngine_io/vultr collection is using the APIv1.0, this version is deprecated.  

Dependencies
------------

None  


Example Playbook
----------------

To run this role locally  

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - { role: dorancemc.ansible-vultr, tags: [ vultr ] }  
```  


License
-------

Apache 2.0  


Author Information
------------------

Dorance Martinez dorancemc@gmail.com
