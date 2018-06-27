# Ansible

## 1. pinpoint
pinpoint setup guide on localhost
> 다른 서버에 setup 하기 위해서는 /etc/ansible/hosts에 해당 서버를 정의 후 

- set configs for collector and web in roles/pinpoint-server/default/main.yml
- set configs for agent in roles/pinpoint-agent/default/main.yml


how to run setup
```sh
ansible-playbook -v setup-pinpoint.yml
```
