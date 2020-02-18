## JUNIT 5

```java

package com.enigma.testing;

import org.junit.Test;
import org.junit.runner.MethodSorters;
import.org.junit.Before;
import org.junit.FixMethodOrder;

public class SquareTest {
	@Test
	public void perimeterShouldEquals(){
		Square shape =new Square(10);
		Assert.assetEquals(40, shape.perimeter(), 0));
		System.out.println("init");	
		}
		
		@Test
		public void areaShouldEquals(){
		Asser.assertEquals(100, shape.area(), 0);
		
		System.out.println("areaShouldEquals");
		}
		
		@After
		public void after(){
		shape = null;
	}
}


//Menampilkan Error

		@Test(timeout = 500)
		public void ShouldNotTImeout ()throws Exception {
			Thread.sleep(1000); //menunda sebuah proses
		}

		@Test 
		public void perimeterShouldEquals() throws Exception {
		Square shape =new Square(10);
		Assert.assetEquals(40, shape.perimeter(), 0));
		System.out.println("init");	
		}
		
		@Test
		public void areaShouldEquals() throws Exception {
		Asser.assertEquals(100, shape.area(), 0);
		
		System.out.println("areaShouldEquals");
		}
		
		@After
		public void after(){
		shape = null;
	}
	
```

**ASSERT STATEMENT**

Junit Assert apasih?
Jadi junit assert sendiri fungsinya untuk menentukan status lulus atau gagalnya dari sebuah kasus uji/sebuah project yang ingin di uji.

Ada berbagai jenis pernyataan didalam assert junit seperti Boolean, Null, Identical dll.

Assert itu class dari JUNIT yang menyediakan banyak metode pernyataan berguna dalam menulis kasus uji dan untuk mendeteksi kegagalan tes.

Contoh Implementasinya :

```java
package com.enigma.testing.shape;

import org.junit.*;

@RunWith(Parameterized.class)
public class SquareTest {
    private Square shape;


    @Parameter(0)
    double side;

    @Parameter(1)
    double result;

    @Parameter
    public static List<Double[]> data () {
        Double[] [] data = new Double[] [] {{5.0, 20.0}, {10.0, 40.0}, {50.0, 200.0}};
    }

    @Before
    public void init () throws Exception {
        shape = new Square(side);

        System.out.println(" init: " + side);
    }

    @Test
    public void perimeterShouldEquals() throws Exception {
        Square shape = new Square(side);
        Assert.assertEquals(result, shape.perimeter(), 0);
        System.out.println("perimeterShouldEquals : " + side);
    }

    @Test
    public void areaShouldEquals () throws Exception {
        Square shape = new Square (side);
        Assert.assertEquals(area, shape.area(), 0);

        System.out.println("areaShouldEquals: " + side);
    }
    @After
    public void done() {
            shape = null;
    }
}
```


*

## Migrating to the New Java 8 Date Time API

```java
package com.enigmacamp;
import java.util.*;

public final class Application {
    public static void main(String[] args){
        // Date data = new Date();
        
        // long now = System.currentTimeMillis();
        // System.out.println(now);

        // Thread.sleep(500);

        // long afterNow = System

    //     DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");
    //     DateTimeFormatter formatter2 = DateTimeFormatter.ofPattern("yyyy-MM-dd");


    //     LocalDate now = LocalDate.now();
    //     DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");
    //     System.out.println(formattedDate);

    //     String formattedDate = now.format(formatter);
    //     System.out.println(formattedDate2);

    //     LocalDate parsedDate = LocalDate.parse(formattedDate, formatter);
    //     System.out.println(parsedDate);

        BigInteger i = BigInteger.valueOf(Long.MAX_VALUE);
        BigInteger i2 = i.add(BigInteger.ONE);
        System.out.println(i2);

        BigDecimal d = new BigDecimal("0");
        System.out.println(d);

    }
}

```

## GIT ADVANCED

git fetch = Nyari update aja. untuk memastikan ada update'an atau nggak. 

setelah itu baru bisa

>git pull

>git add .

>git commit -m "[temp] Create sample.files."


change your text or data

>git merge tool

>git rebase 
>git add .
>git rebase --continue

git stash 

>git stash

>git pull

>git stash pop

