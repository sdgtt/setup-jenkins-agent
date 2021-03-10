# setup-jenkins-agent
Automates configuration of a jenkins agent using ansible.

## Requirements
Make sure Ubuntu(currently supported platform) is up and running in the target agent \
and is connected to the same network with the control node.


## Usage

### Installation
#### Clone source code
```
git clone https://github.com/kimpaller/setup-jenkins-agent.git
```

### Configure
Set target by configuring the [agents] section inside `./inventory` file.\
Make sure to point to correct IP address of the target machine \
and connection through ssh using the specified fields is possible: \
`ansible_user`, `ansible_password`, `ansible_become_password`

Additionally, replace fields in group_vars/all according to setup.

Currently supported fields are:
+ agent_user
+ agent_password
+ agent_home
+ agent_user_file
+ agent_password_file
+ agent_name
+ agent_label
+ agent_executors
+ master_ip
+ master_user
+ master_pass
+ master_user_file
+ master_pass_file
+ jenkins_plugin_dir

### Execute script

`$ ansible-playbook -i inventory playbooks/setup_node.yaml \[-vvv\]`

After succesful jenkins and jenkins_swarm_client install, reboot target system.

Execute then the following playbook to install additional utilities:

`$ ansible-playbook -i inventory playbooks/configure_agent.yaml \[-vvv\]`




