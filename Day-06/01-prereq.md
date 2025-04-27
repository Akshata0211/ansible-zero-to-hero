# Setup EC2 Collection and Authentication

## Install boto3

```
pip install boto3
```

## Install AWS Collection

```
ansible-galaxy collection install amazon.aws
```

## Setup Vault 

1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```

3. To run an Ansible playbook using the `inventory.ini` file and automatically decrypt any encrypted variables using the password stored in `vault.pass`.

```
 ansible-playbook -i inventory.ini 02-playbook.yaml --vault-password-file vault.pass
```



