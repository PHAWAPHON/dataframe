# Dataframe Pandas🤡
- Pandas เป็น lib ของ python 
- Dataframe คือ Data Structure ที่มีลักษณะคล้ายตาราง excel ที่มี row column เป็นแถวๆรวมกัน
- โดย DataFrame จะทีความคล้ายคลึงกับ sql table แต่จะใข้งานง่ายกว่าและมีแนวโน้มที่จะเร็วกว่าจากการที่มีส่วนประกอบจาก python และ numpy มาช่วยในการจัดการ ซึ่งเราสามารถนำ pandas dataframe มาประยุกต์ใช้ได้หลายอย่างเช่น นำ Data ที่ได้มา clean ก่อนนำไปใช้งาน นำมา plot เป็นกราฟเพื่อใช้เปรียบเทียบได้สะดวก และ จัดระเบียบ data ได้อีกด้วย

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
```Python
- df.drop_duplicates(inplace=True) drop แถวที่ซ้ำกัน
```
![dup1](https://github.com/PHAWAPHON/dataframe/assets/141826630/91aff3aa-5d68-4e9c-a604-6c6fe8bf9543)
![dup2](https://github.com/PHAWAPHON/dataframe/assets/141826630/ff5971a4-78a2-48b8-a222-254d60d12fef)

- df.drop(columns="[Not_Useful_Column]") drop column ที่ไม่ใช้ ณ ที่นี้คือ column -> "Not_Useful_Column"
- df.dropna(inplace=True) drop แถวที่มี missing value หรือ null
- df.fillna(['']) fill data ที่ null ด้วย ''
- df.sort_values('[Column_that_you_want_to_sort]', ascending = False) ตรง ascending false=มากไปน้อย true=น้อยไปมาก


## คำสั่งของ Pandas ที่ใช้บ่อยๆ
### การอ่านไฟล์ CSV
#### .read_csv("ชื่อไฟล์")
```Python 
import pandas as pd
data = pd.read_csv('Example.csv')
```
### การดูข้อมูลจากแถวบนสุด
#### .head
```Python 
data.head()
```
### การดูข้อมูลจากแถวล่างสุด
#### .tail
```Python 
data.tail()
```
### การเช็คความผิดปกติใน Data Frame
#### .info()
```Python 
data.info()
```
### การแปลงชนิดของข้อมูล
#### .astype(‘ชนิดของข้อมูลที่ต้องการ’)
```Python 
df['A'] = df['A'].astype(int)
```
### การหาค่า (count, mean ,std ,min ,25% ,50% ,75%, max)ของข้อมูลแต่ละ column
#### .describe()
```Python 
data.describe()
```
### วิธีลบค่าที่เป็นmissing values
#### .dropna()
```Python 
clean_data = data.dropna()
```
### วิธีเช็คข้อมูล ที่เป็น Null
#### .isnull()
```Python 
print(data.isnull())
```
### วิธีเช็คข้อมูล ที่เป็น Null ในไฟล์ทั้งหมด
#### .isnull().sum()
```Python 
data.isnull().sum()
```
### วิธีกรองข้อมูลแบบมีเงื่อนไข
#### .query(‘เงื่อนไขที่ต้องการ’)
```Python 
print(data.query("max_speed<2"))
```
### การ join ขอมูลด้วยคำสั่ง
#### .merge(table1, table2, left_on=”column table1”, right_on=”column table2”, how=”รูปแบบการ join”)
#### รูปแบบการ join นั้นแบ่งออกเป็น

#### ”inner” = innerjoin

#### “outer” = outer join

#### “left” = left join

#### “right” = right join
```Python 
df3 = pd.merge(df,df.T,Left_on="max_speed",right_on="type",how = "inner")
```
### การหาค่า mean, max , sum (aggregate)ทั้ง dataframe
#### .agg()
```Python 
print(data.agg("sum","max",mean))
```
### การหาค่าข้อมูลที่ไม่ซ้ำกันในแต่ละ column
#### .unique()
```Python 
print(data['max_speed'].unique())
```
### การหาข้อมูลที่ซ้ำในตาราง
#### .duplicated()
```Python 
print(data['max_speed'].duplicated())
```
### การแทนค่าข้อมูลในตาราง
#### .replace()
```Python 
df2 = df..replace(1,523)
```
### การเขียนไฟล์
#### .to_csv()
```Python 
data.to_csv("data.csv")
```




# Pandas - Plotting
  การใช้ dataframe ร่วมกับ matplotib
  
## Scatter Plot
```Python 
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('Salaries.csv')

df.plot(kind='bar', x='sex', y='salary')

plt.show()
```

`ผลลัพธ์`
<br>
![My Image](https://camo.githubusercontent.com/f57eaa260faffca4cf03dd6930d41571dadb68d175ac7f4a25bc6fad877b2fbf/68747470733a2f2f696d6775722e636f6d2f3032394c7070792e706e67)
<br>