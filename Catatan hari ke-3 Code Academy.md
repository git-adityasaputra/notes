# CATATAN HARI KETIGA
**LOOPING HURUF**

```java
package id.code.codeacademy;
class Kelas {
    static int sampleSize(int value){
        return value;
    }
    public static void main (String [] args){
            args = new String []{"10"};
            int size = Integer.parseInt(args[0]);
            int counter = 0;
            for (int row = 0; row < size; row++) {
                for (int col = 0; col <= row; col++) {
                    if (++counter > 9) {
                        counter = 0;
                    }
                    System.out.print(++ counter);
                }
                System.out.println();
        }      
    }
}
```

**RECURSIVE**

```java
package id.code.codeacademy;
class Kelas {
    static int squareRootWithoutRecursive(int a, int b){ // untuk menyimpan angka nilai dgn pangkat nya
        int result = a;
        for (int i = 0; i < b; i++) {
            result = result * a;
        }
        return result;
    }
    
    static int squareRoot(int a, int b){
        return b > 0 ? a * squareRoot(a,b - 1): 1; // nilai a = 2 | nilai b dimuali dari : 1 kemudian dikalikan dengan a= 2
    }
    
    /* 
    2 x (5)squareRoot (2,5)
    2 x (4)squareRoot (2,4)
    2 x (3)squareRoot (2,3)
    2 x (2)squareRoot (2,2)
    2 x (1)squareRoot (2,1)
    1
    
    
    */
    public static void main (String [] args){
        int result = squareRoot(2,5);
        System.out.println("Result = " + result);
        
    }
}

/*
Outputnya 32 karna 2 pangkat 5
*/
```
   
**CONSTRAKTOR**

Constraktor sama seperti method 

A class contains constructors that are invoked to create objects from the class blueprint. Constructor declarations look like method declarations—except that they use the name of the class and have no return type. For example, Bicycle has one constructor:

```java
public Bicycle(int startCadence, int startSpeed, int startGear) {

    gear = startGear;
    cadence = startCadence;
    speed = startSpeed;
}

/* Untuk membuat sebuah new objek Bicycle objeknya memanggil myBike, nah si konstruktor akan membuat new operator: */

Bicycle myBike = new Bicycle(30, 0, 8);

/* new Bicycle(30, 0, 8) membuat ruang dalam memori untuk object dan inisiasi sebuah field. */

Although Bicycle only has one constructor, it could have others, including a no-argument constructor:

public Bicycle() {
    gear = 1;
    cadence = 10;
    speed = 0;
}
```

**Arbitrary Number of Arguments**

varargs sebetulnya Array tandanya  <...>
varargs sebagai parameter atau Array itu sendiri.

You can use a construct called varargs to pass an arbitrary number of values to a method. You use varargs when you don't know how many of a particular type of argument will be passed to the method. It's a shortcut to creating an array manually (the previous method could have used varargs rather than an array).

To use varargs, you follow the type of the last parameter by an ellipsis (three dots, ...), then a space, and the parameter name. The method can then be called with any number of that parameter, including none.

```java
public Polygon polygonFrom(Point... corners) {
    int numberOfSides = corners.length;
    double squareOfSide1, lengthOfSide1;
    squareOfSide1 = (corners[1].x - corners[0].x)
                     * (corners[1].x - corners[0].x) 
                     + (corners[1].y - corners[0].y)
                     * (corners[1].y - corners[0].y);
    lengthOfSide1 = Math.sqrt(squareOfSide1);

    // more method body code follows that creates and returns a 
    // polygon connecting the Points
}
```

You can see that, inside the method, corners is treated like an array. The method can be called either with an array or with a sequence of arguments. The code in the method body will treat the parameter as an array in either case.



**Constraktor**

Setiap class setidaknya memiliki satu constaraktor, 

misalnya kita punya 2 class


```java
N n = new N(); // object

class M {
    public M(){
        System.out.println("Called from M.")
    }
}

class N extends{ //extends = cara membuat bahwa si N anaknya dari si M
    int value;
}


```

construktor hanya untuk menyimpan nilai, jangan pernah menyimpan proses di constraktor.