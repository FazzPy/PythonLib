# Fazz | Python RSA Kütüphanesi

> pip install rsa

**Not : Bunlar benim notlarımdır.**

```python
import rsa

mesaj = "Hello GitHub!".encode("utf-8")

PublicKey, PrivateKey = rsa.newkeys(512) # Public ve Private Key belirliyoruz

crypto = rsa.encrypt(mesaj, PublicKey) # Mesajı şifreliyoruz

print(crypto)

message = rsa.decrypt(crypto, PrivateKey) # Şifreyi çözüyoruz

print(message.decode("utf-8"))

```

*Kaynak : [Documentation](https://stuvel.eu/python-rsa-doc/index.html)*
