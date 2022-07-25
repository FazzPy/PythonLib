# Fazz | Python | Nmap Kütüphanesi

> pip install python-nmap

**Not : Bunlar benim notlarımdır.**

```python
import nmap

nm = nmap.PortScanner()

nm.scan("192.168.1.0/24", arguments="-sP") # Subnetting -sP Taraması yapılır.

list = []

sayac = 0

for i in nm.all_hosts():
	# bir döngü ile tüm host bilgileri toplanır 
	# ve dönen sonuçlar önceden belirlenen list[] boş listesine eklenir.
	list.append(i) 
	sayac = sayac+1

for x in range(1, sayac):
	print(list[x]) # Ardından liste elemanları yazılır.

```

```python

# Port aralığını alır

begin = 75
end = 80

# taranacak hedef ipi atayın

target = "127.0.0.1"

# bir PortScanner nesnesini örnekle

scanner = nmap.PortScanner()

for i in range(begin,end+1):
	# hedef portu tara

	res = scanner.scan(target,str(i))

	# sonuç içeren bir sözlük
    	# sadece ihtiyacımız olan birkaç bilgi
    	# portun açılıp kapanmadığını kontrol edin
    	# yani sadece bu bilgilere erişeceğiz
    	# sözlükte

	res = res['scan'][target]['tcp'][i]['state']

	print(f'port {i} is {res}.')

```
*Kaynak : Geeksforgeeks.org*
