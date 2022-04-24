# Requests Kütüphanesi

>Kurulum
>Linux : sudo apt-get install python3-pip<br>
>pip3 install requests<br>
>Windows : pip3 install requests<br>

**HTTP İSTEKLERİ**
>Örnek Site : http://httpbin.org/get<br>

r = requests.get('http://httpbin.org/get')<br>
r = requests.post('http://httpbin.org/post')<br>
r = requests.put('http://httpbin.org/put')<br>
r = requests.delete('http://httpbin.org/delete')<br>

Bu şekilde istekler gönderebiliyoruz. Elbette ki istek göndermek ile olmuyor, parametre gönderme ihtiyacı var. Şimdi istek atarken nasıl parametre gönderebileceğimize bakalım.<br>

**Parametre Göndermek**<br>
>Parametre göndermek için params sözlüğünü kullanıyoruz. Hemen bir örnek verelim.<br>

r = requests.get('http://httpbin.org/get', params={"kategori":"elektronik","marka":"samsung"})<br>
r.url('http://httpbin.org/get?marka=samsung&kategori=elektronik')<br>

*params sözlüğü içinde parametre geçtim, url methodu ile de istek yapılan url adresini görebilirsiniz. Dikkat ettiyseniz verdiğimiz parametreler bağlantı adresinin sonuna eklendi.*<br>

*Bazen istek attığınız sayfa başka bir sayfaya yönleniyor olabilir, bu yönlenmeyi takip edebilir veya etmeyebiliriz, bunun için de allow_redirects=True veya False kullanılıyor.*<br>

r = requests.get("http://httpbin.org/redirect/1",allow_redirects=False)<br>
r.status_code<br>
>302


r = requests.get("http://httpbin.org/redirect/1",allow_redirects=True)<br>
r.status_code<br>
>200

**Dikkat ederseniz allow_redirects=False yapıldığında yönlendirmeyi kapattı ve o sayfanın status_code değeri 302 döndü. True yapınca da yönlendirmeye izin verildi ve status_code 200 döndü.**<br>

**Bu örnek GET isteği içindi, şimdi bir de POST için sanki bir HTML formu doldurmuş ve o bilgileri post etmişiz gibi davranalım.**<br>

r = requests.post("http://httpbin.org/post", data={"username":"sinan","password":"asd123"})<br>
r.status_code<br>
>200<br>

r.json()<br>

>{'files': {}, 'args': {}, 'url': 'http://httpbin.org/post', 'json': None, 'data': '', 'headers': {'Host': 'httpbin.org', 'Accept': '*/*', 'Accept-Encoding': 'gzip, deflate', 'Connection': 'close', 'Content-Length': '30', 'User-Agent': 'python-requests/2.9.1', 'Content-Type': 'application/x-www-form-urlencoded'}, 'origin': '78.190.133.110', 'form': {'username': 'sinan', 'password': 'asd123'}}

r.json()["form"]<br>
>{'username': 'sinan', 'password': 'asd123'}

**Dikkat ettiyseniz data parametresi ile username ve password bilgilerini formdata olarak gönderdim. Ardından status_code methodu ile 200 yani başarılı olduğunu kontrol ettim. Ardından json methodu ile dönen değeri ekrana bastırdım. Kullandığımız httpbin.org servisi, post ettiğimiz parametreleri bize geri döndürüyor. Bu nedenle json içinden sadece form alanını çekerek gönderdiğim parametreleri görebildim.**<br>

İstek atarken timeout değeri de belirleyebilirsiniz, saniye olarak bir değer atayabilirsiniz.<br>

r = requests.get("http://httpbin.org/get", timeout=1)<br>

**Belirtilen timeout içinde cevap alamaz ise hata verecektir.**<br>

*Burada bir parantez açalım, REST API ile çalışıyorsak, farklı endpointlere json post etmemiz gerekecek. Bu noktada da hemen json modülü bize yardım ediyor. Basit bir örnek yapalım ve bu konuyu bitirelim.*<br>

**Kodlar :**<br>
'''
    import json<br>
    import requests<br>
    endpoint = "http://httpbin.org/post"<br>
    myData =   {<br>
...     "id": 1,<br>
...     "name": "Leanne Graham",<br>
...     "username": "Bret",<br>
...     "email": "Sincere@april.biz",<br>
...     "address": {<br>
...       "street": "Kulas Light",<br>
...       "suite": "Apt. 556",<br>
...       "city": "Gwenborough",<br>
...       "zipcode": "92998-3874",<br>
...       "geo": {<br>
...         "lat": "-37.3159",<br>
...         "lng": "81.1496"<br>
...       }<br>
...     },<br>
...     "phone": "1-770-736-8031 x56442",<br>
...     "website": "hildegard.org",<br>
...     "company": {<br>
...       "name": "Romaguera-Crona",<br>
...       "catchPhrase": "Multi-layered client-server neural-net",<br>
...       "bs": "harness real-time e-markets"<br>
...     }<br>
...   }<br>
r = requests.post(endpoint, data=json.dumps(myData))<br>
r.status_code<br>

>200

'''

**Özel Header Kullanımı**<br>

*İstek atarken, headers parametresi ile sözlük formatında istediğiniz bilgileri girebilirsiniz.*<br>

r = requests.post("http://httpbin.org/post",headers={"User-Agent":"Sinan-Chrome"})<br>
r.status_code<br>
>200

**Bu örnek içerisinde headers parametresi ile özel bir user-agent değeri göndermiş oldum. status_codemethodu ile de isteğe dönen durum kodunu kontrol ettim. Benim örneğimde 200 gelmiş, yani başarılı.**<br>

**İstek attıktan sonra kullanılan methodlar**<br>

*Tüm örneklerde bir r değişkenine aktarmıştık attığımız tüm istekleri, şimdi bu r değişkeni içinde yani requests modülü içindeki istek attıktan sonra kullanabileceğimiz methodları inceleyelim.*<br>

**text**<br>
r = requests.get("http://httpbin.org/")<br>
r.text<br>

**headers**<br>

*Header bilgilerini gösterir.*<br>

r = requests.get("http://httpbin.org/")<br>
r.headers<br>

>{'Content-Length': '13011', 'Content-Type': 'text/html; charset=utf-8', 'Server': 'meinheld/0.6.1', 'Date': 'Tue, 17 Oct 2017 21:29:49 GMT', 'Connection': 'keep-alive', 'Via': '1.1 vegur', 'X-Processed-Time': '0.00539398193359', 'Access-Control-Allow-Credentials': 'true', 'Access-Control-Allow-Origin': '*', 'X-Powered-By': 'Flask'}<br>

**Dilerseniz istediğiniz header bilgilerini siz get isteği ile birlikte belirtebilirsiniz.**<br>

r = requests.get("http://httpbin.org/", headers={'user-agent': 'sinanerdinc'})<br>

**URL**<br>
*Hangi url adresine istek gönderdiğini döner. İstek yaparken parametre olarak bazı değerler gönderebilirsiniz.*<br>

r = requests.get("http://httpbin.org/", params={"ad":"sinan","soyad":"erdinc"})<br>
r.url<br>

>'http://httpbin.org/?soyad=erdinc&ad=sinan'

Url adresinin sonunda verdiğim parametrelerin nasıl iliştirildiğine dikkat edin.<br>

**status_code**<br>
*İsteğin HTTP durum kodunu döndürür.*<br>

r = requests.get("http://httpbin.org/")<br>
r.status_code<br>
>200

**history**<br>
*Bir istek attınız ve status_code değeri 200 geldi. Ancak belki 2 kere 301 sonra 1 kere 302 yönlendirme ile en son bir sayfaya geldi ve 200 döndü. Buna bakabilmek için bu method kullanılıyor.*<br>

r = requests.get("http://httpbin.org/redirect/4",allow_redirects=True)<br>
r.history<br>

>[<Response [302]>, <Response [302]>, <Response [302]>, <Response [302]>]

http://httpbin.org/redirect/4 adresi 4 kere 302 yönlendirmesi yapıyor. İşte buraya istek atınca history methodu ile de kontrol edince geçmişteki HTTP durum kodlarını görebiliyoruz.<br>

**encoding**<br>
*Sayfanın encode değerini döner.*<br>

r = requests.get("http://github.com", timeout=1)<br>
r.encoding<br>

>'utf-8'

**request**<br>
*Yaptığınız isteğin ne olduğunu döner, GET,POST v.s.*<br>

r.request<br>

> <PreparedRequest [GET]>

r.request.method<br>

>'GET'


**elapsed**
*Geçen zamanı döner.*<br>

r.elapsed.total_seconds()<br>

>0.566292


Kaynak : <br>
>https://medium.com/python/python-requests-mod%C3%BCl%C3%BC-4af79ebdb8c8<br>
>http://www.sinanerdinc.com/python-requests-modulu
