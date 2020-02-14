# CATATAN HARI KE - 4

```java
package id.code.bootcamp;
public class BelajarMetode {

            public static int bolaPantul(double tinggiAwal){
                double height = tinggiAwal;
                int count = 0;
                while (height >= 1){
                    height *= 0.75;
                    count++;
                }
                return count++;
            }
            
            public static int bolaPantulR(double tinggiAwal){
                return tinggiAwal >= 1 ? bolaPantulR(tinggiAwal * 0.75) + 1 : 0;
            }
    public static void main(String[] args) {
        System.out.println(bolaPantul(4));
        
//        Langkah awal pengerjaan
            // 4 x 0.75
              // dst

//outputnya 5

      }
}

```

THIS 

this itu nilai object, masing2 this menempalkan pada instance nya masing2. This harus dibaris pertama


**CONTROLLING ACCES TO MEMBERS OF A CLASS**

sebuah claas bisa didklasarakan public, puclic bisa di akses dimanapun. Kalau sebuah class tidak ada publicnya. LEVEL Class public dan default. Ini hanya akan nampak di package nya sendiri 


di Level member bisa menggunakan public atau tanpa modifier, ada akses tambah private dan protected. 


| Modifier  | Class | Package  | Subclass | World  |
| ----- | --- | ----- | --- | ----- | 
| public   | y  | y   | y  | y  | 
| protected | y  | y   | y  | n   | 


kalau ada programmer lain menggunakan class kita, akses level bisa menolong kamu akan hal ini. Jadi by default pakailah private 

Contohnya 

```java
public final Int STUDENT(){

}
```

hindari field public kecuali constan
contohnya kalau conts pakai keyword FINAL

```java
public final Int STUDENT(){

}
```

**Class variabel**

Static itu class varibel. kalau static tidak perlu membuat objectnya dulu, jadi dia sudah ada ketika class itu ada. Instance itu ya object. Object itu ya sudah ada namanya. Class member tidak perlu dijadikan object dahulu.

**ANONYMOS CLASS**

Class tanpa ada deklarasi, misal kita punya 

Interface Sample {

}



**CLASS NESTED**


Soal 

Class Bootcamp
 properti contohnya get/set
1. Name
2. Trainees --> (trainee,name,email)
3. metod findTraineeByName
   
    - set Trainees()
    - set trainee(name,index)


penilaian 
logic
design
convention
kebersihan