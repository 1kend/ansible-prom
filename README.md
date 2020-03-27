# ansible-prom

This will allow you to keep all of your ansible and prometheus configs in version control.

1) Clone this repository
2) Install Prometheus to your repository root folder 
    a) you may need to redownload the repository prometheus/prometheus.yml file if the installation overwrites it
3) Install Ansible
    a) Delete /etc/ansible
    b) sudo ln -s <ansible-prom root directory>/ansible /etc/ansible
    
Test with the following command:
```
ansible-playbook -i hosts playbooks/test.yml
```
