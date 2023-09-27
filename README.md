## Ansible Ploybooks to Install and Configure both a Cribl Leader and Worker node(s)

This is a work in progress. Included in this repo are two Ansible playbooks for creating a Cribl environment. Updates to this git repo will happen pretty regularly, so please check back often to pull those latest changes. If there is a bug or suggestions for adding more functionality to these playbooks, please submit a PR request or log an issue.


The latest updates to these playbooks should test for any conditions that could cause the playbook to error out before. If you still see any errors running either playbook, please submit a PR or issue.


The worker playbook expects a few variables to be set for the worker to establish a connection with the leader node. These variables can be set on the command line or within the Ansible inventory file. Below are the variable names and expected values. Also, I've included an example static inventory file that includes the required variables.


leaderhost: IP or Hostname of the leader node
workergroup: The worker group to place the worker into
leadertls: Set to 'true' or 'false' for setting up TLS communcation between leader and worker (TLS must already be set up on the leader)
leaderport: Set to '4200' unless it has been changed in the leader config.
leaderauth: The auth token for the worker node


```
[leader]
  leader.criblenv.com
[worker]
  worker1.criblenv.com 
[worker:vars]
leaderhost="leader.criblenv.com"
workergroup="default"
leadertls="false"
leaderport="4200"
leaderauth="criblmaster"

```


Note: If you are running these playbooks from a Mac and are getting an error message related to the process fork. Export the following variable in the shell before trying to run the playbook again.

```
export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES
``` 
