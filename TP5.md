# TP 5.

## I. Setup

**☀️ Uniquement avec des commandes, prouvez-que :**

- **vous avez bien configuré les adresses IP demandées :**

**Routeur :**

[noah@routeur ~]$ ip a

    enp0s8:
        inet 10.5.1.254/24 brd 10.5.1.255 scope global noprefixroute enp0s8

**Client-1 :**

noah@client1:~$ ip a

    2: enp0s8:
        inet 10.5.1.11/24 brd 10.5.1.255 scope global 

**Client-2 :**

noah@client2:~$ ip a

    2: enp0s8:
        inet 10.5.1.12/24 brd 10.5.1.255 scope global

- **vous avez bien configuré les hostnames demandés :**

**Routeur :**

[noah@routeur ~]$ sudo hostnamectl set-hostname routeur.tp5.b1

    [noah@routeur.tp5.b1 ~]$

**Client-1 :**

noah@client1:~$ sudo hostnamectl set-hostname client1.tp5.b1

    noah@client1.tp5.b1:~$

**Client-2 :**

noah@client2:~$ sudo hostnamectl set-hostname client2.tp5.b1

    noah@client2.tp5.b1:~$

- **tout le monde peut se ping au sein du réseau 10.5.1.0/24**

**Routeur :**

[noah@routeur.tp5.b1 ~]$ ping 10.5.1.11

    PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
    64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=2.71 ms
    64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=1.13 ms
    64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=0.991 ms

    --- 10.5.1.11 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2005ms
    rtt min/avg/max/mdev = 0.991/1.608/2.708/0.779 ms

[noah@routeur.tp5.b1 ~]$ ping 10.5.1.12
    
    PING 10.5.1.12 (10.5.1.12) 56(84) bytes of data.
    64 bytes from 10.5.1.12: icmp_seq=1 ttl=64 time=1.55 ms
    64 bytes from 10.5.1.12: icmp_seq=2 ttl=64 time=0.950 ms
    64 bytes from 10.5.1.12: icmp_seq=3 ttl=64 time=1.26 ms

    --- 10.5.1.12 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2005ms
    rtt min/avg/max/mdev = 0.950/1.254/1.551/0.245 ms

**Client-1 :**

noah@client1.tp5.b1:~$ ping 10.5.1.254

    PING 10.5.1.254 (10.5.1.254) 56(84) bytes of data.
    64 bytes from 10.5.1.254: icmp_seq=1 ttl=64 time=1.25 ms
    64 bytes from 10.5.1.254: icmp_seq=2 ttl=64 time=1.16 ms
    64 bytes from 10.5.1.254: icmp_seq=3 ttl=64 time=1.33 ms

    --- 10.5.1.254 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2008ms
    rtt min/avg/max/mdev = 1.160/1.246/1.326/0.067 ms

noah@client1.tp5.b1:~$ ping 10.5.1.12

    PING 10.5.1.12 (10.5.1.12) 56(84) bytes of data.
    64 bytes from 10.5.1.12: icmp_seq=1 ttl=64 time=0.800 ms
    64 bytes from 10.5.1.12: icmp_seq=2 ttl=64 time=1.02 ms
    64 bytes from 10.5.1.12: icmp_seq=3 ttl=64 time=1.88 ms

    --- 10.5.1.12 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2013ms
    rtt min/avg/max/mdev = 0.800/1.232/1.878/0.465 ms

**Client-2 :**

noah@client2.tp5.b1:~$ ping 10.5.1.254

    PING 10.5.1.254 (10.5.1.254) 56(84) bytes of data.
    64 bytes from 10.5.1.254: icmp_seq=1 ttl=64 time=3.03 ms
    64 bytes from 10.5.1.254: icmp_seq=2 ttl=64 time=1.21 ms
    64 bytes from 10.5.1.254: icmp_seq=3 ttl=64 time=2.14 ms

    --- 10.5.1.254 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2005ms
    rtt min/avg/max/mdev = 1.206/2.122/3.026/0.743 ms

noah@client2.tp5.b1:~$ ping 10.5.1.11

    PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
    64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=0.877 ms
    64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=1.59 ms
    64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=0.921 ms

    --- 10.5.1.11 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2008ms
    rtt min/avg/max/mdev = 0.877/1.128/1.587/0.324 ms

## II. Accès internet pour tous

### 1. Accès internet routeur

**☀️ Déjà, prouvez que le routeur a un accès internet**

[noah@routeur.tp5.b1 ~]$ ping www.ynov.com

    PING www.ynov.com (104.26.11.233) 56(84) bytes of data.
    64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=54 time=19.4 ms
    64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=2 ttl=54 time=19.2 ms
    64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=3 ttl=54 time=19.0 ms

    --- www.ynov.com ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2003ms
    rtt min/avg/max/mdev = 19.002/19.194/19.359/0.147 ms

☀️ **Activez le routage**

[noah@routeur.tp5.b1 ~]$ sudo firewall-cmd --add-masquerade --permanent

    success

[noah@routeur.tp5.b1 ~]$ sudo firewall-cmd --reload

    success

### 2. Accès internet clients

**☀️ Prouvez que les clients ont un accès internet**

**Client-1 :**

noah@client1.tp5.b1:~$ ping www.ynov.com

    PING www.ynov.com (104.26.11.233) 56(84) bytes of data.
    64 bytes from 104.26.11.233: icmp_seq=1 ttl=53 time=22.5 ms
    64 bytes from 104.26.11.233: icmp_seq=2 ttl=53 time=21.4 ms
    64 bytes from 104.26.11.233: icmp_seq=3 ttl=53 time=21.3 ms
    64 bytes from 104.26.11.233: icmp_seq=4 ttl=53 time=25.7 ms
    
    --- www.ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3008ms
    rtt min/avg/max/mdev = 21.331/22.727/25.700/1.777 ms

**Client-2 :**

noah@client2.tp5.b1:~$ ping www.ynov.com

    PING www.ynov.com (172.67.74.226) 56(84) bytes of data.
    64 bytes from 172.67.74.226: icmp_seq=1 ttl=53 time=22.9 ms
    64 bytes from 172.67.74.226: icmp_seq=2 ttl=53 time=22.5 ms
    64 bytes from 172.67.74.226: icmp_seq=3 ttl=53 time=21.1 ms
    64 bytes from 172.67.74.226: icmp_seq=4 ttl=53 time=20.5 ms

    --- www.ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3008ms
    rtt min/avg/max/mdev = 20.480/21.761/22.941/1.005 ms

**☀️ Montrez-moi le contenu final du fichier de configuration de l'interface réseau**

noah@client2.tp5.b1:~$ cat /etc/netplan/01-netcfg.yaml

    network:
      version: 2
      renderer: networkd
      ethernets:
        enp0s8:
          dhcp4: no
          addresses: [10.5.1.12/24]
          gateway4: 10.5.1.254
          nameservers:
            addresses: [1.1.1.1]

## III. Serveur SSH

**☀️ Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH**

**Routeur :**

[noah@routeur.tp5.b1 ~]$ sudo ss -lnpt

    State    Recv-Q   Send-Q     Local Address:Port     Peer Address:Port   Process
    LISTEN   0        128              0.0.0.0:22            0.0.0.0:*       users:(("sshd",pid=686,fd=3))
    LISTEN   0        128                 [::]:22               [::]:*       users:(("sshd",pid=686,fd=4))

[noah@routeur.tp5.b1 ~]$ sudo ss -lnpt | grep 22

    LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=686,fd=3))
    LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=686,fd=4))

**☀️ Sur routeur.tp5.b1, vérifier que ce port est bien ouvert**

[noah@routeur.tp5.b1 ~]$ cat /etc/services | grep 22

    ssh             22/tcp                          # The Secure Shell (SSH) Protocol
    ssh             22/udp                          # The Secure Shell (SSH) Protocol

## IV. Serveur DHCP

### 3. Rendu attendu

#### A. Installation et configuration du serveur DHCP

**☀️ Installez et configurez un serveur DHCP sur la machine routeur.tp5.b1**

[root@routeur.tp5.b1 noah]# dnf -y install dhcp-server

[root@routeur.tp5.b1 noah]# vi /etc/dhcp/dhcpd.conf

    option domain-name-servers      1.1.1.1;
    subnet 10.5.1.0 netmask 255.255.255.0 {
        range dynamic-bootp 10.5.1.137 10.5.1.237;
        option routers 10.5.1.254;
    }     

[root@routeur.tp5.b1 noah]# firewall-cmd --add-service=dhcp

[root@routeur.tp5.b1 noah]# firewall-cmd --runtime-to-permanent

[root@routeur.tp5.b1 noah]# systemctl enable --now dhcpd

#### B. Test avec un nouveau client      

noah@client3.tp5.b1:~$ ip a

    2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        inet 10.5.1.137/24 brd 10.5.1.255 scope global dynamic noprefixroute enp0s8

noah@client3.tp5.b1:~$ ping ynov.com

    PING ynov.com (104.26.10.233) 56(84) bytes of data.
    64 bytes from 104.26.10.233: icmp_seq=1 ttl=53 time=22.4 ms
    64 bytes from 104.26.10.233: icmp_seq=2 ttl=53 time=20.1 ms
    64 bytes from 104.26.10.233: icmp_seq=3 ttl=53 time=22.9 ms
    64 bytes from 104.26.10.233: icmp_seq=4 ttl=53 time=20.4 ms

    --- ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3010ms
    rtt min/avg/max/mdev = 20.102/21.470/22.931/1.223 ms

#### C. Consulter le bail DHCP

**☀️ Consultez le bail DHCP qui a été créé pour notre client**

[root@routeur noah]# cd /var/lib/dhcpd/

[root@routeur dhcpd]# cat dhcpd.leases

    lease 10.5.1.137 {
        starts 1 2024/10/21 09:38:21;
        ends 1 2024/10/21 21:38:21;
        cltt 1 2024/10/21 09:38:21;
        binding state active;
        next binding state free;
        rewind binding state free;
        hardware ethernet 08:00:27:aa:25:90;
        uid "\001\010\000'\252%\220";
        client-hostname "client3.tp5.b1";
        }

**☀️ Confirmez qu'il s'agit bien de la bonne adresse MAC**

[root@routeur dhcpd]# cat dhcpd.leases

    lease 10.5.1.137 {  
        hardware ethernet 08:00:27:aa:25:90;

noah@client3.tp5.b1:~$ ip a

    2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc       fq_codel state UP group default qlen 1000
    link/ether 08:00:27:aa:25:90 brd ff:ff:ff:ff:ff:ff
