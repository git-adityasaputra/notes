## CATATAN HARI KE - 8 CODE ACADEMY

**Java Collections Cheat Sheet**
Review

![Gambar teks editor VS Code](https://snippetjournal.files.wordpress.com/2013/11/collections.png?w=700)




**Basic I/O**

Seperti yang kita ketahui, program komputer terdiri dari tiga komponen utama, yaitu: input, proses, dan output.

**IO STREAMS**

Stream merupakan dasar operasi input-output ( I/O ) dalam Java yang menggunakan package java.io sebagai package utama. Stream adalah representasi abstrak dari input dan output device, dimana aliran bytes akan ditransfer seperti file dalam harddisk, file pada sistem remote atau printer.

IO Streams mem reprentasikan source code untuk sebuah output. Stream itu squence dari data. Jadi, sebuah program menggunakan input data dari sumber dalam satu waktu. 

Contohnya :

![Gambar teks editor VS Code](https://docs.oracle.com/javase/tutorial/figures/essential/io-ins.gif)


> dalam kode *System.out.println(" Output ");*
System out : Membaca output dari Sistem Operasi.

**Byte Streams**

Stream itu aliran, aliran apa? aliran data.

```java
// Menampilkan data per Bytes, per karakter (StandarCharset)

package com.day.studies;
import java.io.ByteArrayInputStream;
import java.io.ByteArrayOutputStream;
public class Learnjava {
    public static void main(String[] args) throws Throwable {
        
    String dataIn = "ABCDEFGHIJK";
    ByteArrayInputStream in = new ByteArrayInputStream(dataIn.getBytes());
    ByteArrayOutputStream out = new ByteArrayOutputStream();

    byte[] b = new byte[2]; //jumlah arraynya
    int length;
    while ((length = in.read(b)) != - 1){
        out.write(b, 0, length);
    }
    
    in.close();
    out.flush();
    String dataOut = new String(out.toByteArray());
    out.close();
    
        System.out.println(dataOut);
        
        }   
        
}


> 

//Kita punya output didalam stream yang sudah Bytes.
//Nilai karakter ini 0  sampai 255

```

Pada intinya stream untuk memanipulasi data.

**Using Karakter Stream**
