NOT A README, just examples on how to run this

ansible-playbook create_temp_dir.yaml --extra-vars 'git_repo_url=git@gitlab.com:itential/sales-engineer/sedemos/iag_device_backups.git git_repo_branch=master' -vvv

ansible-playbook -i ../../inventory/hosts.yml backup_configs_device_array.yaml --extra-vars 'target_devices=["IOS-WS-1","IOS-WS-2","IOS-WS-3","IOS-WS-4"] tempdir=/tmp/ansible.fd8xwjp1' -vvv

ansible-playbook delete_temp_dir.yaml --extra-vars='tempdir=/tmp/ansible.fd8xwjp1' -vvv