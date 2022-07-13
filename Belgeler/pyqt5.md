# Python | PyQt5 Notları

## Made By Fazz

> Burdaki kodlar benim notlarımdır.<br>
> **Daha fazla öğrenmeniz için en alta kaynaklar, indirme linkleri ve eğitimler bıraktım.**


**Pencere Oluşturma :**
```python
import sys
from PyQt5 import QtWidgets
from PyQt5.QtWidgets import QApplication, QMainWindow, QToolTip
from PyQt5.QtGui import QIcon

# Pencere Oluşturma

def Window():
    app = QApplication(sys.argv) # Uygulamayı belirler
    win = QMainWindow() # Pencereyi belirler
    
    win.setWindowTitle("My First Screen!") # Pencere başlığıdır.
    win.setGeometry(200,200,500,500) # 200,200 Konum bilgisidir | 500,500 Pencere boyutu
    win.setWindowIcon(QIcon("icon.png")) # Başlık iconudur.
    
    win.setToolTip("My Tool Tip") # Mouse bir süre durduğunda altında yazı belirir.
    
    win.show() # Pencereyi gösterir
    sys.exit(app.exec_()) # Çarpıya basınca kapanmasını sağlar(Yazılması zorunludur.)
    
Window()

```

Araçlar ve Objelerin eklenmesi :

```python

import sys
from PyQt5 import QtWidgets
from PyQt5.QtWidgets import QApplication, QMainWindow, QToolTip
from PyQt5.QtGui import QIcon


# Araçlar ve Objeler oluşturma

def Window():
    app = QApplication(sys.argv)
    win = QMainWindow()
    
    win.setWindowTitle("My First Screen!")
    win.setGeometry(200,200,700,700)
    win.setWindowIcon(QIcon("icon.png"))
    win.setToolTip("My Tool Tip")
    
    
    lbl_name = QtWidgets.QLabel(win, ) # Label(Yazı Cismi) Oluşturur. 
    lbl_name.setText("Name : ") # Yazılacak metin belirlenir.
    lbl_name.move(50,30) # Label'ın konumunu belirler.
    
    lbl_surname = QtWidgets.QLabel(win, )
    lbl_surname.setText("Surname : ")
    lbl_surname.move(50, 70)
    
    txt_name = QtWidgets.QLineEdit(win) # Text(Giriş Cismi Oluşturur(Entry)).
    txt_name.move(100, 30) # Text'in konumunu belirler.
    
    txt_surname = QtWidgets.QLineEdit(win)
    txt_surname.move(100, 70)
    
    # Buton için işlev fonksiyonu yazılıyor.
    
    def clicked(self):
        print("Name : "+txt_name.text()+" | "+"Surname : "+txt_surname.text())
    
    btn_save = QtWidgets.QPushButton(win) # PushButton(Buton Cismi Oluşturur).
    btn_save.setText("Save") # Butona yazı verir.
    btn_save.move(100, 120) # Butonun konumunu belirler.
    
    btn_save.clicked.connect(clicked) # Butona fonksiyon ile işlev belirlenir. Parantez içindeki işlev fonksiyonudur.
    
    
    win.show()
    sys.exit(app.exec_())
    
Window()

```

Not : Üstteki kodları icon.png adlı dosya olmadan veya icon kodunu silmeden çalıştıramazsınız.

Kaynaklar :

BTKAkademi : https://www.btkakademi.gov.tr/portal/course/sifirdan-ileri-seviye-python-programlama-5877
Qt Designer  : build-system.fman.io/qt-designer-download
Tutorialspoint : https://www.tutorialspoint.com/pyqt5/index.htm
PyQt6 Tutorial : https://www.pythonguis.com/pyqt6-tutorial/
Jie Jenn : https://www.youtube.com/watch?v=tlhFIAymKnQ&list=PL3JVwFmb_BnRpvOeIh_To4YSiebiggyXS
PyQt6 Parwiz : https://www.youtube.com/watch?v=ot94H3-d5d8

