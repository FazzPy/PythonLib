# Python JSON Kütüphanesi

> Json kütüphanesi veri depolamak ve değiştirmek için kullanılır.

```python
import json

# Json Verisi :

x = '{ "ad":"Recep", "yas":30, "sehir":"Bursa"}'<br>

y = json.loads(x)

print(y["sehir"])

# Sonuç : Bursa gözükecektir.

```

*Python -> Json Dönüştürme*

```python

import json
 
# Python Objesi(dictionary):
x = {
  "ad": "Recep",
  "yas": 30,
  "city": "Bursa"
}
 
# JSON' a çevir:
y = json.dumps(x)
 
# JSON string:
print(y)
```
**Aşağıdaki türlerdeki Python nesnelerini JSON dizelerine dönüştürebilirsiniz :**
>dict<br>
list<br>
tuple<br>
string<br>
int<br>
float<br>
True<br>
False<br>
None<br>


