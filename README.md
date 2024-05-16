# Dataframe Pandas🤡
- Pandas เป็น lib ของ python 
- Dataframe คือ Data Structure ที่มีลักษณะคล้ายตาราง excel ที่มี row column เป็นแถวๆรวมกัน
- ซึ่งเราสามารถนำ pandas dataframe มาประยุกต์ใช้ได้หลายอย่างเช่น นำ Data ที่ได้มา clean ก่อนนำไปใช้งาน นำมา plot เป็นกราฟเพื่อใช้เปรียบเทียบได้สะดวก และ จัดระเบียบ data ได้อีกด้วย

วิธีใช้
### python
``` python
import pandas as pd
df = pd.DataFrame({'ID':[1,2,3,4],
              'name':[a,b,c,d]})
```

ตัว ID,name เป็นหัวข้อcolumn
> คำสั่งอื่นๆ
- pd.DataFrame[data,index,columns]
- df.head([int]) เรียกด้านบนของตารางมาดูตาม parameters
- df.loc[row(int)] , df.loc[row(int),col(int)] เรียกดูตาม row กับ col ที่ใส้
- df.loc[row(string)] เรียกดูช่องตาม string

 ### clean data pandas
- df.isnull() เช็คว่ามี data ที่ null รึเปล่า
- df.drop_duplicates(inplace=True) drop แถวที่ซ้ำกัน
- df.drop(columns="[Not_Useful_Column]") drop column ที่ไม่ใช้ ณ ที่นี้คือ column -> "Not_Useful_Column"
- df.dropna(inplace=True) drop แถวที่มี missing value หรือ null
- df.fillna(['']) fill data ที่ null ด้วย ''
- df.sort_values('[Column_that_you_want_to_sort]', ascending = False) ตรง ascending false=มากไปน้อย true=น้อยไปมาก



## เนื้อหาในหัวข้อนี้ ##
- การสุ่มตัวเลขด้วยคลาส Random
- การสุ่มตัวเลขจาก 1-100
- การสุ่มตัวเลขทศนิยม
- เปรียบความแตกต่างของการสุ่มตัวเลขของภาษา Dart , C , Java , Python

 ## การสุ่มตัวเลขด้วยคลาส Random
 คลาส Random ใช้สร้างค่าสุ่มใน Dart จากไลบรารี dart:math เราสามารถสร้างค่า boolean, integer หรือ double สุ่มได้โดยใช้คลาสนี้ ก่อนอื่นต้อง Import dart:math เข้ามาก่อน
 
`Import`
 ```dart    
import 'dart:math';
```

## การสุ่มตัวเลขจากคลาส Random จะมีด้วยกันอยู่ 2 แบบคือ

`แบบที่ 1 Random()`
 ```dart    
Random r1 = new Random();
```
`แบบที่ 2 Random.secure()`
 ```dart    
Random r2 = new Random.secure();
```

### แบบที่ 1 คือ Random([int? seed]) ###
   คือ ตัวสร้าง (constructor) ของคลาส Random ในภาษา Dart ที่ใช้สร้าง random number generator โดยมีพารามิเตอร์ชื่อ seed เป็นค่าทางเลือกที่คุณสามารถระบุได้ พารามิเตอร์ seed นี้ถูกใช้เพื่อกำหนดค่าเริ่มต้นของสถานะ random number generator ซึ่งจะทำให้ค่าที่สุ่มออกมามีลักษณะและลำดับที่สอดคล้องกันหากกำหนด seed

`Example`
 ```dart    
import 'dart:math';

void main() {
   print("\nUsing Random()");
   Random r1 = new Random();
   print(r1.nextInt(100)); //จะทำการสุ่มตััวเลขตั้งแต่ 0-99
}
```
<details>
  <summary><strong>Output</strong></summary>
</details>

```dart  
Using Random()
37
```
   ### แบบที่ 2 คือ Random.secure() 
 คือ Random.secure() ใช้ สร้างrandom number generator ที่มีความสามารถในการสร้างตัวเลขสุ่มที่เหมาะสำหรับการใช้งานทางความปลอดภัย โดยใช้แหล่งเอนโทรปีที่มีความสามารถในการสร้างตัวเลขสุ่มที่มีความสามารถเพิ่มเติมเหมือนในการทำงานเรื่องความปลอดภัย

 `Example`
 ```dart    
import 'dart:math';

void main() {
   print("\nUsing Random.secure()");
   Random r2 = new Random.secure();
   print(r2.nextInt(100));
}
```
<details>
  <summary><strong>Output</strong></summary>
</details>

```dart  
Using Random.secure()
29
```
> เราจะเห็นได้ว่า method nextInt() ที่รับ parameter เป็นจำนวนเต็ม จะทำการสุ่มตัวเลข ตั้งแต่ค่า default ก็คือ 0 จนถึง n-1
>
 ## ❗❗❗ แล้วถ้าเราอยากจะเปลี่ยนค่าเริ่มต้นจะต้องทำยังไง? ❗❗❗ 
 ## การสุ่มตัวเลขจาก 1-100
  โดยปกติแล้วตัวเลขที่ได้จากการสุ่มจากเมธอดทั้งหมดนั้นจะเริ่มต้นจาก 0 ซึ่งนี่เป็นการทำงานพื้นฐานของเมธอด แต่ในการเขียนโปรแกรมจริงนั้น คุณอาจต้องการสุ่มตัวเลขจากช่วงอื่นๆ ยกตัวอย่างเช่น 1 - 10, 1 - 100 หรือ 50 - 100 เป็นต้น ในตัวอย่างนี้ เราจะมาประยุกต์ใช้เมธอดจากตัวอย่างก่อนหน้าเพื่อสุ่มตัวเลขที่มีค่าระหว่าง 1 - 10 , 1 - 100 , 50 - 100   นี่เป็นโค้ดของโปรแกรม
  
 `Example`
 ```dart    
import 'dart:math';

void main() {
   Random r1 = new Random();     //ตัวเลขจำนวนเต็มที่บวกเข้าไปข้างหลังmethod จะเป็นตัวกำหนดค่าเริ่มต้น
   print(r1.nextInt(10)+1);      // สุ่มตัวเลขตั้งแต่ 1-10
   print(r1.nextInt(100)+1);    // สุ่มตัวเลขตั้งแต่ 1-100
   print(r1.nextInt(101)+50); // สุ่มตัวเลขตั้งแต่ 50-100
}
```
<details>
  <summary><strong>Output</strong></summary>
</details>

```dart  
9
55
78
```
> เราจะเห็นได้ว่าหลัง method nextInt() ที่บวกด้วยค่า constant จะเป็นตัวกำหนดค่าเริ่มต้น
> 
> ส่วนค่าใน parameter จะเป็นตัวกำหนดค่าสุดท้ายที่จะสุ่มได้ ถ้าค่าเริ่มต้นคือ 1 และ ค่าสุดท้ายคือ n
>
> range ของเลขที่จะสุ่มคือ [ 0 , n - 1]

## การสุ่มตัวเลขทศนิยม
   การสุ่มตัวเลขทศนิยมเราใช้ method `nextDouble()` ในการสุ่ม

`Example`
```dart    
import 'dart:math';

void main() {
   Random r1 = new Random();
   print(r1.nextDouble()); 
   print(r1.nextDouble()*256);
   print((r1.nextDouble()*(256-250)+250));  
}
```
<details>
  <summary><strong>Output</strong></summary>
</details>

```dart  
0.6221115104341204
176.945116547545
253.53952131205276
```

> เราจะเห็นได้ว่า method nextDouble() ถ้าเราไม่ * ค่าคงที่เข้าไปข้างหลังช่วงที่จะสุ่มได้จะเป็น [0.0 , 1.0)
>
> แต่ถ้าเราทำการ * ค่าคงที่เข้าไปหลัง nextDouble() จะเป็นการกำหนดช่วงค่าสุดท้ายที่จะสุ่มได้ 
> อย่างเช่นตัวอย่าง r1.nextDouble()*256 ช่วงของตัวเลขที่จะสุ่มได้คือ [0.0 , 256.0)
### เปรียบความแตกต่างของการสุ่มตัวเลขของภาษา Dart , C , Java , Python

- ตัวอย่างการสุ่มเลข 0 - 99
  
### Dart
```dart    
import 'dart:math';

void main() {
   Random r1 = new Random();
   print(r1.nextInt(100));
}
```

<details>
  <summary><strong>Output</strong></summary>
</details>

```dart    
40
```

### C
```C  
#include <stdio.h>      
#include <stdlib.h>  
void main()  
{     
   int num;  
   num = rand() % 99
   printf ("%d", num);  
}  
```

<details>
  <summary><strong>Output</strong></summary>
</details>

```C   
65
```

### Java
```Java 
import java.util.Random;
   
public class generateRandom{
   
    public static void main(String args[])
    {
        Random rand = new Random();
        int rand_int1 = rand.nextInt(100);
        System.out.println(rand_int1);
    }
}
```

<details>
  <summary><strong>Output</strong></summary>
</details>

```Java  
99
```
### Python
```Python 
import random
print(random.randint(0,99))
```

<details>
  <summary><strong>Output</strong></summary>
</details>

```Python  
11
```

> ✔️เราจะเห็นได้ว่า ภาษา Dart,C และ Python มีการใช้ Random ที่คล้ายกันคือการรับ parameter ค่าคงที่ที่กำหนดช่วงของค่าสุดท้ายที่สามารถสุ่มได้ ✔️
> 
> ❗❗ แต่ในภาษา C จะต้องนำตัวเลขมา % ข้างหลังเพื่อกำหนดค่าสิ้นสุดที่สามารถสุ่มได้ ❗❗

1.dataframe
2.read csv
3.read json
4.cleaning data 
5.plotting 

## คำสั่งของ Pandas ที่ใช้บ่อยๆ
### การอ่านไฟล์ CSV
#### .read_csv("ชื่อไฟล์")
```Python 
import pandas as pd
data = pd.read_csv('Example.csv')
```




# Pandas - Plotting
  การใช้ dataframe ร่วมกับ matplotib

  
