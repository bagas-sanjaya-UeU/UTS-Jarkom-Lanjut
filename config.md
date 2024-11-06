# Konfigurasi IP

R1 Citra

1. hubungkan router ke internet menggunakan dhcp Client
   ip -> dhcp client -> + -> ether 1 -> klik Ok

apabila status bound berarti sudah terkoneksi

2. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.1.1/24 -> Ether 2
   ip 2, 12.12.12.1/29 -> IPIP Tunnel

3. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

R2 KJ

1. hubungkan router ke internet menggunakan dhcp Client
   ip -> dhcp client -> + -> ether 1 -> klik Ok

apabila status bound berarti sudah terkoneksi

2. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.2.1/24 -> Ether 2
   ip 2, 12.12.12.2/29 -> IPIP Tunnel
   IP 3, 11.11.11.1/29 -> IPIP Tunnel

3. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

R3 KHI

1. hubungkan router ke internet menggunakan dhcp Client
   ip -> dhcp client -> + -> ether 1 -> klik Ok

apabila status bound berarti sudah terkoneksi

2. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.3.1/24 -> Ether 2
   ip 2, 11.11.11.2/29 -> IPIP Tunnel

3. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

# Konfigurasi IP-in-IP (IPIP)

R1 Citra

1. Untuk menambahkan interface IPIP Tunnel

- buka menu Interface > IP Tunnel > Add :

Local address : 10.5.5.1
Remote Address R2 : 10.5.5.2

- buka menu Interface > IP Tunnel > Add :

Local address : 10.5.5.1
Remote Address R3: 10.4.4.2

R2 KJ

1. Untuk menambahkan interface IPIP Tunnel

- buka menu Interface > IP Tunnel > Add :

Local address : 10.5.5.2
Remote Address R1 : 10.5.5.1

- buka menu Interface > IP Tunnel > Add :

Local address : 10.4.4.1
Remote Address R3: 10.4.4.2

R3 KHI

1. Untuk menambahkan interface IPIP Tunnel

- buka menu Interface > IP Tunnel > Add :

Local address : 10.4.4.2
Remote Address R1 : 10.5.5.1

- buka menu Interface > IP Tunnel > Add :

Local address : 10.4.4.2
Remote Address R2: 10.4.4.1

# Konfigurasi routing

R1 CR

1. Ip -> routes -> +
Ke R2
- dst address 192.168.2.0/24
- gateway 12.12.12.2

Ke R3
- dst address 192.168.3.0/24
- gateway 11.11.11.2

R2 KJ

1. Ip -> routes -> +
Ke R1
- dst address 192.168.1.0/24
- gateway 12.12.12.1

Ke R3
- dst address 192.168.3.0/24
- gateway 11.11.11.2

R3 KHI

1. Ip -> routes -> +
Ke R1
- dst address 192.168.1.0/24
- gateway 12.12.12.1

Ke R2
- dst address 192.168.2.0/24
- gateway 11.11.11.1
