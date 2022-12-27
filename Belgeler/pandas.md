# Veri Bilimi

## Pandas Kütüphanesi

**Pandas kütüphanesi verileri görselleştirmeye ve dataframe haline getirmeye yarar.**<br>

*Kendi notlarımı koyuyorum reponun sonunda işinize yarıyacak kaynaklar vs. bulabilirsiniz.*

>**Kurulum**<br>
>Windows : **pip install pandas**<br>
>Linux : **pip3 install pandas**

<h3>Yeni pandas notları</h3>

```python
import pandas as pd
import numpy as np

Data1 = ["Merve","Yusuf", "Ayşe","Zehra"]

Seri1 = pd.Series(Data1)

print("Pandas Serisi | 1")

print(Seri1)

print("\n")

# ======================================

Seri2 = pd.Series([1,2,3,4])

print("Pandas Serisi | 2")

print(Seri2)

print("\n")

# =====================================

Dizi1 = np.array(['b','i','l','i','ş','i','m'])

Seri3 = pd.Series(Dizi1)

print("Pandas Serisi | 3")

print(Seri3)

print("\n")

# =====================================

Dict1 = {"tr":"Türkiye","fr":"Fransa","de":"Almanya"}

Seri4 = pd.Series(Dict1)

print("Pandas Serisi | 4")

print(Seri4)

print("\n")

# =====================================

# Pandas DataFrame, sütun ve satırlardan oluşan iki boyutlu veri tablolarıdır.
# Axis 0 = index (Satırlar), Axis 1 = Sütunlar

Liste1 = [1,2,3,"a","b","c"]

DataFrame1 = pd.DataFrame(Liste1, columns=["Veriler"])

Liste2 = [['Ali',10],['Ayşe',12],['Mehmet',13]]

DataFrame2 = pd.DataFrame(Liste2,columns=['Ad','Yaş'])

print("Pandas Data Frames | 1, 2, 3, 4")

print(DataFrame1)

print("\n")

print(DataFrame2)

print("\n")

Dict2 =  {'Ad':['Ali', 'Ayşe', 'Mehmet'],'Yaş':[10,12,13]}

DataFrame3 = pd.DataFrame(Dict2)

print(DataFrame3)

print("\n")

Liste3 = [['Mert',16],['Levent',15],['Fazz',16]]

DataFrame4 = pd.DataFrame(Liste3, index=['Ogrenci1','Ogrenci2','Ogrenci3'])

print(DataFrame4)

print("\n")

# =====================================

# Pandas Seri / DataFrame incelemesi

Data2 = np.random.randint(1,100,size=(3,3))

DataFrame5 = pd.DataFrame(Data2, columns=["x1","x2","x3"])

print(f"""

Data Frame İncelemeleri

İnfo : {DataFrame5.info()}

Axes (Satır ve sütun bilgileri) : {DataFrame5.axes()}

Shape (Boyut bilgileri) : {DataFrame5.shape()} 

Ndim (Dataframe boyutu) : {DataFrame5.ndim()}

Size (DF Eleman sayısı) : {DataFrame5.size()}

Values (Eleman değerleri) : {DataFrame5.values()}

Head (DF İlk beş satırı görüntüler) : {DataFrame5.head()}

Tail (DF Son beş satırı görüntüler) : {DataFrame5.tail()}

""")

print("\n")

# =====================================

# Pandas Seri / DataFrame seçimi

d1=np.random.randint(0,100,size=10)
d2=np.random.randint(0,100,size=10)
d3=np.random.randint(0,100,size=10)
d4=np.random.randint(0,100,size=10)

Dict3 = {"seri1":d1,"seri2":d2,"seri3":3,"seri4":d4}

DataFrame6 = pd.DataFrame(Dict3)

# 2 indeks numaralı satırından başlayarak 4 indeks numaralı satıra kadar çeker

print(DataFrame6[2:4]) 

# seri1 sütununu çeker

print(DataFrame6["seri1"])

# seri1'i özellik olarak seçer

Feature1 = DataFrame6.seri1

# Birden fazla  sütunu seçmek

print(DataFrame6[["seri1","seri4"]])

# iloc komutu ile satır seçme

print(DataFrame6.iloc[0])

print(DataFrame6.iloc[1])

# iloc komutu ile sutün seçme

print(DataFrame6.iloc[:, 0])

print(DataFrame6.iloc[:, 1])

print(DataFrame6.iloc[:, -1])

# iloc komutu ile hem satır hem sütun seçme

print(DataFrame6.iloc[0:3])

print("\n")

# Pandas Loc Komutu ile satır seçmek

print(DataFrame6.loc[0])

print(DataFrame6.loc[1])

print(DataFrame6.loc[:,"seri1"])

print("\n")

# =====================================

# Pandas Seri / DataFrame birleştirme

rastgele1=np.random.randint(1,20,size=(4,3))
rastgele2=np.random.randint(20,40,size=(4,3))

DataFrame7 = pd.DataFrame(rastgele1,columns=["x","y","z"])
DataFrame8 = pd.DataFrame(rastgele2,columns=["x","y","z"])

# Concat komutu ile veri birleştirme

# indeks numaralarını düzenlemek için ignore index parametresini kullanırız.

# Sütun adlarına göre birleştirmek için join parametresini kullanırız.

DataFrame8.columns=["x","y","a"]

BirlesikDf = pd.concat([DataFrame7 , DataFrame8], ignore_index=True, join="inner")

print("\n")

sol = pd.DataFrame({
 "anahtar": ["A0", "A1", "A2", "A3"],
 "X": ["X0", "X1", "X2", "X3"],
 "Y": ["Y0", "Y1", "Y2", "Y3"],
 })

sag = pd.DataFrame({
 "anahtar": ["A0", "A1", "A2", "A3"],
 "Z": ["Z0", "Z1", "Z2", "Z3"],
 "T": ["T0", "T1", "T2", "T3"],
 })

# Merge methodu ile DF leri birleştiriyoruz

birlesim = pd.merge(sol, sag, on="anahtar")

print("\n")

# =====================================
```

<h3>Eski pandas notları</h3>

```python

import numpy as np
import pandas as pd


Sozlugum = {"Batın" : 18, "Mert" : 19, "Bedirhan" : 18}

v = pd.Series(Sozlugum)

data = np.random.randn(4,3) # 4 İla 3 arasında rastgele sayılar verir

dataFrame = pd.DataFrame(data) # Veriye dizin ve kolon ismi verir

dataFrame[0] # Data Framenin 0. Kolonunu verir

yeniDataFrame = pd.DataFrame(data, index=["Fazz", "Fazz2", "Fazz3", "Fazz4"], columns=["Maas", "Yas", "Calisma Saati"]) 
#İndex ve kolonların isimlerini belirler

yeniDataFrame[["Maas", "Yas"]] # Maaş ve yaş kolonlarını gösterir

yeniDataFrame.loc["Fazz"] # Fazz indexinin verilerini gösterir

yeniDataFrame["Emeklilik Yasi"] = yeniDataFrame["Yas"] + yeniDataFrame["Yas"] # Yeni bir kolon ekler ve indexini yaşın 2 katı yapar

yeniDataFrame.drop("Emeklilik Yasi", axis=1, inplace=True) 
# Emeklilik yaşı kolonunu siler Axis = 1 ise kolonu siler Axis = 0 ise indexi siler inplace bunu kalıcı yapar

yeniDataFrame[yeniDataFrame > 0] # 0 dan küçük indexleri True diğerlerini False olarak gösterir

yeniDataFrame.reset_index() # İndexleri sıfırlar

indexListesi = [8000, 7500, 7800] # Yeni İndexlerin listesi

# yeniDataFrame["Maas"] = indexListesi # Maaş kolonunun indexlerini indexListesindeki veriler ile değiştirir

# yeniDataFrame.set_index("Maas", inplace=True) #Maas kolonunu ve indexlerini en başa alır

# Multi İndex

ilkİndexler = ["Fazz", "Fazz", "Fazz", "Fazz2", "Fazz2", "Fazz2"]

icİndexler = ["Cokiyi1", "Cokiyi2", "Cokiyi3", "Cokcokiyi", "cokcokiyi2", "cokcokiyi3"]

birlesmisİndexler = list(zip(ilkİndexler,icİndexler)) # ilk İndexleri ve İç indexleri birleştirir

Toplamİndex = pd.MultiIndex.from_tuples(birlesmisİndexler) # Birleşmiş İndexleri Multi İndex yapar

BenimListem = [[40, "A"], [30, "B"], [10, "C"], [9, "D"], [20, "E"], [11, "F"]]

benimNumpyDizim = np.array(BenimListem)

ToplamDataFrame = pd.DataFrame(benimNumpyDizim, index=Toplamİndex, columns=["Yas","Meslek"]) 
# Tüm Listeleri ve ve indexleri toplar ve Multi İndex Yapar

ToplamDataFrame.loc["Fazz"].loc["Cokiyi1"] # İndexinin Cokiyi1 elemanını getirdi

ToplamDataFrame.index.names = ["Fazzlar", "Durum"] # İndexlerin Başlığını belirler

örnekVeri1 = {"İstanbul":[30,29,np.nan], "Ankara":[31,31,29]} #np.nan Boş Satır Olarak gözükür NaN Olarak Gösterilir

örnekVeri1.dropna(axis = 1) #NaN Olan indexleri siler axis = 1 eklersek kolonları alır axis = 0 indexleri alır

örnekVeri1.dropna(axis = 1, thresh=2) #2 Ve üzeri NaN Olanları siler 1 Adet olanlar kalır

örnekVeri1.fillna(20) #Tüm Boş (NaN) Olanları 20 Yapar

GrupObjesi = örnekVeri1.groupby("Ankara")
#Groupby komutu ile tek bir kolon veya index için düzenlemeler yapılabilir veya görüntülene bilir

GrupObjesi.count() #Ankara indexinde kaç sayı olduğunu gösterir

GrupObjesi.mean() #Ankara objesindeki sayıların ortalamasını verir

GrupObjesi.max() #Maximum değerleri verir min() yazarsak minimum

GrupObjesi.describe() #Tüm dönüşümleri yapıp gösterir (count, mean, min, max vs.)

veri1 = {"İsimler" : ["Fazz", "Tech", "Design", "Market"], 
"Sporlar" : ["Koşu", "Yüzme", "Basketbol", "Futbol"],
"Kalori" : [250,220,250,230]}

veri2 = {"İsimler" : ["Selam", "Ben", "Fazz", "Tech"], 
"Sporlar" : ["Pırt", "Yüzdü", "cikcik", "saldı"],
"Kalori" : [31,62,93,124]}

veri3 = {"İsimler" : ["Steve", "Bill", "Mark", "Fazz"], 
"Sporlar" : ["kasmerto", "adam", "bitık", "Cokiyi"],
"Kalori" : [31,31,31,999]}

dataFrame1 = pd.DataFrame(veri1, index=[0,1,2,3])

dataFrame2 = pd.DataFrame(veri2, index=[4,5,6,7])

dataFrame3 = pd.DataFrame(veri3, index=[8,9,10,11])

#Concatenation

concat = pd.concat([dataFrame1, dataFrame2, dataFrame3]) 
#DataFrameleri birleştirir | axis = 1 yazarsak yan yana koyar ve verilerin çoğu NaN Olarak gözükür

#Merge | Birleştirmek

mergeVeri1 = {"İsim" : ["Ahmet", "Mehmet", "Zeynep", "Atıl"],
              "Spor" : ["Koşu", "Yüzme", "Koşu", "Basketbol"],
              }

mergeVeri2 = {"İsim" : ["Ahmet", "Mehmet", "Zeynep", "Atıl"],
              "Kalori" : [500,300,250,150],
              }

mergeDataFrame1 = pd.DataFrame(mergeVeri1)

mergeDataFrame2 = pd.DataFrame(mergeVeri2)

pd.merge(mergeDataFrame1,mergeDataFrame2, on="İsim") 
#on Parametresi hangi kolon üstünden işlem yapıcağımızı belirtir ve bunları birleştirir

veri1 = {"İsim" : ["Atıl", "Zeynep", "Mehmet", "Ahmet"],
        "Departman" : ["Yazılım", "Satış", "Pazarlama", "Yazılım"],
        "Maas" : [200,300,400,500]
        }

dataFrame = pd.DataFrame(veri1)

dataFrame["Departman"].unique() 
#Departman kolonunun elemanlarını verir

dataFrame["Departman"].nunique() 
#Kaç Adet farklı eleman olduğunu gösterir

dataFrame["Departman"].value_counts() 
#Her farklı elemandan kaç adet olduğunu gösterir

dataFrame.isnull() 
#Eksik değer var mı yok mu onu gösterir var ise True yok ise False gösterir

def zam(maas):
    return maas * 0.66

dataFrame["Maas"].apply(zam) 
#Zam fonksiyonunu kullanır ve Maas kolonunun verilerini 0.66 ile çarpar

#Pivot Table

veri1 = {"İsimler" : ["Batın", "Mert", "Levent", "Bedirhan", "Bedirhan"], 
"Sporlar" : ["Koşu", "Yüzme", "Basketbol", "Futbol", "Futbol"],
"Kalori" : [250,220,250,20, 10]}

dataFrame1 = pd.DataFrame(veri1)

dataFrame1.pivot_table(values="Kalori", index=["İsimler", "Sporlar"]) 
# Aynı indexlerin sayılarını bir adet ortalamasını verir

dataFrame1.pivot_table(values="Kalori", index=["İsimler", "Sporlar"], aggfunc=np.sum) 
#Aynı indexlerin değerlerini toplar

# Excel İşlemleri

pd.read_excel("dosya.xlsx")

dataFrame1.to_excel("dosya.xlsx")

dataFrame1.to_csv("dosya.xlsx")
```

**Kendi notlarım bu kadardı aşağıda kullandığım kaynaklar ve aldığım eğitimler mevcuttur.**<br>

[BTK Akademi](https://www.btkakademi.gov.tr/portal/course/veri-bilimi-icin-python-ve-tensorflow-11705)<br>
[Git Hub](https://github.com/atilsamancioglu/BTK-PythonTensorflow)<br>
[Python Git Hub](https://github.com/atilsamancioglu/PythonCourse)<br>
[Medium](https://medium.com/deep-learning-turkiye/adan-z-ye-pandas-tutoriali-ba%C5%9Flang%C4%B1%C3%A7-ve-orta-seviye-4edf0094e0d5)<br>
[Veri Bilimi Okulu](https://www.veribilimiokulu.com/python-pandas-ile-temel-islemler/)<br>
[Muhammed Dincer](https://muhammeddincer.com/pandas-dataframe-ve-kod-ornekleri/)<br>

**Fazz iyi yazılımlar diler...**
