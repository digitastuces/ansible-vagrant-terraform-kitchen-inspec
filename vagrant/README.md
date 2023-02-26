## Commandes ansibles 

```sh
ansible -i inventaires/hosts.yaml all -m copy -a "dest=/home/vagrant/test.txt content='Conenu avec variable env {{ env }}\n'"
```