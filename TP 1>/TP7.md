# TP7 : On dit chiffrer pas crypter

## II. Serveur Web

### 1. HTTP

#### B. Configuration

**🌞 Lister les ports en écoute sur la machine**

[root@web ~]# sudo ss -lnpt

    State    Recv-Q   Send-Q     Local Address:Port     Peer Address:Port   Process
    LISTEN   0        511              0.0.0.0:80            0.0.0.0:*       users:(("nginx",pid=1353,fd=6),("nginx",pid=1352,fd=6))
    LISTEN   0        511                 [::]:80               [::]:*       users:(("nginx",pid=1353,fd=7),("nginx",pid=1352,fd=7))

**🌞 Ouvrir le port dans le firewall de la machine**

[root@web ~]# sudo firewall-cmd --permanent --add-port=80/tcp

    success

[root@web ~]# sudo firewall-cmd --reload

    success

#### C. Tests client

**🌞 Vérifier que ça a pris effet**

noah@client1:~$ ping sitedefou.tp7.b1

    PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
    64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=2.34 ms
    64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=2 ttl=64 time=1.22 ms
    64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=3 ttl=64 time=1.98 ms
    64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=4 ttl=64 time=1.31 ms

    --- sitedefou.tp7.b1 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3004ms
    rtt min/avg/max/mdev = 1.216/1.712/2.343/0.469 ms

noah@client1:~$ curl http://sitedefou.tp7.b1

    meow !

#### D. Analyze

**🌞 Capture tcp_http.pcap**

[lien vers ma capture](./tcp_http.pcap)

**🌞 Voir la connexion établie**

noah@client1:~$ sudo ss -npt

    State      Recv-Q      Send-Q                 Local Address:Port                  Peer Address:Port       Process
    ESTAB      0           0                         10.7.1.101:51582                    10.7.1.11:80          users:(("firefox",pid=6866,fd=106))

### 2. On rajoute un S

**🌞 Lister les ports en écoute sur la machine**

[root@web noah]# sudo ss -lnpt

    State      Recv-Q     Send-Q         Local Address:Port          Peer Address:Port     Process
    LISTEN     0          511                10.7.1.11:443                0.0.0.0:*         users:(("nginx",pid=1523,fd=6),("nginx",pid=1522,fd=6))

**🌞 Gérer le firewall**

[root@web noah]# sudo firewall-cmd --permanent --add-port=443/tcp

    success

[root@web noah]# sudo firewall-cmd --reload

    success

[root@web noah]# sudo firewall-cmd --permanent --remove-port=80/tcp

    success

[root@web noah]# sudo firewall-cmd --reload

    success

