# ansible-playbook-aws

## Requirements
- ansible >= 2.3
- [AWS Account w/ IAM access](AWS.md)
- [Accept EULA for AWS Marketplace](https://aws.amazon.com/marketplace/pp?sku=csv6h7oyg29b7epjzg7qdr7no)


## Setup
```bash
# 2018-07
virtualenv ~/.venv
source ~/.venv/bin/activate

(.venv) sudo -H pip install --upgrade ansible
(.venv) sudo -H pip install --ignore-installed six	# fix bug with boto
(.venv) sudo -H pip install --ignore-installed python-dateutil	# fix bug with botocore
(.venv) sudo -H pip install --upgrade botocore boto boto3 passlib
(.venv) sudo -H pip install --upgrade --user awscli

# bashrc
#xport PYTHONPATH=$(python -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())")
#export PATH=~/Library/Python/2.7/bin:$PATH

# Other deps
# mysql_*
# sudo -H pip install --upgrade MySQL-python
```

### Set org_id
Keep it lowercase.
- `./run`
- `./playbook.yml`



### Setup secrets
1. Create `~/.vault_password` with the contents being a long random password.

2. Create `group_vars/all/secrets.yml`.

```yml
---

## AWS ##
# IAM Access key
aws_access_key: ''
aws_secret_key: ''

# RDS
db_password: ''
```

3. Encrypt secrets. `ansible-vault encrypt group_vars/all/secrets.yml --vault-password-file ~/.vault_password`

## Run
`./run`

## AWS VPC
- [x] Setup localhost AWS profile
- [x] Scaffold VPC networking
- [x] Setup AWS private ssh key
- [ ] Fix EIP / Ansible Bug

### TODO
- [ ] Add `delete on termination` to ec2 volumes
- [ ] Encrypted RDS not supported in ansible + boto - https://github.com/boto/boto/pull/3027

## Security
### AWS
- [ ] update access policy (ansible user) https://awspolicygen.s3.amazonaws.com/policygen.html

## TODO
- [ ] laravel server setup
- [ ] rds setup
- [ ] laravel app deploy
