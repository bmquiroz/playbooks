# Swarm Automated Deployment

The Swarm Deployment tool can be used to provision and configure multi-node Docker clusters in AWS environments. The tool is made up of two Ansible playbooks. The first playbook creates the ASG/LC configuration, deploys the configuration, provisions EC2 instances, and kickstarts the Docker swarm initalization script. The second playbook installs Docker CE and applies all base configuration settings. Each cluster that is launched using the tool, has a unique hosts (inventory) and manager_conf/worker_conf (token strings) config files. These config files are stored in Bitbcuket and are created automatically when the cluster is launched. 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

The following dependencies must be installed on the Ansible workstation that will be used to deploy swarm clusters. 

```
aws-provision/
├── roles
│   └── aws-ag-deploy
│       ├── defaults
│       │   └── main.yml
│       ├── tasks
│       │   └── main.yml
│       └── templates
│           └── boot_strap.yml.j2
└── site.yml
```

### Prerequisites

The following dependencies must be installed on the Ansible workstation that will be used to deploy swarm clusters. 

```
key_pair: EC2 key pair
region: AWS region
security_groups: Security group
azs: Availibity Zone
subnets: Subnets
min_size: "2"
max_size: "2"
desired_size: "2"
lifecycle: "{{ lifecycle }}"
cluster: "{{ cluster }}"
docker_profile: Instance profile
placement: "swarm-{{ lifecycle }}-{{ cluster }}"
instance_type: 'm5.large'
ami_id: "ami-a371c1dc"
volume_size: Size of secondary volume
