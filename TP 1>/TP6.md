# TP 6.

## I. Le setup

### 2. Marche à suivre

**☀️ Prouvez que...**

**DHCP lan 1 :**

[noah@dhcp ~]$ ping ynov.com

    PING ynov.com (104.26.10.233) 56(84) bytes of data.
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=1 ttl=54 time=42.3 ms
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=2 ttl=54 time=37.1 ms
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=3 ttl=54 time=42.7 ms
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=4 ttl=54 time=41.9 ms

    --- ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3008ms
    rtt min/avg/max/mdev = 37.084/40.996/42.730/2.278 ms

**WEB lan 2 :**

[noah@web ~]$ ping ynov.com

    PING ynov.com (104.26.10.233) 56(84) bytes of data.
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=1 ttl=54 time=48.7 ms
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=2 ttl=54 time=37.4 ms
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=3 ttl=54 time=37.7 ms
    64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=4 ttl=54 time=35.1 ms

    --- ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3006ms
    rtt min/avg/max/mdev = 35.144/39.730/48.671/5.255 ms

**DHCP lan 1 ---> DNS lan 2 :**

[noah@dhcp ~]$ ping 10.6.2.12

    PING 10.6.2.12 (10.6.2.12) 56(84) bytes of data.
    64 bytes from 10.6.2.12: icmp_seq=1 ttl=63 time=2.05 ms
    64 bytes from 10.6.2.12: icmp_seq=2 ttl=63 time=3.17 ms
    64 bytes from 10.6.2.12: icmp_seq=3 ttl=63 time=2.11 ms
    64 bytes from 10.6.2.12: icmp_seq=4 ttl=63 time=2.39 ms

    --- 10.6.2.12 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3007ms
    rtt min/avg/max/mdev = 2.053/2.432/3.174/0.446 ms

## II. LAN clients

### 2. Client

**☀️ Prouvez que...**

noah@client1:~$ ip a

    2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
        link/ether 08:00:27:b7:19:71 brd ff:ff:ff:ff:ff:ff
        inet 10.6.1.37/24 brd 10.6.1.255 scope global dynamic noprefixroute enp0s8

noah@client1:~$ resolvectl status

    Link 2 (enp0s8)
        Current Scopes: DNS
            Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
    Current DNS Server: 1.1.1.1
            DNS Servers: 1.1.1.1

noah@client1:~$ ip rout show

    default via 10.6.1.254 dev enp0s8 proto dhcp src 10.6.1.37 metric 100 
    10.6.1.0/24 dev enp0s8 proto kernel scope link src 10.6.1.37 metric 100 

noah@client1:~$ ping ynov.com

    PING ynov.com (104.26.11.233) 56(84) bytes of data.
    64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=54 time=35.2 ms
    64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=2 ttl=54 time=36.7 ms
    64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=3 ttl=54 time=37.8 ms
    64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=4 ttl=54 time=37.0 ms

    --- ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3006ms
    rtt min/avg/max/mdev = 35.211/36.660/37.750/0.924 ms

## III. LAN serveurzzzz

### 1. Serveur Web

#### 3. Analyse et test

**☀️ Déterminer sur quel port écoute le serveur NGINX**

[root@web noah ~]$ ss -lnpt | grep 80

    LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1861,fd=6),("nginx",pid=1860,fd=6))
    LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1751,fd=7),("nginx",pid=1752,fd=7))

**☀️ Ouvrir ce port dans le firewall**

[root@web noah ~]$ sudo firewall-cmd --permanent --add-port=80/tcp

    success

[root@web noah ~]$ sudo firewall-cmd --reload

    success

**☀️ Visitez le site web !**

noah@client1:~$ curl http://10.6.2.11 
           
    <!doctype html>
    <html>
      <head>
        <meta charset='utf-8'>
        <meta name='viewport' content='width=device-width, initial-scale=1'>
        <title>HTTP Server Test Page powered by: Rocky Linux</title>
        <style type="text/css">
