# Python | Cryptography Kullanımı

> Windows : pip install cryptography<br>
> Linux/MacOs : pip3 install cryptography

**Not : Bu kodlar benim notlarımdır. Daha fazla öğrenmek için en aşağıya kaynak bıraktım.**

```python

from cryptography.fernet import Fernet

def write_key():
    key = Fernet.generate_key() # Key üretme
    with open("key.key", "wb") as key_file: # Key'in yazılacağı dosyayı açar
        key_file.write(key) # Key'i yazar
        
def load_key():
    return open("key.key", "rb").read() # Dosyayı açar, dosyada kayıtlı key'i okur ve return eder

message = input("Şifrelenecek Mesaj: ").encode() # Mesajı alır ve şifreler
write_key() # Key'i key dosyasına yazar

key = load_key() # Key'i yükler ve değişkene atar

# Yukarıda oluşturduğumuz değişkeni fernet ile başlatıyoruz.

f = Fernet(key)

# Şimdi girilen mesajı şifreleyip yazdıralım.

encrypted_message = f.encrypt(message)
print(encrypted_message)

# Şifreyi çözmek için;

decrypted_message = f.decrypt(encrypted_message)
print("<-----> Şifresi Çözülmüş Mesaj <----->")
print(decrypted_message)

```

Kaynaklar :<br>
https://www.tutorialspoint.com/cryptography_with_python/cryptography_with_python_quick_guide.htm<br>
https://ichi.pro/tr/python-kullanarak-uygulama-sifresini-sifreleme-ve-sifresini-cozme-23679175134191<br>
https://onursahin.net/python-ile-veri-sifreleme-ve-cozme-fernet/<br>
