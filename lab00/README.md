# 🐧 Uvod v Linux: osnove dela v ukazni lupini

V prvem delu si bomo podrobneje pogledali (in ponovili) delo z ukazno vrstico v operacijskem sistemu Linux OS.

Linux je odprtokodni operacijski sistem podoben Unixu. Unix je bil razvit v 70-ih letih prejšnjega stoletja v Bell Labs. Takrat je veljal za prvi večuporabniški večopravilni operacijski sistem. Iz njega je na univerzi v Berkley izšla posebna različica poznana kot "Berkley Software Distribution" ali BSD. Danes mu jee zelo podoben tudi MacOS, ki izhaja iz družine BSD, konkretno FreeBSD. 

Linux sicer označuje ime jedra operacijskega sistema. Na voljo pa je veliko distribucij, ki temeljijo na Linux jedru: Debian, Ubuntu, Fedora, CentOS, Kali Linux, Arch Linux, ...



## 🎯 Cilj
Naučiti se osnovnega dela z ukazno vrstico v Linux okolju. 

Pri tej vaji bomo spoznali kako:  
✅ izvajamo osnovne ukaze v Linuxu  
✅ pregledamo imenike, ustvarimo imenike in datoteke  
✅ se povežemo na Linux strežnik preko ssh  

---

## ⚙️ Priprava okolja

Za to vajo bomo uporabili [GitHub Codespaces](https://github.com/features/codespaces)

GitHub Codespaces je razvojno okolje, ki gostuje v oblaku. Namenjeno je sicer razvoju projektov, kjer se povežemo z GitHub repozitorijem, kar omogoča, da razvijamo v sklopu spletnega brskalnika, dostopamo pa lahko tudi do virtualnega okolja.

Zaželjeno je, da si za potrebe vaj do naslednjič pripravite svoje virtualno okolje bodisi:
- znotraj virtualega okolja (VMWare, VirtualBox ipd.)
- Windows Subsystem for Linux (WSL)
- Microsoft Azure ali druga oblačna storitev
- obstoječe okolje v kolikor uporabljate Linux OS/Max OS X/BSD ipd. 

Priporočeno je, da si namestite distribucijo Kali Linux, ki že vključuje vsa orodja, ki jih bomo uporabljali v sklopu vaj.

---

## 🧪 Ustvarjanje Github Codespace okolja:

1. Na povezavi [GitHub Codespaces](https://github.com/features/codespaces) izberemo opcijo "Get  started for free"
2. Na levi strani ali preko hitrega dostopa izberemo opcijo "Blank"
3. Github Codespaces bo za nas ustvaril spletno okolje preko katerega lahko dostopamo do ukazne vrstice. 

Privzeto Github Codespaces ne omogoča dostopa preko SSH, zato bomo uporabili trik in si uredili dostop preko SSH. Za produkcijsko reštitev tovorsten pristop odsvetujem, uporabite raje gh cli. Nadlednji del služi zgolj kot demonstracija. 

Najprej ustvarimo uporabnika s katerim bomo delali, da ne uporabljamo prizetega uporabnika.

```bash
whoami              # preverimo trenutnega uporabnika
sudo adduser user   # user je vaše željeno uporabniško ime, čarovnik nas bo vprašal po geslu in podatkih uporabnika, kar potrdimo. Pozor: geslo se ne vidi, ko se vpisuje.
sudo usermod -aG sudo user
sudo visudo
```

Dodamo naslednji zapis pod # User privilege specification
```bash
user ALL=(ALL:ALL) ALL
```

Sedaj zaženemo SSH storitev
```bash
sudo service ssh start      # zagon storitve ssh
sudo apt update             # posodobimo seznam paketov
sudo apt install tmate      # namestimo paket tmate
tmate # zaženemo tmate
```

Izpiše se nam podatek za povezavo na ssh preko posebne seje. S Ctrl + C prekinemo izpis in dobimo dostop do uporabe ukazne vrstice.

## 🧪 Povezava na strežnik

Na strežnik se lahko prijavimo iz obsoječe lupine. 
```bash
su - user # preklopimo na uporabnika, ki smo ga ustvarili in vpišemo geslo
```

## 🧪 Vaja: Osnovni ukazi

### 1️⃣ Krmarjenje po sistemu
```bash
pwd           # prikaže trenutno pot
ls            # prikaže vsebino imenika
ls -l         # prikaže vsebino s podrobnostmi
cd /pot/do/imenika  # spremeni imenik
cd ..         # premik na nadrejeni imenik
```

✅ **Naloga:**  
- Premaknite se v domači imenik.
- Ustvarite imenik `linux-vaja`.
- Vstopite vanj.

---

### 2️⃣ Delo z datotekami in imeniki
```bash
mkdir novaMapa         # ustvari nov imenik
touch datoteka.txt     # ustvari prazno datoteko
nano datoteka.txt      # urejanje vsebine (ali `vim` / `code`)
cat datoteka.txt       # izpiše vsebino
rm datoteka.txt        # izbriše datoteko
rm -r novaMapa         # izbriše imenik z vsebino
```

✅ **Naloga:**
- Ustvarite datoteko `opis.txt` in vanjo zapiši svoje ime.
- Ustvarite imenik `testni`.
- Premaknite `opis.txt` v `testni`.

---

### 3️⃣ Premikanje in kopiranje
```bash
mv dat.txt druga.txt            # preimenuje datoteko
cp file1.txt file2.txt          # kopira datoteko
mv file.txt /pot/do/drugamape/  # premik
```

✅ **Naloga:**
- Preimenujte `opis.txt` v `moj_profil.txt`.
- Kopirajte `moj_profil.txt` v domačo mapo.

---

### 4️⃣ Pravice in velikosti
```bash
ls -lh          # velikost in pravice
du -sh ./*      # velikost datotek/imenikov
chmod 644 file  # spremeni pravice
```

✅ **Naloga:**
- Preverite velikost vseh datotek v mapi.
- Spremenite pravice datoteki `moj_profil.txt` tako, da je samo za branje za vse.

---

### 5️⃣ Prikaz sistemskih informacij
```bash
whoami           # tvoje uporabniško ime
uname -a         # podatki o sistemu
df -h            # poraba diska
top              # aktivni procesi
```

✅ **Naloga:**
- Ugotovite ime svojega uporabnika in velikost domačega imenika.
- Preverite, koliko prostora je na voljo v sistemu.

---

## 💡 Dodatna naloga
Poiščite največjo datoteko v svojem domačem imeniku:

```bash
du -ah ~ | sort -rh | head -n 5
```


## Reference

1. Reddit, SSH into Codespace without GitHub CLI, https://www.reddit.com/r/github/comments/15pvnj3/comment/kd23ess/

2. OpenAI, (2025), *ChatGPT* (Aug 2025) [Large language model], https://chat.openai.com/


tamaral@codespaces-d623b7:~$ touch vaja00.txt
tamaral@codespaces-d623b7:~$ history >> vaja00.txt
tamaral@codespaces-d623b7:~$ cat vaja00.txt
    1  whoami
    2  pwd
    3  cd /home/tamaral/
    4  pwd
    5  mkdir linux-vaja
    6  cd /home/tamaral/linux-vaja
    7  pwd
    8  touch opis.txt
    9  echo "Tamara" >> opis.txt
   10  cat opis.txt
   11  mkdir testni
   12  mv opis.txt /home/tamaral/linux-vaja/testni
   13  ls
   14  ls -l
   15  mv opis.txt moj_profil.txt
   16  cd /home/tamaral/linux-vaja/testni/
   17  ls
   18  mv opis.txt moj_profil.txt
   19  ls
   20  cat moj_profil.txt
   21  cp moj_profil.txt ~/
   22  ls -lh
   23  chmod 400 moj_profil.txt
   24  ls -lh
   25  cd /home/tamaral/
   26  whoami
   27  du -sh
   28  du -sh ~
   29  df -h
   30  du .ah ~ | sort -rh | head -n 5
   31  du -ah ~ | sort -rh | head -n 5
   32  touch vaja00.txt
   33  history >> vaja00.txt