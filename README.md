## Ansible Ploybooks to Install and Configure both a Cribl Leader and Worker node(s)

This is a work in progress. Included in this repo are two Ansible playbooks for creating a Cribl environment. Updates to this git repo will happen pretty regularly, so please check back often to pull those latest changes. If there is a bug or suggestions for adding more functionality to these playbooks, please submit a PR request or log an issue.


The latest updates to these playbooks should test for any conditions that could cause the playbook to error out before. If you still see any errors running either playbook, please submit a PR or issue.


The worker playbook expects a variable to be set that includes the connection string to the leader node. An example static inventory file is listed below that includes how that connection string should be formatted.

```
[leader]
  leader.criblenv.com
[worker]
  worker1.criblenv.com 
[worker:vars]
leader_connection="tcp://criblmaster@leader.criblenv.com:4200?group=default"
```

Note: If you are running these playbooks from a Mac and are getting an error message related to the process fork. Export the following variable in the shell before trying to run the playbook again.

```
export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES
``` 
