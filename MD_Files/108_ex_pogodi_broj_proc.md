## Pogodi broj

Implementirajmo još jedan jednostavan program: igru "pogodi broj."
Zamislimo prvo ovu igru kao da je igraju dvije osobe. Jedan igrač tajno
odabire broj u nekom rasponu, na primjer između jedan i sto. Drugi igrač
zatim pokušava pogoditi broj tako što kaže neki broj koji je prvi igrač
mogao odabrati i kaže ga prvom igraču. Prvi igrač tada odgovara s
"Točno!" ukoliko je drugi igrač pogodio broj ili s "Ne, odabrani broj je
veći." ili "Ne, odabrani broj je manji." kako bi dao drugom igraču
dodatne informacije za pogađanje broja.

Kako ovo isprogramirati? Korisno je prvo riječima opisati
najjednostavniji oblik ovog programa.

1. ṗrogram mora odabrati slučajan broj u određenom rasponu

2. ṗrogram mora obavijestiti korisnika o tome u kojem rasponu se traži
broj

3. k̇orisnik mora unijeti neki broj

4. ṗrogram mora provjeriti da li je taj broj odabrani broj i zatim:

    a) ȧko je korisnik pogodio broj, ispisati mu da je uspješno završio igru

    b) ȧko korisnik nije pogodio broj, ispisati mu da li je traženi broj veći
ili manji i zatražiti ga da unese novi broj

5. k̇oraci 3. i 4. se moraju ponavljati sve dok korisnik ne uspije pogoditi
broj

Kao što vidimo, u ovom programu potrebna nam je mogućnost odabira nekog
slučajnog broja. Ovo je česta potreba u programiranju pa većina
operativnih sustava i programskih jezika uključuje ovu mogućnost. Za
vježbu, pokušajte sami pronaći kako s Pythonom generirati slučajan
cijeli broj. Ovakve potrebe, naime, ne valja učiti na pamet već se
potrebno moći sam snaći pretraživanjem dokumentacije ili weba.

Pokušajte sami implementirati opisani program prije no što nastavite
čitati skriptu!

Kada pokrenemo prikazani program i unosimo brojeve sve dok ne pogodimo
traženi broj ispis izgleda otprilike ovako:

```python
# Pogodi broj između 1 i 100.

>>> Pogodi broj: 50
Nije točno! Broj je veći.

>>> Pogodi broj: 75
Nije točno! Broj je veći.

>>> Pogodi broj: 87
Nije točno! Broj je veći.

>>> Pogodi broj: 95
Nije točno! Broj je veći.

>>> Pogodi broj: 97
Nije točno! Broj je manji.

>>> Pogodi broj: 96
BRAVO!
```

Kao što vidimo, u Pythonu je odabir slučajnih brojeva potpomognut
standardnim modulom ‘random‘. Funkcija za odabir slučajnih cijelih
brojeva zove se ‘randint‘ i njeno korištenje za odabir slučajnog broja
između 1 i 100 izgleda ovako: ‘n = random.randint(1, 100)‘. Ova funkcija
uključuje obje granice kao mogući rezultat, odnosno u prijašnjem slučaju
mogu se odabrati i ‘1‘ i ‘100‘. Naravno, ovo su detalji koje također
nije potrebno znati na pamet, jednostavno je previše toga i detalji se
mogu razlikovati među programskim jezicima. Sjetite se da ako nas
zanimaju detalji vezani za tu funkciju, to možemo lako dobiti tako što u
Python komandnu liniju uvezemo modul random s ‘import random‘, a zatim
izvršimo ‘help(random.randint)‘.

U svakom slučaju, ovo je relativno jednostavan program koji opet
demonstrira mogućnosti petlje ‘while‘. Vježbe radi, doraditi ćemo ga
kako bi demonstrirali razlike između petlji ‘for‘ i ‘while‘. Program
sada korisniku dopušta pogađanje broja bilo koji broj puta. Kako
doraditi program da dopušta samo određen broj pokušaja? Drugim riječima,
ako korisnik prebaci, na primjer, pet ili deset pokušaja, program mu
treba javiti da nije uspio pogoditi broj u dozvoljenom broju pokušaja i
završiti igru.

Pokušajte sami implementirati ovu nadogradnju.

Rješenje koje koristi petlju ‘while‘ bi moglo izgledati ovako. Korisniku
smo u ispisu prikazali i broj pokušaja.

Ovo možemo riješiti i petljom ‘for‘. Sada naime, znamo da kod želimo
ponoviti točno n puta (dozvoljen broj pokušaja) što pogoduje korištenju
petlje while. Prikazano je i dobar primjer za korištenje mogućnosti ‘for
... else‘.ž

```
 1 import random
 2
 3 # definiraj osnovne postavke za program
 4 n_min = 1
 5 n_max = 100
 6 n_max_tries = 7 # definiraj dozvoljen broj pokušaja
 7
 8 # postavi interne vrijednosti za rad ovog programa
 9 n = random.randint(n_min, n_max) # odaberi broj koji će se pogađati
 10
 11 print('Pogodi broj između', n_min, 'i', n_max)
 12
 13 # ponavljaj sljedeće radnje do maksimalnog broja pokušaja
 14 for n_tries in range(n_max_tries):
 15     # stvori poruku za korisnika koja uključuje i broj pokušaja
 16     # varijabli n_tries dodajemo 1 kako korisniku prvi pokušaj ne bismo prikazivali kao 0
 17     message = 'Pogodi broj (pokušaj ' + str(n_tries + 1) + '/' + str(n_max_tries) + '): '
 18     # pitaj korisnika za unos
 19     n_user = input(message)
 20     # pripremi unos
 21     n_user = int(n_user)
 22     # usporedi brojeve ...
 23     # ako je korisnik pogodio broj
 24     if n_user == n:
 25     print('BRAVO!')
 26     break # čim korisnik pogodi prekidamo petlju
 27     # ako je traženi broj veći
 28     elif n_user < n:
 29     print('Nije točno! Broj je veći.')
 30
 31     # ako je traženi broj manji
 32 else:
 33 print('Nije točno! Broj je manji.')
 34 else:
 35 # ovaj kôd će se izvršiti samo ako petlja 'for' nije prekinuta s naredbom break;
 36 # u ovom slučaju, to je samo ako korisnik nije uspio pogoditi broj u zadanom broju pokušaja
 37 print('Traženi broj', n, 'nije pronađen u dozvoljenom broju pokušaja!')
 39 input('Igra je gotova. Pritisni <enter> za kraj'
```

Rješenje petljom ‘for‘ ima par linija kôda manje i nekima može biti
elegantnije. U ovom slučaju svejedno je koji pristup odaberemo pa je
najbolje odabrati onaj koji nam je samima najlogičniji. U oba slučaja
program će se ponašati identično i njegovo izvršavanje može proizvesti
sljedeći ispis:

```python
# Pogodi broj između 1 i 100.

>>> Pogodi broj (pokušaj 1/5): 50
Nije točno! Broj je veći.

>>> Pogodi broj (pokušaj 2/5): 75
Nije točno! Broj je veći.

>>> Pogodi broj (pokušaj 3/5): 87
Nije točno! Broj je veći.

>>> Pogodi broj (pokušaj 4/5): 94
Nije točno! Broj je manji.

>>> Pogodi broj (pokušaj 5/5): 90
Nije točno! Broj je veći.

Nisi uspio pogoditi traženi broj u dozvoljenom broju pokušaja!
```

Ovaj program je sada više-manje gotov.




