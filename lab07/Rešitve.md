<img width="945" height="611" alt="image" src="https://github.com/user-attachments/assets/38b6c3ae-b280-4856-a1ca-3beaa0615761" />
To mi ne dela. Čakala sem 15 minut in ni bilo nič.

Posnetek zalosna lažne spletne strani:
<img width="945" height="343" alt="image" src="https://github.com/user-attachments/assets/c2577fc4-fa03-4ff3-bdae-d52ee2b05708" />

Posnetek zaslona terminala s zajetimi podatki:
V terminalu nisem videla zajetih podatkov, videla sem jih z GET.
<img width="945" height="389" alt="image" src="https://github.com/user-attachments/assets/5bf23a6f-658b-4eba-b49a-3a6ed3b327fa" />
<img width="945" height="303" alt="image" src="https://github.com/user-attachments/assets/457f9a5a-75b1-4049-bc6c-967f598f18c9" />

Ker sem spremenila metodo post v get bi žrtev lahko prepoznala, da gre za phishing po tem ko bi že oddala informacije.
Žrtev bi lahko prepoznala da gre za phishing stran tudi po tem da ni https, ampak http ali po sumljivem URL.

Katere značilnosti so značilne za phishing strani (npr. napačen URL): napačen url, http namesto https, nedelujoče povezave, slabše kakovosti slik,
slovnične nepravilnosti, zahteve po podatkih, ki jih navadno ne potrebujemo za priajvo.
Kako bi se zaščitili pred takšnim napadom: MFA, Passwordmanagers, previdnost ko naletimo na sumljive strani
Moderne strani otežujejo phishing strani napade z https, varnostnimi certifikati, preverjanjem integritete naprave in preverjanjem lokacije.


# Prepoznavanje in preprečevanje phishing napadov

📅 **Trajanje: 2 uri**

Na tej vaji boste spoznali, kako delujejo phishing napadi, kako jih prepoznati in zakaj so nevarni. Praktično boste izvedli simulacijo phishing napada z uporabo Social Engineering Toolkita (SET) in preprostega obrazca ter analizirali zajete podatke.

# 🧪 Prepoznavanje in preprečevanje phishing napadov

Phishing je ena najpogostejših tehnik socialnega inženiringa, s katero napadalci uporabnike pretentajo, da sami vnesejo svoje prijavne podatke na lažno stran. Cilj te vaje je, da se naučite, kako takšne strani izgledajo, kako delujejo in kako pomembno je prepoznati znake napada.

---

## 1️⃣ Uvod

Cilj je, da se kot uporabniki naučimo kako:  
✅ prepoznati tipične znake phishing strani  
✅ izvesti simulacijo phishing napada z uporabo SET  
✅ analizirati zajete podatke in razumeti omejitve  
✅ ozavestiti pomen preverjanja URL in varnostnih indikatorjev

---

## 2️⃣ Aktivnost

### 🖥️ Navodila

Študenti boste izvedli naslednje korake in dokumentirali rezultate:

---

#### 1️⃣ Priprava testnega obrazca
- Na svojem računalniku naredite datoteko `login.html` z naslednjo vsebino:
```html
<!DOCTYPE html>
<html lang="sl">
<head>
<meta charset="UTF-8">
<title>Prijava</title>
</head>
<body>
<h2>Prijava v sistem</h2>
<form method="POST" action="">
  Uporabniško ime: <input type="text" name="username"><br>
  Geslo: <input type="password" name="password"><br>
  <input type="submit" value="Prijava">
</form>
</body>
</html>
```

Shranjeno stran odprite v brskalniku — to je preprost prijavni obrazec, ki ga bomo uporabili kot tarčo.

---

#### 2️⃣ Zagon SET in kloniranje strani
- Zaženite SET:
```bash
sudo setoolkit
```

- Izberite menije:
  ```
  1) Social-Engineering Attacks
  2) Website Attack Vectors
  3) Credential Harvester Attack Method
  2) Site Cloner
  ```

- Ko vas vpraša za IP naslov za zajem podatkov, vpišite svoj lokalni IP naslov (npr. `192.168.x.x`) ali pustite predlaganega.

- Za URL kloniranja vpišite pot do vaše `login.html`:
  ```
  file:///home/youruser/login.html
  ```

- SET bo pripravil lažno stran in začel poslušati na portu 80.

---

#### 3️⃣ Testiranje
- Odprite brskalnik in obiščite naslov:
  ```
  http://<tvoj_IP>
  ```
- Vpišite testne podatke (npr. uporabnik: `test`, geslo: `geslo123`).

- V SET terminalu boste videli zajete podatke:
  ```
  [*] WE GOT A HIT!
  username: test
  password: geslo123
  ```

---

### 📝 Analiza in poročilo

Oddajte poročilo z naslednjimi vsebinami:
- Posnetek zaslona lažne prijavne strani
- Posnetek zaslona terminala s zajetimi podatki
- Kratek opis, kako bi žrtev prepoznala, da gre za phishing stran

---

## 3️⃣ Refleksija in analiza

- Katere značilnosti so značilne za phishing strani (npr. napačen URL)?
- Kako bi se zaščitili pred takšnim napadom?
- Zakaj moderne strani otežujejo takšne napade?

---

📄 *Opomba: Vaja je namenjena izključno izobraževalnim namenom. Nikoli ne izvajajte teh tehnik na resničnih uporabnikih brez njihove vednosti in dovoljenja.*
