# repro-consul-acls
A repository for a reproduction of enabling Consul ACLs in a production environment with minimum downtime

# How to use
Run `vagrant up` in the main directory. You can then `vagrant ssh <box>` into a box. By default, the boxes are

- `consul01` to `consul05` - IP addresses 10.10.10.111 - 10.10.10.115
- `vault01` to `vault03` - IP addresses 10.10.10.101 - 10.10.10.105

Vault will be initialized and the tokens and unseal keys will be present in node `vault01` in `/root/recovery_key.txt`. Once that happens, you will need to use the unseal keys there and unseal each Vault node with `vault operator unseal`.

# How to modify
Inspect the `Vagrantfile` for more info. To change the amount of instances, modify the following lines in the file:

    consul_servers = 5
    vault_servers = 3

# Thanks
Much inspiration and even more code samples and snippets were elegantly borrowed from [@kikitux](https://github.com/kikitux)