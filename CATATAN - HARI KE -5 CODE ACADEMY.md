# CATATAN HARI KE - 5 ENIGMACAMP PAMULANG

**LAMDA EXPRESSIONS**



```java
public class coba{
    public static void printLine(int col){
        for (int i = 0; i < col; i++) {
            if (i == 0){
                System.out.print("");
            }
            System.out.print("---+");
        }
        System.out.println();
    }

    public static void printLLine(int col){
        for (int i = 0; i < col; i++) {
            if (i == 0){
                System.out.print("|");
            }
            System.out.print("   |");
        }
        System.out.println();
    }
    public static void main(String[] args){
        int row = 2, col =3;

        for (int i = 0; i < row; i++) {
            if (i == 0){
                    printLine(col);
            }
            printLLine(col);
            printLine(col);
        }
    }
}



//public class coba{
//    public static void main(String[] args){
//        int size = 3;
//
//        for (int row = 0; row < size; row++) {
//            for (int s = 0; s < size - 1 - row; s++) {
//                System.out.print(" ");
//            }
//            for (int i = 0; i < row + 1; i++) {
//                if (i > 0){
//                    System.out.print(" ");
//                }
//                System.out.print("*");
//            }
//            System.out.println();
//        }
//    }
//}

//public class coba {
//
//    public static int countNumberInArray(int[] arr, int n){
//        int count = 0;
//        for (int i : arr){
//            if (i == n){
//                count++;
//            }
//        }
//        return count;
//    }
//    public static void main(String[] args){
//        int[] numbers = {29, 10, 14, 37, 14};
//        int result = countNumberInArray(numbers, 14);
//        System.out.println(result);
//
//    }
//}



//public class coba {
//    public static void main(String[] args) {
//        int[] a = {5,3,7,0,1,6};
//
//        System.out.println("Array Sebelum Di Sort : ");
//        for(int x = 0; x<a.length; x++) {
//            System.out.print(" "+a[x]);
//        }
//        System.out.println();
//        System.out.println("Array Sesudah Di Sort : ");
//        for(int i = (a.length-1); i>0; i--) {
//            for(int j = 0; j<i; j++) {
//                if(a[j]>a[(j+1)]) {
//                    int temp = a[(j+1)];
//                    a[(j+1)] = a[j];
//                    a[j] = temp;
//                }
//            }
//        }
//        for(int x = 0; x<a.length; x++) {
//            System.out.print(" "+a[x]);
//        }
//    }
//}
```
