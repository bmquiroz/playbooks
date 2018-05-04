### Playbook structure

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

### Parameters

Update parameters in `/defaults/main.yml`

```
key_pair: EC2 key pair
region: AWS region
security_groups: Security group
azs: Availibity Zones
subnets: Subnets
manager_min_size: "5"
manager_max_size: "5"
manager_desired_size: "5"
worker_min_size: "20"
worker_max_size: "20"
worker_desired_size: "20"
lifecycle: "{{ lifecycle }}"
cluster: "{{ cluster }}"
docker_profile: Instance profile
placement: "swarm-{{ lifecycle }}-{{ cluster }}"
instance_type: 'm5.large'
ami_id: "ami-a371c1dc"
volume_size: Size of secondary volume
