# Jarkom-Modul-1-C03-2021

- Junaedi Akbar 05111940000041
- Zydhan Linnar Putra 05111940000118
- M.Fajri Davyza Chaniago 05111940000180

## 1

> Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!
> Untuk Menjalankan :

```
http.host == “ichimarumaru.tech”
```

Maka akan diperoleh hasil berikut
<br>
<img src="./img/1.jpg" width="700" height="400">
<br>

## 2

> Temukan paket dari web-web yang menggunakan basic authentication method!
> Untuk Menjalankan :

```
http.authbasic
```

Maka akan diperoleh hasil berikut
<br>
<img src="./img/2.jpg" width="700" height="400">
<br>

## 3

> Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
> Gunakan perintah untuk mendapatkan kode dan pass

```
 http.host contains basic.ichimarumaru.tech
```

Maka akan diperoleh hasil berikut
<br>
<img src="./img/3.jpg" width="700" height="400">
<br>
Kode dan User name terletak pada bagian credentials .
<br>
Kemudian Berikut hasil dari web pencarian dengan menggunakan kode damn password yang di dapat
<br>
<img src="./img/31.jpg" width="700" height="400">
<br>

## 4

> Temukan paket mysql yang mengandung perintah query select!
> Untuk Menjalankan :
> Digunakan 'SELECT' dengan menggunakan huruf besar dan kecil

```
mysql.query contains "select"
```

```
mysql.query contains "SELECT"
```

Maka akan diperoleh hasil berikut
<br>
<img src="./img/4.jpg" width="700" height="400">
<img src="./img/41.jpg" width="700" height="400">
<br>

## 5

> Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
> Untuk Menjalankan :

```
http.authbasic
```

Maka akan diperoleh hasil berikut
<br>
<img src="./img/5.jpg" width="700" height="400">
<br>
Kemudian Berikut hasil dari web pencarian dengan menggunakan kode damn password yang di dapat
<br>
<img src="./img/51.jpg" width="700" height="400">
<br>

## 6

> Cari username dan password ketika melakukan login ke FTP Server!

Menjalankan filter:

```
 ftp.request.command == USER || ftp.request.command == PASS
```

Maka akan diperoleh hasil berikut
<br>
<img src="./img/soal6-1.jpg" width="700" height="400">
<br>

## 7

> Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Menjalankan filter:

```
frame contains “Real.pdf”
```

Sehingga diperoleh hasil berikut:
<br>
<img src="./img/soal7-1.jpg" width="700" height="400">
<br>
Selanjutnya _Follow_ -> _TCP Stream_ dan download sebagai RAW
<br>
<img src="./img/soal7-2.jpg" width="700" height="400">
<br>
Berikut adalah file yang diperoleh:
<br>
<img src="./img/soal7-3.jpg" width="700" height="400">
<br>

## 8

> Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Sehingga perlu mencari string RETR (untuk mengambil file)
Menjalankan filter:

```
ftp-data.command contains RETR
```

<br>
<img src="./img/soal8.jpg" width="700" height="400">

## 9

> Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Menjalankan filter:

```
ftp-data.command contains "secret.zip"
```

<br>
<img src="./img/soal9.jpg" width="700" height="400">
<br>
Diperoleh file `wanted.pdf` di dalam `secret.zip` namun masih memerlukan password untuk membukanya.

## 10

> Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Menjalankan filter:

```
ftp-data.command contains "history.txt"
```

Untuk mencari file `history.txt`
<br>
Diperoleh:
<br>
<img src="./img/soal10-1.jpg" width="700" height="400">
<br>
Selanjutnya follow TCP Stream, diperoleh
<br>
<img src="./img/soal10-2.jpg" width="700" height="400">
<br>
ditemukan `key = "$(tail -1 bukanapaapa.txt)`
<br>
sehingga perlu mencari file **bukanapaapa.txt**, dengan filter:

```
ftp-data.command contains "bukanapaapa.txt"
```

Sehingga diperoleh:
<br>
<img src="./img/soal10-3.jpg" width="700" height="400">
<br>
diperoleh password : `d1b1langbukanapaapajugagapercaya`
<br>
Selanjutnya buka file `wanted.pdf` pada `secret.zip`
<br>
<img src="./img/soal10-4.jpg" width="700" height="400">
<br>

## 11

> Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

Menjalankan filter:

```text
src port 80
```

Setelah itu untuk mendapatkan hasil di wireshark perlu dilakukan pembukaan website yang menggunakan http (port 80) seperti monta.if.its.ac.id.

![Filter src port 80](https://cdn.discordapp.com/attachments/769183322147389460/891289545759420436/unknown.png)

## 12

> Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Menjalankan filter:

```text
port 21
```

Setelah itu untuk mendapatkan hasil di wireshark perlu dilakukan curl ke web dengan protokol FTP (port 21) seperti [ftp://ftp.unicode.org/public/unidata/unicodedata.txt](ftp://ftp.unicode.org/public/unidata/unicodedata.txt).

![Filter port 21](https://cdn.discordapp.com/attachments/769183322147389460/891292989387853824/unknown.png)

## 13

> Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

Menjalankan filter:

```text
dst port 443
```

Kita tidak perlu membuka apapun karena banyak _background task_ sistem yang melakukan komunikasi ke port 443.

![Filter dst port 443](https://cdn.discordapp.com/attachments/769183322147389460/891293510848897054/unknown.png)

## 14

> Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

Menjalankan filter:

```text
dst host kemenag.go.id
```

Setelah membuka kemenag.go.id didapatkan hasil sebagai berikut.

![Filter dst host kemenag.go.id](https://cdn.discordapp.com/attachments/769183322147389460/891293953561886761/unknown.png)

## 15

> Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

Menjalankan filter: (IP saya 192.168.1.2)

```text
src host 192.168.1.2
```

Kita tidak perlu membuka apapun karena banyak _background task_ sistem yang melakukan komunikasi ke server luar.

![Filter src host 192.168.1.2](https://cdn.discordapp.com/attachments/769183322147389460/891294662621544468/unknown.png)

<hr>

## Kendala

Jaringan internet saat hari pengerjaan modul kurang mendukung sehingga kesulitan dalam mendownload file .pcap
