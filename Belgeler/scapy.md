**Python Scapy Kütüphanesi**

>kurulum<br>
>**Linux : sudo apt-get install scapy**<br>
>**Windows : [Npcan indir](https://nmap.org/npcap/dist/npcap-0.97.exe) Bu yazılımı indirdiktan sonra [Github Dosyası](https://github.com/secdev/scapy/archive/master.zip) Bunu indirip içindeki setup.py dosyasını çalıştırıyoruz.<br>**
>**Not : Kali Linux kullanan arkadaşlarda zaten indirilmiştir.**<br>

>Scapy Nedir ?

**Scapy, kullanıcının ağ paketlerini göndermesini, koklamasını, parçalara ayırmasını ve oluşturmasını sağlayan bir Python programıdır. Bu özellik, ağları araştırabilen, tarayabilen veya saldırabilen araçların oluşturulmasına olanak tanır. Başka bir deyişle, Scapy güçlü bir etkileşimli paket manipülasyon programıdır. Çok sayıda protokolün paketlerini taklit edebilir veya kodunu çözebilir, bunları kabloya gönderebilir, yakalayabilir, istekleri ve yanıtları eşleştirebilir ve çok daha fazlasını yapabilir. Scapy, tarama, izleme yönlendirme, sondalama, birim testleri, saldırılar veya ağ bulma gibi klasik görevlerin çoğunu kolayca yerine getirebilir. HPING, arpspoof, arp-sk, arping, p0f ve hatta Nmap, tcpdump ve tshark'ın bazı kısımlarının yerini alabilir.**<br>

<img src=https://github.com/FazzPy/PythonMaster/blob/main/Belgeler/testing-taxonomy.png><br>

**Scapy ayrıca, geçersiz çerçeveler göndermek, kendi 802.11 çerçevelerinizi enjekte etmek, teknikleri birleştirmek (VLAN atlama + ARP önbellek zehirlenmesi, WEP şifreli kanalda VOIP kod çözme,...) gibi diğer araçların çoğunun üstesinden gelemediği diğer birçok özel görevde de çok iyi performans gösterir.**<br>


**Fikir basit. Scapy temel olarak iki şey yapar: paket göndermek ve cevaplar almak. Bir paket kümesi tanımlarsınız, bunları gönderir, yanıtları alır, istekleri yanıtlarla eşleştirir ve paket çiftlerinin bir listesini (istek, yanıt) ve eşleşmeyen paketlerin bir listesini döndürür. Bu, bir cevabın (açık / kapalı / filtrelenmiş) indirgenmediği, ancak tüm paket olduğu Nmap veya hping gibi araçlara göre büyük bir avantaja sahiptir.**<br>

**Bunun da ötesinde, örneğin traceroutes yapan ve sonuç olarak yalnızca isteğin başlangıç TTL'sini ve cevabın kaynak IP'sini veren daha üst düzey işlevler oluşturulabilir. Bütün bir ağa ping atan ve telefonlayan makinelerin listesini veren biri. Bağlantı noktası taraması yapan ve LaTeX raporu döndüren bir rapor.**<br>

*Scapy İle Ağ Paketi Oluşturmak ve Göndermek :*<br>

ip_basligi = IP(dst="Hedef ip", src="kaynak ip", ttl=20)<br>
icmp_basligi=ICMP(type=8, code=0)<br>
icmp_paketi=ip_basligi/icmp_basligi<br>
send(icmp_paketi)<br>

*DHCP Paketi :*<br>
**Ip, udp ve dhcp basliklarını kullanacağız.**<br>

ip_basligi=IP(src="0.0.0.0", dst="255.255.255.255")<br>

udp_basligi=UDP(dport=67, sport=68)<br>

dhcp_basligi=DHCP(options=[("lease_time", 70000)])<br>

dhcp_paketi=ip_basligi/udp_basligi/dhcp_basligi<br>

send(dhcp_paketi)<br>

*DNS Paketi :*<br>

ip_basligi=IP(dest="8.8.8.8")<br>

udp_basligi=UDP(dport=53)<br>

dns_basligi=DNS(rd=1, qd=DNSQR(qname="www.threearrowsec.com"))<br>

dns_paketi=ip_basligi/udp_basligi/dns_basligi<br>

send(dns_paketi)<br>

>**TCP Paketi :**<br>

tcp_basligi=TCP(sport=8080, dport=22, flags="S")<br>

ip_basligi=IP(src="127.0.0.1",dst=”127.0.0.1")<br>

tcp_paketi=ip_basligi/tcp_basligi<br>

send(tcp_paketi)<br>

**Scapy Rehberi buraya kadardı devamı gelecektir...**<br>
