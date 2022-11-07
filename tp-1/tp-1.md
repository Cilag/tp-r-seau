# I. Exploration locale en solo

## 1. Affichage d'informations sur la pile TCP/IP locale

### En ligne de commande

**🌞 Affichez les infos des cartes réseau de votre PC**

```
Carte réseau sans fil Wi-Fi,F8-B5-4D-43-18-4A,10.33.16.193
```

**🌞 Affichez votre gateway**
```
10.33.16.254
```
**🌞 Déterminer la MAC de la passerelle**
```
00-c0-e7-e0-04-4e
```
### En graphique (GUI : Graphical User Interface)  
**🌞 Trouvez comment afficher les informations sur une carte IP (change selon l'OS)**
```
ouvrir le panneau de configuration, aller dans réseau et Internet, ouvrir Center Réseau et partage, cliquez sur Modifier les paramètre de la carte, ouvrir Wi-Fi et détails
```
## 2. Modifications des informations
### A. Modification d'adresse IP (part 1)  
🌞 Utilisez l'interface graphique de votre OS pour **changer d'adresse IP** :
```
ouvrir le panneau de configuration, aller dans réseau et Internet, ouvrir Center Réseau et partage,cliquez sur le lien Connexions, cliquez sur l’onglet Propriétés dans la fenêtre qui s’ouvre, sélectionnez Internet Protocol version 4 (TCP/IP v4), sélectionnez Utiliser l’adresse IP suivante et saisissez l’adresse IP, Sélectionnez Utiliser le serveur DNS suivant et saisissez l’adresse appropriée, cochez la case Valider les paramètres à la sortie et cliquez sur OK, votre PC exécute automatiquement des diagnostics réseau et vérifie votre connexion 
```
🌞 **Il est possible que vous perdiez l'accès internet.**
```
si l'IPV4 est déjà prise alors c'est l première ordinateur qui garde l'adresse et le réseau rejet la connection
```
# I. Exploration locale en solo
## 1. Affichage d'informations sur la pile TCP/IP locale
### En ligne de commande
**🌞 Affichez les infos des cartes réseau de votre PC**
```
Carte réseau sans fil Wi-Fi,F8-B5-4D-43-18-4A,10.33.16.193
```
**🌞 Affichez votre gateway**
```
10.33.19.254
```
**🌞 Déterminer la MAC de la passerelle**
```
00-c0-e7-e0-04-4e
```
### En graphique (GUI : Graphical User Interface)
**🌞 Trouvez comment afficher les informations sur une carte IP (change selon l'OS)**
```
ouvrir le panneau de configuration, aller dans réseau et Internet, ouvrir Center Réseau et partage, cliquez sur Modifier les paramètre de la carte, ouvrir Wi-Fi et détails
```
## 2. Modifications des informations
### A. Modification d'adresse IP (part 1)  
🌞 Utilisez l'interface graphique de votre OS pour **changer d'adresse IP** :

```
ouvrir le panneau de configuration, aller dans réseau et Internet, ouvrir Center Réseau et partage,cliquez sur le lien Connexions, cliquez sur l’onglet Propriétés dans la fenêtre qui s’ouvre, sélectionnez Internet Protocol version 4 (TCP/IP v4), sélectionnez Utiliser l’adresse IP suivante et saisissez l’adresse IP, Sélectionnez Utiliser le serveur DNS suivant et saisissez l’adresse appropriée, cochez la case Valider les paramètres à la sortie et cliquez sur OK, votre PC exécute automatiquement des diagnostics réseau et vérifie votre connexion 
```
🌞 **Il est possible que vous perdiez l'accès internet.** 
```
si l'IPV4 est déjà prise alors c'est l première ordinateur qui garde l'adresse et le réseau rejet la connection
```
# II. Exploration locale en duo
## 1. Prérequis
## 2. Câblage
## Création du réseau (oupa)
## 3. Modification d'adresse IP
🌞 **Modifiez l'IP des deux machines pour qu'elles soient dans le même réseau**
```
Adresse IPv4. . . . . . . . . . . . . .: 10.10.10.225(en double)
Masque de sous-réseau. . . . . . . . . : 255.255.255.0
```
🌞 **Vérifier à l'aide d'une commande que votre IP a bien été changée**
```
ipconfig /all
```

🌞 **Vérifier que les deux machines se joignent**
```
ping 10.10.10.213
Envoi d’une requête 'Ping'  10.10.10.213 avec 32 octets de données :
Réponse de 10.10.10.213 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.213 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.213 : octets=32 temps=3 ms TTL=128
Réponse de 10.10.10.213 : octets=32 temps=1 ms TTL=128
```
🌞 **Déterminer l'adresse MAC de votre correspondant**
``` arp -a
Interface : 10.33.19.192 --- 0xb
  Adresse Internet      Adresse physique      Type
  10.33.17.98           24-ee-9a-5a-77-60     dynamique
```
## 4. Utilisation d'un des deux comme gateway
🌞**Tester l'accès internet**
```
ping 1.1.1.1

Envoi d’une requête 'Ping'  1.1.1.1 avec 32 octets de données :
Réponse de 1.1.1.1 : octets=32 temps=24 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=21 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=24 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=21 ms TTL=55
```
🌞 **Prouver que la connexion Internet passe bien par l'autre PC**
```
tracert 1.1.1.1

Détermination de l’itinéraire vers one.one.one.one [1.1.1.1]
avec un maximum de 30 sauts :

  1     2 ms     2 ms     4 ms  10.33.19.254
  2     3 ms     3 ms     2 ms  137.149.196.77.rev.sfr.net [77.196.149.137]
  3    11 ms     7 ms     7 ms  108.97.30.212.rev.sfr.net [212.30.97.108]
  4    21 ms    21 ms    18 ms  222.172.136.77.rev.sfr.net [77.136.172.222]
  5    19 ms    20 ms    20 ms  221.172.136.77.rev.sfr.net [77.136.172.221]
  6    22 ms    21 ms    23 ms  221.10.136.77.rev.sfr.net [77.136.10.221]
  7    22 ms    22 ms    20 ms  221.10.136.77.rev.sfr.net [77.136.10.221]
  8    19 ms    22 ms    26 ms  141.101.67.254
  9    23 ms    24 ms    22 ms  172.71.132.2
 10    20 ms    20 ms    23 ms  one.one.one.one [1.1.1.1]
 ```
## 5. Petit chat privé
🌞 **sur le PC *serveur*** avec par exemple l'IP 192.168.1.1

```
PS C:\Users\pc\Downloads\netcat-1.11> ping 10.10.10.210

        Envoi d’une requête 'Ping'  10.10.10.210 avec 32 octets de données :
        Réponse de 10.10.10.210 : octets=32 temps<1ms TTL=128
        Réponse de 10.10.10.210 : octets=32 temps<1ms TTL=128
        Réponse de 10.10.10.210 : octets=32 temps<1ms TTL=128
        Réponse de 10.10.10.210 : octets=32 temps<1ms TTL=128

        Statistiques Ping pour 10.10.10.210:
        Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
        Durée approximative des boucles en millisecondes :
        Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
        PS C:\Users\pc\Downloads\netcat-1.11> .\nc.exe -l -p 8888
        mec
        ftg
        tg
        bouffon
        fdp
        chu mort ca marche
        c bi1
```

🌞 **sur le PC *client*** avec par exemple l'IP 192.168.1.2

```
ping 10.10.10.213

Envoi d’une requête 'Ping'  10.10.10.213 avec 32 octets de données :
Réponse de 10.10.10.213 : octets=32 temps<1ms TTL=128
Réponse de 10.10.10.213 : octets=32 temps<1ms TTL=128
Réponse de 10.10.10.213 : octets=32 temps<1ms TTL=128
Réponse de 10.10.10.213 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.10.10.213:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
PS C:\Users\cedri\Desktop\netcat-1.11> ^C
PS C:\Users\cedri\Desktop\netcat-1.11> .\nc.exe 10.10.10.213 8888
ftg
mec
tg
bouffon
fdp
chu mort ca marche
c bi1
```

🌞 **Visualiser la connexion en cours**

```
netstat -a -n -b
 TCP    10.10.10.225:8888      10.10.10.210:54361     ESTABLISHED
 [nc.exe]
```

🌞 Pour aller un peu plus loin

- si vous faites un netstat sur le serveur AVANT que le client netcat se connecte, vous devriez observer que votre serveur netcat écoute sur toutes vos interfaces
```
.\nc.exe -l -p 8888

 netstat -a -n -b | select-string 8888

  TCP    0.0.0.0:8888           0.0.0.0:0              LISTENING
```

- il est possible d'indiquer à netcat une interface précise sur laquelle écouter
  - par exemple, on écoute sur l'interface Ethernet, mais pas sur la WiFI

.\nc.exe -l -p 8888 -s 10.10.10.225
```
netstat -a -n -b | select-string 8888

  TCP    10.10.10.225:8888      0.0.0.0:0              LISTENING
```

## 6. Firewall

Toujours par 2.

Le but est de configurer votre firewall plutôt que de le désactiver

🌞 **Activez et configurez votre firewall**
```
ouvrir pare-feu windows defender puis cliquez sur régles de traffic entrant et sélectionner Partagede fichiers et d'imprimantes (Demande d'écho - Trafic entrant ICMPv4)
```
  
# III. Manipulations d'autres outils/protocoles côté client

## 1. DHCP

🌞**Exploration du DHCP, depuis votre PC**
```
PS C:\Users\Guillaume> ipconfig /all

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Killer(R) Wi-Fi 6 AX1650i 160MHz Wireless Network Adapter (201NGW)
   Adresse physique . . . . . . . . . . . : 4C-03-4F-E9-73-F7
   DHCP activé. . . . . . . . . . . . . . : Oui <---- 
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::b980:3214:57b0:7a1d%6(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.16.193(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.252.0
   Bail obtenu. . . . . . . . . . . . . . : mercredi 5 octobre 2022 09:05:38 <----------
   Bail expirant. . . . . . . . . . . . . : jeudi 6 octobre 2022 09:05:38 <----------
   Passerelle par défaut. . . . . . . . . : 10.33.19.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.19.254 <----------
   IAID DHCPv6 . . . . . . . . . . . : 88867663
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-29-C3-B8-56-08-8F-C3-51-69-8E
```
## 2. DNS
🌞** Trouver l'adresse IP du serveur DNS que connaît votre ordinateur**
```
PS C:\Users\Guillaume> ipconfig /all

   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       8.8.4.4
                                       1.1.1.1
```

🌞 Utiliser, en ligne de commande l'outil `nslookup` (Windows, MacOS) ou `dig` (GNU/Linux, MacOS) pour faire des requêtes DNS à la main
```
PS C:\Users\Guillaume> nslookup google.com
Serveur :   dns.google
Address:  8.8.8.8  <---- requête à cette adresse

Réponse ne faisant pas autorité :
Nom :    google.com
Addresses:  2a00:1450:4007:819::200e
          142.250.178.142
```
```
PS C:\Users\Guillaume> nslookup ynov.com
Serveur :   dns.google
Address:  8.8.8.8 <---- requête à cette adresse
Réponse ne faisant pas autorité :
Nom :    ynov.com
Addresses:  2606:4700:20::681a:ae9
          2606:4700:20::681a:be9
          2606:4700:20::ac43:4ae2
          172.67.74.226
          104.26.11.233
          104.26.10.233
```
Les deux utilises le même DNS, celui de google.

```
PS C:\Users\Guillaume> nslookup.exe 231.34.113.12
Serveur :   dns.google
Address:  8.8.8.8

*** dns.google ne parvient pas à trouver 231.34.113.12 : Non-existent domain

PS C:\Users\Guillaume> nslookup.exe 78.34.2.17
Serveur :   dns.google
Address:  8.8.8.8

Nom :    cable-78-34-2-17.nc.de <---- Domaine
Address:  78.34.2.17

```
Ici seulement une des deux adresses existes sur la première on voit que le premier n'a pas de domaine, `231.34.113.12 ` n'est donc pas présent dans le DNS de google.
# IV. Wireshark
**Wireshark est un outil qui permet de visualiser toutes les trames qui sortent et entrent d'une carte réseau.**
🌞 Utilisez le pour observer les trames qui circulent entre vos deux carte Ethernet. Mettez en évidence :

![](https://i.imgur.com/TjPLyW4.jpg)
![](https://imgur.com/a/RjnqdlS)
![](https://i.imgur.com/9v8O7xz.png)
🌞 Wireshark it
Notre PC se connecte à l'adresse 77.136.192.79 et au port 443