# Ansible_AWS_EC2

1. Go to AWS Console -> IAM -> Access management - Users -> Create user -> Give name -> Attach Policies - AmazonEC2FullAccess -> Create user


2. In the AM -> Access management - Users -> Select the created user -> Security credentials -> Create access key -> Select Application running outside AWS -> Next -> Create access key -> Done 


3. In the Local System for VSCode install below

    Plugins - YAML by RedHat & Ansible by RedHat
    
    Install boto3 - `pip install boto3`
    
    Install AWS Collection - `ansible-galaxy collection install amazon.aws`
    
    Create a password for vault - `openssl rand -base64 2048 > vault.pass`
    
    Add your AWS credentials using the below vault command - `ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass`
    
    Store your access key and secret access key
  

4. Use the Code as per the Repo 


5. Create 3 Instances
```
ansible-playbook ec2_create.yml --vault-password-file /home/pavan/lab/vault.pass
```
![ANSIBLE-RUN](https://github.com/Pavan-1997/Ansible_AWS/assets/32020205/9bac4259-4dda-4618-8410-2ecccc6bc081)


6. Setup Passwordless Authentication
```
ssh-copy-id -f "-o IdentityFile /mnt/c/Users/pavan/Desktop/DevOps-SRE/Ansible_Project/pavan-ansible-keypair.ppk" ubuntu@13.201.115.134
```


7. Automate the shutdown of Ubuntu Instances only using Ansible Conditionals
```
ansible-playbook -i inventory.ini rc2_stop.yaml --vault-password-file /home/pavan/lab/vault.pass
```
