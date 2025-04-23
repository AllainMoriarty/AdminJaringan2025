<div align="center">
  <h1 style="text-align: center;font-weight: bold">LAPORAN RESMI WORKSHOP<br>ADMINISTRASI JARINGAN</h1>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
  <h3 style="text-align: center;">Disusun Oleh : </h3>
  <p style="text-align: center;">
    <strong>Nama : Achmad Risel Araby</strong><br>
    <strong>Kelas : 2 D3 IT A</strong><br>
    <strong>NRP : 3123500025</strong>
  </p>

<h3 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2024/2025</h3>
  <hr><hr>
</div>

## LAPORAN WORKSHOP 8: Migrasi NTP, DNS, SAMBA ke Jaringan Lab

Praktikum ini bertujuan untuk memindahkan pengaturan layanan NTP (Network Time Protocol), DNS (Domain Name System), dan SAMBA (server berbagi file) dari jaringan internal menuju jaringan lab, sesuai dengan pembagian kelompok masing-masing. Berikut adalah langkah-langkah yang harus dilakukan untuk melakukan konfigurasi tersebut.

### Konfigurasi NTP (NTPSec) Pada VM 1 (Server)

1. Instalai paket ntpsec
![alt text](images/ntp-1.1.png)

2. Konfigurasi NTP server
![alt text](images/ntp-1.2.png)
Berikan modifikasi server dengan mengganti server NTP

3. Restart service ntpsec Jalankan perintah systemctl restart ntpsec

4. Validasi NTP Server
![alt text](images/ntp-1.3.png)

### Instalasi dan Konfigurasi Samba

Samba adalah perangkat lunak open-source yang memungkinkan berbagi file dan printer antara sistem operasi Windows dan Unix-like (seperti Linux, macOS, dan lainnya). Samba mengimplementasikan protokol SMB/CIFS (Server Message Block/Common Internet File System), yang merupakan protokol berbagi file dan printer yang digunakan secara luas di jaringan Windows. Berikut langkah konfigurasinya.

1. Instalasi package Samba
![alt text](images/samba-1.1.png)

2. Konfigurasi pada samba
![alt text](images/samba-1.2.png)

3. Membuat sebuah file di direktori /home/share
![alt text](images/samba-1.4.png)

4. Percobaan akses dari jaringan kelompok
![alt text](images/samba-1.5.png)

5. Percobaan akses dari host jaringan kelompok lain
![alt text](images/samba-1.6.png)

### Instalasi & Konfigurasi Bind9
DNS Server: 192.168.1.247

#### Konfigurasi DNS Server (Bind9) Pada Server

1. Instalasi paket dengan menjalankan perintah apt -y install bind9 bind9utils

2. Modifikasi file /etc/bind/named.conf
![alt text](images/bind9-1.1.png)

3. Modifikasi file vi /etc/bind/named.conf.options
![alt text](images/bind9-1.2.png)

4. Konfigurasi internal zone pada file /etc/bind/named.conf.internal-zones
![alt text](images/bind9-1.3.png)

5. Konfigurasi file /etc/default/named
![alt text](images/bind9-1.4.png)

6. Buat file sesuai dengan domain lokal
![alt text](images/bind9-1.5.png)

7. Buat file sesuai dengan IP Address
![alt text](images/bind9-1.6.png)

#### Tes DNS Server 1
Tes DNS Server dari jaringan dalam kelompok
![alt text](images/bind9-1.7.png)