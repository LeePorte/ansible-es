# Ansible ES 

This configures a VPC within AWS creates a loadbalancer and Elastic search within the public subnet cluster and adds the cluster members to the loadbalancer.

## INSTALLATION

- Install python [boto3](https://github.com/boto/boto3) and Ansible:

```
$ easy_install pip
$ pip install boto3
$ pip install ansible
```

- Create ~/.boto with the following contents

```
[Credentials]
aws_access_key_id = <your_aws_access_key>
aws_secret_access_key = <your_aws_secret_key>

[default]
region=eu-west-1
```

- Clone the repository:

```
$ cd somewhere
$ git clone https://github.com/LeePorte/ansible-es.git && cd ansible-es
```

## RUNNING

To run launch the core infrastructure, use the following command:
```
$ ansible-playbook -i hosts launch.yml
```
This will create the vpc and lauch the ElasticSearch hosts.

To provision and add them to the loadbalncer run the following command:
```
$ ansible-playbook -i ec2.py -u ubuntu playbook.yml
```
By seperating the two it enables safe configuration changes to be made without adding new instances unintentionally to to VPC.

## IMPROVEMENTS

Add in direct connect or VPN connections (requires known variables).
Move hosts into private subnet and use a bastion to connect.




