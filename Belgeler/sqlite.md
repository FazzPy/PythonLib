# Veri Tabanı

## Sqlite Kütüphanesi

>**Kurulum*<br>
>Windows : **pip install db-sqlite3**<br>
>Linux : **pip3 install db-sqlite3**<br>

**Aşağıdakiler benim notlarımdır en altta daha faza öğrenebileceğiniz kaynaklar koydum.**<br>

```python
import sqlite3 as sql

conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
print("Bağlantı Gerçekleştirildi")


cursor = conn.cursor() #Cursor Oluşturur
print("Cursor Oluşturuldu")

cursor.execute("CREATE TABLE IF NOT EXISTS STUDENTS(name text, lastname text, age integer)") #Tablo oluşturur
print("Tablo Oluşturuldu")

#Tablo Silmek : cursor.execute("DROP TABLE IF EXISTS STUDENTS") Not: STUDENTS Tablo ismi

cursor.execute("DROP TABLE STUDENTS")
print("Tablo Silindi")



conn.commit() #Değişiklikleri kaydeder
conn.close()  #Database ile bağlantımızı keser

```

```python
conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
print("Bağlantı Gerçekleştirildi")


cursor = conn.cursor() #Cursor Oluşturur
print("Cursor Oluşturuldu")

ekleme = "INSERT INTO STUDENTS VALUES{}"
data1 = ('Fazz', 'Tech', 41)

cursor.execute(ekleme.format(data1))



conn.commit() #Değişiklikleri kaydeder
conn.close()  #Database ile bağlantımızı keser

```

```python
conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
print("Bağlantı Gerçekleştirildi")


cursor = conn.cursor() #Cursor Oluşturur
print("Cursor Oluşturuldu")


datas = [("Selam", "Ben", 38), ("Fazz", "Cok", 35), ("iyiyim", "he", 21)]

ekleme = "INSERT INTO STUDENTS VALUES{}"

for data in datas:
    cursor.execute(ekleme.format(data))



conn.commit() #Değişiklikleri kaydeder
conn.close()  #Database ile bağlantımızı keser
```

```python

def ekle(name, lastname, age):
    conn = sql.connect("Calisma.db") #Databaseye bağlanır
    cursor = conn.cursor() #Cursor oluşturur

    ekleme = "INSERT INTO STUDENTS VALUES{}" #Veri ekleme komutu
    data = (name, lastname, age) #Veriler
    cursor.execute(ekleme.format(data))#Verileri yürütür ve kaydeder
    conn.commit() #Kaydeder
    conn.close() #Bağlantıyı keser.
    print("Başarılı!")

ekle("Fazz", "Tech", 16) #Fonksiyonu çağırır ve verileri yazar.

```

```python

conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
print("Bağlantı Gerçekleştirildi")


cursor = conn.cursor() #Cursor Oluşturur
print("Cursor Oluşturuldu")


cursor.execute("UPDATE STUDENTS SET lastname= 'Rüzgar' WHERE name = 'Simay' ") #Verileri güncelleme komutu
print("Güncelleme Başarılı!")

cursor.execute("UPDATE STUDENTS SET lastname= 'Işık' WHERE name = 'Batın' AND lastname = 'Ölez' ")
#Verileri günceller fakat aynı isimde başka veriler olabileceğinden hangi verinin değiştirileceği için soyadı yazdık.
print("Güncelleme Başarılı!")

cursor.execute("UPDATE STUDENTS SET lastname= 'Ateş' WHERE rowid = 6") #Satır numarası ile veri güncelleme
print("Güncelleme Başarılı!")

cursor.execute("UPDATE STUDENTS SET age = age+1 WHERE age > 16") #Yaşı 16'dan büyük olanların yaşını 1 arttırır
print("Güncelleme Başarılı!")


conn.commit() #Değişiklikleri kaydeder
conn.close()  #Database ile bağlantımızı keser

```

```python

# cursor.execute("DELETE from STUDENTS WHERE lastname = 'Veli' or lastname = 'Işık' ") #Soyadı Veli ve Işık olan verileri siler
print("Silme işlemi yapılıyor...")

def delete_age(age):
    conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
    print("Bağlantı Gerçekleştirildi")

    cursor = conn.cursor() #Cursor Oluşturur
    print("Cursor Oluşturuldu")

    silKomutu = "DELETE from STUDENTS WHERE age = {}" # Veri tabanından silme komutu

    cursor.execute(silKomutu.format(age)) #Yaşı siler.

    conn.commit() #Değişiklikleri kaydeder
    conn.close()  #Database ile bağlantımızı keser

delete_age(42)
print("Silme işlemi tamamlandı!")

```

```python
def delete_name(name):
    conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
    print("Bağlantı Gerçekleştirildi")

    cursor = conn.cursor() #Cursor Oluşturur
    print("Cursor Oluşturuldu")

    silKomutu = "DELETE from STUDENTS WHERE name = '{}'" # Veri tabanından silme komutu

    cursor.execute(silKomutu.format(name)) #Yaşı siler.

    conn.commit() #Değişiklikleri kaydeder
    conn.close()  #Database ile bağlantımızı keser

delete_name("Roket")
print("Silme işlemi tamamlandı!")
```

```python

conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
print("Bağlantı Gerçekleştirildi")

cursor = conn.cursor() #Cursor Oluşturur
print("Cursor Oluşturuldu")

'''
Notlar :

name ve lastname yerine * koyarsak hepsini almış oluruz.

cursor.execute(" * from STUDENTS WHERE age >= 40") # 40 Yaşındakileri veya büyükleri alır.

cursor.execute(" * from STUDENTS WHERE NOT age >= 40") #40tan büyük veya eşit olmayanları alır.

list_all = cursor.fetchone() #ilk satırdakini alır altına bir daha yazarsak 2.yi alır

many = cursor.fetchmany(3) #ilk 3 elemanı alır  

'''

cursor.execute(" SELECT name, lastname from STUDENTS ")

list_all = cursor.fetchall()

for student in list_all:
    print(student)


#Fonksyion ile yazımı

def print_all():
    conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
    print("Bağlantı Gerçekleştirildi")

    cursor = conn.cursor() #Cursor Oluşturur
    print("Cursor Oluşturuldu")

    cursor.execute(" SELECT * from STUDENTS ")
    tüm_liste = cursor.fetchall()

    for satir in tüm_liste:
        print(satir)

    conn.close()


#Hepsini yazdırma işlemi

cursor.execute(" SELECT rowid, * from STUDENTS ")

list_all = cursor.fetchall()

for student in list_all:
    print(student)



conn.commit() #Değişiklikleri kaydeder
conn.close()  #Database ile bağlantımızı keser

```

```python
conn = sql.connect("Calisma.db") #Database oluşturur veya bağlantı kurar
print("Bağlantı Gerçekleştirildi")

cursor = conn.cursor() #Cursor Oluşturur
print("Cursor Oluşturuldu")

'''
Notlar :

Güncelleme ve değiştirme kodu : UPDATE STUDENTS SET age = 17 WHERE name = 'Simay' 

Silme kodu : DELETE from STUDENTS WHERE name = 'Simay'

Ekleme kodu : INSERT INTO STUDENTS VALUES

Tablo oluşturma kodu : CREATE TABLE IF NOT EXISTS STUDENTS(name text, lastname text, age integer)

Tablo silme kodu : DROP TABLE STUDENTS

Tablo oluşturma kodu 2 : CREATE TABLE CALISANLAR(id integer PRIMARY KEY, ad text, soyad text, maas integer)

Veri ekleme 2 : INSERT INTO CALISANLAR(ad,soyad,maas) VALUES(?, ?, ?) | cursor.executemany(add_command, datas)

Ekrana Yazdırma : cursor.execute("SELECT * FROM CALISANLAR") | list_all = cursor.fetchall()
Ekrana Yazdırma For döngüsü : for calisan in list_all:
                                  print(calisan)
                                
Belirli isimlerin var olup olmadığını öğrenme : SELECT * FROM CALISANLAR WHERE ad IN ('demet', 'Burak', 'Deniz', 'Batın')

Maaşı 1500 ile 3000 arası gösterir : SELECT * FROM CALISANLAR WHERE maas BETWEEN 1500 AND 3000

Baş harfler ile arama yapma : SELECT * FROM CALISANLAR WHERE ad LIKE 'Ba%' "

Tablo listeleme : cursor.execute("SELECT name from sqlite_master WHERE type = 'table' ") | tables = cursor.fetchall()

Tablo listeleme for döngüsü : for table in tables: print(table)

'''

cursor.execute("SELECT name from sqlite_master WHERE type = 'table' ")
tables = cursor.fetchall()


for table in tables:
    print(table)

conn.commit() #Değişiklikleri kaydeder
conn.close()  #Database ile bağlantımızı keser
```
**Benim notlarım buraya kadardı daha fazla öğrenmek için aşağıda verdiğim kaynakları ve eğitimlere göz atabilirsiniz...**<br>

[YouTube](https://www.youtube.com/watch?v=ncwGmoLoTq0&list=PL6aO3uebmKiF_IxQUyNhgQShKcq5epKVy)<br>
[İstihza](https://python-istihza.yazbel.com/standart_moduller/sqlite.html)<br>
[info4idea](https://info4idea.com/python-notlarim-8-sqlite-kullanimi/)<br>
[ichi.pro](https://ichi.pro/tr/sqlite-kullanarak-python-da-veritabanlari-ile-programlama-84579699727033)

**Fazz iyi yazılımlar diler...**
