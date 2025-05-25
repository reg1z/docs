# Ansible

> [!info]+ What is Ansible?
> **Ansible** is an open-source automation tool used for configuration management, application deployment, and task automation across multiple systems. It works by connecting to nodes (servers or devices) over SSH and executing tasks using **YAML-based playbooks** without requiring agents on the remote systems. Ansible is known for its simplicity, using a **declarative language** to describe desired states, and it’s especially popular for managing Linux environments.


> [!list]+ Potential Links
> - tryhackme room | On-Premises IaC: https://tryhackme.com/room/onpremisesiac


## Inventories
- Configuration files that provide ansible with host information / network locations. These are things like endpoint IPs / FQDNs.
- Can be created in `.ini` or `.yaml` format.
	- e.g. `inventory.ini` or `inventory.yaml`


`.ini` example
```ini
[myhosts]
192.0.2.50
192.0.2.51
192.0.2.52
```

`.yaml` example
```yaml
myhosts:
  hosts:
    my_host_01:
      ansible_host: 192.0.2.50
    my_host_02:
      ansible_host: 192.0.2.51
    my_host_03:
      ansible_host: 192.0.2.52
```


> [!quote]+ [Ansible Docs - Tips for building inventories](https://docs.ansible.com/ansible/latest/getting_started/get_started_inventory.html#tips-for-building-inventories)
> - Ensure that group names are meaningful and unique. Group names are also case sensitive.
> - Avoid spaces, hyphens, and preceding numbers (use `floor_19`, not `19th_floor`) in group names.
> - Group hosts in your inventory logically according to their **What**, **Where**, and **When**.
> 
> **What**
> Group hosts according to the topology, for example: db, web, leaf, spine.
> 
> **Where**
> Group hosts by geographic location, for example: datacenter, region, floor, building.
> 
> **When**
> Group hosts by stage, for example: development, test, staging, production.
> 



## ad-hoc commands