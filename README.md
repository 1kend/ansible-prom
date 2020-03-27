# ansible-prom

This will allow you to keep all of your ansible and prometheus configs in version control.

* Clone this repository
* Install Prometheus to your repository root folder 
    - you may need to redownload the repository prometheus/prometheus.yml file if the installation overwrites it
* Install Ansible
    - Delete /etc/ansible
    - sudo ln -s \<ansible-prom root directory>/ansible /etc/ansible
    
Test with the following command:
```
ansible-playbook -i hosts playbooks/test.yml
```
