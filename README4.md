# CloudFormation templates for OxC AWS environments

This repository containes CloudFormation templates for creation and managerment of resorces (stacks) within AWS OxC environments. 
The StackMaster CLI tool can be used to streamline and consolidate stacks deployment. 

## Getting Started

Install the pre-reqs listed below and ensure StackMaster is running on the latest build. More info on StackMaster can be found here [StackMaster](https://github.com/envato/stack_master).

### Prerequisites

The following dependencies must be installed on the workstation that will be used to manage CloudFormation stacks. 

```
Workstation:
- Boto3
- AWS CLI
- Python 3
- Ruby 2.5.1

AWS:
- API user account for each environment being managed - Automation policy should be attached to user account
- SSH keypair used to pull/push from Bitbucket repos
```

### Directory Structure
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

### Installation

Ensure all prerequisites are met. Update playbook parameters. Navigate to `/aws-provision` and execute play:

Clone repo to get the latest version of the templates `git clone ssh://git@bitbucket.gxicloud.com:7999/foun/foundry_automations.git`

Change to the directory of the environment you wish to manage and execute `stack_master apply`

## Contributing

WIP

## Versioning

WIP

## Authors

* **Boris Quiroz** - *Initial work*
