# Fazz | Python MySql Notları

> pip install mysql-connector-python
> pip install mysql-connector<br>

**Not : Bunlar benim notlarımdır daha fazla öğrenmeniz için en alta kaynaklar bıraktım.**


```python
import mysql.connector

# MySql Download : https://www.mysql.com/products/community/
# Kurulum Videosu : https://www.youtube.com/watch?v=Dr_cdBFWVnY

"""
İNDİRME NOTLARI :

Sadece MySql Server ve Workbench indirmeniz yeterlidir. 
Veri ekleme tablo oluşturma ve yazılım işleri arayüzden halledilebilir.


"""

# MySql Çalışma [1]


mydb = mysql.connector.connect(
    host = "localhost", # SERVER IP ADDRESS
    root = "root", # KULLANICI ADI ROOT USER
    password = "mysql1234" # ROOT USER ŞİFRESİ
    # ÖZEL DATABASE KULLANMAK İSTERSEK : ( database = "mydatabase" )   
)

# VERI TABANI OLUŞTURUR

mycursor = mydb.cursor()

mycursor.execute("CREATE DATABASE mydatabase")

# TÜM VERI TABANLARINI GÖSTERİR

mycursor.execute("SHOW DATABASES") 

for x in mycursor:
    print(x)
    
# CUSTOMERS ADLI TABLOYU OLUŞTURUR

mycursor.execute("CREATE TABLE customers (name VARCHAR(255), address VARCHAR(255))")


```

```python

import mysql.connector

# MySql Çalışma [2]

mydb = mysql.connector.connect(
    host = "localhost", # SERVER IP ADDRESS
    root = "root", # KULLANICI ADI ROOT USER
    password = "mysql1234", # ROOT USER ŞİFRESİ
    database = "schooldb", # schooldb veritabanını seçiyoruz
)

mycursor = mydb.cursor()

# Veri ekleme fonksiyonu

def insert():
    sql = "INSERT INTO Products(name, price, imageUrl, description) VALUES(%s,%s,%s,%s)"
    values = ("Samsung S5", 1000, "img.png", "Telefon satışı")
    mycursor.execute(sql, values)
    
    try:
        mydb.commit()
    except mysql.connector.Error as err:
        print("Hata : "+err)
    finally:
        mydb.close()
        print("Database bağlantısı kapandı.")   


```

```python

import mysql.connector

# MySql Çalışma [3]

mydb = mysql.connector.connect(
    host = "localhost", # SERVER IP ADDRESS
    root = "root", # KULLANICI ADI ROOT USER
    password = "mysql1234", # ROOT USER ŞİFRESİ
    database = "mydatabase", # VERİTABANI SEÇİMİ
)

mycursor = mydb.cursor()

# TÜM VERİLERİ GETİRİR.

def Select():
    mycursor.execute("Select * From Products")
    
    result = mycursor.fetchall
    
    for product in result:
        print(product)
    
    print("======================================")
    
    for product in result:
        # PRODUCT TABLOSUNDAKİ NAME VE PRİCE KOLONLARINI GETİRİR
        
        print(f"Name : {product[1]} | Price : {product[2]}")
        
def Select2():
    # YİNE SADECE NAME VE PRİCE KOLONLARINI GETİRİR
    # BU SEFER BULDUĞU İLK KAYDI GETİRİR
    
    mycursor.execute("Select name,price From Products")
    
    result = mycursor.fetchone()
    
def Select3():
    # WHERE SORGUSUNU KULLANARAK İD'Sİ 1 OLANI GETİRİR
    
    mycursor.execute("Select * From Products Where id=1")
    
    # WHERE SORGUSU İLE İSMİ SAMSUNG S8 VE FİYATI 3000 VEYA DAHA DÜŞÜĞÜ OLANI GETİRDİK
    
    mycursor.execute("Select * From Products Where name='Samsung S8' and price=<3000")
    
    # WHERE SORGUSU İLE İSİMLERİN İÇİNDE SAMSUNG GEÇENLERİ VERİR.
    
    # EĞER SADECE BAŞINA % KOYARSAK BAŞI SAMSUNG SONU NE OLURSA OLSUN DEMEKTİR.
    
    mycursor.execute("Select * From Products Where name LIKE '%Samsung%' ")
    
    result = mycursor.fetchall()

```

```python

import mysql.connector

# MySql Çalışma [4]

mydb = mysql.connector.connect(
    host = "localhost", # SERVER IP ADDRESS
    root = "root", # KULLANICI ADI ROOT USER
    password = "mysql1234", # ROOT USER ŞİFRESİ
    database = "mydatabase", # VERİTABANI SEÇİMİ
)

mycursor = mydb.cursor()

def Alignment():
    # İSİME GÖRE SIRALAMA YAPAR
    
    # ORDER BY ID İLE ID SIRALAMASI YAPAR
    
    mycursor.execute("Select * From Products Order By name")
    
    result = mycursor.fetchall()
    
    for product in result:
        print(f"ID : {product[0]} Name : {product[1]} Price : {product[2]}")
        

def Aggregate():
    # HESAPLAMA FONKSİYONLARI
    
    sql = "Select COUNT(*) From Products" # KOLON SAYISINI VERIR
    
    sql1 = "Select AVG(Price) From Products" # TÜM SAYILARIN ORTALAMASINI VERIR
    
    sql2 = "Select SUM(Price) From Products" # TÜM SAYILARI TOPLAR
    
    sql3 = "Select MIN(Price) From Products" # MINIMUM DEĞERİ GÖSTERİR
    
    sql4 = "Select MAX(Price) From Products" # MAXIMUM DEĞERİ GÖSTERİR      
    
    mycursor.execute(sql)
    
    result = mycursor.fetchone
    
    print(f"ID : {result[0]} Name : {result[1]} Price : {result[2]}")


```

```python

import mysql.connector

# MySql Çalışma [5]

mydb = mysql.connector.connect(
    host = "localhost", # SERVER IP ADDRESS
    root = "root", # KULLANICI ADI ROOT USER
    password = "mysql1234", # ROOT USER ŞİFRESİ
    database = "mydatabase", # VERİTABANI SEÇİMİ
)

mycursor = mydb.cursor()

def Update():
    # 5 VEYA 6 IDLİ VERİLERİN İSİMLERİNİ Samsung S10 yapar
    # mycursor.rowcount Değiştirilen, eklenen vs. verilerin sayısını verir.
    
    sql = "Update products Set name='Samsung S10' where id=5 or id=6"
    
    mycursor.execute(sql)
    
    try:
        mydb.commit()
        print(f"{mycursor.rowcount} tane kayıt güncellendi.")
    except mysql.connector.Error as err:
        print("Hata : ", err)
    finally:
        mydb.close()
        print("Database bağlantısı kesildi.")
        
        
def Delete():
    sql = "delete from products" # PRODUCTS TABLOSUNUN TÜM KAYITLARINI SİLER
    
    sql = "delete from products where id=6" # IDsi 6 OLAN VERİYİ SİLER
    
    mycursor.execute(sql)
    
    try:
        mydb.commit()
        print(f"{mycursor.rowcount} tane kayıt silindi.")
    except mysql.connector.Error as err:
        print("Hata : ", err)
    finally:
        mydb.close()
        print("Database bağlantısı kesildi.")

```

Kaynaklar :<br>
https://en.wikipedia.org/wiki/MySQL<br>
https://kerteriz.net/python-ile-mysql-veritabani-baglantisi-ve-islemleri/<br>
https://www.youtube.com/watch?v=09gyEOC2AVE<br>
https://www.btkakademi.gov.tr/portal/course/sifirdan-ileri-seviye-python-programlama-5877<br>
