# Python | Veri Tabanı
## MongoDB

```python

class MongoDB():

  # https://cloud.mongodb.com/ Sitesinden mongodb ayarlanabilir

  def ekle():

    data = {
        "name":"Can",
        "age":"18"
    }

    collection.insert_one(data) #Bir adet veri ekler. (insert_many) daha fazla eklemeyi sağlar
    print(Fore.RED+"Veri ekleme tamamlandı.")
    #Veriye {"_id":1,} eklersek id belirleyebiliriz.


  def bul():
    print(collection.find_one()) #Tek ilk veriyi gösterir.
    print(Fore.RED+"İlk veri gösterildi.")

    for i in collection.find():
      print(i) #Tüm verileri gösterir.
    
    print(Fore.RED+"Tüm veriler gösterildi.")
    
    for i in collection.find({},  {"_id":0, "name":1}):
      print(i) #İlk süslü parantez SQL Komutları için ikincisi ise görmek istediğimiz sütunları alıyoruz.
      print(Fore.CYAN+"İstediğiniz veriler bulundu.")
      #Yazdırmak istediğimiz sütunlara 1 istemediğimiz sütunlar 0 olur.
      #ilk id stünuna 0 verirsek diğerlerine vermemize gerek yok.

  def sorgu():
    print(Fore.LIGHTMAGENTA_EX+"Sorgu başlıyor...")

    #Yazdığımız kişiyi veri tabanında bulur
    # "age":{"$gt":25} 25 Ten büyük olanları alır. | Örnek Kod :
    #for i in collection.find({"age":{"$gt":25} }, {"_id":0}):
    # print(i) #$gte yazarsak 25 ve üstünü alır. # $lt yazarsak aşağısını alır lte olursa 25 ve aşağısını alır.
    # "$ne": 30 yazarsak 30 olmayanları getirir.
    # "$in":[30,21] 30 ve 21 sayılarını getirir. # "$nin" olursa 30 ve 21 olmayanları getirir.
    sorgu = {"name":"Batın"}
    for i in collection.find(sorgu,{"_id":0}):
      print(i)

    print(Fore.LIGHTBLUE_EX+"Regex Sorgusu başlıyor...")

    for i in collection.find({"name": {"$regex": "." } }):
      print(i) # . koyarsak tüm veriyi getirir.
      # https://regex101.com/ Sitesinden daha çok regex hakkında araştırma yapılabilir.

    print(Fore.WHITE+"Sort sorgusu başlıyor...")
    for i in collection.find().sort("age", -1):
      print(i) # Yaşa göre sıralama yapar yaşı olmayanları en üste verir. 
      # 1 yerine -1 yazarsanız büyükten küçüğe sıralama yapar

    print(Fore.LIGHTBLACK_EX+"And / Or Sorguları başlıyor...")
    for i in collection.find({"$and": [{"name":"Batın"}, {"age":16}] }):
      print(i) # Adı batın ve yaşı 16 olanı getirir

    for i in collection.find({"$or":[{"name":"Batın"}, {"age":"16"}] } ):
      print(i) # ya ismi batın olanı yada yaşı 16 olanı getirir.

  def güncelle():
    print(Fore.LIGHTYELLOW_EX+"Güncelleme başlıyor...")

    a = {"name":"Batın", "age":16} #Şuanki veri
    b = {"$set", {"age":17}} #Güncellenicek veri

    collection.update_one(a,b) # Tek bir veriyi günceller.


    for i in collection.find():
      print(i) # Tüm verileri gösterir.

  def limit():
    print(Fore.LIGHTRED_EX+"Limit sorguları başlıyor...")
    for i in collection.find({}, {"_id":0}).limit(40):
      print(i) # ilk 40 veriyi getirir bu yaş için vs. olabilir daha araştırılacak.

  def silme():
    print(Fore.RED+"Silme işlemi başlıyor...")

    for i in collection.find():
      print(i)

    a = { "name":"Batın" }
    
    collection.delete_one(a)

    # Tüm verileri silmek için.

    collection.delete_many({})

    collection.drop() # Tabloyu siler

    # Tekli silmek için aşağıdaki gibi de yapılabilir.

    collection.remove({"name":"Batın"})


```
