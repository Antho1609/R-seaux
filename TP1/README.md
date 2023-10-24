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

III. Manipulations d'autres outils/protocoles côté client

 ```


 ```