# TP 1.

## I. Récolte d'informations
**🌞 Adresses IP de ta machine**

PS C:\Users\noahg> ipconfig

Carte réseau sans fil Wi-Fi :

    Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.29

**🌞 Si t'as un accès internet normal, d'autres infos sont forcément dispos...**

PS C:\Users\noahg> ipconfig

Carte réseau sans fil Wi-Fi :

    Passerelle par défaut. . . . . . . . . : 10.33.79.254

PS C:\Users\noahg> ipconfig /all

Carte réseau sans fil Wi-Fi :
    
    Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8

PS C:\Users\noahg> ipconfig /all

Carte réseau sans fil Wi-Fi :

    Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254

**🌟 BONUS : Détermine s'il y a un pare-feu actif sur ta machine**

PS C:\Users\noahg> Get-NetFirewallProfile | ft Name,Enabled

    Name    Enabled
    ----    -------
    Domain     True
    Private    True
    Public     True

PS C:\Windows\system32> New-NetFirewallRule -DisplayName "Autoriser le Bureau à distance (RDP)" -Group "Bureau à distance" -Profile Domain -Enabled True -Action Allow


    Name                          : {5135e636-7c6c-42fd-be6d-b9d072cc1124}
    DisplayName                   : Autoriser le Bureau à distance (RDP)
    Description                   :
    DisplayGroup                  : Bureau à distance
    Group                         : Bureau à distance
    Enabled                       : True
    Profile                       : Domain
    Platform                      : {}
    Direction                     : Inbound
    Action                        : Allow
    EdgeTraversalPolicy           : Block
    LooseSourceMapping            : False
    LocalOnlyMapping              : False
    Owner                         :
    PrimaryStatus                 : OK
    Status                        : La règle a été analysée à partir de la banque. (65536)
    EnforcementStatus             : NotApplicable
    PolicyStoreSource             : PersistentStore
    PolicyStoreSourceType         : Local
    RemoteDynamicKeywordAddresses : {}
    PolicyAppId                   :

## II. Utiliser le réseau
**🌞 Envoie un ping vers...**

PS C:\Users\noahg> ping 10.33.77.29

    Envoi d’une requête 'Ping'  10.33.77.29 avec 32 octets de données :
    Réponse de 10.33.77.29 : octets=32 temps<1ms TTL=128
    Réponse de 10.33.77.29 : octets=32 temps<1ms TTL=128
    Réponse de 10.33.77.29 : octets=32 temps<1ms TTL=128
    Réponse de 10.33.77.29 : octets=32 temps<1ms TTL=128

    Statistiques Ping pour 10.33.77.29:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms

PS C:\Users\noahg> ping 127.0.0.1

    Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

    Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms

**🌞 On continue avec ping**

PS C:\Users\noahg> ping 10.33.79.254

    Envoi d’une requête 'Ping'  10.33.79.254 avec 32 octets de données :
    Délai d’attente de la demande dépassé.

PS C:\Users\noahg> ping 10.33.77.159

    Envoi d’une requête 'Ping'  10.33.77.159 avec 32 octets de données :
    Réponse de 10.33.77.159 : octets=32 temps=12 ms TTL=128
    Réponse de 10.33.77.159 : octets=32 temps=12 ms TTL=128
    Réponse de 10.33.77.159 : octets=32 temps=12 ms TTL=128
    Réponse de 10.33.77.159 : octets=32 temps=16 ms TTL=128

    Statistiques Ping pour 10.33.77.159:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
    Minimum = 12ms, Maximum = 16ms, Moyenne = 13ms

PS C:\Users\noahg> ping www.google.fr

    Envoi d’une requête 'ping' sur www.google.fr [172.217.20.195] avec 32 octets de données :
    Réponse de 172.217.20.195 : octets=32 temps=19 ms TTL=116
    Réponse de 172.217.20.195 : octets=32 temps=19 ms TTL=116
    Réponse de 172.217.20.195 : octets=32 temps=19 ms TTL=116
    Réponse de 172.217.20.195 : octets=32 temps=18 ms TTL=116

    Statistiques Ping pour 172.217.20.195:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
    Minimum = 18ms, Maximum = 19ms, Moyenne = 18ms

**🌞 Faire une requête DNS à la main**

PS C:\Users\noahg> nslookup www.thinkerview.com

    Serveur :   dns.google
    Address:  8.8.8.8

    Réponse ne faisant pas autorité :
    Nom :    www.thinkerview.com
    Addresses:  2a06:98c1:3120::7
                2a06:98c1:3121::7
                188.114.96.7
                188.114.97.7

PS C:\Users\noahg> nslookup www.wikileaks.org

    Serveur :   dns.google
    Address:  8.8.8.8

    Réponse ne faisant pas autorité :
    Nom :    wikileaks.org
    Addresses:  80.81.248.21
                51.159.197.136
    Aliases:  www.wikileaks.org

PS C:\Users\noahg> nslookup www.torproject.org

    Serveur :   dns.google
    Address:  8.8.8.8

    Réponse ne faisant pas autorité :
    Nom :    www.torproject.org
    Addresses:  2a01:4f8:fff0:4f:266:37ff:feae:3bbc
                2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
                2a01:4f9:c010:19eb::1
                2620:7:6002:0:466:39ff:fe32:e3dd
                2620:7:6002:0:466:39ff:fe7f:1826
                204.8.99.144
                95.216.163.36
                116.202.120.165
                116.202.120.166
                204.8.99.146

## III. Sniffer le réseau

**🌞 J'attends dans le dépôt git de rendu un fichier ping.pcap**

[lien vers ma capture](./ping.pcapng)

**🌞 Livrez un deuxième fichier : dns.pcap**

[lien vers ma capture](./dns.pcapng)

## IV. Network scanning et adresses IP

**🌞 Effectue un scan du réseau auquel tu es connecté**

PS C:\Users\noahg> nmap -sn -PR 10.33.77.0/20

    Nmap scan report for 10.33.77.29
    Host is up.
    Nmap done: 4096 IP addresses (627 hosts up) scanned in 155.18 seconds

**🌞 Changer d'adresse IP**

ip choisi : 10.33.70.7

PS C:\Users\noahg> ipconfig

    Carte réseau sans fil Wi-Fi :

    Adresse IPv4. . . . . . . . . . . . . .: 10.33.70.7
    Masque de sous-réseau. . . . . . . . . : 255.255.240.0
    Passerelle par défaut. . . . . . . . . : 10.33.79.254