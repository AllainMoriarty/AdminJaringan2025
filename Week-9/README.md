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

## LAPORAN WORKSHOP 9: Migrasi NTP, DNS, SAMBA dan Apache2 ke Jaringan Lab (Kelompok 1)

Praktikum ini bertujuan untuk memindahkan konfigurasi NTP (Network Time Protocol), DNS (Domain Name System), dan SAMBA (file sharing server) dari jaringan internal network ke jaringan lab sesuai dengan kelompk masing-masing. Berikut langkah-langkah konfigurasinya.

#### Desain Tekologi
   ![alt text](images/topologi.png)

#### Konfigurasi NTP (NTPSec) Pada VM 1 (Server)

1. Instalai paket `ntpsec`

   ![alt text](images/ntp-install.png)

2. Konfigurasi server NTP

   ![alt text](images/ntp-conf.png)

   Berikan modifikasi server dengan mengganti server NTP

3. Restart service ntpsec
   Jalankan perintah `systemctl restart ntpsec`

4. Validasi NTP Server
   ![alt text](images/ntp-q.png)

#### Instalasi dan Konfigurasi Samba

Samba adalah perangkat lunak open-source yang memungkinkan berbagi file dan printer antara sistem operasi Windows dan Unix-like (seperti Linux, macOS, dan lainnya). Samba mengimplementasikan protokol SMB/CIFS (Server Message Block/Common Internet File System), yang merupakan protokol berbagi file dan printer yang digunakan secara luas di jaringan Windows. Berikut langkah konfigurasinya.

#### Instalasi package Samba

 <img src="images/samba-install.png" alt="asset">

#### Percobaan Akes FIle Samba

1. Konfigurasi pada samba

![alt text](images/samba-conf.png)

2. Membuat sebuah file di direktori /home/share

![alt text](images/samba-fully-mkdir.png)

3. Percobaan akses dari jaringan kelompok

![alt text](images/samba-access-kelompok.png)

4. Percobaan akses dari host jaringan kelompok lain

![alt text](images/samba-access-kelompok-lain.jpeg)

### Konfigurasi Bind9

DNS Server: 192.168.1.247

#### Konfigurasi DNS Server (Bind9) Pada Server

1. Instalasi paket dengan menjalankan perintah `apt -y install bind9 bind9utils`
2. Modifikasi file `/etc/bind/named.conf`

   ![alt text](images/namedconf.png)

3. Modifikasi file `vi /etc/bind/named.conf.options`

   ![alt text](images/named-conf-options.png)

4. Konfigurasi internal zone pada file `/etc/bind/named.conf.internal-zones`

   ![alt text](images/internal-zones.png)

5. Konfigurasi file `/etc/default/named`

   ![alt text](images/named.png)

6. Buat file sesuai dengan domain lokal

   ![alt text](images/kelompok1.home.png)

7. Buat file sesuai dengan IP Address

   ![alt text](images/1.168.192.db.png)

#### Tes DNS Server 1

1. Tes DNS Server dari jaringan dalam kelompok

![alt text](images/percobaan-dns-internal.png)


#### Konfigurasi Web Server (Apache 2)

1. Instalasi paket apache2
   Jalankan perintah berikut untuk menginstal Apache2:

   ![alt text](images/apache-install.png)

2.  Pengaturan Dasar Apache2
   - ServerTokens: Edit /etc/apache2/conf-enabled/security.conf dan ubah baris:'

       ![alt text](images/apache-conf-enabled.png)

   Ini digunakan menyembunyikan informasi detail versi Apache pada header HTTP, meningkatkan keamanan.

   - DirectoryIndex: Edit /etc/apache2/mods-enabled/dir.conf dan atur urutan file index yang dicari ketika direktori diakses:

   ![alt text](images/apache-mods-install.png)

   - ServerName: Edit /etc/apache2/apache2.conf dan tambahkan baris berikut untuk      mendefinisikan nama server:
      ![alt text](images/apache-apache2.conf.png)

   Ini mencegah munculnya peringatan “Could not reliably determine the server's fully qualified domain name”.


   - ServerAdmin: Edit /etc/apache2/sites-enabled/000-default.conf dan ubah baris email admin:
   ![alt text](images/apache-sites-enabled.png)

3. Custom tampilan halaman 

   ![alt text](images/html.png)

4. Percobaan Akses

   ![alt text](images/apache-page.png)

Dengan hasil yang terdapat dapat percobaan, berarti konfigurasiu web server sudah berhasil.