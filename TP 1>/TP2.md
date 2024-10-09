# TP 2.

## I. Quelques pings

**🌞 Prouvez que votre configuration est effective**

PS C:\Users\noahg> Get-NetIPAddress -InterfaceAlias "Ethernet 2"

    IPAddress         : fe80::e798:8d55:3517:a8c%15
    InterfaceIndex    : 15
    InterfaceAlias    : Ethernet 2
    AddressFamily     : IPv6
    Type              : Unicast
    PrefixLength      : 64
    PrefixOrigin      : WellKnown
    SuffixOrigin      : Link
    AddressState      : Preferred
    ValidLifetime     :
    PreferredLifetime :
    SkipAsSource      : False
    PolicyStore       : ActiveStore

    IPAddress         : 192.168.56.1
    InterfaceIndex    : 15
    InterfaceAlias    : Ethernet 2
    AddressFamily     : IPv4
    Type              : Unicast
    PrefixLength      : 24
    PrefixOrigin      : Manual
    SuffixOrigin      : Manual
    AddressState      : Preferred
    ValidLifetime     :
    PreferredLifetime :
    SkipAsSource      : False
    PolicyStore       : ActiveStore

**🌞 Tester que votre LAN + votre adressage IP est fonctionnel**

PS C:\Users\noahg> ping 192.168.56.104

    Envoi d’une requête 'Ping'  192.168.56.104 avec 32 octets de données :
    Réponse de 192.168.56.104 : octets=32 temps=1 ms TTL=64
    Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64
    Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64
    Réponse de 192.168.56.104 : octets=32 temps=1 ms TTL=64

    Statistiques Ping pour 192.168.56.104:
        Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
        Minimum = 0ms, Maximum = 1ms, Moyenne = 0ms

noah@VMLinux:~$ ping 192.168.56.1

    PING 192.168.56.1 (192.168.56.1) 56(84) bytes of data.
    64 bytes from 192.168.56.1: icmp_seq=1 ttl=128 time=0.676 ms
    64 bytes from 192.168.56.1: icmp_seq=2 ttl=128 time=0.596 ms
    64 bytes from 192.168.56.1: icmp_seq=3 ttl=128 time=0.747 ms
    64 bytes from 192.168.56.1: icmp_seq=4 ttl=128 time=1.63 ms
    --- 192.168.56.1 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3445ms
    rtt min/avg/max/mdev = 0.596/0.912/1.631/0.418 ms

**🌞 Capture de ping**

[lien vers ma capture](./pingVm.pcapng)

## II. Utilisation des ports

**🌞 Sur le PC serveur**

PS C:\Users\noahg\Desktop\netcat-1.11> .\nc.exe -l -p 9999

**🌞 Sur le PC serveur toujours**



**🌞 Sur le PC client**

noah@VMLinux:~$ nc 192.168.56.1 9999

**🌞 Echangez-vous des messages**

    PS C:\Users\noahg\Desktop\netcat-1.11> .\nc.exe -l -p 9999
    coucou
    Bien ?

    noah@VMLinux:~$ nc 192.168.56.1 9999
    coucou
    Bien ?

**🌞 Utilisez une commande qui permet de voir la connexion en cours**

PS C:\Windows\system32> netstat -a -b -n

    [nc.exe]
    TCP    192.168.56.1:49919     192.168.56.104:22      ESTABLISHED

**🌞 Faites une capture Wireshark complète d'un échange**

[lien vers ma capture](./netcat1.pcapng)

**🌞 Utilisez Wireshark pour capturer du trafic HTTP**

[lien vers ma capture](./http.pcapng)

