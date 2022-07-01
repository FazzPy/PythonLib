# Python | Beatiful Soup

> Not : Bunlar bir anlatımdan çok benim notlarımdır. En altta daha fazla kaynak verilmiştir.<br>

> Bunları daha rahat anlamak için temel html bilginiz olması gerekiyor.

```python

# Bu kodda N11 Datasını çekiyoruz

# Kütüphaneler
import requests
from bs4 import BeautifulSoup

# Verileri çekilecek sitenin url adresi
Url = "https://www.n11.com/bilgisayar/dizustu-bilgisayar"

html = requests.get(Url).content # Requests ile htmli çekiyoruz.

Soup = BeautifulSoup(html, "html.parser") # Çektiğimiz html belgesini yalınlaştırıyoruz.

Liste = Soup.find_all("li", {"class":"column"}, limit=5) # HTML Belgesindeki li'lerdeki sınıfı column olanları çağırıyoruz
# limit kaç adet çıkarılıcağını gösterir yazmazsanız hepsini gösterir.

for x in Liste:
    name = x.div.a.h3.text.strip() # Verinin ismini çeker ve boşlukları siler.
    
    link = x.div.a.get("href") # Verinin adresini alır.
    
    oldprice = x.find("div", {"class":"priceContainer"}).find_all("span")[0].text.strip().strip("TL")
    
    # priceContainer sınıfndaki spanları çekip boşlukları ve "TL" yazılarını siler
    
    newprice = x.find("div", {"class":"priceContainer"}).find_all("span")[1].text.strip().strip("TL")
    rating = x.find("div", {"class":"proDetail"}).find_all("span")[1].text.strip()
    
    #proDetail sınıfndaki spanlardaki 1. olanı çeker ve boşlukları siler.
    
    print(f"""
    Bilgisayar : {name}  
    Link : {link}     
    İndirimsiz Fiyat : {oldprice} TL
    İndirimli Fiyat : {newprice}  TL
    Rating : {rating}
    """)

```

**Kaynaklar :**<br>
*https://www.btkakademi.gov.tr/portal/course/sifirdan-ileri-seviye-python-programlama-5877*<br>
*https://beautiful-soup-4.readthedocs.io/en/latest/*<br>
*https://realpython.com/beautiful-soup-web-scraper-python/*<br>
*https://yasar11732.github.io/python/beautiful-soup-ve-basitce-kullanimi.html*

