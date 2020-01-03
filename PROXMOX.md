

## Backups

* [Backup and Restore](https://pve.proxmox.com/wiki/Backup_and_Restore)

## SSL


* [Latest Letsencrypt Instructions Proxmox](https://pve.proxmox.com/wiki/Certificate_Management)

Then Run new commands (will do with ansible on all hosts once we get it done manually):

```
# export EMAIL='timo@someemail.com'

# export DOMAIN='website.com'

# pvenode acme account register default $EMAIL

# pvenode acme account list

#  pvenode config set --acme domains=$DOMAIN


# pvenode acme cert order --force

```

## Create Cluster

* [PVECM Create Cluster](https://pve.proxmox.com/wiki/Cluster_Manager#pvecm_create_cluster)
