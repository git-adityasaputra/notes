20200205 GIT BASIC
==================


**GIT BASIC**
---------

**Git** adalah salah satu tool yang sering digunakan dalam proyek pengembangan software. Git bahkan menjadi tool yang wajib dipahami oleh programmer, karena banyak digunakan di mana-mana.

Server GIT kalau diUser Interface (UI) konfigurasinya menggunakan username dan password. Kalau menggunakan command prompt melalui sertifikat. Contohnya menggunakan SSH

Jika kita menggunakan SSH Key, kita tidak perlu lagi mengisi username dan password.
SSH Key adalah metode alternatif untuk autentikasi ke Gitlab. SSH Key cukup kita buat satu kali dan bahkan bisa digunakan lagi di tempat lain seperti GIthub dan Bitbucket.

SSH Key sendiri ada 2 yaitu :
	- SSH Private yang tidak bisa dishare keserver GIT 
 	- SSH Public yang bisa dishare keserver git

Langkah 1 membuat SSH Key untuk Gitlab:

1. Buka Terminal jika anda menggunakan Linux, buka command prompt jika anda menggunakan Windows.
2. Generate sebuah kunci ED25519 SSH :
       'ssh-keygen -t ed25519 -C "email@example.com"'
3. Kemudian buat directory config

 	'touch config'

   Isi config dengan
 	'Host git.enigmacamp.com'
 	'HostName git.enigmacamp.com'
 	'User git'
 	'IdentityFIle ~/.ssh/git_enigma_ed25519'
4. lalu kopikan ssh public ke website git.enigma
 	
5. coba tes koneksi dengan mengetik
 	'ssh -T git@git.enigmacamp.com'


Langkah 2 Membuat Respository
1. Pembuatan repositori dapat dilakukan dengan perintah git init nama-directory. 

Contoh: 'git init folder1'

Perintah tersebut akan membuat direktori bernama folder1. Kalau direktorinya sudah ada, maka Git akan melakukan inisialisasi di dalam direktori tersebut.
Perintah git init akan membuat sebuah direktori bernama .git di dalam proyek kita. Direktori ini digunakan Git sebagai database untuk menyimpan perubahan yang kita lakukan.


**PERINTAH – PERINTAH GIT COMMANDS**
-------------------------------------


1.git config

git config untuk mengatur email dan username:

'git config --global user.email didit@email.com'
2. git init
Ini digunakan untuk membuat repository baru. git init [nama foldernya]
'git init [nama foldernya]'

3. git status
Perintah ini digunakan untuk melihat status dari git kita. 
'git status'

4. git add
Dalam git itu ada 3 area dalam proses pengerjaanya mengerjakan.
    1. Working area – area yang belum di add 
    2. Staging area – area yang sudah di add dan siap di commit 
    3. Repository area – area yang sudah di commit 
Misalnya kita membuat file baru dalam repository nah file baru tersebut akan masuk ke working area dahulu sebelum kita melakukan git add caranya dengan!

'git add [namafile]'

Jika kita ingin memindahkan semua yang ada di working area ke staging area kita bisa memasukan perintah

'git add .'
Titik akhir menandakan stagging area.

5.git commit
Untuk meyimpang ke repository dengan perintah!

'git commit -m "isi aja terserah"/'

6. git log
Untuk menampilkan daftar commit yang sudah dibuat perintahnya!

'git log'

**Perintah Git Untuk Gitlabs Enigma**
------------------------------------------

1.git clone
Ini digunakan biasanya untuk mengcopy projeck kita yang ada di githu. Perintahnya sebagai berikut
'git clone [url repository gitlabs nya]'

2.git push
Biasa digunakan untuk mengupdate project yang ada di gitlabs dari git. Untuk melakukan push bisa diawali dengan mengclone terlebih dahulu lalu jika project kita sudah diubah kita bisa mengubahnya juga di gitlabs dengan printah!

**Git push**

untuk push remote dari local ke server

'git push origin master'

3.git pull
Ini adalah kebalikan dari git push kalo push untuk mengupdate project kita yang ada digitlabs. Kalo git pull untuk mengupdate project kita yang ada di local yang sudah di clone. Perintahnya!

'Git pull'