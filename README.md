# Jarkom-Modul-5-E28-2023

## Kelompok E28
- Shafa Nabilah Hanin / 5025211222
- Nizam Hakim Santoso / 5025211209

# Lapres Praktikum 5
## Daftar Isi
- [Topologi](#topologi)
- [Network Configuration](#network-configuration)
- [Subnetting & Routing](#subnetting--routing)
- [DHCP Configuration](#dhcp-configuration)
- [Iptables File](#iptables-file)
- [Soal Praktikum](#soal-praktikum)
    - [No 1](#no-1)
    - [No 2](#no-2)
    - [No 3](#no-3)
    - [No 4](#no-4)
    - [No 5](#no-5)
    - [No 6](#no-6)
    - [No 7](#no-7)
    - [No 8](#no-8)
    - [No 9](#no-9)
    - [No 10](#no-10)

## Topologi
Topologi yang digunakan pada praktikum 5 adalah sebagai berikut:

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/15ccf883-2511-4174-897f-5bce788db692)  

## Network Configuration
#### Aura
```
#NAT static
auto eth0
iface eth0 inet static
	address 192.168.122.2
	netmask 255.255.255.0
	gateway 192.168.122.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

#A1
auto eth1
iface eth1 inet static
	address 192.220.1.105
	netmask 255.255.255.252

#A4
auto eth2
iface eth2 inet static
	address 192.220.1.109
	netmask 255.255.255.252
```

#### Heiter_Relay
```
#A1
auto eth0
iface eth0 inet static
	address 192.220.1.106
	netmask 255.255.255.252
	gateway 192.220.1.105
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

#A2
auto eth1
iface eth1 inet static
	address 192.220.8.1
	netmask 255.255.248.0

#A3
auto eth2
iface eth2 inet static
	address 192.220.4.1
	netmask 255.255.252.0
```

#### Frieren
```
#A4
auto eth0
iface eth0 inet static
	address 192.220.1.110
	netmask 255.255.255.252
	gateway 192.220.1.109
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

#A5
auto eth1
iface eth1 inet static
	address 192.220.1.113
	netmask 255.255.255.252

#A6
auto eth2
iface eth2 inet static
	address 192.220.1.117
	netmask 255.255.255.252
```

#### Himmel_Relay
```
#A6
auto eth0
iface eth0 inet static
	address 192.220.1.118
	netmask 255.255.255.252
	gateway 192.220.1.117
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

#A7
auto eth1
iface eth1 inet static
	address 192.220.2.1
	netmask 255.255.254.0

#A8
auto eth2
iface eth2 inet static
	address 192.220.1.129
	netmask 255.255.255.128
```

#### Fern_Relay
```
#A8
auto eth0
iface eth0 inet static
	address 192.220.1.130
	netmask 255.255.255.128
	gateway 192.220.1.129
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

#A9
auto eth1
iface eth1 inet static
	address 192.220.1.121
	netmask 255.255.255.252

#A10
auto eth2
iface eth2 inet static
	address 192.220.1.125
	netmask 255.255.255.252
```

#### Revolte_DHCP
```
#A10
auto eth0
iface eth0 inet static
	address 192.220.1.126
	netmask 255.255.255.252
	gateway 192.220.1.125
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### Richter_DNS
```
#A9
auto eth0
iface eth0 inet static
	address 192.220.1.122
	netmask 255.255.255.252
	gateway 192.220.1.121
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### Stark_Web
```
#A5
auto eth0
iface eth0 inet static
	address 192.220.1.114
	netmask 255.255.255.252
	gateway 192.220.1.113
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### Sein_Web
```
#A3
auto eth0
iface eth0 inet static
	address 192.220.4.2
	netmask 255.255.252.0
	gateway 192.220.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### TurkRegion_1022
```
auto eth0
iface eth0 inet dhcp
```

#### GrobeForest_512
```
auto eth0
iface eth0 inet dhcp
```

#### LaubHills_255
```
auto eth0
iface eth0 inet dhcp
```

#### SchwerMountains_64
```
auto eth0
iface eth0 inet dhcp
```

## Subnetting & Routing
Pada praktikum ini dilakukan subnetting menggunakan metode VLSM dengan perhitungan sebagai berikut:

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/8f4c5bff-f132-4fb0-b046-40194434e5c9)  

![Prak5_VLSM](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/6cb3b0eb-f586-447a-bcaf-84ac0c31a9fe)  

Tabel perhitungan lengkap ada di [Spreadsheet](https://docs.google.com/spreadsheets/d/17xy5rJhhSw-FtZohDc3dlJ-p-5X52oG9iJi4lcXu5D0/edit?usp=sharing) dan Tree ada di [Canva](https://www.canva.com/design/DAF2sF6njB8/YvCkceY0lo9vV5gCHLy4gQ/edit?utm_content=DAF2sF6njB8&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

Setelah didapatkan subnet-subnetnya, kemudian dilakukan routing untuk masing-masing routernya. Konfigurasi routingnya adalah menggunakan command-command sebagai berikut:

#### Aura
```sh
route add -net 192.220.8.0 netmask 255.255.248.0 gw 192.220.1.106
route add -net 192.220.4.0 netmask 255.255.252.0 gw 192.220.1.106
route add -net 192.220.1.112 netmask 255.255.255.252 gw 192.220.1.110
route add -net 192.220.1.116 netmask 255.255.255.252 gw 192.220.1.110
route add -net 192.220.2.0 netmask 255.255.254.0 gw 192.220.1.110
route add -net 192.220.1.128 netmask 255.255.255.128 gw 192.220.1.110
route add -net 192.220.1.120 netmask 255.255.255.252 gw 192.220.1.110
route add -net 192.220.1.124 netmask 255.255.255.252 gw 192.220.1.110
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.122.1
```

#### Heiter_Relay
```sh
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.220.1.105
```

#### Frieren
```sh
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.220.1.109
route add -net 192.220.2.0 netmask 255.255.254.0 gw 192.220.1.118
route add -net 192.220.1.128 netmask 255.255.255.128 gw 192.220.1.118
route add -net 192.220.1.120 netmask 255.255.255.252 gw 192.220.1.118
route add -net 192.220.1.124 netmask 255.255.255.252 gw 192.220.1.118
```

#### Himmel_Relay
```sh
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.220.1.117
route add -net 192.220.1.120 netmask 255.255.255.252 gw 192.220.1.130
route add -net 192.220.1.124 netmask 255.255.255.252 gw 192.220.1.130
```

#### Fern_Relay
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.220.1.129
```

## DHCP Configuration
Karena pada soal alokasi IP untuk subnet SchwerMountain, LaubHills, TurkRegion, dan GrobeForest diminta menggunakan DHCP maka perlu dilakukan konfigurasi DHCP sebagai berikut:

### DHCP Server

Lakukan Instalasi DHCP pada Revolte sebagai DHCP Server,
```sh
apt-get update
apt-get install isc-dhcp-server -y
```

Ubah isi file `/etc/default/isc-dhcp-server` menjadi,
```
INTERFACESv4="eth0"
INTERFACESv6=""
```

Ubah isi file `/etc/dhcp/dhcpd.conf` menjadi,
```
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

ddns-update-style none;
authoritative;
log-facility local0;

subnet 192.220.1.104 netmask 255.255.255.252{

}

subnet 192.220.8.0 netmask 255.255.248.0{
    range 192.220.8.2 192.220.15.254;
    option routers 192.220.8.1;
    option broadcast-address 192.220.15.255;
    option domain-name-servers 192.168.122.1;
}

subnet 192.220.4.0 netmask 255.255.252.0{
    range 192.220.4.3 192.220.7.254;
    option routers 192.220.4.1;
    option broadcast-address 192.220.7.255;
    option domain-name-servers 192.168.122.1;
}

subnet 192.220.1.108 netmask 255.255.255.252{

}

subnet 192.220.1.112 netmask 255.255.255.252{

}

subnet 192.220.1.116 netmask 255.255.255.252{

}

subnet 192.220.2.0 netmask 255.255.254.0{
    range 192.220.2.2 192.220.3.254;
    option routers 192.220.2.1;
    option broadcast-address 192.220.3.255;
    option domain-name-servers 192.168.122.1;
}

subnet 192.220.1.128 netmask 255.255.255.128 {
    range 192.220.1.131 192.220.1.254;
    option routers 192.220.1.129;
    option broadcast-address 192.220.1.255;
    option domain-name-servers 192.168.122.1;
}

subnet 192.220.1.120 netmask 255.255.255.252{

}

subnet 192.220.1.124 netmask 255.255.255.252{

}
```

Restart DHCP service menggunakan command berikut
```sh
rm /var/run/dhcpd.pid
service isc-dhcp-server restart
service isc-dhcp-server status
```

### DHCP Relay
Karena ada DHCP client yang terletak di subnet yang berbeda dengan Revolte maka diperlukan instalasi beberapa DHCP relay pada beberapa router.  

Pada router Fern, Heiter, dan  Himmel, lakukan instalasi DHCP relay,
```sh
apt-get update
apt-get install isc-dhcp-relay -y
```

Ubah isi file `/etc/default/isc-dhcp-relay` menjadi,
```
SERVERS="192.220.1.126"
INTERFACES="eth0 eth1 eth2"
OPTIONS=""
```

Ubah isi file `/etc/sysctl.conf` menjadi,
```
net.ipv4.ip_forward=1
```

Restart DHCP relay service,
```sh
service isc-dhcp-relay start
service isc-dhcp-relay restart
```

## Iptables File
Berikut adalah file iptables.sh yang berisi aturan-aturan filtering iptables secara urut.  

#### Aura
```
#No 1
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 192.220.0.0/20 --to-source 192.168.122.2
```

#### Richter
```
#No 2
iptables -A INPUT -p udp -j DROP
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP

#No 3
iptables -I INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
iptables -I INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

#### Revolte
```
#No 3
iptables -I INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
iptables -I INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

#### Sein
```
#No 8
iptables -A INPUT -s 192.220.1.124/30 -m time --datestart 2023-12-10 --datestop 2024-02-15 -j REJECT

#No 6
iptables -A INPUT -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT
iptables -A INPUT -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT

#No 5
iptables -A INPUT -m time --timestart 16:01 --timestop 23:59 --weekdays Mon,Tue,Wed,Thu,Fri -j REJECT
iptables -A INPUT -m time --timestart 00:00 --timestop 07:59 --weekdays Mon,Tue,Wed,Thu,Fri -j REJECT
iptables -A INPUT -m time --weekdays Sat,Sun -j REJECT

#No 4
iptables -A INPUT -p tcp --dport 22 -m iprange --src-range 192.220.4.3-192.220.7.254 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j REJECT
```

#### Stark
```
#No 8
iptables -A INPUT -s 192.220.1.124/30 -m time --datestart 2023-12-10 --datestop 2024-02-15 -j REJECT

#No 6
iptables -A INPUT -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT
iptables -A INPUT -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT

#No 5
iptables -A INPUT -m time --timestart 16:01 --timestop 23:59 --weekdays Mon,Tue,Wed,Thu,Fri -j REJECT
iptables -A INPUT -m time --timestart 00:00 --timestop 07:59 --weekdays Mon,Tue,Wed,Thu,Fri -j REJECT
iptables -A INPUT -m time --weekdays Sat,Sun -j REJECT

#No 4
iptables -A INPUT -p tcp --dport 22 -m iprange --src-range 192.220.4.3-192.220.7.254 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j REJECT
```

## Soal Praktikum
### No 1
> Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.

#### Answer:
MASQUERADE dapat digantikan menggunakan POSTROUTING SNAT seperti pada `iptables.sh` sebagai berikut:
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 192.220.0.0/20 --to-source 192.168.122.2
```

Aura akan mentranslate source IP packet yang menuju eth0 (eth arah NAT) dan berasal dari subnet 192.220.0.0/20 menjadi 192.168.122.2

#### Testing:
Lakukan testing dengan cara ping google.com dari sebarang node:

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/a680a522-2257-4597-8fe0-08c0a7d83ab3)

### No 2
> Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.

#### Answer:
No 2 kami implementasikan pada file `iptables.sh` pada node Richter seperti berikut:
```
iptables -A INPUT -p udp -j DROP
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP
```

Richter akan mengdrop semua koneksi UDP dan semua koneksi TCP kecuali TCP pada port 8080.  

#### Testing:
Lakukan instalasi netcat pada Richter dan TurkRegion(client) menggunakan command,  
```
apt-get update
apt-get install netcat -y
```
##### UDP
Jalankan netcat UDP listening mode pada port 80 di node Richter
```sh
nc -ulvp 80
```

Buat koneksi UDP ke node Richter dari node TurkRegion
```sh
nc -u 192.220.1.122 80
```
Ketikkan `Hello World` pada TurkRegion. Tidak akan terjadi apa-apa karena paket didrop oleh Richter.  

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/03f8634b-6dc3-47b8-8196-3109a5d12d26)

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/cc8e0ddd-82a6-4d11-aa03-5434602bb678)

##### TCP
Jalankan netcat TCP listening mode pada port 8080 di node Richter  
```sh
nc -lvp 8080
```

Buat koneksi TCP ke node Richter dari node TurkRegion  
```sh
nc 192.220.1.122 8080
```
Ketikkan `Hello World` pada TurkRegion. `Hello World` akan terkirim pada terminal Richter.  

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/9dd12de7-0352-4c9e-b23e-f0b3f16969d2)

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/e3ba6695-cf1b-4040-9870-b4a57c6c7e97)

### No 3
> Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.

#### Answer:
Konfigurasi ini diatur pada `iptables.sh` pada node Revolte dan Richter  
```
iptables -I INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
iptables -I INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```
Revolte(DHCP) dan Richter(DNS) akan melakukan drop paket dengan icmp protocol(ping) ketika koneksi yang tersambung lebih dari 3

#### Testing:
Lakukan ping Richter(DNS) menggunakan GrobeForest, LaubHills, SchwerMountains, dan TurkRegion secara bersamaan:

Terjadi error pada TurkRegion karena sudah ada 3 koneksi yang tersambung

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/4b23c88a-8bd7-4603-86ad-b03ab288f306)


### No 4
> Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.

#### Answer:
Pembatasan IP GrobeForest untuk koneksi SSH diatur pada file `iptables.sh` pada Sein dan Stark di bagian,
```
iptables -A INPUT -p tcp --dport 22 -m iprange --src-range 192.220.4.3-192.220.7.254 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j REJECT
```
Sein dan Stark akan mereject semua koneksi SSH(port 22) yang tidak berasal dari IP range GrobeForest  

#### Testing:
Lakukan instalasi SSH Server pada Sein dan Stark,
```
apt-get update
apt-get install openssh-server -y
service ssh start
```

Buat user baru dengan username "e28" dan password "e28"  
```
useradd -m -s /bin/bash e28
passwd e28
```

Buat SSH connection ke Sein melalui node TurkRegion sebagai user e28,
```
ssh-keygen -f "/root/.ssh/known_hosts" -R 192.220.4.2
ssh e28@192.220.4.2
```

Connection refused karena bukan tidak di dalam range IP

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/f4fd70ca-19dc-4d98-99a5-117fec638717)

Buat SSH connection ke Sein melalui node GrobeForest sebagai user e28,
```
ssh-keygen -f "/root/.ssh/known_hosts" -R 192.220.4.2
ssh e28@192.220.4.2
```

Berhasil login  

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/33114fcd-e75a-4cbd-bab3-24663578d980)

### No 5
> Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.

#### Answer:
Konfigurasi fitering pada hari Senin - Jumat jam 08:00 - 16:00 dilakukan dengan cara mereject input dari jam 16:01 - 23:59 dan 00:00 - 07:59. Kemudian reject juga input pada hari sabtu dan minggu.  
```
iptables -A INPUT -m time --timestart 16:01 --timestop 23:59 --weekdays Mon,Tue,Wed,Thu,Fri -j REJECT
iptables -A INPUT -m time --timestart 00:00 --timestop 07:59 --weekdays Mon,Tue,Wed,Thu,Fri -j REJECT
iptables -A INPUT -m time --weekdays Sat,Sun -j REJECT
```
Hal ini berarti hanya input pada hari Senin - Jumat pada jam 08:00 - 16:00 yang akan diterima  

#### Testing:
Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi Selasa jam 06:00,
```sh
date --set="2023-12-19 06:00:00"
```

Lakukan ping ke Sein dari TurkRegion  
```sh
ping 192.220.4.2
```

Connection refused karena diluar interval jam (06:00)  

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/dd6af37a-58fe-4bcd-83f1-b386b6173eef)  

Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi Selasa jam 10:00,
```sh
date --set="2023-12-19 10:00:00"
```

Lakukan ping ke Sein dari TurkRegion  
```sh
ping 192.220.4.2
```

Berhasil karena jam 10:00 didalam interval

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/5ab5747c-7434-4d9d-81a8-021b7ae33b4b)


### No 6
> Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).

#### Answer:
Konfigurasi ini diatur pada `iptables.sh` pada bagian,
```
iptables -A INPUT -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT
iptables -A INPUT -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT
```
Input pada hari Senin - Kamis pada jam 12:00 - 13:00 dan input pada hari Jumat pada jam 11:00 - 13:00 akan ditolak (jam istirahat).

#### Testing:
Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi Selasa jam 12:30,
```sh
date --set="2023-12-19 12:30:00"
```

Lakukan ping ke Sein dari TurkRegion  
```sh
ping 192.220.4.2
```

Connection refused karena dalam interval jam istirahat (12:00 - 13:00)

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/a4b2ea6d-7ef3-492b-854f-2e2a517022e1)

Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi jumat jam 11:30,
```sh
date --set="2023-12-22 11:30:00"
```

Lakukan ping ke Sein dari TurkRegion  
```sh
ping 192.220.4.2
```

Connection refused karena dalam interval jam istirahat (11:00 - 13:00)

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/ced40906-242b-4894-b8a9-98a058c59850)

### No 7
> Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.

#### Answer:

Buat konfigurasi `iptables` pada router-router yang berada dekat dengan web server seperti berikut ini:

```
iptables -A PREROUTING -t nat -p tcp --dport 80 -d 192.220.4.2 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.220.4.2:80
iptables -A PREROUTING -t nat -p tcp --dport 80 -d 192.220.4.2 -j DNAT --to-destination 192.220.1.114:80
iptables -A PREROUTING -t nat -p tcp --dport 443 -d 192.220.1.114 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.220.1.114:443
iptables -A PREROUTING -t nat -p tcp --dport 443 -d 192.220.1.114 -j DNAT --to-destination 192.220.4.2:443
```

#### Testing:

- Untuk menjalankan di port 80, masukkan script `while true; do nc -l -p 80 -c 'echo "Stark"'; done` pada Stark dan `while true; do nc -l -p 80 -c 'echo "Sein"'; done` pada Sein. Kemudian lakukan testing menggunakan netcat dengan `nc 192.220.4.2 80`
- Untuk menjalankan di port 443, masukkan script `while true; do nc -l -p 443 -c 'echo "Stark"'; done` pada Stark dan `while true; do nc -l -p 443 -c 'echo "Sein"'; done` pada Sein. Kemudian lakukan testing menggunakan netcat dengan `nc 192.220.1.114 443`

### No 8
> Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.

#### Answer:
Pemilu Presiden dan Wakil Presiden Indonesia 2024 berakhir pada tanggal 15 Februari 2024, sehingga kita perlu memblokir akses subnet revolte dari tanggal 10 Desember 2023 sampai 15 Februari 2024. Konfigurasi ini diatur pada `iptables.sh` pada bagian,
```
iptables -A INPUT -s 192.220.1.124/30 -m time --datestart 2023-12-10 --datestop 2024-02-15 -j REJECT
```
Semua input dari subnet revolte (192.220.1.124/30) sejak tanggal 10 Desember 2023 sampai 15 Februari 2024 akan di reject

#### Testing:
Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi 19 Desember 2023 jam 10:00:00,
```sh
date --set="2023-12-19 10:00:00"
```

Lakukan ping ke Sein dari Revolte  
```sh
ping 192.220.4.2
```
Connection refused karena 19 Desember 2023 masih dalam masa pemilu  

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/aa29eef8-b10a-4c46-8642-b681242b4a9d)

Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi 13 Februari 2024 jam 10:00:00,
```sh
date --set="2024-2-13 10:00:00"
```

Lakukan ping ke Sein dari Revolte  
```sh
ping 192.220.4.2
```
Connection refused karena 13 Februari 2024 masih dalam masa pemilu  

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/0e02ce86-d947-43c5-b445-0ec25884cd8f)

Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi 15 Februari 2024 jam 10:00:00,
```sh
date --set="2024-2-15 10:00:00"
```

Lakukan ping ke Sein dari Revolte  
```sh
ping 192.220.4.2
```
Berhasil karena masa pemilu berakhir pada 15 Februari 2024 jam 00:00:00 sedangkan sekarang jam 10:00:00  

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/7723c56f-a3e0-4d74-b6a1-9fef0d54fe25)

Lakukan penggantian waktu dan tanggal pada Sein dan Stark menjadi 19 Februari 2024 jam 10:00:00,
```sh
date --set="2024-2-19 10:00:00"
```

Lakukan ping ke Sein dari Revolte  
```sh
ping 192.220.4.2
```
Berhasil karena masa pemilu berakhir pada 15 Februari 2024 jam 00:00:00

![image](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/91371703/9f695f3c-5eb0-4753-bbe9-b238d77ac96c)

### No 9
> Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir  alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. 
(clue: test dengan nmap)


#### Answer:
Karena membutuhkan scanning port, maka dari itu membutuhkan rantai `portscan`. Rantai ini digunakan untuk mengatur rules deteksi port scanning.

```
iptables -N portscan

iptables -A INPUT -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP
iptables -A FORWARD -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP

iptables -A INPUT -m recent --name portscan --set -j ACCEPT
iptables -A FORWARD -m recent --name portscan --set -j ACCEPT

```

Penjelasan:
`iptables -N portscan`: Membuat chain (rantai) iptables baru yang disebut "portscan". Ini akan digunakan untuk menangani aturan-aturan khusus terkait deteksi serangan port scanning.

`iptables -A INPUT -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP`: Ini adalah aturan untuk chain INPUT. Ini berarti bahwa setiap paket yang masuk ke mesin akan diarahkan ke chain "portscan". Jika ada lebih dari 20 paket dalam rentang waktu 600 detik (10 menit), maka paket tersebut akan di-drop (ditolak).

`iptables -A FORWARD -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP`: Ini adalah aturan untuk chain FORWARD. Ini menangani paket yang di-forward melalui mesin. Aturan ini juga memeriksa apakah ada lebih dari 20 paket dalam rentang waktu 600 detik dan, jika ya, akan menolak paket tersebut.

`iptables -A INPUT -m recent --name portscan --set -j ACCEPT`: Aturan ini memberikan instruksi untuk menyetel hitcount ke 0 dan memperbarui timestamp pada setiap paket yang melewati chain "portscan" pada INPUT. Ini diatur untuk menerima paket-paket ini.

`iptables -A FORWARD -m recent --name portscan --set -j ACCEPT`: Aturan yang serupa dengan sebelumnya, tetapi berlaku untuk chain FORWARD. Ini memperbarui timestamp dan mengatur hitcount ke 0 untuk paket yang di-forward melalui mesin.

Dengan rules di atas, skrip mencoba mendeteksi serangan port scanning dengan menghitung jumlah paket yang mencoba terhubung ke banyak port dalam rentang waktu tertentu. Jika jumlah ini melebihi batas tertentu, paket-paket tersebut akan ditolak untuk mencegah serangan port scanning yang berpotensi merugikan.

#### Testing:

Lakukan ping ke Web Server

![no. 9](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/120880399/a46ac479-534f-4ef9-b596-b5c345577704)

Test dengan nmap

![nmap-test](https://github.com/NizamHakim/Jarkom-Modul-5-E28-2023/assets/120880399/e9bdf472-20e2-418f-a437-214ea1b8b740)


### No 10
> Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level. 

#### Answer:

Buat konfigurasi di bawah pada web server:

```
iptables -A INPUT -j LOG --log-level debug --log-prefix 'Dropped Packet' -m limit --limit 1/second --limit-burst 10
```

Itu akan menambahkan aturan pada chain INPUT untuk mengirimkan log pesan ke syslog setiap kali ada paket yang di-drop. Ini akan mencatat pesan log dengan tingkat "debug" dan awalan "Dropped Packet". Pengaturan --limit dan --limit-burst memastikan bahwa tidak terlalu banyak pesan log yang dibuat dalam waktu singkat untuk menghindari kelebihan log.
