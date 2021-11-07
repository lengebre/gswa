# Ansible Test Environment

1. Create Docker Image
   ```bash
   cd Docker
   docker build . -t gwsa
   ```
2. Run docker command
   ```bash
   docker run -it --rm gswa /bin/bash  
   ```


## Useful Ansible Commands
`ansible-doc`
`ansible-doc -t connection -l`
`ansible` - ad hoc command is ment for running one off commands
   - does not keep any sort of record or script of what is occuring
   - helpful to use the -h command
   - There are various modules you can use


### Copy file from Central Location

```bash
ansible -m copy -a "src=.gitconfig dest=~/.gitconfig" localhost
```




ansible all -m ping  -i ./inventory/targets.ini

Ansible Playbooks is ansible's orchestration language

- Different actions performed by tasks are called modules
    - command
    - script
    - service
    - yum

- ansible-playbook **playbook name**

Ansible modules are categorized into groups
- system - actions to be performed at a system level (stopping/starting/restarting services)
- **commands**: - shell, scripts, 
- **files**: works with files
- **database**: help when working with databases
- **cloud**: various cloud providers
- **windows**: work with windows environment


**command**: 
- execute a command on a remote node
- free_form - takes a free form command to run

**script**:
- execute a script locally after transfering the script over
- automatically copy the script to the remote node

**service**
- used to maintain services on a system
- must pass in parameter as key value pair formated
- can be written in a dictionary or map format
- action is started because it will check if it is running

**Idepontency** - results are always right without unessary repeats
- you should be able to run the command again

**lineinfile** - search for a line in a file and replace it if it doesn't exist

### Variables

- Stores information that varies between hosts
- Variables can be define inside the playbook
    - vars
        - key value pairs of variables can be found here
- Variables can also be define in a variable files
- hardcoded value can be replace with {{}} -
    - this is known as Jinja2 templatin
- ansible will replace with the value in the variable
- you can create host variable files for better organization