# Veri Bilimi
## Numpy Kütüphanesi

**Neden numpy kullanılır?**<br>
>*Python’da dizilerin amacına hizmet eden listelerimiz var, ancak işlenmesi yavaştır. NumPy, geleneksel Python listelerinden 50 kata kadar daha hızlı bir dizi nesnesi sağlamayı amaçlamaktadır. NumPy’deki dizi nesnesi (array) ndarray olarak adlandırılır ve ndarray, çalışmayı çok kolaylaştıran birçok destekleyici işlev sağlar. Diziler, hız ve kaynakların çok önemli olduğu veri biliminde çok sık kullanılır.*

**Kurulum**<br>
>**Windows : pip install numpy**<br>
>**Linux : pip3 install numpy**<br>

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

**Numpy Rehberimiz bu kadardı dostlar daha faza kaynak ve bilgi için aşağıdaki kaynaklara göz atabilirsiniz...**<br>

[Kerteriz Numpy](https://kerteriz.net/python-numpy-kullanimi-nedir-ve-nasil-kullanilir/)<br>
[Bilişim Hareketi](https://medium.com/bili%C5%9Fim-hareketi/veri-bilimi-i%CC%87%C3%A7in-temel-python-k%C3%BCt%C3%BCphaneleri-1-numpy-750429a0d8e5)<br>
[Teknoloji.org](https://medium.com/bili%C5%9Fim-hareketi/veri-bilimi-i%CC%87%C3%A7in-temel-python-k%C3%BCt%C3%BCphaneleri-1-numpy-750429a0d8e5)<br>
[Hakan Ceran](https://hakanceran.com.tr/numpy-hizli-baslangic-kilavuzu/)<br>
