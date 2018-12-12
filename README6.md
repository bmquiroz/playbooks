# Server Name Generator Tool

The Server Name Generator (SNG) Tool allows you to create 15 character host names based on the Aon standard naming convention (e.g. NL4DWDPCMS1234). 

For a complete list of values and functional mappings, please visit this page.

## Getting Started

These instructions will help you get a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

The following dependencies must be installed on the Ansible workstation that will be used to deploy swarm clusters. 

```
Ansible workstation:
- Boto3
- AWS CLI
- Python 3
- Ansible 2.4 (devel)

AWS:
- 3 subnets in different AZs with ~20 free IP addresses (per subnet)
- Docker swarm manager and worker Security Groups
- IAM API user account - Used by Ansible to create ASG and deploy instances
- IAM instance profile - Used by EC2 insances to create ENI and modify configuration
- Standard AMI that can be used to launch m5.xlarge instances
- SSH keypair used to pull/push from Bitbucket repos
```

### Playbooks
```
aws-provision
```
Used to deploy EC2 instances in auto scaling group across multiple AZs. EC2 instances are bootstrapped using cloud-init config template which creates and launches a bash start up script.

```
swarm-init
```
Docker swarm installation and initialization playbook. Creates a cluster based on parameters that are passed by aws-provision.

### Installation

Ensure all prerequisites are met. Update playbook parameters. Navigate to `/aws-provision` and execute play:

```
git clone ssh://git@bitbucket.gxicloud.com:7999/foun/foundry_automations.git
ansible-playbook site.yml -e "lifecycle=qa cluster=02"
```
Parameters passed to playbooks are `lifecycle` which represents the environment you are deploying to and `cluster` which represents the cluster.

## Contributing

WIP

## Versioning

WIP

## Authors

* **Boris Quiroz** - *Initial work*
