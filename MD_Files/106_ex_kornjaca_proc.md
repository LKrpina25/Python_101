## Programiranje s kornjačom

"Kornjača" je alat za učenje programiranja koji se koristio u jeziku
Logo još kasnih 1960-ih. Python uključuje ovaj alat kao standardni
modul. Koncept je sljedeći: postoji kornjača koju možemo kretati kroz
dvodimenzionalni prostor s jednostavnim naredbama poput "odi naprijed 50
piksela" ili "skreni lijevo za 45 stupnjeva". Kornjača se najčešće
prikazuje kao strelica, a vrlo je lako s njom početi eksperimentirati i
interaktivno.

<p align="center">
 <strong>Slika 5:</strong> Interaktivan rad s kornjačom.
  <img src="https://github.com/LKrpina25/Python_101/blob/main/Slike/turtle_idle.png" alt="Slika 5: Interaktivan rad s kornjačom">
  <br>
 
</p>


Kornjača živi u modulu `turtle`, a prozor u kojem je vizualizacija se
može pokrenuti s naredbom `turtle.showturtle()`. Osnovne naredbe za
kretanje kornjače su `turtle.forward(distance)`, gdje je `distance`
udaljenost za koju će se kornjača pomaknuti u smjeru u kojem je
orijentirana, te `turtle.left(angle)` i `turtle.right(angle)`, gdje je
`angle` broj stupnjeva za koji će kornjača promijeniti orijentaciju u
lijevo ili desno. Kada program pišemo u datoteku, dobro dođe i naredba
`turtle.done()` koja pokreće kornjaču kao aplikaciju koja čeka
korisnički unos. Ovo je korisno i već ako samo želimo spriječiti da se
prozor zatvori čim se program završi, kao što smo to ranije radili
naredbom `input("Pritisni <enter> za kraj")`.

Također, možemo modificirati i razne postavke kornjače kao što su brzina
crtanja, debljina i boja linije i oblik kornjače. U ovom smislu
najvažniji su nam brzina kornjače kako bi lakše mogli vidjeti što se
zbiva i debljina linije, kako bi lakše vidjeli što je kornjača nacrtala.
Brzinu kornjače možemo postaviti s funkcijom `turtle.speed(n)` gdje je
je n broj od jedan do deset, a jedan je najsporije kretanje. Debljinu
linije možemo postaviti s funkcijom `turtle.width(n)` gdje je n broj
piksela.

Imajući to na umu probajte implementirati program u kornjači koji crta
kvadrat. Pokušajte napisati ovaj program prije no što nastavite čitati
skriptu!

Najjednostavnije rješenje ovog problema je kako slijedi:

**Primjer kornjača i kvadrat 1**
 ```
 1 import turtle
 2
 3 # podesi kornjaču
 4 turtle.showturtle() # pokaži prozor
 5 turtle.width(3)
 6 turtle.speed(1)
 # postavi širinu linije na 3 piksela
 # postavi brzinu na sporo crtanje
 7
 8 # pomakni kornjaču kako treba
 9 turtle.forward(100) # kreni napred zadani broj piksela
 10 turtle.left(90)
 # skreni lijevo za 90 stupnjeva
 11 turtle.forward(100)
 12 turtle.left(90)
 13 turtle.forward(100)
 14 turtle.left(90)
 15 turtle.forward(100)
 16 turtle.left(90)
 17
 18 # spriječi prozor od zatvaranja nakon izvršenja
 19 turtle.done()
```



<p align="center">
  <strong>Slika 6:</strong> Rezultat programa kornjača i kvadrat.
  <br><br>
  <img src="https://github.com/LKrpina25/Python_101/blob/main/Slike/turtle_square.png" alt="Slika 6: Rezultat programa kornjača i kvadrat" width="600">
</p>


Ovo rješenje radi što treba, ali je strukturalno loš program. Prvi
problem je što se dvije posve iste naredbe, odnosno naredbe koje se
sastoje od poziva na iste funkcije s istim parametrima, se u paru
ponavljaju četiri puta. Kada krenemo na ovaj način ponavljati naredbe to
je signal da možemo iskoristiti petlju. Također, ulazne vrijednosti za
izvršenje programa se ponavljaju u samim pozivima za funkcije što ih
čini težim za uočiti i mijenjati, a tako je i lakše tako napraviti
grešku u kôdu. Na primjer, kada bismo željeli promijeniti dužinu
stranice, morali bismo to učiniti na četiri različita mjesta u programu,
a riječ je o banalno jednostavnom primjeru. Pogledajmo rješenje koje te
vrijednosti izdvaja ranije kako bi njima bilo lakše baratati te koristi
petlju za izbjegavanje ponavljanja kôda.

**Primjer kornjača i kvadrat 2**
```
 1 import turtle
 2
 3 # ZADAJ ULAZNE VRIJEDNOSTI
 4 # kako bi bile vidljivije i jednostavnije za mijenjati
 5
 6 # postavke kornjače
 7 line_width = 3
 9
 10 # postavke kvadrata, odnosno zadavanje podataka za kretanje
 11 n_steps = 4
 # stupanj pod kojim se skreće
 13 move_length = 100 # duljina kretanja, u ovom slučaju definira stranicu kvadrata
 8 speed = 1
 12 turn_angle = 90
 # debljina linije
 # brzina kornjače
 # broj koraka koji će kornjača napraviti
 14
 15 # IZVEDI PROGRAM
 16 # pokreni kornjaču i namijesti postavke
 17 turtle.showturtle()
 18 turtle.width(line_width)
 19 turtle.speed(speed)
 20
 24
 25
 21 # iskoristi petlju kako bi iste dvije naredbe ponovio četiri puta
 22 # u petlji se koriste samo varijable čije vrijednosti smo organizirali drugdje
 23 for i in range(n_steps):
 turtle.forward(move_length)
 turtle.left(turn_angle)
 26
 27 turtle.done()
```

Na ovaj način jasno su nam odvojeni podaci i proces samog crtanja, a
proces crtanja ne samo da izbjegava ponavljanje kôda već i omogućuje
laku promjenu broja koraka kornjače. To ne samo da nam olakšava promjene
ovog programa, već nam i otvara nove mogućnosti.

<div class="important">

Ponavljajte petljom i odvojite podatke od logike
Izbjegavajte
ponavljanje istih naredbi dupliciranjem. Tome služi petlja. Također,
odvajajte podatke od logike jer ih je tako lakše kasnije saznati i
mijenjati. Navedeno olakšava održavanje i promjene te umanjuje mogućnost
pogrešaka u većim programima.

</div>

U postavkama sada možemo namjestiti crtanje bilo kojeg pravilnog
poligona. Pogledajmo primjere za trokut i heksagon.

<div class="pythonp">
**Kornjača i trokut**
 
```
# ...
n_steps = 3                 # broj koraka koji će kornjača
napraviti turn_angle = 120  # stupanj pod kojim se skreće
# ...
```
</div>

<p align="center">
 <strong>Slika 5:</strong> Interaktivan rad s kornjačom.
  <img src="https://github.com/LKrpina25/Python_101/blob/main/Slike/turtle_triangle.png" alt="Slika 7: Rezultat programa Kornjača i trokut">
  <br>
 
</p>
 
**Kornjača i heksagon**

```
# ...
n_steps = 6                # broj koraka koji će kornjača
napraviti turn_angle = 60  # stupanj pod kojim se skreće 
# ...
```

</div>

**Slika 8: Rezultat programa Kornjača i heksagon.**





![Slika 8: Rezultat programa Kornjača i heksagon](https://github.com/LKrpina25/Python_101/blob/main/Slike/turtle_hex.png)



Dapače, ukoliko razmislimo i prisjetimo se malo rudimentarne
trigonometrije (ili pronađemo formule *online*), stupanj skretanja
možemo automatski izračunati iz broja stranica čime više ni tu
vrijednost nije potrebno namještati. Dorađeni program, koji se u
potpunosti bazira na poligonima i napustio je koncept kvadrata vidimo
niže.

**Primjer Kornjača i Poligon**

```
 1 import turtle
 2
 3 # ZADAJ ULAZNE VRIJEDNOSTI
 4 # kako bi bile vidljivije i jednostavnije za mijenjati
 5
 6 # postavke poligona
 7 n_sides = 15
 # preimenovano iz n_moves kako bi bilo preciznije
 8 side_length = 100 # preimenovano iz move_length kako bi bilo preciznije
 9
 71
10 # postavke kornjače
 11 line_width = 3
 12 speed = 1
 13
 14 # izračunate vrijednosti
 15 turn_angle = 360 / n_sides # turn_angle se sada računa iz n_sides
 16
 17 # IZVEDI PROGRAM
 18 # ostatak kôda je isti osim što su neke varijable preimenovane
 19 turtle.showturtle()
 20 turtle.width(line_width)
 21 turtle.speed(speed)
 22
 23 for i in range(n_sides):
 24
 25
 26
 turtle.forward(side_length)
 turtle.left(turn_angle)
 27 turtle.done()
```

Program je sada postavljen da crta pravilne poligone bilo kojeg broja
stranica. Ima međutim još jedan problem, unosi su postavljeni tako da
čim je veći broj stranica, tim je veći i poligon ukoliko sami ne
promijenimo dužinu stranice. Navedeno je vidljivo i u ovome tekstu u
razlici u veličini između prikazano trokuta i heksagona, a kako raste
broj stranica, tako raste i veličina. Na slici
<a href="#fig:turtle_big_poly" data-reference-type="ref"
data-reference="fig:turtle_big_poly">5</a> vidimo poligon koji je
pobjegao s ekrana.

**Slika 9: Interaktivan rad s kornjačom.**



![Slika 9: Interaktican rad s kornjačom](https://github.com/LKrpina25/Python_101/blob/main/Slike/turtle_big_poly.png)



Što ukoliko želimo da nam svi poligoni imaju istu veličinu bez ručnog
podešavanja dužine stranice? Obzirom da su nam ulazne vrijednosti u kôdu
izdvojene, navedeno možemo promijeniti trigonometrijskim izračunima
radije no promjenama u toku programa. Možemo, na primjer, postaviti da
je radijus, a ne dužina stranice, osnovna ulazna vrijednost. Dužinu
stranice možemo zatim izračunati. Pogledajmo kako.

**Primjer 6.4: Kronjača i poligon 2.**

```
 1 import turtle
 2 import math # treba nam funkcija za sinus, odnosno math.sin
 3
 4 # ZADAJ ULAZNE VRIJEDNOSTI
 5 # kako bi bile vidljivije i jednostavnije za mijenjati
 6
 7 # ulazne vrijednosti
 8 n_sides = 8
 9 radius = 100
 10
 11 # postavke kornjače
 12 line_width = 3
 13 speed = 1
 14
 15 # izračunate vrijednosti
 16 turn_angle = 360 / n_sides
 17 side_length = 2 * radius * math.sin(math.pi / n_sides)
 18
 19 # IZVEDI PROGRAM
 20 # kôd je isti kao i prije!
 21 turtle.showturtle()
 22 turtle.width(line_width)
 23 turtle.speed(speed)
 24
 25 for i in range(n_sides):
 26
 27
 28
 29 turtle.done()
```
Dodali smo samo formulu za izračun dužine stranice iz radijusa. Na ovaj
način kad crtamo poligone istog radijusa, oni ne rastu s brojem
stranica. Dok ovaj kod prikazuje svrsishodnu upotrebu trigonometrije u
programiranju, za potrebe učenja programiranja nam je ovdje najvažnije
da smo dobrom strukturom, odnosno korištenjem petlje i jasnim odvajanjem
ulaznih podataka od samih naredbi, razvili općenit postupak crtanja
poligona, a krenuli smo od koncepta kvadrata. Sada kad smo razvili
postupak, crtanje poligona bi mogli definirati kao zasebnu funkciju čime
bi omogućili crtanje poligona kroz jednu naredbu. Obzirom da je ovo vrlo
važno za programiranje iole kompleksnijih programa, naučiti ćemo to
kasnije u ovom tekstu, ali pogledajmo prvo još koji primjer koji se
koristi znanjem koje smo već usvojili.

Također, vrijedi spomenuti da smo ovdje prikazali samo najosnovnije
mogućnosti kornjače pa ćemo se na to još vratiti, ali ako netko želi
eksperimentirati s kornjačom više neka se referira na [službenu
dokumentaciju](https://docs.python.org/3.8/library/turt le.html).
Čitanje dokumentacije i traženje odgovora *online* je i dobra vježba jer
se radi o nezaobilaznom koraku prilikom programiranja, a na čitanje
dokumentacije se treba naviknuti (i to pogotovo kada se radi o službenoj
dokumentaciji jer je često pisana tehničkim jezikom) pa je dobro početi
s vježbom.

Također, s kornjačom se mogu raditi kojekakve čudesne i uglavnom
beskorisne stvari. Programiranje radi umjetnosti. Ukoliko smo Python
instalirali prema uputama iz ove skripte i u komandnoj liniji pokrenemo
naredbu `python -m turtledemo` pokrenuti će nam se grafičko sučelje koje
prikazuje napredne primjere i mogućnosti kornjače. Ukoliko, na primjer,
iz padajućeg izbornika "examples" odaberemo primjer "bytedesign" te
kliknemo na "start", dobiti ćemo sliku
<a href="#fig:turtle_examples" data-reference-type="ref"
data-reference="fig:turtle_examples">6</a>.

**Slika 10: Napredni primjeri mogućnosti s kornjačom.**


![Slika 10: Napredni primjeri mogućnosti s kornjačom](https://github.com/LKrpina25/Python_101/blob/main/Slike/turtle_examples.png)

Ipak, ovi primjeri su uglavnom napredni i koriste mnoge koncepte koje
još nismo objasnili pa u njih nećemo sada dublje ulaziti. Ovdje su
spomenuti jer prikazuju mogućnost programiranja radi kreativnog procesa
radije no pragmatične vrijednosti programa.








