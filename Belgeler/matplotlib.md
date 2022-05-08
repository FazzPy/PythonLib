# Veri Görselleştirme

## Matplotlib Kütüphanesi

>**Kurulum**<br>
>Windows : **pip install matplotlib**<br>
>Linux : **pip3 install matplotlib**<br>

**Bunlar kendi notlarımdır aşağıda daha fazla öğrenebileceğiniz kaynaklar ve eğitimler bırakıyorum**<br>

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

yasListesi = [10,20,30,30,30,40,50,60,70,75]

kiloListesi = [40,50,60,60,65,70,75,67,90,80]

numpyYasListesi = np.array(yasListesi)

numpyKiloListesi = np.array(kiloListesi)

plt.plot(numpyYasListesi,numpyKiloListesi,"g") 
# 2 Adet listeyi grafik şeklinde gösterir "g" Rengi belirler (ilk yazılan liste x ikinci y ekseninde olur)

plt.xlabel("Yaş") # Grafiğin X Eksenine Yaş yazdırır.
plt.ylabel("Kilo") # Grafiğin y Eksenine Kilo yazdırır.
plt.title("Fazz Tech") # Başlık Belirler

numpyDizisi1 = np.linspace(0,10,20)
numpyDizisi2 = numpyDizisi1 ** 3

plt.plot(numpyDizisi1,numpyDizisi2,"g--") #Çizgiyi kesik verir

plt.plot(numpyDizisi1,numpyDizisi2,"g*-") #Çizgiyi yıldızlar ile verir

# 2 Adet Grafik Ekleme

plt.subplot(1,2,1)
plt.plot(numpyDizisi1,numpyDizisi2, "r*-")
plt.subplot(1,2,2) #1 Sıra olacak, 2 Kolon olacak, şuan 2. grafiği çizdirir
plt.plot(numpyDizisi1,numpyDizisi2, "g--")

plt.show()

numpyDizisi1 = np.linspace(0,10,20)
numpyDizisi2 = numpyDizisi1 ** 3

benimFigure = plt.figure() #Boş bir figür oluşturur

figureAxes = benimFigure.add_axes([0.2, 0.2, 0.9, 0.9]) 
# Boş figüre axes belirler 0.9 0.9 width ve height
figureAxes.plot(numpyDizisi1, numpyDizisi2, "g") 
# Veri Çizgisi
figureAxes.set_xlabel("X Ekseni Veri İsmi") 
# X Eksenindeki Yazı
figureAxes.set_ylabel("Y Ekseni Veri İsmi") 
# Y Eksenindeki Yazı
figureAxes.set_title("Grafik Başlığı") 
# Grafik Başlığı

figure2 = plt.figure()

eksen1 = figure2.add_axes([0.1, 0.1, 0.7, 0.7])
eksen2 = figure2.add_axes([0.3, 0.3, 0.3, 0.3])

eksen1.plot(numpyDizisi1, numpyDizisi2, "g")
eksen1.set_xlabel("X Ekseni")
eksen1.set_ylabel("Y Ekseni")
eksen1.set_title("Başlık")

eksen2.plot(numpyDizisi2, numpyDizisi1, "r")
eksen2.set_xlabel("X Ekseni")
eksen2.set_ylabel("Y Ekseni")
eksen2.set_title("Başlık 2")


plt.show()

dizi1 = np.linspace(0,10,20)
dizi2 = dizi1 ** 3

#(benimFigürler, benimEksenler) = plt.subplots(nrows=1, ncols=2) # Subplots ile boş 2 adet grafik oluşturur.
# (2 Adet yaptığımız için for döngüsü ile eksenleri koyacağız)

# For döngüsü ile verileri grafiğe ekledik.

#for eksen in benimEksenler:
    #eksen.plot(dizi1, dizi2, "g")
    #eksen.set_xlabel("X Ekseni")
    #eksen.set_ylabel("Y Ekseni")
    #eksen.set_title("Başlık")



yeniFigur = plt.figure(figsize=(7,5), dpi=100) 
# Figür belirler figsize=() komutu ile figür boyutu ayarlanır | dpi=100 komutu ile çözünürlük ayarlanır

yeniEksen = yeniFigur.add_axes([0.1, 0.1, 0.9, 0.9]) # Yeni bir Eksen belirler

yeniEksen.plot(dizi1, dizi2 ** 2, label="FazzTech") #Label Sol üstte bulunan Çizgi gösterme yazısıdır
yeniEksen.plot(dizi1, dizi2 ** 3, label="FazzTech") #2. Bir Çizgi Eklemek
yeniEksen.legend(loc=2)#Labeli gösterir loc=1 komutu ile Labelin konumu belirlenir

yeniFigur.savefig("Benimfigür.png", dpi=200) #Figürü resim olarak kaydeder

plt.tight_layout()

plt.show()


dizi1 = np.linspace(0,10,20)
dizi2 = dizi1 ** 3

(benimFigür, benimEksen) = plt.subplots()
benimEksen.plot(dizi1,dizi2, color="#ff3300", linewidth = 2.5, linestyle=":") 
# 2.5 Kalınlığında kırmızı ve kesik çizgili çizgi yapar
benimEksen.plot(dizi2,dizi1,"b", linestyle="-.") 
# Kesik ve noktalı çizgi yapar -- koyulursa nokta nokta çizgi yapar.
benimEksen.plot(dizi2,dizi1,"b", linestyle="--", marker="o", markerfacecolor="red") 
#Noktalı çizgi yapar ve üstüne kırmızı o ile işaret koyar 

# Scatter

plt.scatter(dizi1, dizi2) #Normal Çizgi verir fakat daha dağıtılmış olur.

# Histogram

yeniDizi = np.random.randint(0,100,50)

plt.hist(yeniDizi) #Kare şeklide bir grafik çizer

# Box Plot

plt.boxplot(yeniDizi) # Sadece bir kutu içerisinde verileri gösterir

plt.show()

```

**Kaynaklar ve eğitimler : **<br>

[BTK Akademi](https://www.btkakademi.gov.tr/portal/course/veri-bilimi-icin-python-ve-tensorflow-11705)<br>
[Matplotlib](https://matplotlib.org/)<br>
[W3Schools](https://www.w3schools.com/python/matplotlib_intro.asp)<br>
[Tutorialspoint](https://www.tutorialspoint.com/matplotlib/index.htm)<br>

**Fazz iyi yazılımlar diler...**
