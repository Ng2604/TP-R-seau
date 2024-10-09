# TP 3.

## I. ARP basics

**☀️ Avant de continuer...**

PS C:\Users\noahg> ipconfig /all

    Carte réseau sans fil Wi-Fi :
        Adresse physique . . . . . : 58-CD-C9-22-43-FD

**☀️ Affichez votre table ARP**

PS C:\Users\noahg> arp -a

    Interface : 10.33.77.29 --- 0x9
        Adresse Internet      Adresse physique      Type
        10.33.65.63           44-af-28-c3-6a-9f     dynamique
        10.33.73.77           98-8d-46-c4-fa-e5     dynamique
        10.33.77.159          f8-54-f6-ba-c5-1a     dynamique
        10.33.77.160          c8-94-02-f8-ab-97     dynamique
        10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
        10.33.79.255          ff-ff-ff-ff-ff-ff     statique
        224.0.0.22            01-00-5e-00-00-16     statique
        224.0.0.251           01-00-5e-00-00-fb     statique
        224.0.0.252           01-00-5e-00-00-fc     statique
        239.255.255.250       01-00-5e-7f-ff-fa     statique
        255.255.255.255       ff-ff-ff-ff-ff-ff     statique

    Interface : 192.168.56.1 --- 0xf
        Adresse Internet      Adresse physique      Type
        192.168.56.255        ff-ff-ff-ff-ff-ff     statique
        224.0.0.22            01-00-5e-00-00-16     statique
        224.0.0.251           01-00-5e-00-00-fb     statique
        224.0.0.252           01-00-5e-00-00-fc     statique
        239.255.255.250       01-00-5e-7f-ff-fa     statique
        255.255.255.255       ff-ff-ff-ff-ff-ff     statique

**☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école**

PS C:\Users\noahg> arp -a

    Interface : 10.33.77.29 --- 0x9
        10.33.79.254          7c-5a-1c-d3-d8-76     dynamique

**☀️ Supprimez la ligne qui concerne la passerelle**

PS C:\Windows\system32> arp -d 10.33.79.254

**☀️ Prouvez que vous avez supprimé la ligne dans la table ARP**

PS C:\Windows\system32> arp -a

    Interface : 10.33.77.29 --- 0x9
        Adresse Internet      Adresse physique      Type
        10.33.65.63           44-af-28-c3-6a-9f     dynamique
        10.33.73.77           98-8d-46-c4-fa-e5     dynamique
        10.33.77.159          f8-54-f6-ba-c5-1a     dynamique
        10.33.77.160          c8-94-02-f8-ab-97     dynamique
        10.33.79.255          ff-ff-ff-ff-ff-ff     statique
        224.0.0.22            01-00-5e-00-00-16     statique
        224.0.0.251           01-00-5e-00-00-fb     statique
        224.0.0.252           01-00-5e-00-00-fc     statique
        239.255.255.250       01-00-5e-7f-ff-fa     statique
        255.255.255.255       ff-ff-ff-ff-ff-ff     statique

    Interface : 192.168.56.1 --- 0xf
        Adresse Internet      Adresse physique      Type
        192.168.56.255        ff-ff-ff-ff-ff-ff     statique
        224.0.0.22            01-00-5e-00-00-16     statique
        224.0.0.251           01-00-5e-00-00-fb     statique
        224.0.0.252           01-00-5e-00-00-fc     statique
        239.255.255.250       01-00-5e-7f-ff-fa     statique
        255.255.255.255       ff-ff-ff-ff-ff-ff     statique

**☀️ Wireshark**

[lien vers ma capture](./arp1.pcapng)

## II. ARP dans un réseau local

**☀️ Déterminer**

PS C:\Users\noahg> ipconfig

    Carte réseau sans fil Wi-Fi :

        Suffixe DNS propre à la connexion. . . :
        Adresse IPv6. . . . . . . . . . . . . .: 2a04:cec0:c023:eb6f:7bb4:98d3:2407:df78
        Adresse IPv6 temporaire . . . . . . . .: 2a04:cec0:c023:eb6f:995a:a835:8d82:594e
        Adresse IPv6 de liaison locale. . . . .: fe80::b9b:ea93:27e4:994a%9
        Adresse IPv4. . . . . . . . . . . . . .: 192.168.231.80
        Masque de sous-réseau. . . . . . . . . : 255.255.255.0
        Passerelle par défaut. . . . . . . . . : fe80::e40f:c1ff:fe06:f51d%9
                                       192.168.231.2

PS C:\Users\noahg> arp -a

    Interface : 192.168.231.80 --- 0x9
        Adresse Internet      Adresse physique      Type
        192.168.231.2         e6-0f-c1-06-f5-1d 

**☀️ DIY**

PS C:\Users\noahg> ipconfig /all

    Carte réseau sans fil Wi-Fi :

        Suffixe DNS propre à la connexion. . . :
        Description. . . . . . . . . . . . . . : MediaTek Wi-Fi 6E MT7922 (RZ616) 160MHz Wireless LAN Card
        Adresse physique . . . . . . . . . . . : 58-CD-C9-22-43-FD
        DHCP activé. . . . . . . . . . . . . . : Non
        Configuration automatique activée. . . : Oui
        Adresse IPv6. . . . . . . . . . . . . .: 2a04:cec0:c023:eb6f:7bb4:98d3:2407:df78(préféré)
        Adresse IPv6 temporaire . . . . . . . .: 2a04:cec0:c023:eb6f:995a:a835:8d82:594e(préféré)
        Adresse IPv6 de liaison locale. . . . .: fe80::b9b:ea93:27e4:994a%9(préféré)
        Adresse IPv4. . . . . . . . . . . . . .: 192.168.231.7(préféré)
        Masque de sous-réseau. . . . . . . . . : 255.255.255.0
        Passerelle par défaut. . . . . . . . . : fe80::e40f:c1ff:fe06:f51d%9
                                       192.168.231.2
        IAID DHCPv6 . . . . . . . . . . . : 89705929
        DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-E1-81-6D-00-FD-6B-09-15-EE
        Serveurs DNS. . .  . . . . . . . . . . : 192.168.231.2
        NetBIOS sur Tcpip. . . . . . . . . . . : Activé

**☀️ Pingz !**

PS C:\Users\noahg> ping 192.168.231.56

    Envoi d’une requête 'Ping'  192.168.231.56 avec 32 octets de données :
    Réponse de 192.168.231.56 : octets=32 temps=19 ms TTL=128
    Réponse de 192.168.231.56 : octets=32 temps=8 ms TTL=128
    Réponse de 192.168.231.56 : octets=32 temps=11 ms TTL=128
    Réponse de 192.168.231.56 : octets=32 temps=13 ms TTL=128

    Statistiques Ping pour 192.168.231.56:
        Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
        Minimum = 8ms, Maximum = 19ms, Moyenne = 12ms


PS C:\Users\noahg> ping 192.168.231.25

    Envoi d’une requête 'Ping'  192.168.231.25 avec 32 octets de données :
    Réponse de 192.168.231.25 : octets=32 temps=41 ms TTL=128
    Réponse de 192.168.231.25 : octets=32 temps=29 ms TTL=128
    Réponse de 192.168.231.25 : octets=32 temps=28 ms TTL=128
    Réponse de 192.168.231.25 : octets=32 temps=11 ms TTL=128

    Statistiques Ping pour 192.168.231.25:
        Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
        Minimum = 11ms, Maximum = 41ms, Moyenne = 27ms

**☀️ Affichez votre table ARP !**

PS C:\Users\noahg> arp -a

    Interface : 192.168.231.7 --- 0x9
        Adresse Internet      Adresse physique      Type
        192.168.231.25        f8-54-f6-ba-c5-1a     dynamique
        192.168.231.56        28-c5-d2-ea-30-53     dynamique

➜ **Wireshark that**

[lien vers ma capture](./arp2.pcapng)

