Install ansible on a node of your choice (This is the *UBUNTU* branch):

```
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible sshpass
```

Edit the hosts.yml file, and ensure your key exists across all nodes (coming soon, this code will add it all for you), then simply run:

```
ansible-playbook -i hosts.yml site.yml
```

And voila!

```
127.0.0.1:6379> CLUSTER NODES
08f2a5b901af30317006c1c46c3141f01665f83f 10.209.69.221:6379 master - 0 1426120440033 6 connected 5461-10922
b64ffb6cdc58c66166df318ebac8dda5e42eb81f 10.209.70.204:6379 master - 0 1426120439432 4 connected 10923-16383
5eb97e5791230d9965e9f29709fe01d5bd2fc183 10.209.70.200:6379 slave 0d348cd90d6b38808795ee299cd0dba4153ab92c 0 1426120439232 5 connected
0b0ef36438ec56e553f1352c71589c2820c1b505 10.209.70.104:6379 myself,slave 08f2a5b901af30317006c1c46c3141f01665f83f 0 0 1 connected
e700ec4b18f65f88760dc03a3242c63dfcbeddbe 10.209.70.123:6379 slave b64ffb6cdc58c66166df318ebac8dda5e42eb81f 0 1426120440434 4 connected
0d348cd90d6b38808795ee299cd0dba4153ab92c 10.209.69.136:6379 master - 0 1426120438932 5 connected 0-5460
```

Plans:

- Add variables to specify:
  - Number of replicas
  - Number of shards
  - This will allow you to spin up a dynamic cluster without having to go in and tune specific files
- Automated node creation for RAX cloud server (Maybe AWS)
- Automated SSH keys
- Ubuntu support alongside CentOS (This branch is the start)
 

PRs welcome (and encouraged)!
