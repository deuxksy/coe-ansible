# Ansible

## 1. pinpoint
pinpoint setup guide on localhost  
> 다른 서버에 setup 하기 위해서는 /etc/ansible/hosts에 해당 서버를 정의 후
> setup-pinpoint.yml 파일의 hosts: 내용을 변경해야 함

### prerequisites
- unzip이 설치되어 있어야 함
- pinpoint 가이드에 따라 JDK6 ,JDK7, JDK8 가 반드시 필요

### configurations
- set configs for collector and web in roles/pinpoint-server/default/main.yml
- set configs for agent in roles/pinpoint-agent/default/main.yml


### how to run setup

```sh
ansible-playbook -v setup-pinpoint.yml
```

### start pinpoint services
- sudo systemctl start pinpoint-web
- sudo systemctl start pinpoint-collector
