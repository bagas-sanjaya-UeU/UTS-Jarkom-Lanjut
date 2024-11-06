R1 Citra

1. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.1.1/24 -> Ether 2
   ip 2, 11.11.11.1 -> Ether 3
   ip 3, 12.12.12.1 -> Ether 4

2. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

R2 KJ

1. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.2.1/24 -> Ether 2
   ip 2, 10.10.10.1 -> Ether 3
   ip 3, 12.12.12.2 -> Ether 4

2. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

R3 KHI

1. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.3.1/24 -> Ether 2
   ip 2, 10.10.10.2 -> Ether 3
   ip 3, 11.11.11.2 -> Ether 4

2. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

# Routing RIP

R1 Citra

1. Konfigurasi Routing RIP
   Routing -> RIP -> + Interface

- interface Ether 3 -> receive v1-2 -> send v1-2 -> ok
- interface Ether 4 -> receive v1-2 -> send v1-2 -> ok

2. Tambahkan Network yang menjadi ip address pada router yang telah di petakan
   Routing -> RIP -> Networks -> +

- Address 192.168.1.0
- Address 11.11.11.0
- Address 12.12.12.0

3. Pilih tab Neighbours untuk memasukan ip port yang terhubung di tetangga

Neighbours -> + 11.11.11.2
Neighbours -> + 12.12.12.2

R2 KJ

1. Konfigurasi Routing RIP
   Routing -> RIP -> + Interface

- interface Ether 3 -> receive v1-2 -> send v1-2 -> ok
- interface Ether 4 -> receive v1-2 -> send v1-2 -> ok

2. Tambahkan Network yang menjadi ip address pada router yang telah di petakan
   Routing -> RIP -> Networks -> +

- Address 192.168.2.0
- Address 10.10.10.0
- Address 12.12.12.0

3. Pilih tab Neighbours untuk memasukan ip port yang terhubung di tetangga

Neighbours -> + 10.10.10.2
Neighbours -> + 12.12.12.1

R3 KHI

1. Konfigurasi Routing RIP
   Routing -> RIP -> + Interface

- interface Ether 3 -> receive v1-2 -> send v1-2 -> ok
- interface Ether 4 -> receive v1-2 -> send v1-2 -> ok

2. Tambahkan Network yang menjadi ip address pada router yang telah di petakan
   Routing -> RIP -> Networks -> +

- Address 192.168.3.0
- Address 10.10.10.0
- Address 11.11.11.0

3. Pilih tab Neighbours untuk memasukan ip port yang terhubung di tetangga

Neighbours -> + 10.10.10.1
Neighbours -> + 11.11.11.1
