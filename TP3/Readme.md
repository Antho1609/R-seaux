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
[anthony@localhost ~]$ ip neigh show 10.3.1.12

10.3.1.12 dev enp0s3 lladdr 08:00:27:79:03:a8 STALE

```
et une commande pour afficher la MAC de marcel, depuis marcel

```
[anthony@localhost ~]$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:79:03:a8 brd ff:ff:ff:ff:ff:ff
    inet 10.3.1.12/24 brd 10.3.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe79:3a8/64 scope link
       valid_lft forever preferred_lft forever

```
2. Analyse de trames

utilisez la commande tcpdump pour réaliser une capture de trame

```
[anthony@localhost ~]$ sudo tcpdump
[sudo] password for anthony:
dropped privs to tcpdump
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on enp0s3, link-type EN10MB (Ethernet), snapshot length 262144 bytes
12:11:01.126363 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 694699714:694699774, ack 3278639915, win 501, length 60
12:11:01.126538 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 60:96, ack 1, win 501, length 36
12:11:01.126563 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 96:204, ack 1, win 501, length 108
12:11:01.126695 IP 10.3.1.1.51668 > localhost.localdomain.ssh: Flags [.], ack 96, win 8211, length 0
12:11:01.126714 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 204:300, ack 1, win 501, length 96
12:11:01.126851 IP 10.3.1.1.51668 > localhost.localdomain.ssh: Flags [.], ack 300, win 8211, length 0
12:11:01.126879 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 300:472, ack 1, win 501, length 172
12:11:01.167292 IP 10.3.1.1.51668 > localhost.localdomain.ssh: Flags [.], ack 472, win 8210, length 0
12:11:01.217444 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 472:644, ack 1, win 501, length 172
12:11:01.217544 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 644:828, ack 1, win 501, length 184
12:11:01.217670 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 828:864, ack 1, win 501, length 36
12:11:01.217730 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 864:1012, ack 1, win 501, length 148
12:11:01.217794 IP 10.3.1.1.51668 > localhost.localdomain.ssh: Flags [.], ack 828, win 8209, length 0
12:11:01.217795 IP 10.3.1.1.51668 > localhost.localdomain.ssh: Flags [.], ack 1012, win 8208, length 0
12:11:01.217859 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 1012:1048, ack 1, win 501, length 36
12:11:01.217913 IP localhost.localdomain.ssh > 10.3.1.1.51668: Flags [P.], seq 1048:1188, ack 1, win 501, length 140

```
videz vos tables ARP, sur les deux machines, puis effectuez un ping

```
[anthony@localhost ~]$ sudo ip neigh flush all
```
```
[anthony@localhost ~]$ ping 10.3.1.11
PING 10.3.1.11 (10.3.1.11) 56(84) bytes of data.
64 bytes from 10.3.1.11: icmp_seq=1 ttl=64 time=0.741 ms
64 bytes from 10.3.1.11: icmp_seq=2 ttl=64 time=0.590 ms
64 bytes from 10.3.1.11: icmp_seq=3 ttl=64 time=0.444 ms
64 bytes from 10.3.1.11: icmp_seq=4 ttl=64 time=0.483 ms
```
# II. Routage
1. Mise en place du routage

Ajouter les routes statiques nécessaires pour que john et marcel puissent se ping

```
[anthony@localhost ~]$ sudo ip route add 10.3.1.11 via 10.3.1.254 dev enp0s3
[sudo] password for anthony:
RTNETLINK answers: File exists

[anthony@localhost ~]$ sudo ip route add 10.3.1.12 via 10.3.1.254 dev enp0s3
[sudo] password for anthony:
RTNETLINK answers: File exists

```
verifions la route 
```
[anthony@localhost ~]$ ip route show
10.3.1.0/24 dev enp0s3 proto kernel scope link src 10.3.1.11 metric 100
10.3.1.11 via 10.3.1.254 dev enp0s3
10.3.1.12 via 10.3.1.254 dev enp0s3
```
3. Accès internet 

```
[anthony@localhost ~]$ ping 8.8.8.8

Envoi d’une requête 'Ping'  8.8.8.8 avec 32 octets de données :
Réponse de 8.8.8.8 : octets=32 temps=19 ms TTL=112
Réponse de 8.8.8.8 : octets=32 temps=19 ms TTL=112
```

Donnez un accès à vos machines - config client 

```
[anthony@localhost ~]$ ping 8.8.8.8

PING 8.8.8.8 (8.8.8.8) 56(64) bytes of data.
64 bytes from 8.8.8.8: impc_seq1 ttl=114 time=164ms
64 bytes from 8.8.8.8: impc_seq2 ttl=114 time=18.5ms
64 bytes from 8.8.8.8: impc_seq3 ttl=114 time=24.7ms

```