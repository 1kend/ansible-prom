# ansible-prom

This will allow you to keep all of your ansible and prometheus configs in version control.

To use:
* Clone this repository
* Install ansible via your systems package manager
* cd into this repos root directory

To install the prometheus server run:
```
ansible-playbook playbooks/setup_prometheus_server.yml
```

To install the prometheus exporters run:
```
ansible-playbook playbooks/setup_prometheus_exporters.yml
```

# Inventory:
## Group Vars
### prometheus_servers
This is the group of nodes that should have prometheus installed on them. 
### prometheus_targets
This is the group of nodes that has exporters for prometheus to scrape.
### vms
the nodes in this group are VMs
### vm_creds
I cant remember how to do this correctly so im storing the login credentials for my vms in this file. You will have to create and fill it out manualy
```
    ---
    ansible_user: {{usernamehere}}
    ansible_password: {{passwordhere}}
```
## Host Vars
### 192.168.56.104
This server was used for the prometheus traning, it has several exporters not managed by ansible

# Roles:

## exporters
This role is for any node that exporters described in {{prometheus_exporters}}
It uses the name of the exporter to include the appropreate YML file for instalation
NOTE: This task failing to find a file causes an error but everything else still runs

## oper
Confgures the oper user and group
Also adds the provided public keys to the authorized keys file.

## prometheus
Installs and configures prometheus

### configuration generation
Each node has the same labels applied to all of its exporters
Exporters are grouped into jobs with the exporters name as the job name

#### To add a new exporter
* Add it to {{prometheus_exporter_types}} in this role 
* Add it to the {{prometheus_exporters}} of the nodes it will run on.
* If nesisary create a file for it in the exporters role to install it 

## systemconfig
Configures system elements
currently just firewall rules

