# Ansible

## 0. install
#### instll ansible
```
sudo apt-get update
sudo apt-get install software-properties-common

sudo apt-add-repository ppa:ansible/ansible

sudo apt-get update
sudo apt-get install ansible
```
#### add hosts for ansible
/etc/ansible/hosts
```
[pinpoint-server] # name for hosts in main playbook
localhost ansible_connection=local
```

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

### how to remove
```sh
# stop&disable service
sudo systemctl stop hbase
sudo systemctl stop pinpoint-web
sudo systemctl stop pinpoint-collector
sudo systemctl disable hbase
sudo systemctl disable pinpoint-web
sudo systemctl disable pinpoint-collector

# remove service 
sudo rm /etc/systemd/system/hbase.service
sudo rm /etc/systemd/system/pinpoint-web.service
sudo rm /etc/systemd/system/pinpoint-collector.service

# reload daemon
sudo systemctl daemon-reload
sudo systemctl reset-failed

# remove folders
sudo rum -rf {pinpoint_hbase_install_dir}
sudo rum -rf {pinpoint_data_dir}
sudo rum -rf {pinpoint_hbase_log_dir}

sudo rum -rf {pinpoint_collector_tomcat_home}
sudo rum -rf {pinpoint_collector_tomcat_log_dir}

sudo rum -rf {pinpoint_web_tomcat_home}
sudo rum -rf {pinpoint_web_tomcat_log_dir}

# remove users&groups (optional)
```
