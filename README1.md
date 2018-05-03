# Swarm Automated Deployment

The Swarm Deployment tool can be used to provision and configure multi-node Docker clusters in AWS environments. The tool is made up of two Ansible playbooks. The first playbook creates the ASG/LC configuration, deploys the configuration, provisions EC2 instances, and kickstarts the Docker swarm initalization script. The second playbook installs Docker CE and applies all base configuration settings. Each cluster that is launched using the tool, has a unique hosts (inventory) and manager_conf/worker_conf (token strings) config files. These config files are stored in Bitbcuket and are created automatically when the cluster is launched. 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

The following dependencies must be installed on the Ansible workstation that will be used to deploy swarm clusters. 

```
Workstation:
- Boto3
- AWS CLI
- Python 3
- Ansible 2.4 (devel)

AWS:
WIP
```

### Playbooks
```
aws-provision
```
Used to deploy EC2 instances in Autoscaling group across multiple AZs. EC2 instances are bootstrapped using cloud-init config template which creates and launches a bash start up script.

```
swarm-init
```
Docker swarm installation and initialization playbook. Creates a cluster based on parameters that are passed by aws-provision.

### Installation

Ensure all dependencies are met. Update playbook parameters. Navigate to /aws-provision and execute play:

```
ansible-playbook site.yml -e "lifecycle=qa cluster=02"
```

## Contributing

WIP

## Versioning

WIP

## Authors

* **Boris Quiroz** - *Initial work*
