# CloudFormation templates for OxC AWS environments

The Swarm Deployment tool can be used to provision and configure multi-node Docker clusters in AWS environments. The tool is made up of two Ansible playbooks. The first playbook creates the ASG/LC configuration, deploys the configuration, provisions EC2 instances, and kickstarts the Docker swarm initalization script. The second playbook installs Docker CE and applies all base configuration settings. Each cluster that is launched using the tool, has a unique hosts (inventory) and manager_conf/worker_conf (token strings) config files. These config files are stored in Bitbucket and are created automatically when the cluster is launched. 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

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
cf-templates/
├── perf
│   ├── parameters
│   │   ├── docker_swarm.yml
│   │   ├── oxc_perf_efs.yml
│   │   ├── oxc_perf_security_groups.yml
│   │   └── us-east-1
│   │       └── polar_sftp.yml
│   ├── stack_master.yml
│   └── templates
│       ├── docker-swarm.yml
│       ├── oxc-perf-efs.yml
│       ├── oxc-perf-security-groups.yml
│       └── oxc-perf-security-groups.yml.bak
├── prod
│   ├── parameters
│   │   ├── oxc_perf_devops_tools.yml
│   │   └── oxc_prod_security_groups.yml
│   ├── stack_master.yml
│   └── templates
│       ├── oxc-perf-devops-tools.yml
│       └── oxc-prod-security-groups.yml
├── qa
│   ├── parameters
│   │   ├── oxc_qa_security_groups.yml
│   │   └── polar_sftp.yml
│   ├── stack_master.yml
│   └── templates
│       ├── oxc-qa-security-groups.yml
│       └── polar-sftp.yml
├── shared
│   ├── parameters
│   │   ├── oxc_shared_devops_tools.yml
│   │   └── oxc_shared_security_groups.yml
│   ├── stack_master.yml
│   └── templates
│       ├── oxc-shared-devops-tools.yml
│       ├── oxc-shared-security-groups.yml
│       └── trident-devops-tools-iam.yml
└── stage
    ├── parameters
    │   └── oxc_stage_security_groups.yml
    └── templates
        └── oxc-stage-security-groups.yml
```

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
