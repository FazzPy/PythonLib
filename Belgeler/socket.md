# Fazz | Python Socket Kütüphanesi

> pip install socket

**Soket programlama, birbirleriyle iletişim kurmak için bir ağdaki iki düğümü bağlamanın bir yoludur. 
Bir soket (düğüm) bir IP'deki belirli bir bağlantı noktasını dinlerken, diğer soket bir bağlantı oluşturmak için diğerine uzanır. 
İstemci sunucuya ulaşırken sunucu dinleyici yuvasını oluşturur. 
Bunlar, web'de gezinmenin arkasındaki gerçek omurgalardır. Daha basit bir ifadeyle, bir sunucu ve bir istemci var. 
Soket programlama, soket kütüphanesinin içe aktarılması ve basit bir soket yapılarak başlatılır.**

```python
import socket
import sys


ip = socket.gethostbyname('www.google.com') # IP Adresini alır
print(ip)

# Google'a bağlanma scripti

try:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    print ("Socket successfully created")
except socket.error as err:
    print ("socket creation failed with error %s" %(err))
 
# Soket için varsayılan bağlantı noktası.
port = 80
 
try:
    host_ip = socket.gethostbyname('www.google.com')
except socket.gaierror:
    # bu, ana bilgisayarın çözümlenemediği anlamına gelir.
    print ("there was an error resolving the host")
    sys.exit()
 
# connecting to the server
s.connect((host_ip, port)) # www.google.com'un ip adresini çeker ve 80 portu ile bağlanır.
 
print ("the socket has successfully connected to google")

```
**Bir sunucunun, belirli bir IP ve bağlantı noktasına bağlayan bir bind() 
yöntemi vardır, böylece bu IP ve bağlantı noktasındaki gelen istekleri dinleyebilir. 
Bir sunucunun, sunucuyu dinleme moduna geçiren bir listen() yöntemi vardır. Bu, sunucunun gelen bağlantıları dinlemesini sağlar. 
Ve son olarak bir sunucunun accept() ve close() yöntemleri vardır. 
Kabul yöntemi istemciyle bir bağlantı başlatır ve close yöntemi istemciyle bağlantıyı kapatır.**

```python
# Sunucu-İstemci Programı

import socket            
 
# daha sonra soket nesnesi oluştur
s = socket.socket()        
print ("Socket successfully created")
 
# Bilgisayarınızda bir port ayırtın
# durumda 12345 ama herhangi bir şey olabilir
port = 12345               
 
# Bağlantı noktasına sonraki bağlama
# ip alanına herhangi bir ip yazmadık
# bunun yerine boş bir dize girdik
# bu, sunucunun istekleri dinlemesini sağlar
# ağdaki diğer bilgisayarlardan geliyor
s.bind(('', port))        
print ("socket binded to %s" %(port))
 
# soketi dinleme moduna geçirin
s.listen(5)    
print ("socket is listening")           
 
# kesintiye uğratana kadar sonsuza dek sürecek bir döngü veya
# bir hata oluşuyor
while True:
 
# İstemci ile bağlantı kurun.
  c, addr = s.accept()    
  print ('Got connection from', addr )
 
  # Müşteriye bir teşekkür mesajı gönderin. bayt türü göndermek için kodlama.
  c.send('Thank you for connecting'.encode())
 
  # İstemciyle bağlantıyı kapatın
  c.close()
   
  # Bağlantı kapandıktan sonra kopma
  break

```

**Her şeyden önce, gerekli olan soketi ithal ediyoruz. 
Sonra bir soket nesnesi yaptık ve bilgisayarımızda bir port ayırdık. 
Bundan sonra, sunucumuzu belirtilen bağlantı noktasına bağladık. 
Boş bir dize iletmek, sunucunun diğer bilgisayarlardan gelen bağlantıları da dinleyebileceği anlamına gelir. 
Eğer 127.0.0.1'i geçseydik, o zaman sadece yerel bilgisayarda yapılan aramaları dinlerdi. 
Bundan sonra sunucuyu dinleme moduna geçiririz.
5 burada, sunucu meşgulse 5 bağlantının beklemeye devam ettiği ve 6. bir soket bağlanmaya çalışırsa bağlantının reddedildiği anlamına gelir. 
Sonunda, bir süre döngü yapıyoruz ve gelen tüm bağlantıları kabul etmeye başlıyoruz ve bağlı tüm soketlere bir teşekkür mesajından sonra bu bağlantıları kapatıyoruz.**

Client :

```python

# Sunucuyu başlat
$ python server.py

# yukarıdaki terminali açık tutun
# şimdi başka bir terminal açın ve şunu yazın :
 
$ telnet localhost 12345

```

Output :

```python

# server.py terminalinde göreceksiniz
# Çıktı : 
Socket successfully created
socket binded to 12345
socket is listening
Got connection from ('127.0.0.1', 52617)

# Telnet terminalinde şunları alacaksınız :
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Thank you for connectingConnection closed by foreign host.

```

**Bu çıktı sunucumuzun çalıştığını gösterir. Şimdi müşteri tarafına gelelim :**


```python

# Soket modülünü içe aktarma
import socket            
 
# Socket nesnesi oluşturma
s = socket.socket()        
 
# Bağlanmak istediğiniz bağlantı noktasını tanımlayın
port = 12345               
 
# yerel bilgisayardaki sunucuya bağlanma
s.connect(('127.0.0.1', port))
 
# sunucudan veri alma ve dizeyi almak için kod çözme.
print (s.recv(1024).decode())
# Bağlantıyı kapatma
s.close() 

```
**Her şeyden önce, bir soket nesnesi yapıyoruz. 
Ardından localhost'a 12345 numaralı bağlantı noktasında (sunucumuzun çalıştığı bağlantı noktası) bağlanıyoruz. 
Ve son olarak sunucudan veri alıp bağlantıyı kapatıyoruz. 
Şimdi bu dosyayı client.py olarak kaydedin ve sunucu komut dosyasını başlattıktan sonra terminalden çalıştırın.**

```python

# Sunucuyu başlat :
$ python server.py
Socket successfully created
socket binded to 12345
socket is listening
Got connection from ('127.0.0.1', 52617)

# İstemciyi başlat :
$ python client.py
Thank you for connecting

```

*Kaynak : [Geeksforgeeks](https://www.geeksforgeeks.org/socket-programming-python/)*

