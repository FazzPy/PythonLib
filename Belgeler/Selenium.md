# Python | Selenium Notları

> Not : Bu bir anlatım veya kaynak değildir. Kendi çalışma notlarımdır.<br>
> **Aşağıya daha iyi öğrenebileceğiniz kaynaklar bıraktım.**

```python

# Giriş

from selenium import webdriver # Kütüphaneler Eklenir

driver = webdriver.Chrome() # Browser belirlenir

url = "https://batinolez.ml" # İşlem yapılıcak site belirtilir

driver.get(url)

```


```python
# Temeller

# Kütüphaneler Eklenir
from selenium import webdriver 
import time


driver = webdriver.Chrome() # Browser belirlenir.

url = "https://github.com" # İşlem yapılıcak site belirtilir.

driver.get(url) # Belirlediğimiz sayfaya browser aracılığıyla gider.

time.sleep(2) # 2 Saniye Bekler.

driver.maximize_window() # Ekranı büyütür.

driver.save_screenshot("github-homepage.png") # Ekran görüntüsü alır ve kaydeder.

print(driver.title) # Gittiğimiz sitenin başlığını yazdırır.

url = "https://github.com/FazzPy"

driver.get(url) # 2. Belirlediğimiz sayfaya gider.

driver.save_screenshot("fazz-page.png")# 2. Belirlediğimiz sayfadan ekran görüntüsü alır.

print(driver.title) # Gittiğimiz sitenin başlığını yazdırır.

time.sleep(2)

driver.back() # Eski sayfaya döner.
# İleriye gitmek için forward kullanılır.

time.sleep(2)

url = "https://batinolez.ml" # Yeni sayfa belirleriz

driver.get(url) # Yeni sayfaya gider

# Eğer yeni sayfanın başlığı Batın Ölez ise ekran başlığı yazdır ve ekran görüntüsü al.

if "Batın Ölez" in driver.title:
    print(driver.title)
    driver.save_screenshot("batin.png")

time.sleep(2)

driver.back() # Geri dön.

time.sleep(2)

driver.close() # Tarayıcıyı kapatır.

```

```python
# Son

# Kütüphaneler ekleniyor

from selenium import webdriver
from selenium.webdriver.common.keys import Keys # Tuşlara basmak için kullanılır.
from selenium.webdriver.common.by import By
import time


driver = webdriver.Chrome()

url = "http://github.com"

driver.get(url)

searchInput = driver.find_element("name", "q") # Elementi isim ile arar ve q adlı elementi bulur.

searchInput.send_keys("FazzPython") # FazzPython yazdırır.

time.sleep(1)

searchInput.send_keys(Keys.ENTER) # Enter'a basar.

result = driver.find_elements(By.CSS_SELECTOR, ".repo-list-item em") # CSS İle seçim yapar

# Not : By.XPATH, "" kodu ile seçim yapılabilir.

for element in result:
    print(element.text) # Verilerin hepsini çıkartır


time.sleep(5)


driver.close() # Browseri kapar


```

**Kaynaklar :**<br>
*https://www.btkakademi.gov.tr/portal/course/sifirdan-ileri-seviye-python-programlama-5877*<br>
*https://selenium-python.readthedocs.io/*<br>
*https://www.geeksforgeeks.org/selenium-python-tutorial/*<br>
*https://networkdersleri.net/2021/09/26/python-selenium-kullanimi/*<br>

