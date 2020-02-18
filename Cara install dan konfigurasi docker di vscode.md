## DOCKER
Docker adalah sebuah aplikasi yang bersifat open source yang berfungsi sebagai wadah/container untuk mengepak/memasukkan sebuah software secara lengkap beserta semua hal lainnya yang dibutuhkan oleh software tersebut dapat berfungsi. Pengaturan software beserta file/hal pendukung lainnya akan menjadi sebuah Image (istilah yang diberikan oleh docker). Kemudian sebuah instan dari Image tersebut kemudian disebut Container.

**Mengenal Docker Workflow**

Dalam praktek dasarnya ada beberapa perintah Docker yang sering digunakan yaitu build, push, pull, run commit.

Perintah-perintah tersebut akan dibahas secara singkat dan akan dilengkapi kemudian saat diperlukan.

Di bawah ini terdapat illustrasi sederhana dari docker worflow – alur kerja docker yang dasar.


**CARA INSTALL DOCKER DI LINUX**


Buka Website *https://hub.docker.com/_/sonarqube/* lalu copy dan paste kan

>docker pull sonarqube

diterminal linux. Maka terminal akan mendownload dan install secara otomatis.

>Setelah itu instal Dockernya. sudo apt-get install docker

Lalu, cek dockernya apa sudah terinstall atau belum.

>docker --version

Untuk menjalankan dockernya, tuliskan

>systemctl start docker
>systemctl status docker

untuk menghentikannya 
>systemctl stop docker



