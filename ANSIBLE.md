### ANSIBLE

List hosts

This is if you run into an issue parsing your hosts file see here:

*[Unable to parse](https://stackoverflow.com/questions/53205687/ansible-unable-to-parse-etc-ansible-hosts-as-an-inventory-source)

```
$ ansible all --list-hosts
```


Run Ansible playbook against single host:

```
debops install-tool.yml -i "machine.com," -u timo

```

Run Ansible play book against localhost:

[Ansible ssh Error Local host connection](https://stackoverflow.com/questions/37184699/ansible-ssh-error-connection-in-localhost)


Add SSH Key to all hosts:

```
ansible -i ./container-inventory all -m copy -a 'src=./files/customer.pub dest=/home/support/.ssh/authorized_keys mode=0600 owner=support group=support' -e ansible_become=yes -e ansible_ssh_user=timo

```

Ping users in group:

(Ping users in web group in ansible inventory)
```
ansible web -m ping

```


### Install packages based on architecture:

This will install a package based on the architecture:

```
- name: install mysql-client
  apt:
    name: mysql-community-client
    state: latest
  become: yes
  when: ansible_architecture == "x86_64"

# Since mysql-client isn't available here just install mariadb-client instead
- name: install Mariadb-client
  apt:
    name: mariadb-client
    state: latest
  become: yes
  when: ansible_architecture == "aarch64"

```


# Ansible How to source ~/.bashrc 

This example does source ~/.sdkman/bin/sdkman-init.sh:

```
- name: Installing gradle with sdkman
  shell: "source /home/admin/.sdkman/bin/sdkman-init.sh && sdk install gradle {{gradle_version}}"
  args:
    executable: /bin/bash

```


## Specify branch in requirements.yml

Something like this:

```

- src: git@github.com:timogoosen/ansible-role.git
  name: base
  scm: git
  version: CPE-1475

```

Can then test installing it like this(Locally, not on remote host):

```

ansible-galaxy install -r requirements.yml

```