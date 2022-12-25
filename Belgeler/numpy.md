# Veri Bilimi
## Numpy Kütüphanesi

**Neden numpy kullanılır?**<br>
>*Python’da dizilerin amacına hizmet eden listelerimiz var, ancak işlenmesi yavaştır. NumPy, geleneksel Python listelerinden 50 kata kadar daha hızlı bir dizi nesnesi sağlamayı amaçlamaktadır. NumPy’deki dizi nesnesi (array) ndarray olarak adlandırılır ve ndarray, çalışmayı çok kolaylaştıran birçok destekleyici işlev sağlar. Diziler, hız ve kaynakların çok önemli olduğu veri biliminde çok sık kullanılır.*

**Kurulum**<br>
>**Windows : pip install numpy**<br>
>**Linux : pip3 install numpy**<br>

<h3> Numpy Notlarım - V1 </h3>

```python
# Python | Yapay Zeka Notları

import numpy as np

# Dizi1 = Bir boyutlu dizidir ve veriler int'e dönüştürülmüştür. 

Dizi1 = np.array([1,2,3,4,5], dtype=int)

print(f"Tek boyutlu Dizi 1 : {Dizi1}")

print("\n")

# Dizi2 = İki boyutlu dizidir iki adet farklı liste ile oluşturulur.

Dizi2 = np.array([[1,2,3,4,5], [1,2,3,4,5]])

print(f"İki boyutlu Dizi 2 : {Dizi2}")

print("\n")

# Dizi3 = Üç boyutlu dizidir dört farklı liste ile oluşturulur.

Dizi3 = np.array([[1,2,3], [4,5,6], [1,2,3], [4,5,6]])

print(f"Üç boyutlu Dizi 3 : {Dizi3}")

print("\n")

# Zeros komutu ile sıfırlardan oluşan bir yer tutucu dizin oluşturuyoruz

np.zeros(5)

Dizi4 = np.zeros((4,3), dtype=int)

print(f"Sıfırlardan oluşan int Dizi 4 : {Dizi4}")

print("\n")

Dizi5 = np.ones((4,3), dtype=int)

print(f"Birlerden oluşan int Dizi 5 : {Dizi5}")

print("\n")

Dizi6 = np.full((4,3),10)

print(f"Belirlediğimiz sayılardan oluşan Dizi 6 : {Dizi6}")

print("\n")

# Dizi 7 = bitiş ve artış değerlerinden oluşan dizi oluşturur.

Dizi7 = np.arange(1,30,2)

print(f"Bitiş ve artış değerlerinden oluşan Dizi 7 : {Dizi7}")

print("\n")

# Dizi 8 = Eşit aralıklı sayılardan oluşan diziyi oluşturur.

Dizi8 = np.linspace(0, 10, num=5)

print(f"Eşit aralıklı Dizi 8 : {Dizi8}")

print("\n")

# Dizi 9 ve 10 rastgele sayılardan oluşan dizileri oluşturur.

Dizi9 = np.random.randint(0,10,5)

Dizi10 = np.random.randint(0,10,(4,3))

print(f"Rastgele sayılardan oluşan Dizi 9 : {Dizi9}")

print("\n")

print(f"Rastgele sayılardan oluşan 3 Boyutlu Dizi 10 : {Dizi10}")

print("\n")

# Numpy dizi incelemesi : shape, ndrim, size, dtype ve itemsize komutları ile olur.

Dizi11 = np.array([[1,2,3], [4,5,6]])

Shape = Dizi11.shape

Dizi12 = np.array([1,2,3,4,5])

Ndim = Dizi12.ndim

Dizi13 = np.array([[1,2,3,4], [5,6,7,8]])

Ndim2 = Dizi13.ndim

Size = Dizi12.size

dtype = Dizi12.dtype

itemsize = Dizi12.itemsize

print(f"""

Numpy dizi incelemesi

Shape : {Shape}

Ndim : {Ndim}

Ndim2 : {Ndim2}

Size : {Size}

Dtype : {dtype}

İtemsize : {itemsize}

""")

print("\n")

# Numpy indexleme

Dizi14 = np.array([1,2,3,4])

print("Numpy İndexleme")

print(f"0. İndex : {Dizi14[0]}")

print(f"1. İndex : {Dizi14[1]}")

v1 = Dizi14[2]=99

print(f"2. Değiştirilmiş İndex : {Dizi14[2]}")

print("\n")

Dizi15 = np.array([[1,2,3,4,5], [6,7,8,9,10], [11,12,13,14,15]])

Dizi15[1,2]=99

print(f"""

Dizi 15 İndexleme

İndex 1 : {Dizi15[2][1]}

İndex 2 : {Dizi15[2,1]}

İndex 3 : {Dizi15[1,2]}

""")

Dizi16 = np.array([[[1,2,3], [4,5,6]], [[7,8,9], [10,11,12]]])

Dizi16[1,1,1]=99

print(f"""

3 Boyutlu indexleme

İndex 1 = {Dizi16[0, 1, 2]}

İndex 2 = {Dizi16[1,1,1]}

Negatif indexleme

İndex 1 = {Dizi16[-1, -2, -3]}

""")

print("\n")

# Dilimleme ile verileri çekmek

Dizi17 = np.arange(10, 30)

print("Dizi17 Sonuç : "+Dizi17[0:4])

print("\n")

Dizi18=np.random.randint(0,10,(4,4))

# İkinci satırın tüm sütunlarını seçer

print(Dizi18[1,:])

# ilk iki satırı ile ilk üç sütununu çekme işlemi

print(Dizi18[0:2,0:3])

# ilk iki sütununu çeker

print(Dizi18[:,0:2])

# 4 sayısından büyük değere sahip olanları çeker

print(Dizi18[Dizi18>4])

print("\n")

# NumPy Yeniden boyutlandırma

Dizi19 = np.arange(1,10)

print(Dizi19.ndim)

yeniDizi = Dizi19.reshape(3, 3)

print(f"Yeniden boyutlandırılmış dizi : {yeniDizi}")

yeniDizi2 = Dizi19.reshape(3,3,1)

print(f"Yeniden boyutlandırılmış 3D Dizi : {yeniDizi2}")

yeniDizi2.reshape(-1)

print(f"Yeniden boyutlandırılmış 3D to 2D Dizi : {yeniDizi2}")

print("\n")

# NumPy Dizileri birleştirme, ayrıştırma ve sıralama

# Dizi20,21 = 2 adet diziyi birleştirerek 1 boyutlu dizi oluşturur.

Dizi20=np.array([1,2,3])
Dizi21=np.array([4,5,6])
Birlestirilmis=np.concatenate([Dizi20,Dizi21])

print(f"Birleştirilmiş Dizi 20, 21 : {Birlestirilmis}")

Dizi22=np.array([[1,2,3],[4,5,6]])
Dizi23=np.array([[7,8,9],[10,11,12]])
Birlestirilmis2=np.concatenate([Dizi22,Dizi23])

print(f"Birleştirilmiş 2. Dizi 22,23 : {Birlestirilmis2}")

print("\n")

# Ayrıştırma

# Dizi24 = Split komutu ile diziyi 3 parçaya ayırır.

Dizi24 = np.array([11,12,13,14,15,16,17,18,19])

np.split(Dizi24, 3)

print(f"3 Parçaya ayrılmış Dizi 24 : {Dizi24}")

# Dizi 25 = indeks numaraları kullanarak belli aralıkta ayrıştırır ve farklı değişkenlere kaydeder.

Dizi25 = np.array([11,12,13,14,15,16,17,18,19])

Ayristirma1, Ayristirma2, Ayristirma3 = np.split(Dizi25,[2,6])

print(f"""

Ayrıştırılmış 1. Değişken : {Ayristirma1}

Ayrıştırılmış 2. Değişken : {Ayristirma2}

Ayrıştırılmış 3. Değişken : {Ayristirma3}

""")

print("\n")

# iki boyutlu diziyi reshape ile ayrıştırma

Dizi26 = np.arange(16).reshape(4,4)

print(f"Reshape ile ayırma Dizi 26 : {Dizi26}")

# VSplit ile ayrıştırılan 2 boyutlu diziyi satır bazında alt dizilere aktarır

Ayrı1, Ayrı2 = np.vsplit(Dizi26, 2)

print(f"""

Ayrıştırılmış 2 Boyutlu 1. : {Ayrı1}

Ayrıştırılmış 2 Boyutlu 2. : {Ayrı2}

""")

# HSplit ile iki boyutlu diziyi sütun bazında alt dizilere aktarır

Ayrı3, Ayrı4 = np.hsplit(Dizi26, 2)

print(f"""

Ayrıştırılmış 2 Boyutlu 3. : {Ayrı3}

Ayrıştırılmış 2 Boyutlu 4. : {Ayrı4}

""")

print("\n")

# Mantıksal operatörler ile işlemler

Dizi27 = np.array([10,20,30])

Dizi28 = np.array([1,2,3])

# Add fonksiyonu ile toplama işlemi yapıyoruz

np.add(Dizi27,5)
np.add(Dizi27,Dizi28)

# Subtract fonksiyonu ile çıkartma işlemi yapıyoruz

np.subtract(Dizi27,5)
np.subtract(Dizi27,Dizi28)

# Multiply fonksiyonu ile çıkartma işlemi yapıyoruz

np.multiply(Dizi27,5)
np.multiply(Dizi27,Dizi28)

# Power fonksiyonu ile çıkartma işlemi yapıyoruz

np.power(Dizi27,2)
np.power(Dizi27,Dizi28)

# Trigonometri fonksiyonları ile işlem yapma

Dizi29 = np.array([0,30,60,90,120,150,180])

# Sinüs değerini bulmak

sinüs = np.sin(Dizi29*np.pi/180)

# kosinüs değerlerini bulmak

kosinüs = np.cos(Dizi29*np.pi/180)

# tanjant değerlerini bulmak 

tanjant = np.tan(Dizi29*np.pi/180)

print(f"""

Trigonometri fonksiyonları ile işlem yapmak

Sinüs : {sinüs}

Kosinüs : {kosinüs}

tanjant : {tanjant}

""")

print("\n")

# istatiksel fonksiyonlar ile işlemler

# Dizi 30 = 0 ile 100 arasında rastgele sayılardan oluşan 10x3 bir dizidir.

# Not : Fonksiyonların içine axis verirseniz eksenleri ile işlem yaparsınız

Dizi30 = np.random.randint(0,101,([10,3]))

Büyük = Dizi30.max()

Küçük = Dizi30.min()

# Dizinin tamamının toplamını verir (sum fonksiyonu)

Toplam = Dizi30.sum()

# mean fonksiyonu ile dizinin ortalamasını alır.

Ortalama = Dizi30.mean()

# Ortalamaya göre değişiklik gösteren varyansını bulmak (var fonksiyonu)

Varyans = Dizi30.var()

# Dizinin ortalamaya göre ne kadar saptığını gösteren standart sapmasını bulmak (std fonksiyonu)

Sapma = Dizi30.std()
```

 <h3>Eski notlarım - v2</h3>

```python
import numpy as np #Numpy'ı içeri aktardık

arr = np.array([1, 2, 3, 4, 5]) #Bir numpy dizisi oluşturur
#NumPy genellikle np alias (takma adı) altında içe aktarılır. 
#alias Python’da, aynı şeye atıfta bulunmak için alternatif bir addır. 
#İçe aktarırken as anahtar sözcüğüyle bir alias oluşturabilirsiniz.

#Numpy sürümünü kontrol etme

print(np.__version__)

#0-D dizileri veya Skalarlar, bir dizideki öğelerdir. Bir dizideki her değer bir 0-D dizisidir.
arr = np.array(42)
print(arr)

#Öğeleri olarak 0-D dizileri olan bir dizi, tek boyutlu veya 1-D dizi olarak adlandırılır. Bunlar en yaygın ve temel dizilerdir.

arr = np.array([1, 2, 3, 4, 5])
print(arr)


#Öğeleri olarak 1 boyutlu dizilere sahip bir diziye 2 boyutlu dizi denir. 
#Bunlar genellikle matris veya 2. derece tensörleri temsil etmek için kullanılır.

arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr)

#Elemanları olarak 2 boyutlu dizilere (matrisler) sahip olan bir dizi, 3 boyutlu dizi olarak adlandırılır. 
#Bunlar genellikle 3. dereceden bir tensörü temsil etmek için kullanılır.

arr = np.array([[[1, 2, 3], [4, 5, 6]], [[1, 2, 3], [4, 5, 6]]])
print(arr)

#NumPy Dizileri, dizinin kaç boyuta sahip olduğunu bize söyleyen bir tamsayı döndüren ndim niteliğini sağlar. 
#Dizilerin kaç boyuta sahip olduğunu kontrol etmek için ndim kullanabiliriz :

a = np.array(42)
b = np.array([1, 2, 3, 4, 5])
c = np.array([[1, 2, 3], [4, 5, 6]])
d = np.array([[[1, 2, 3], [4, 5, 6]], [[1, 2, 3], [4, 5, 6]]])

print(a.ndim)  # 0
print(b.ndim)  # 1
print(c.ndim)  # 2
print(d.ndim)  # 3

#Bir dizi herhangi bir sayıda boyuta sahip olabilir. Dizi oluşturulduğunda, 
#ndmin bağımsız değişkenini kullanarak boyutların sayısını tanımlayabilirsiniz. 
#Örneğin 5 boyutlu bir dizi oluşturmak için aşağıdaki kullanıma bakabilirsiniz:

arr = np.array([1, 2, 3, 4], ndmin=5)

print(arr)                         # [[[[[1 2 3 4]]]]]
print('Boyut sayısı:', arr.ndim)   # 5

#Bu dizide en içteki boyut (5. boyut) 4 öğeye, 4. boyut vektör olan 1 öğeye, 3. boyut vektörün bulunduğu 
#matris olan 1 öğeye, 2. boyutun ise 3 boyutlu dizi olan 1 öğesi ve 1. dim, 4D dizisi olan 1 öğeye sahiptir.

#Dizi indexleme
#Dizi indeksleme, bir dizi öğesine erişimle aynıdır. Bir dizi öğesine, dizin numarasına başvurarak erişebilirsiniz. 
#NumPy dizilerindeki indexler 0 ile başlar, yani bu, ilk öğenin indexi 0’a ve ikincinin indexi 1’e sahip olduğu anlamına gelir.

arr = np.array([1, 2, 3, 4])
print(arr[0])  # 1

#Aşağıdaki örnek, diziden ikinci öğeyi alır :

arr = np.array([1, 2, 3, 4])
print(arr[1])  # 2

#2 boyutlu dizilerden öğelere erişmek için, öğenin boyutunu ve dizinini temsil eden virgülle ayrılmış tamsayılar kullanabiliriz.

arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])
print('1. boyuttaki 2.eleman: ', arr[0, 1])

#3 boyutlu dizilerden öğelere erişmek için, öğenin boyutlarını ve dizinini temsil eden virgülle ayrılmış tamsayılar kullanabiliriz.

arr = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])
print(arr[0, 1, 2])

#Negatif indexleme
#Bir diziye sondan erişmek için negatif indeksleme kullanabilirsiniz. Örneğin, 2. boyuttan son öğeyi yazdırmak için :

arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])
print('Last element from 2nd dim: ', arr[1, -1])

#Dizileri dilimleme

#Python’da dilimleme, belirli bir dizinden belirli bir dizine öğe almak anlamına gelir.
#İndeks yerine dilimi şu şekilde geçiririz: [start: end]. Ayrıca adımı şu şekilde tanımlayabiliriz: [start: end: step].
#Aşağıdaki diziden index 1’den index 5’e öğeleri dilimlemek için :

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[1:5])   # [2 3 4 5]

#Öğeleri index 4’ten dizinin sonuna kadar dilimlemek için :

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[4:])   # [5 6 7]


Öğeleri baştan 4. indexe kadar dilimleyin :

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[:4])   # [1 2 3 4]

#Negatif Dilimleme
#Sondan bir indexe başvurmak için eksi operatörünü kullanılır. 
#Örneğin sondan 3. indexten sondan 1. indexe kadar dilimlemek için şunu kullanabiliriz:

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[-3:-1])   # [5 6]

#Dilimleme adımını belirlemek için step değerini kullanınız. 
#Örneğin index 1’den index 5’e diğer kadar her 2 ögeden birini döndürür:

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[1:5:2])   # [2 4]


#4 Boyutlu dizileri dilimleme
#İkinci öğeden, öğeleri index 1’den index 4’e kadar dilimlemek için aşağıdaki kodu kullanabilirsiniz:

arr = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])
print(arr[1, 1:4])   # [7 8 9]


#Her iki öğeden, index 2’yi döndür :

arr = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])
print(arr[0:2, 2])   # [3 8]

#NumPy Dizi Yeniden Şekillendirme (Reshaping)
#Yeniden şekillendirme, bir dizinin şeklini değiştirmek anlamına gelir. 
#Bir dizinin şekli, her boyuttaki öğelerin sayısıdır. Yeniden şekillendirerek boyutları ekleyebilir, 
#kaldırabilir veya her boyuttaki öğe sayısını değiştirebiliriz.

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
newarr = arr.reshape(4, 3)
print(newarr)

# [[ 1  2  3]
# [ 4  5  6]
# [ 7  8  9]
# [10 11 12]]

#Aşağıdaki 1-D diziyi 12 elemanlı bir 3-D dizisine dönüştürelim. 
#En dıştaki boyut, her biri 2 öğe içeren 3 dizi içeren 2 diziye sahip olacaktır:



arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
newarr = arr.reshape(2, 3, 2)
print(newarr)

# [[[ 1  2]
#  [ 3  4]
#  [ 5  6]]

# [[ 7  8]
#  [ 9 10]
#  [11 12]]]

#Herhangi bir Şekle Yeniden Şekillendirebilir miyiz?
#Evet, yeniden şekillendirme için gerekli öğeler her iki şekilde de eşit olduğu sürece reshape yapabiliriz. 
#8 öğeli bir 1D dizisini 2 satırlı 2D dizide 4 öğeye yeniden şekillendirebiliriz, 
#ancak 3×3 = 9 öğe gerektireceği için onu 3 öğeli 3 satırlı 2D diziye yeniden şekillendiremeyiz.
#8 öğeli 1D diziyi, her boyutta 3 öğeli bir 2D diziye dönüştürmeyi deneyelim (bir hataya neden olur) :

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8])
newarr = arr.reshape(3, 3)

print(newarr)  # ValueError: cannot reshape array of size 8 into shape (3,3)
```

**Daha fazla kaynak ve bilgi için aşağıdaki kaynaklara göz atabilirsiniz...**<br>

[Kerteriz Numpy](https://kerteriz.net/python-numpy-kullanimi-nedir-ve-nasil-kullanilir/)<br>
[Bilişim Hareketi](https://medium.com/bili%C5%9Fim-hareketi/veri-bilimi-i%CC%87%C3%A7in-temel-python-k%C3%BCt%C3%BCphaneleri-1-numpy-750429a0d8e5)<br>
[Teknoloji.org](https://medium.com/bili%C5%9Fim-hareketi/veri-bilimi-i%CC%87%C3%A7in-temel-python-k%C3%BCt%C3%BCphaneleri-1-numpy-750429a0d8e5)<br>
[Hakan Ceran](https://hakanceran.com.tr/numpy-hizli-baslangic-kilavuzu/)<br>
 
```python
#Son olarak kendi notlarımı buraya bırakıyorum.

listem = [20,30,40]

np.array(listem) #Listeyi dizi yapar

matrixListesi = [[10,20,30],[40,50,60],[70,80,90]]

np.array(matrixListesi) #Listeyi dizi yapar

for i in range(20,50):
    print(i) #20 ile 50 Arasında sayılar oluşturur

dizi1 = np.arange(1,9) #1 ile 9 arasındaki sayıları oluşturur

np.zeros(9,9) # 0'lardan 9,9 Stünlar oluşturur

np.ones(5) # 1'lerden 5 adet dizi oluşturur 

np.linspace(0,20,5) #0 ile 20 Arasında 5 adet eşit dağıtılmış rakam yapar

np.eye(10) # 10 Adet çapraz 1 dizer

np.random.randn(8) # Rastgele 8 adet rakam üretir

np.random.randint(1,10) #1,10 a kadar rastgele bir adet sayı üretir

np.random.randint(1,10,5) #1,10 a kadar rastgele 5 adet sayı üretir

matrixListesi.reshape(6,5) # Diziyi Düzenler

matrixListesi.max() #Maximum sayıyı getirir

matrixListesi.min() # Minimum sayıyı getirir

benimDizim = np.arange(0, 15)

benimDizim[5] # Diziden 5. Elemanı alır. Listeler ile aynı çalışır.

slicingDizisi = benimDizim[4:9] #Slicing dizisi benim dizimdeki 4 ile 9 arasındaki rakamları alır

slicingDizisi[:] = 50 #slicingDizisindeki tüm rakamları 50 yapar

KopyaDizisi = benimDizim.copy() #KopyaDizisi benimDizim ile aynı değerleri alır ve kopyalar 2. bir dizi oluşturur.

liste1 = [[20,30,40],[10,30,50],[20,40,30]]

matrixDizisi = np.array(liste1) #liste1 i Matrix Dizisi yapar

yeniDizi = np.arange(0, 50)

hesapla1 = yeniDizi > 23 #Yeni dizideki 23 ten büyük sayıları True diğerlerini False olarak gösterir

yeniDizi[hesapla1] # Sadece True olan sayıları alır (23Ten büyük olan sayıları)
```

**Fazz iyi yazılımlar diler...**
