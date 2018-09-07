# prerequisite
- virtualbox
- vagrant

# usage
build infrastructure
```vagrant up```

## provisioning
ssh to provisioner
```vagrant ssh provisioner```

provision vocbench3
```ansible-playbook vocbench.yml -i ./hosts```

provision graphdb (need to obtain a copy from ontotext and put it in provisioning/roles/graphdb/files)
```ansible-playbook graphdb.yml -i ./hosts```

## configure
use vocbench UI to configure graphdb (optional)

# todo
- start vocbench and graphdb after provisioning
- better documentation
