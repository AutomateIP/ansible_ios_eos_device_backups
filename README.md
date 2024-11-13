NOT A README, just examples on how to run this

ansible-playbook create_temp_dir.yaml --extra-vars 'git_repo_url=git@gitlab.com:itential/sales-engineer/sedemos/iag_device_backups.git git_repo_branch=master' -vvv

ansible-playbook -i ../../inventory/hosts.yml backup_configs_device_array.yaml --extra-vars 'target_devices=["IOS-WS-1","IOS-WS-2","IOS-WS-3","IOS-WS-4"] tempdir=/tmp/ansible.fd8xwjp1' -vvv

ansible-playbook delete_temp_dir.yaml --extra-vars='tempdir=/tmp/ansible.fd8xwjp1' -vvv

ansible-playbook -i inventory.yml backup_configs_local_groups.yaml --extra-vars 'target_group=ios git_repo_branch=master git_repo_url=git@gitlab.com:itential/sales-engineer/sedemos/iag_device_backups.git' -vv


IAG 5 Stuff

iagctl create repository device_backups --url https://github.com/AutomateIP/ansible_ios_eos_device_backups.git

iagctl create decorator backup_configs_local_group --schema @../ansible_ios_eos_device_backups/backup_configs_local_groups.decorator.json

iagctl create service ansible-playbook --repository device_backups --playbook backup_configs_local_groups.yaml --inventory inventory.yml --verbosity 6 --decorator backup_configs_local_group --description "Playbook that executes config backups to a git repo based on device group"