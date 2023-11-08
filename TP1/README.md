# TP1

I. Exploration locale en solo

Affichez les infos des cartes réseau de votre PC

```

PS C:\Users\apapi> ipconfig

Configuration IP de Windows


Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :

Carte Ethernet Ethernet 2 :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::947a:f737:29b7:f4f6%17
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.56.1
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :

```

Affichez votre gateway

```
utilisez une commande pour connaître l'adresse IP de la passerelle (ou gateway) de votre carte WiFi

Carte réseau sans fil Wi-Fi :

PS C:\Users\apapi> ipconfig

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::25eb:8129:7a65:ed46%20
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.48.98
   Masque de sous-réseau. . . . . . . . . : 255.255.252.0
   Passerelle par défaut. . . . . . . . . : 10.33.51.254

```
 Déterminer la MAC de la passerelle

 ```
Interface : 10.33.48.98 --- 0x14
  Adresse Internet      Adresse physique      Type
  10.33.48.14           e4-b3-18-48-36-68     dynamique
  10.33.51.254          7c-5a-1c-cb-fd-a4     dynamique
  10.33.51.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

 ```

Trouvez comment afficher les informations sur une carte IP
 ```
SSID :	WiFi@YNOV
Protocole :	Wi-Fi 4 (802.11n)
Type de sécurité :	WPA2 - Entreprise
Type d’informations de connexion :	Microsoft: PEAP (Protected EAP)
Bande passante réseau :	2,4 GHz
Canal réseau :	2
Vitesse de connexion (Réception/Transmission) :	144/144 (Mbps)
Adresse IPv6 locale du lien :	fe80::25eb:8129:7a65:ed46%20
Adresse IPv4 :	10.33.48.98
Serveurs DNS IPv4 :	10.33.10.2
8.8.8.8
Fabricant :	Intel Corporation
Description :	Intel(R) Dual Band Wireless-AC 8260
Version du pilote :	20.70.30.1
Adresse physique (MAC) :	DC-8B-28-AD-26-0E

 ```


2. Modifications des informations 

1/ Affichage d'informations sur la pile TCP/IP locale

Utilisez l'interface graphique de votre OS pour changer d'adresse IP
 ```
PS C:\Users\apapi> ipconfig

Configuration IP de Windows

Avant modif :

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::6dc0:75e8:35fb:8abb%20
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.48.98
   Masque de sous-réseau. . . . . . . . . : 255.255.252.0
   Passerelle par défaut. . . . . . . . . : 10.33.51.254

après modif :

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::6dc0:75e8:35fb:8abb%20
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.48.238
   Masque de sous-réseau. . . . . . . . . : 255.255.252.0
   Passerelle par défaut. . . . . . . . . : 10.33.51.254
   
 ```
 Il est possible que vous perdiez l'accès internet. Que ce soit le cas ou non, expliquez pourquoi c'est possible de perdre son accès internet en faisant cette opération.

 ```
 J'ai changé d'adresse ip et elle appartenais a quelqu'un d'autre voila pourquoi je n'ai pas internet

 ```
II. Exploration locale en duo

3. Modification d'adresse IP
Modifiez l'IP des deux machines pour qu'elles soient dans le même réseau
```
panneau de configuration > réseau et internet > centre réseau et partage > Wifi > Propriété > Protocole internet version 4: fAdresse ip : 10.10.10.2 masque de sous réseau : 255.255.255.0
```
Vérifier à l'aide d'une commande que votre IP a bien été changée

```
C:\Users\apapi>ipconfig

Configuration IP de Windows


Carte Ethernet Ethernet :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::9551:3e11:d51b:af73%19
   Adresse IPv4. . . . . . . . . . . . . .: 10.10.10.1
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :
```
Vérifier que les deux machines se joignent
```
C:\Users\apapi>ping 10.10.10.2

Envoi d’une requête 'Ping'  10.10.10.2 avec 32 octets de données :
Réponse de 10.10.10.2 : octets=32 temps=2 ms TTL=128
Réponse de 10.10.10.2 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.2 : octets=32 temps=2 ms TTL=128
Réponse de 10.10.10.2 : octets=32 temps=2 ms TTL=128

Statistiques Ping pour 10.10.10.2:
   Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
   Minimum = 1ms, Maximum = 2ms, Moyenne = 1ms
```
 Déterminer l'adresse MAC de votre correspondant
```
C:\Users\apapi>arp -a
   Interface : 10.10.10.1 --- 0x12
  Adresse Internet      Adresse physique      Type
  10.10.10.2            3c-7c-3f-5f-70-fa     dynamique
  10.10.10.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```

4. PETIT CHAT PRIVÉ
sur le PC client
```
./nc.exe 10.10.10.09 8888
yo
bien ou quoi 
```
Visualiser la connexion en cours
```
netstat -a -n -b | Select-String "8888" -Context 0,1

>   TCP    10.10.10.15:51674      10.10.10.9:8888           ESTABLISHED
[nc.exe]
```


III. Manipulations d'autres outils/protocoles côté client
1. DHCP

Exploration du DHCP, depuis votre PC

```
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . : lan
   Description. . . . . . . . . . . . . . : Intel(R) Dual Band Wireless-AC 8260
   Adresse physique . . . . . . . . . . . : DC-8B-28-AD-26-0E
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2001:861:2c20:76a0:6842:d12c:3cc1:f3c9(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2001:861:2c20:76a0:9c54:4521:d161:a699(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::7904:1047:a151:61f1%7(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.1.43(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Bail obtenu. . . . . . . . . . . . . . : mercredi 8 novembre 2023 14:06:18
   Bail expirant. . . . . . . . . . . . . : jeudi 9 novembre 2023 14:06:16
   Passerelle par défaut. . . . . . . . . : fe80::f605:95ff:fe3d:163c%7
                                       192.168.1.254
   Serveur DHCP . . . . . . . . . . . . . : 192.168.1.254
   IAID DHCPv6 . . . . . . . . . . . : 131894056
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2C-C6-D9-99-E8-6A-64-EB-88-FF
   Serveurs DNS. . .  . . . . . . . . . . : 2001:861:2c20:76a0:f605:95ff:fe3d:163c
                                       192.168.1.254
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   Liste de recherche de suffixes DNS propres à la connexion :
                                       lan
```
2. DNS

afficher l'adresse IP du serveur DNS que connait votre ordinateur 
 ```
PS C:\Users\apapi> ipconfig /all

Configuration IP de Windows

   Nom de l’hôte . . . . . . . . . . : DESKTOP-NU2CS5L
   Suffixe DNS principal . . . . . . :

 ```
Utiliser, en ligne de commande l'outil nslookup (Windows, MacOS) ou dig (GNU/Linux, MacOS) pour faire des requêtes DNS à la main

 ```
 PS C:\Users\apapi> nslookup ynov.com 8.8.8.8
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    ynov.com
Addresses:  2606:4700:20::681a:be9
          2606:4700:20::ac43:4ae2
          2606:4700:20::681a:ae9
          104.26.11.233
          104.26.10.233
          172.67.74.226
 ```

4. Wireshark

 Utilisez le pour observer les trames qui circulent entre vos deux carte Ethernet. Mettez en évidence :