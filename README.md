# Praktikum Jaringan Komputer Modul 3 Kelompok D13

# Jarkom-Modul-3-D13-2022

| **No** | **Nama**                  | **NRP**    |
| ------ | ------------------------- | ---------- |
| 1      | Marcellino Mahesa Janitra | 5025201105 |
| 2      | Kurnia Cahya Febryanto    | 5025201073 |
| 3      | Abisha Kean Tuana Sirait  | 5025201052 |

---

## Daftar Isi

- [Setting](#setting)
- [Nomor 1](#nomor-1)
- [Nomor 2](#nomor-2)

---
### Setting
Pada langkah awal dilakukan setting GNS sesuai dengan modul yang telah diberikan. Konfigurasi yang digunakan adalah sebagai berikut:

#### Ostania
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.191.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.191.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
  address 192.191.3.1
	netmask 255.255.255.0
```

#### SSS
```
auto eth0
iface eth0 inet static
	address 192.191.1.2
	netmask 255.255.255.0
	gateway 192.191.1.1
```

#### Garden
```
auto eth0
iface eth0 inet static
	address 192.191.1.3
	netmask 255.255.255.0
	gateway 192.191.1.1
```

#### WISE
``` 
auto eth0
iface eth0 inet static
	address 192.191.2.2
	netmask 255.255.255.0
	gateway 192.191.2.1
```

#### Berlint
```
auto eth0
iface eth0 inet static
	address 192.191.2.3
	netmask 255.255.255.0
	gateway 192.191.2.1
```

#### Westalis
```
auto eth0
iface eth0 inet static
	address 192.191.2.4
	netmask 255.255.255.0
	gateway 192.191.2.1
```

#### Eden
```
auto eth0
iface eth0 inet static
	address 192.191.3.2
	netmask 255.255.255.0
	gateway 192.191.3.1
```

#### NewstonCastle
```
auto eth0
iface eth0 inet static
	address 192.191.3.3
	netmask 255.255.255.0
	gateway 192.191.3.1
```

#### KemonoPark
```
auto eth0
iface eth0 inet static
	address 192.191.3.4
	netmask 255.255.255.0
	gateway 192.191.3.1
```

masukkan ke `/root/.bashrc` ke setiap node
```
echo nameserver 192.168.122.1 > /etc/resolv.conf
```

### Nomor 1 
Loid bersama Franky berencana membuat peta tersebut dengan kriteria WISE sebagai DNS Server, Westalis sebagai DHCP Server, Berlint sebagai Proxy Server (1)

#### Ostania 
masukkan ke `/root/.bashrc`
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.191.0.0/16
cat /etc/resolv.conf
echo nameserver 192.168.122.1 > /etc/resolv.conf
```

##### WISE -> DNS Server
masukkan ke `/root/.bashrc`
```
apt-get update
apt-get install bind9 -y
```

##### Westalis -> DHCP Server
masukkan ke `/root/.bashrc`
```
apt-get update
apt-get install isc-dhcp-server -y
```

##### Berlint -> Proxy Server
masukkan ke `/root/.bashrc`
```
apt-get update
apt-get install squid -y
service squid start
```
lalu cek dengan `service squid status`

</br>

### Nomor 2 

