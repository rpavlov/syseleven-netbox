# Syseleven Task #3

This ansible playbook will add a server to the netbox instance running on 195.192.130.34. Ansible connects to this vm via agent forwarding from the jumpbox at 195.192.128.96. You will need:

1. The ssh private key for the jumpbox placed in `~/.ssh/sys11` 
2. the ansible-vault password placed in `~/.ansible/.syseleven_vault_pass.txt`. 
3. Ansible and the netbox collection installed: `ansible-galaxy collection install netbox.netbox`

The netbox api token variable will be automatically decrypted and used. You can check if the container host is reachable with `ansible netbox -m ansible.builtin.ping`. 

After running the playbook, you can then verify on the netbox UI that the asset was sucessfully added by forwarding a port from the docker container running netbox to your control machine `ssh syseleven@195.192.128.96 -L 2222:195.192.130.34:443` and then accessing localhost:2222 with credentials admin/admin
