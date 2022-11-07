I. Setup IP
🌞 Mettez en place une configuration réseau fonctionnelle entre les deux machines
```
PS C:\Users\Guillaume>netsh interface ipv4 set address name="Ethernet" static 192.168.233.32 255.255.252.0
```
```
Host address		- 192.168.233.32
Network address		- 192.168.232.0
Broadcast address	- 192.168.235.255
```
🌞 Prouvez que la connexion est fonctionnelle entre les deux machines
```
PS C:\Users\Guillaume> ping 192.168.233.129

Envoi d’une requête 'Ping'  192.168.233.129 avec 32 octets de données :
Réponse de 192.168.233.129 : octets=32 temps<1ms TTL=64
Réponse de 192.168.233.129 : octets=32 temps<1ms TTL=64
Réponse de 192.168.233.129 : octets=32 temps=1 ms TTL=64
Réponse de 192.168.233.129 : octets=32 temps=1 ms TTL=64

Statistiques Ping pour 192.168.233.129:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 1ms, Moyenne = 0ms
```
```
guillaume@user3:~$ ping 192.168.233.32
PING 192.168.233.32 (192.168.233.32) 56(84) bytes of data.
64 bytes from 192.168.233.32: icmp_seq=1 ttl=128 time=0.845 ms
64 bytes from 192.168.233.32: icmp_seq=2 ttl=128 time=1.00 ms
64 bytes from 192.168.233.32: icmp_seq=3 ttl=128 time=0.921 ms
64 bytes from 192.168.233.32: icmp_seq=4 ttl=128 time=1.19 ms
64 bytes from 192.168.233.32: icmp_seq=5 ttl=128 time=0.834 ms
^C
--- 192.168.233.32 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 0.834/0.957/1.186/0.129 ms
```
🌞 Wireshark it
```
Type: 8 (Echo (ping) request)
```
🦈  [capture  qui contient les paquets ICMP qui vous ont permis d'identifier les types ICMP](tp2-01.pcapng)

II. ARP my bro

🌞 Check the ARP table
```
Interface : 10.10.10.32 --- 0x15
  Adresse Internet      Adresse physique      Type
  10.10.10.31           00-0c-29-b3-2c-10     dynamique
  10.10.11.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```

🌞 Manipuler la table ARP
```
sudo ip n flus all
ip n  s
ping 10.10.10.32
10.10.10.32 dev ens33 lladdr 00:50:56:c0:00:01 REACHABLE
```
🌞 Wireshark it
```
Interface : 10.10.10.32 --- 0x15
  Adresse Internet      Adresse physique      Type
  10.10.10.31           00-0c-29-b3-2c-10     dynamique
  10.10.11.255          ff-ff-ff-ff-ff-ff     statique
```
```
Interface : 10.10.10.32 --- 0x15
  Adresse Internet      Adresse physique      Type
  10.10.11.255          ff-ff-ff-ff-ff-ff     statique
```
commande arp -d pour surprimer
ping l'autre pc est voire la table arp se remplir

🦈 PCAP qui contient les trames ARP

[capture qui contient les trames ARP](tp2-02.pcapng)

II.5 Interlude hackerzz

III. DHCP you too my brooo
🌞 Wireshark it
```
Découverte de serveur --->  Alors que l’adresse de destination de découverte d’envoi est diffusée 255.255.255.255 et l’adresse source est 0.0.0.0.

Offre de location IP ---> l contient un paramètre de configuration réseau pour le client comme une adresse IP offerte au client 10.1.1.1.

Demande de bail IP --->Cela signifie accepter l’offre du serveur DHCP avec IP 10.1.1.1. ce message a été envoyé par le client avec l’adresse de destination 255.255.255.255 et l’adresse source est 10.1.1.1.

Reconnaissance de bail DE PI ---> Ce message indique clairement au client que vous pouvez maintenant commencer à utiliser le réseau.

1. une IP à utiliser : Offre de location IP
2. l'adresse IP de la passerelle du réseau : Découverte de serveur
3. l'adresse d'un serveur DNS joignable depuis ce réseau : Demande de bail IP
```
🦈 [capture PCAP qui contient l'échange DORA](tp2-03.pcapng)