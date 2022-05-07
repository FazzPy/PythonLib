# Tkinter Kütüphanesi

>Ne işe yarar ?<br>

*Basit arayüzler oluşturmayı sağlıyan bir python kütüphanesidir.*<br>

>Kurulum <br>

**Linux : sudo apt-get install python3-pip**<br>
**pip3 install tkinter**<br>
**Windows : pip3 install tkinter<br>**
*Python yüklenirken birlikte gelen bir kütüphanedir fakat yine de olmayanlar için yazdım*

>**Örnek : Pencere Oluşturmak**

from tkinter import * #**Kütüphaneyi içe aktarır**<br>

root = Tk() #**Pencere atanır**<br>
root.geometry("500x500") #**Pencerenin boyutu ayarlanır**<br>
root.title("İlk pencerem") #**Pencerenin başlığı ayarlanır**<br>
root.iconbitmap("logo.ico") #**Pencerenin küçük iconu ayarlanır (Sadece ico dosyaları)**<br>
root.resizable(width=False, height=False) #**Pencerenin sonradan boyutu değiştirilmemesine ve sabit kalmasına yarar**<br>
color = "#4B524E" #**Arka plan renginin kodu**<br>
background = Label(bg=color, width=500, height=500)#**Arka plan rengi için kod**<br> 
background.place(x=0, y=0)#**Arka plan için label oluşturduk ve tüm ekranı kapladık ve seçtiğimiz renk oldu**<br>


root.mainloop() #**Pencere sonsuz döngüye sokulur ve otomatik kapanmaz**<br>

>**Kavramlar**

**Label : Bir itemdir istediğiniz gibi şekil veya yazı atıyabilirsiniz.**
**Button : Buton elemanıdır buton ekliyip özelliklerini ayarlıyabilirsiniz**
**Entry : Kullanıcıdan veri almak için bir yazı kutusudur**
**Kalanlarını alttaki örneklerde görebilirsiniz**


>**Bitmaps**

B1 = buton = Button(top, text ="error", relief=RAISED, bitmap="error")<br>
B1.pack()<br>
#**Bir adet buton eklre ve ona error adlı uyarıyı verir**


>**Button**

text1 = Button(root, text="yazi")<br>
text1.place(x=20, y=20)<br>

#**Resimli Buton : **

wallpaper1 = ImageTk.PhotoImage(Image.open("wallpaper.png"))<br>
Button1 = Button(root, image=resim1, width=130, height=50)<br>
Button1.place(x=20, y=80)<br>


>**Check Buton** #Onay kutusu getirir

Check1=Checkbutton(root, text = "Onayla", onvalue = 1, offvalue = 0, height=1, width = 10, bg="gray")<br>
Check1.place(x=0, y=0)<br>


>**Entry**

Entry1 = Entry(root, justify="left")<br>
Entry1.place(x=0, y=0)<br>


*Not : eklediğiniz kodun sonuna place eklerseniz direkt konumunu belirleyebilirsiniz örnek : buton.place(x=50, y=50)<br>

#*Varsayılan yazılı entry yazımı*

v = StringVar(root, value='default text')<br>
e = Entry(root, textvariable=v)<br>
e.pack()<br>
root.mainloop()<br>

state = readonly (Sadece Okumak için)#*Bunu kodun içine eklerseniz sadece okuyabilirsiniz yazı yazamazsınız*<br> 


>file dialog #Dosya seçtirir

**from tkinter import filedialog**<br>

**def dosyaKonumu():**<br>
    **root.filename = filedialog.askdirectory(initialdir="/", title="Klasör Seçin")**<br>
    
>imageTk #Resim belirtir

wallpaper = ImageTk.PhotoImage(Image.open("wallpaper.png"))<br>


>Label

sonuc = Label(root, text="Merhaba!",font="Courier 16 bold", width=20)<br>
sonuc.place(x=-50, y=20)<br>

>List Box # Liste kutusu belirler

Lb1 = Listbox(root, bg="orange")<br>
Lb1.insert(1, "Python")<br>
Lb1.insert(2, "Bash")<br>
Lb1.insert(3, "Ruby")<br>
Lb1.insert(4, "C++")<br>
Lb1.insert(5, "JavaScript")<br>
Lb1.insert(6, "C#")<br>
Lb1.insert(7, "Java")<br>
Lb1.insert(8, "Kotlin")<br>

Lb1.place(x=50, y=50)<br>

>Message Box #Uyarı kutusu verir bitmapsten kullanışlıdır

def dialog():<br>
    var = messagebox.showinfo("Selam!" , "Fazz")<br>



>overrideredirect #Pencerenin etrafındaki borderi siler 

root.overrideredirect(1)<br>

>radio buton işaretlemek için bir küçük yuvarlak bir buton getirir

R1 = Radiobutton(root, text="Option 1", variable=var, value=1<br>


>scrollbar #Aşağı yukarı indirmek için bir araç

scrollbar = Scrollbar(root, orient='vertical', command=degisken.yview)<br>
scrollbar.grid(row=0, column=1, sticky='ns')<br>


Orient = Yön<br>
Vertical = Dikey<br>


>**Top Level #ekstradan bir pencere daha açmaya yarar önemli ve kullanışlıdır**

def openscreen():<br>
    pencere2 = Toplevel(root, bg="#4B524E", height=400, width=400,)<br>
    pencere2.title("Selam!")<br>
    pencere2.resizable(width=False, height=False)<br>
    ceza1 = Button(pencere2, text="Naber", bg="#4B524E", fg="white")<br>
    ceza1.place(x=10, y=10)<br>



**Butona fonksiyon atama**

def komut():<br>
  pass<br>

buton = Button(text="Selam ben buton", command=komut)<br>

**Fazladan Command Atama**
command=lambda:[komut1(), komut1()]<br>


**İçeriklerimiz bu kadardı kendi notlarımdan yazdım son bonus olarak mail gönderme kodu yazmak istiyorum projelerinizde işe yarar**<br>

import smtplib<br>

content = "Content"<br>
mail = smtplib.SMTP("smtp.gmail.com",587)<br>
mail.ehlo()<br>
mail.starttls()<br>
mail.login("YourMail","MailPsw")<br>
mail.sendmail("Your Mail","Sended Mail",content)<br>








