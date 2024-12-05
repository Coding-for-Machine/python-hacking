### SSH 
yordamida boshqa kompyuterga masofaviy ulanish mumkin. SSH (Secure Shell) — bu masofaviy kompyuterga xavfsiz ulanish protokoli.
Siz SSH orqali boshqa kompyuterga, serverga yoki virtual mashinaga ulanish va undagi tizimni boshqarish imkoniyatiga ega bo‘lasiz. 
Bu ulanishda ma'lumotlar shifrlanadi, bu esa ulanishni xavfsiz qiladi.
<br>
```bash
pip install paramiko
```
**SSH (Secure Shell)** — bu kompyuterlar o‘rtasida xavfsiz muloqotni ta’minlash uchun ishlatiladigan tarmoq protokoli.
SSH yordamida masofadagi serverlarga ulanish, ulardagi fayllarni boshqarish va buyruqlarni bajarish mumkin.
Bu protokol parol yoki kalit-fayl asosida ishlaydi va barcha ma’lumotlarni shifrlaydi, shuning uchun ular xavfsiz bo‘ladi.

### SSH asosiy xususiyatlari
#### **Xavfsizlik:* SSH orqali uzatiladigan barcha ma’lumotlar shifrlanadi, shuning uchun ma’lumotlar uchinchi shaxslar tomonidan o‘g‘irlanmaydi.
#### **Masofaviy boshqaruv:* SSH yordamida masofadagi kompyuter yoki serverni boshqarishingiz mumkin.
#### **Tunneling va port forwarding:* SSH xavfsiz kanallar orqali boshqa xizmatlarni ham boshqarish imkonini beradi.
#### **Kalit asosida autentifikatsiya:* SSH parol yoki maxsus kalit fayllardan foydalanadi, bu esa xavfsizlikni oshiradi.
<hr>

### **SSH qanday ishlaydi?*
### SSH asosida ikkita asosiy element ishlaydi:

#### SSH Client: Bu foydalanuvchi kompyuterida o‘rnatilgan dastur bo‘lib, masofaviy serverga ulanishni amalga oshiradi.
#### SSH Server: Bu masofaviy kompyuter yoki server bo‘lib, SSH orqali kirish so‘rovlarini qabul qiladi.
Ulanish jarayoni quyidagicha bo‘ladi:

Foydalanuvchi SSH Client orqali masofaviy serverga ulanish uchun so‘rov yuboradi.
Server ulanishni tasdiqlash uchun foydalanuvchining paroli yoki kalit-faylini tekshiradi.
Tekshirish muvaffaqiyatli bo‘lsa, server bilan shifrlangan kanal o‘rnatiladi.
SSH-dan foydalanish
Linux yoki MacOS tizimlarida
Linux va MacOS tizimlarida SSH terminal orqali o‘rnatilgan bo‘ladi. Buyruqlar quyidagicha ishlatiladi:
### 1-Masofaviy serverga ulanish:
```bash
ssh username@server_ip
```
### MISOL
```bash
ssh root@192.168.1.10
```
### 2-Portni ko‘rsatib ulanish: Agar server boshqa portda ishlayotgan bo‘lsa (standart port 22):
```bash
ssh -p 2222 username@server_ip
```
### Fayl yuborish va yuklab olish (SCP):
#### Faylni masofaviy serverga yuborish:
```bash
scp /path/to/local/file username@server_ip:/path/to/remote/destination
```
**Faylni serverdan yuklab olish**
```bash
scp username@server_ip:/path/to/remote/file /path/to/local/destination
```
## Linux/Mac
```bash
sudo apt update
sudo apt install openssh-server
```

## Windows:
Windows 10 va keyingi versiyalarda OpenSSH serverini o‘rnatishingiz mumkin. PowerShell yordamida quyidagicha:
```bash
Add-WindowsFeature -Name OpenSSH-Server
Start-Service sshd
```
2. Ikkinchi Kompyuteringizning IP Manzilini Tekshirish
Ikkinchi kompyuteringizning IP manzilini aniqlash uchun quyidagi buyruqni ishlating:

***Linux/MacOS:**
```bash
ifconfig
```
**Windows**
```bash
ipconfig
```
Misol uchun, IP manzilingiz 192.168.1.20 bo‘lishi mumkin


Agar Windows kompyuteriga SSH orqali ulanishni xohlasangiz va Windows tizimida PowerShell yoki CMD yordamida ulanishni xohlasangiz, quyidagi qadamlarni bajarishingiz kerak bo‘ladi:

1. Windows kompyuterida SSH serverini yoqish (Windows 10 va undan yuqori versiyalar)
Windows 10 va undan keyingi versiyalarida OpenSSH serveri o‘rnatilishi mumkin. Agar sizning Windows kompyuteringizda SSH server yoqilmagan bo‘lsa, uni quyidagi qadamlar bilan yoqishingiz mumkin:

a) PowerShell yordamida SSH Serverni o‘rnatish
PowerShell ni administrator sifatida oching (Start menyusidan "PowerShell" deb qidiring, so‘ng "Run as Administrator" ni tanlang).

SSH serverni o‘rnatish uchun quyidagi buyruqni yozing:

powershell
Copy code
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
SSH serverni ishga tushirish:

powershell
Copy code
Start-Service sshd
SSH serverni avtomatik ravishda ishga tushirish uchun:

powershell
Copy code
```bash
Set-Service -Name sshd -StartupType 'Automatic'
Windows firewallda SSH portini (22-port) ochish:
```
powershell
Copy code
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Protocol TCP -Action Allow -LocalPort 22
2. Windows kompyuteringizning IP manzilini aniqlash
Ikkinchi kompyuteringizning (Windows) IP manzilini aniqlash uchun PowerShell yoki CMD ni ochib, quyidagi buyruqni yozing:

powershell
Copy code
```bash
ipconfig
```
IP manzilingizni toping, masalan, 192.168.1.20.

3. Birinchi kompyuterdan (Linux/MacOS) SSH orqali ulanish
Endi, sizning birinchi kompyuteringizda (masalan, Linux yoki MacOS) quyidagi buyruqni yozib, Windows kompyuteringizga ulanishni amalga oshirishingiz mumkin:

bash
Copy code
```bash
ssh username@192.168.1.20
```
username – Windows kompyuteringizdagi foydalanuvchi nomi.
192.168.1.20 – Windows kompyuteringizning IP manzili.
Agar ulanishda birinchi marta xatolik yuz bersa, sizdan "Are you sure you want to continue connecting (yes/no)?" degan savol so‘raladi. "yes" deb javob bering.

4. Parolni kiritish
Ulanish muvaffaqiyatli bo‘lsa, sizdan Windows kompyuteringizdagi foydalanuvchi nomiga tegishli parolni kiritish so‘raladi. Parolni kiritganingizdan so‘ng, Windows kompyuteriga ulanishni amalga oshirasiz.

5. Windows PowerShell orqali SSH ulanish
Agar siz Windows tizimidan boshqarish uchun PowerShell yoki CMD orqali SSH ulanishni xohlasangiz, quyidagi buyruqlarni ishlatishingiz mumkin:

PowerShell yoki CMD orqali SSH orqali ulanish:
powershell
Copy code
```bash
ssh username@192.168.1.20
```
Xulosa
Windows kompyuteriga SSH orqali ulanish uchun yuqoridagi qadamlarni bajaring. Windows kompyuterida SSH serverini o‘rnatib, firewall orqali portni ochish orqali ulanishni amalga oshirasiz. Agar boshqa savollaringiz bo‘lsa yoki ulanishda muammo yuzaga kelsa, so‘rashingiz mumkin.


