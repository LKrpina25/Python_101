# Kontrola toka: Kondicionali, petlje i pokušaji {#kontrola_toka}

U programiranju ne bismo daleko dogurali kada bismo jedino mogli po redu izvršavati jedinične radnje. S jedne strane moramo moći prema određenim uvjetima odabrati koje naredbe će se izvršiti, a koje ne. Ovo postižemo *kondicionalima*. S druge strane moramo moći ponavljati iste naredbe. Ovo postižemo *petljama*. U nastavku ćemo se upoznati s detaljima i riječ je o standardnim komponentama gotovo svih programskih jezika. U mnogim jezicima visoke razine postoji i treći koncept u kontroli toka, a to je *pokušaj* provođenja određenih naredbi s jasno definiranim kôdom koji će se izvršiti ako neka od naredbi ne uspije.

## Kondicionali: Ako \... onda \... {#kondicionali}

Kondicionali služe *odabiru* kôda koji će se izvršiti. Kada su neke linije ovisne o kondicionalu, tada se neće izvršavati uvijek već samo kada su određeni uvjeti zadovoljeni. Time dobivamo mogućnosti poput: \"ako se neki izraz evaluira kao True, napravi nešto; a ako ne, napravi nešto posve drugo\". Na taj način možemo reći stvari poput:

-   Ako direktorij ne postoji, stvori ga.
-   Ako datoteka postoji pitaj korisnika da li ju želi prepisati novom
    datotekom.
-   Ako korisničko ime već postoji, javi da je zauzeto, a ako korisničko
    ime ne postoji, stvori novog korisnika.
-   Ako je korisnik upisao odgovor \"a\", javi da je odgovor točan, a
    ako je korisnik upisao \"b\", \"c\" ili \"d\" javi da je odgovor
    netočan, a u svim ostalim slučajevima javi da odgovor nije
    prepoznat.

Kondicionali služe uvjetnom izvršavanju kôda. Oni prema određenim uvjetima odabiru koji će se redak izvršiti, a koji ne.

Kondicionale u programskim jezicima tipično reprezentiramo sa složenom izjavom `if`, a minimalan oblik te izjave u Pythonu je:

## Najjednostavniji oblik kondicionala

```python
# listing:kondicional1
if <izraz>:
    neka_radnja

# Kondicionali u Pythonu

```python
# Osnovni if
if <izraz>:
    neka_radnja
```
"Neka radnja" se izvršava samo ako izraz rezultira vrijednošću koja se procjenjuje kao True
(vidi poglavlje o booleovim vrijednostima za detalje).
Ova radnja se mora sastojati od barem jedne linije kôda, ali može se sastojati i od više njih.
Ispod svake if izjave očekuje se uvučen blok kôda. Taj blok koda se naznačuje tako da su sve linije u bloku jednako uvučene i izvršava se samo ako je uvjet zadovoljen, a u suprotnom se preskače.

Uvlačenje kôda
U Pythonu se uvijek uvlači nakon dvotočke (:) koja se koristi u kondicionalima i petljama.
Python nakon retka koji završava s dvotočkom očekuje barem jednu uvučenu liniju kôda (minimalan blok).

Standard u Pythonu je uvlačiti kôd sa četiri razmaka (tipka Tab obično daje soft tab).
Moguće je koristiti i znak tabulatora, ali se treba pobrinuti da se ne miješaju tabulatori i razmaci.

else blok
Moguće je napisati kondicional koji će uvijek izvršiti neki kôd pomoću else:

``` python
if <izraz>:
    neka_radnja
else:
    # u svim ostalim slučajevima
    neka_druga_radnja
```
Ovakav kondicional će uvijek izvršiti neke naredbe.

Primjer prikazuje tri kondicionala:

Prvi kondicional radi nešto samo ako je uvjet zadovoljen.

Druga dva kondicionala uvijek rade nešto jer imaju komponentu else.

Evaluacija izraza
Svi izrazi koji se pojavljuju kao uvjeti evaluiraju se u booleove vrijednosti.
Ako želimo provjeriti rezultat izraza, najjednostavnije je probati u Python komandnoj liniji:

```python
# Primjer evaluacije
bool(b)          # evaluira se u True ili False
bool(x + y)      # evaluira se u True ili False
```
U Pythonu je moguće implicitno pretvoriti bilo koju vrijednost u booleovu vrijednost:

```python
if vrijednost:
    # isto kao if bool(vrijednost):
Više uvjeta: elif
```
Python koristi elif za više uvjeta (umjesto else if):

```python
if <izraz1>:
    radnja1
elif <izraz2>:
    radnja2
elif <izraz3>:
    radnja3
...
else:
    radnja_n
```
Primjer:

```python
# Kondicional sa svim komponentama
x = 3

if x == 1:
    print("x je 1")
elif x == 2:
    print("x je 2")
elif x == 3:
    print("x je 3")
else:
    print("x je neki drugi broj")
```
Drugim riječima, svaki kondicional ima nužno jedan `if` slučaj, a može imati i bilo koji broj `elif` slučajeva i jedan `else` slučaj.  

Ovakav kondicional smo već vidjeli u primjeru [listing:kviz](#listing:kviz), a u idućim poglavljima ćemo za vježbu isprogramirati nešto konkretnije i iskoristiti kondicionale.  

Upoznajmo se ipak prije toga i s petljama i pokušajima kako bismo zaokružili koncept "kontrole toka".
