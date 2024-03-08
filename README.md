## Ansible
Ansible is an open source, command-line IT automation tool that can be used for configuration management, application automation and infrastucture as code.

### Why ansible ?
1. Agentless: dont need to install any agents on target nodes/servers.
2. Simplicity: ansible configuration are written in yaml which is human readable.

### idempotence in Ansible.
Idempotence means that applying the same configuration multiple times produces the same result.

### Ansible Components
![animation](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ7wkvsc5sPrbEKLV8MuFKCHyMRJhX0txzsYIjlujnODBsjDOYtE-JpN2k&s=10)
1. Control Node: where ansible is installed
2. Managed Nodes: These are the servers or systems that are managed and configured by Ansible
3. Inventory: it stores the information of managed nodes like ip address
4. Playbooks: it define the task to be executed on the managed nodes
5. Roles: organize and package related tasks, variables, and handlers into reusable units
6. Tasks: represents a single unit of work in playbook
7. Handlers: its a tasks that are only executed if they are notified by other tasks
8. Modules: small programs that perform specific tasks on managed nodes like apt,yum,copy
9. Facts: collect data about target nodes
10. Variables: It helps you to assign a value to a variable and use it playbook
