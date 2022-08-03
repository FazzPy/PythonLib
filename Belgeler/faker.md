# Python Faker Kütüphanesi

**pip install faker**

**conda install -c conda-forge faker**

*Kodlar*

```python
from faker import Faker

fake = Faker()
print (fake.email())
print(fake.country())
print(fake.name())
print(fake.text())
print(fake.latitude(), fake.longitude())
print(fake.url())

```
*Output*

```
russellprice@example.com
Gibraltar
Eric Steele
Next whose significant deal sign president detail. Sit soldier teacher wall.
Realize either ball eye piece including glass.
Mission whatever memory. Ten also page form manage class.
-74.9016695 -75.622414
http://www.rojas.info/
```

**Uygulama 1 : Öğrenci adı, adresi, konum koordinatları ve öğrenci rulo numarasını içeren students.json adıyla 100 öğrenciden oluşan bir json oluşturun.**

```python
from faker import Faker 
import json        
from random import randint     
  
fake = Faker() 
  
def input_data(x): 
    student_data ={} 
    for i in range(0, x): 
        student_data[i]={} 
        student_data[i]['id']= randint(1, 100) 
        student_data[i]['name']= fake.name() 
        student_data[i]['address']= fake.address() 
        student_data[i]['latitude']= str(fake.latitude()) 
        student_data[i]['longitude']= str(fake.longitude()) 
    print(student_data) 
  
    # Sözlük json dosyasına json olarak atıldı.
    with open('students.json', 'w') as fp: 
        json.dump(student_data, fp) 
      
  
def main(): 
  
    # Öğrenci sayısını girin
    # Yukarıdaki görev için bunu 100 yapın.
    number_of_students = 10 
    input_data(number_of_students) 
main() 
```

**Output :**

```
{0: {'id': 59, 'name': 'Charles Jordan', 'address': '19069 Michael Estate\nPort Timothyburgh, UT 15356', 'latitude': '-84.5101905', 'longitude': '16.428351'}, 1: {'id': 85, 'name': 'Benjamin Barry', 'address': 'USCGC Rivera\nFPO AE 40779', 'latitude': '25.264988', 'longitude': '-17.723829'}, 2: {'id': 9, 'name': 'Ricardo Cole', 'address': '0463 Juan Mountain\nPort Alexandriaberg, IN 49730', 'latitude': '-20.9764305', 'longitude': '103.247297'}, 3: {'id': 41, 'name': 'Linda Aguirre', 'address': '6113 Vargas Lock Apt. 692\nNew Jameshaven, ND 55990', 'latitude': '88.767454', 'longitude': '-119.315646'}, 4: {'id': 62, 'name': 'Katherine Buchanan', 'address': '602 Cynthia Falls Suite 027\nMossberg, AR 53328', 'latitude': '-64.1769195', 'longitude': '151.657125'}, 5: {'id': 100, 'name': 'Wesley Morgan', 'address': '310 Robertson Parks\nLake Sharon, SC 37445', 'latitude': '80.610692', 'longitude': '-140.127613'}, 6: {'id': 95, 'name': 'David Morales', 'address': '5813 Carla Ways\nLake Matthew, AZ 64019', 'latitude': '84.3397215', 'longitude': '148.829338'}, 7: {'id': 43, 'name': 'Susan Fernandez DDS', 'address': 'USCGC Simpson\nFPO AP 63444', 'latitude': '-67.791486', 'longitude': '111.859099'}, 8: {'id': 14, 'name': 'Jessica Lester', 'address': '5871 Gloria Locks Apt. 297\nRodriguezfurt, DE 67211', 'latitude': '-25.1194695', 'longitude': '111.922430'}, 9: {'id': 32, 'name': 'Jared Rodriguez', 'address': 'USNV Lambert\nFPO AA 57511', 'latitude': '74.406914', 'longitude': '99.022473'}}
```

**Uygulama 2 : Hintçe olarak 10 adet rastegele isim yazdırın.**

```python
from faker import Faker 
  
#'hi_IN' changed the language
fake = Faker('hi_IN')      
  
for i in range(0, 10): 
    print('Name->', fake.name(),
          'Country->', fake.country())
```

**Profil oluşturmak : **

```python

import faker from Faker
fake = Faker()
print(fake.profile())
```
