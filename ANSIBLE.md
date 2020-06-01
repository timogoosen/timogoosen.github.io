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


### Debops

Can be used instead of ansible-playbook command.
