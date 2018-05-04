### Playbook structure

```
swarm-init/
├── README.md
├── roles
│   ├── base
│   │   ├── defaults
│   │   │   └── main.yml
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── daemon.json.j2
│   │       ├── docker-thinpool.profile.j2
│   │       └── journald.conf.j2
│   ├── manager
│   │   ├── defaults
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
│   ├── master
│   │   ├── defaults
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
│   └── worker
│       ├── defaults
│       │   └── main.yml
│       └── tasks
│           └── main.yml
└── site.yml

```

### Parameters

Update parameters in `/defaults/main.yml`

```
