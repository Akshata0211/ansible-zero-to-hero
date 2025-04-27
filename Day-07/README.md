# Ansible Realtime project

## Task 1

Create three(3) EC2 instances on AWS using Ansible loops
- 2 Instances with Ubuntu Distribution
- 1 Instance with Amazon Linux Distribution

Hint: Use `connection: local` on Ansible Control node.

## Task 2

Set up passwordless authentication between Ansible control node and newly created 
instances.

## Task 3

Automate the shutdown of Ubuntu Instances only using Ansible Conditionals

Hint: Use `when` condition on ansible `gather_facts`


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

To run the `ec2_create.yaml` playbook, use your `inventory.ini` file and decrypt any vault-encrypted variables using the `vault.pass`
```
 ansible-playbook -i inventory.ini ec2_create.yaml --vault-password-file vault.pass
```

This command copies your SSH public key to the EC2 instance using the `keypair.pem` file for authentication.
```
ssh-copy-id -f "-o Identityfile <path_to_keypair.pem>" ubuntu@<ec2_public-ip>
```
