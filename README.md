# ansible-jar-deployment-exmple
Deploying a .jar of an Eureka Registry Service with Ansible

## Prerequisites
### Ansible installation in the controller server (on Ubuntu)
```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

## Execute the playbook with the following command :
```
$ ansible-playbook -i inventory.yml --vault-id deploy@.ansible-vault-pw playbook.yml -vv
```

## Steps of creating this repo :

1. [Creatign the inventory file](inventory.yml)

2. Encrypting the remote host password :
> NB: {REPO_DIR} is the work directory
  * Create a vault passphrase
```
$ echo "your_passphrase_here" > {REPO_DIR}/.ansible-vault-pw
```
  * Generate an encrypted variable using the created passphrase
```
$ ansible-vault encrypt_string --vault-id deploy@{REPO_DIR}/.ansible-vault-pw 'your_remote_host_password_here' --name vault_remote_host_password
```
> NB: copy the result in the variables file

3. [Creating the variables file](group_vars/all.yml)
4. [Creating the playbook file](playbook.yml)
5. Execute the playbook with the following command :
```
$ ansible-playbook -i inventory.yml --vault-id deploy@.ansible-vault-pw playbook.yml -vv
```
