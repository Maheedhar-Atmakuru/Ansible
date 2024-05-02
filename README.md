# Ansible

1) Ansible is opensource
2) This is 100% agentless
3) This works bothon push and pull mechanism

### What is the prerequisite for Ansible to work?

4) The only that you need to make sure is that your ANSIBLE NODE should be able to SSh to the nodes that needs your configuration


### Ansible can be operated in 2ways :

    1) Manual way   (No Code Approach and it's 100% not recommended)
    2) Automated way(YAML : Playbooks: 100% )

### Install Ansible :


to ansible, we need to supply the list of servers that needs to be managed by Ansible and we call that file as INVENTORY file.

    inventory file
    Destination Server Username & Password


### Ansible is all about modules

ansible all -i inv -e ansible_user=centos -e ansible_password=DevOps321 -m shell -a uptime

If you go by this approach, you can run or execute only one command/action at a time

Automated way of dealing with Ansible is with playbooks. and playbooks can be writen by using YAML (Presentation language)

Pre-requisites to learn YAML
    1) Dictionaries     (a key value pair)
    2) List             (a key with multiple values)
    3) Map              (a key with multiple key value pairs)

YAML is indendation specific , that means spaces matters a lot. Because Ansible is based on python

    A key with a value is referred as dictionary
        name: ansible (Correct)
        name: ansible (In-Correct)

    A key with multiple values is referred as LISt

        course:
            - devops
            - cloud
            - kubernetes
    
YAML basics official link : https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html

## What is a playbook ?
        ``` Scripts in ansible are referred as playbooks```

A playbook is a list of plays!!!
A play is a list of tasks!!!
A task is nothing an action that you want ansible to perform

Ansible expects the playbook with extension either .yaml or .yml

no two tasks of playbook cannot have same name

### how to run a playbook ?

    ``` $ ansible-playbook -i inv -e ansible_user=centos -e ansble_password=DevOpss321 001-playbook.yaml ```

# Roles In Ansible 

    Roles let you automatically load related vars, files, tasks, handlers, and other Ansible artifacts based on a known file structure. After you group your content into roles, you can easily reuse them and share them with other users.

    The advantage of using ROLES is code re-usability and things will be dry.


    roles/
        common/               # this hierarchy represents a "role"
            tasks/            #
                main.yml      #  <-- tasks file can include smaller files if warranted
            handlers/         #
                main.yml      #  <-- handlers file
            templates/        #  <-- files for use with the template resource
                ntp.conf.j2   #  <------- templates end in .j2
            files/            #
                bar.txt       #  <-- files for use with the copy resource
                foo.sh        #  <-- script files for use with the script resource
            vars/             #
                main.yml      #  <-- variables associated with this role
            defaults/         #
                main.yml      #  <-- default lower priority variables for this role
            meta/             #
                main.yml      #  <-- role dependencies
