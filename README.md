Install ansible on a node of your choice (This is for CentOS, Ubuntu branch is available):

```
yum install ansible sshpass
```

This branch deploys a number of RAX cloud servers specified in group_vars/site.yml. You can specify the number of replicas you want per shard, and the total number of shards you'd like. This determines how many total servers are created.

i.e. If I wanted 3 shards, with 1 replica each, this would create 6 total servers.

In order to do this, you'll need to ensure you have your RAX cloud credentials in ~/.raxpub, and example of that looks like this:

```
#Example .raxpub file:
[rackspace_cloud]
username = myclouduser
api_key = XXXXXXXXXXXXXX
```

As well, you'll want to ensure the server you're running the playbook from has a key uploaded to your available RAX public keys, as this will make your life a lot easier to run this playbook.

Once you have that configured simply run:

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

- Ubuntu support alongside CentOS (Ubuntu Branch available however under branches)
 

PRs welcome (and encouraged)!
