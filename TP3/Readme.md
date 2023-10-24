# TP3

# I. ARP
1. Echange ARP

effectuer un ping d'une machine à l'autre

```
[anthony@localhost ~]$ ping 10.3.1.12
PING 10.3.1.12 (10.3.1.12) 56(84) bytes of data.
64 bytes from 10.3.1.12: icmp_seq=1 ttl=64 time=0.643 ms
64 bytes from 10.3.1.12: icmp_seq=2 ttl=64 time=0.390 ms
64 bytes from 10.3.1.12: icmp_seq=3 ttl=64 time=0.593 ms
^C
--- 10.3.1.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2070ms
rtt min/avg/max/mdev = 0.390/0.542/0.643/0.109 ms


-[anthony@localhost ~]$ ping 10.3.1.11
PING 10.3.1.11 (10.3.1.11) 56(84) bytes of data.
64 bytes from 10.3.1.11: icmp_seq=1 ttl=64 time=0.514 ms
64 bytes from 10.3.1.11: icmp_seq=2 ttl=64 time=0.768 ms
^C
--- 10.3.1.11 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1005ms
rtt min/avg/max/mdev = 0.514/0.641/0.768/0.127 ms

```
observer les tables ARP des deux machines

```
[anthony@localhost ~]$ ip neigh show
10.3.1.1 dev enp0s3 lladdr 0a:00:27:00:00:0e REACHABLE
10.3.1.12 dev enp0s3 lladdr 08:00:27:79:03:a8 STALE

[anthony@localhost ~]$ ip neigh show
10.3.1.11 dev enp0s3 lladdr 08:00:27:27:d9:21 STALE
10.3.1.1 dev enp0s3 lladdr 0a:00:27:00:00:0e REACHABLE
```
repérer l'adresse MAC de john dans la table ARP de marcel et vice-versa

```
10.3.1.11
ip addr
08:00:27:27:d9:21

10.3.1.12
ip addr
08:00:27:79:03:a8

```
prouvez que l'info est correcte (que l'adresse MAC que vous voyez dans la table est bien celle de la machine correspondante)

une commande pour voir la MAC de marcel dans la table ARP de john

```

```
et une commande pour afficher la MAC de marcel, depuis marcel

```


```