# Python | Subprocess Kütüphanesi

**pip install subprocess.run**

**subprocess basit bazı process'leri kullanmak için birkaç tane fonksiyon sunuyor. Daha karmaşık bir process çalıştırmak isterseniz, Popen sınıfını kullanabilirsiniz.**

```python
subprocess.call()
```

*Bu fonksiyon, kendisine verilen komutu parametrelerle birlikte çalıştırır, sonra da bu komutun işlenmesini bekler. Komutların işlenmesi bittikten sonra durum kodunu geri döndürür. Biz de bu durum koduna bakarak işlemin başarılı bir şekilde sonuçlandırılıp sonuçlandırılmadığını kontrol ederiz. Genelde başarılı sonuçlar için 0 sonuç kodu geri döndürülür. Örnek kullanım
Bu komut, programın bulunduğu dizindeki dosyaları listeleyecektir. Eğer hiçbir hata meydana gelmezse bize 0 durum kodunu geri döndürecektir.*

```python
import subprocess

print(subprocess.call(["hostname"])) # CMD'De hostname komutunu çalıştırır.

print(subprocess.Popen("dir", shell=True, stdout=subprocess.PIPE ).communicate()[0].decode("cp850")) # Dir komutunu çalıştırır.

# subprocess.Popen(['ls','-al'], stdout=subprocess.PIPE) # Linux için ls komutunu çalıştırır.

ping = subprocess.Popen(['ping', '8.8.8.8'], shell=True, stdout=subprocess.PIPE ).communicate()[0].decode("cp850") # Ping komutunu çalıştırır.
print(ping)

# subprocess.call(["ifconfig"]) # Linuxda ip adresi vb. şeylerin çıktısını verir.

# subprocess.call(["sudo","apt","update"]) # Linux'da Update komutu ile bunu otomatikleştirip güncellemeler atabilirsiniz.


```

*Son olarak Mac Değiştirici uygulaması yapalım.*

```python
import subprocess


interface = "eth0"


subprocess.call(["ifconfig",interface,"down"])
subprocess.call(["ifconfig",interface,"hw","ether","00:16:18:32:ba:ba"])
subprocess.call(["ifconfig",interface,"up"])


#Burdan sonra yazdıklarım subprocess'in farklı bir özelliği kısaca istediğin şeyi göstermeyi sağlar.
interface_new = subprocess.check_output(["ifconfig",interface])
print(interface_new)

```
