# Python | ImPacket Nedir ?

>"Impacket" kütüphanesi ağ protokolleriyle çalışmak için oluşturulmuş Python yazılım dilinde hazırlanmış özel bir koleksiyondur. Bu paketin amacı; paketlere düşük verili programlı erişim sağlamak ve bazı protokol maddeleri için (Mesela SMB1 - 3 ile MSRPC gibi) mevcut bu protokol uygulamalarının "Impacket" kütüphanesine odaklanarak hazırlanmasıdır. Kullanıcılar paketleri kendileri de sıfırdan yaratabilir ve üstelik ham veriler bütününden ayrıştırabilir ve nesne odaklı API, derin protokol hiyerarşisiyle çalışma uygulamalarını kolaylaştırabilir. Bu kütüphanede neler yapılabileceği kütüphane içeriğinde ki örnekler ile belirtilerek bir dizi araç dahil edilmiştir.

**Impacket Kütüphanesi'nin özellikleri nelerdir?**

* Ethernet, Linux 'Cooked' yakalama özelliği,

* IP, TCP, UDP, ICMP, IGMP, ARP yakalama özelliği,

* IPv4 ve IPv6 Desteği,

* NMB ve SMB1, SMB2 ve SMB3 üst düzey uygulamalar ile çalışma özelliği,

* MSRPC sürüm 5 ile farklı aktarımlar üzerinden: TCP, SMB / TCP, SMB / NetBIOS ve HTTP özelliği,

* Düz, NTLM ve Kerberos kimlik doğrulama özelliği (parola / karmalar / biletler / anahtarlar kullanılarak)

* MSRPC arayüz bölümlerinin takibi / tam uygulaması: EPM, DTYPES, LSAD, LSAT, NRPC, RRP, SAMR, SRVS, WKST, SCMR, BKRP, DHCPM, EVEN6, MGMT, SASEC, TSCH, DCOM, WMI, OXABREF, NSPI, OXNSPI.

* TDS (MSSQL) ve LDAP protokol uygulamalarının tüm bölümleri


<img height="400" align="left" alt="download" src="Belgeler/lYzUkV.png" /><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br>
**"Impacket" Nasıl Yüklenir?**

Yüklemeye başlamadan önce bu üstün nitelikli kütüphanenin çalışabilmesi için bazı gereksinimlere ihtiyaç vardır;

* Bir Python yorumlayıcısı şarttır. (Version 2.6 - 2.7 veya 3.7...)

* "Impacket programının son sürümünü indirmeniz gerekir.

Bu saydığımız basit iki aşamayı geçtikten sonra aşağıda belirttiğimiz yöntemler ile yüklemeye başlayabilirsiniz.

Kaynağı kurmak için, "Impacket" dağıtımı paketinin açıldığı dizinden aşağıdaki komutu girebilirsiniz;

Eğer Python 3.7 ve üst versiyonlar yüklü ise;
pip3 install​

Eğer Python 2.6 veya 2.7 versiyonlar yüklü ise;
pip install​


Bu yükleme işlemlerini yaptıktan sonra doğru çalışıp / çalışmadığını test etmek istiyorsak 3 şekilde bu işlemi gerçekleştirebiliriz;

1) Bir Windows 2012 R2 Etki Alanı Denetleyicisi kurun ve yapılandırın. Ardından "RemoteRegistry" hizmetinin etkinleştirildiğinden ve çalıştığından emin olun,

2) Dcetest.cfg dosyasını gerekli bilgilerle yapılandırın,

3) Tox yükleyin. Bunu da şu komut satırı ile yapabilirsiniz;
pip3 install tox​

Bu işlemi tamamladığınızda Toksin komutunu çalıştırarak sonuçlar alabilirsiniz. Eğer sorun yaşamazsanız tüm test durumlarını aşmış olduğunuzu gösterir. Ayrıca HTML raporunuzu da şu diziden alabilirsiniz;
impacket/tests/htlmcov/index.html​

<img height="400" align="left" alt="download" src="Belgeler/cx0RpI.png" /><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br>

Eğer Docker'da bir imaj oluşturmak isterseniz;
docker build -t "impacket:latest"​

Oluşturulan bu imajı kullanmak için;
docker run -it --rm "impacket:latest"​

Kaynak : https://www.turkhackteam.org/konular/pythonda-impacket-modul-kullanimi-ve-incelikleri.1973476/
