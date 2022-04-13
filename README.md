# Vpliv karantene na pogostost nasilja v družini

## Opis problema
Leto 2020 je zaznamovala epidemija covid-19 virusa, posledica katere je bila dolgotrajno obdobje karantena za državljane republike Slovenija. To je pomenilo, da so družinski člani preživljali več časa skupaj kot poprej. Z seminarsko naogo želimo ugotoviti, kako je to vplivalo na številov primerov kaznivih dejanj nasilja v družini ter njihovo intenziteto. Menimo da so faktorji, kot je uvedba splošne karantene ter omejitev gibanja, vplivali na število primer obravnav družinskega nasilja. Zanimalo nas je tudi, ali je med obdobjem policijske ure delež kriminala upadel.

## Tabele kaznivih dejanj
Podatke smo dobili na <a href="https://www.policija.si/o-slovenski-policiji/statistika/kriminaliteta">spletni strani</a> policije Republike Slovenija. Podatki so zbrani za 10 let(2012 do 2021), za vsako leto v svoji datoteki. Število atributov je za vsako leto enako 33, število vnosov pa se giblje od 100.000 do 170.00. Podatke smo, kjer je bilo to smiselno, ustrezno preoblikovali in dopolnili. Manjkajočih ali napačno vpisanih podatkov je zelo malo, zato smo take vnose odstranili.

## Atributi tabele kaznivih dejanj

- **ZaporednaStevilkaKD** - ID kaznivega dejanja
- **MesecStoritve** - datum v formatu MM.LLLL
- **UraStoritve** - Zaokrožena na polno uro, podano v formatu HH:MM -HH:MM
- **DanVTednu**
- **PUStoritveKD** - Policijska uprava, ki je obravnavala kaznivo dejanje
- **Povratnik**  - Ali ima storilec že predhodna kazniva dejanja
- **OpisKD** - Člen in naziv kaznivega dejanja v kazenskem zakoniku
- **PoglavjeKD** - Zoper katerega področja je bilo kaznivo dejanje storjeno
- **GospodarskiKriminal** - Ali je bilo kaznivo dejanje gospodarkse ali splošne narave
- **OrganiziraniKriminal** - Ali je bilo kaznivo dejanje del organiziranega kriminala
<br>*&ast;Oznaka "ORGANIZIRANA", če je bil organiziran kriminal, v nasprotnem primeru ni zapisa*
- **MladoletnikaKriminaliteta** - Ali je bil storilec mladoleten
<br>*&ast;Oznaka "MLADOLETNIŠKA", če je bil storilec mladoleten, v nasprotnem primeru ni zapisa*
- **Poskus** - Ali je bilo kaznivo dejanje izvedeno, ali pa je bil samo poskus
- **KriminalistinaOznacba1** - oznaka kaznivega dejanja
- **KriminalisticnaOznacba2**
- **KriminalisticnaOznacba3**
<br>*&ast;KO2 in KO3 sta neobvezna atributa, katera lahko vsebujeta dodatne informacije.*
- **UporabljenoSredstvo1** - Če in katero sredstvo je bilo uporabljeno pri storitvi kaznivega dejanja.
- **UporabljenoSredstvo2**
- **UporabljenoSredstvo3**
- **UporabljenoSredstvo4**
<br>*&ast;US2, US3 in US4 so neobvezni atributi, ki imajo vrednost v primeru, da je bilo uporabljenih več sredstev ali pa za dodaten opis sredstva*
- **UpravnaEnotaStoritve** - Upravna enota, ki je obravnavala kaznivo dejanje
- **OpisKraja** - Oznaka kraja, kjer je bilo storjeno kaznivo dejanje
- **LetoZakljucnegaDokumenta** - Leto ko je bil primer zaključen
- **VrstaZakljucnegaDokumenta** - Ali je bila zoper dejanja podana kazenska ovadba, ali samo napisano poročilo
- **ZaporednaStevilkaOsebeVKD** - ZaporednaStevilkaKD dodana z oznako osebe
- **VrstaOsebe** - Vloga osebe v kazniven dejanju
- **StarostniRazred** - Starostni razred osebe
<br>*&ast;Razpon med 18-24, nato pa na vsake 10 let*
- **Spol**
- **Drzavljanstvo**
- **Poskodba**
<br>*&ast;Pri "Poškodba" je veliko praznih vnosov, kljub temu da lahko ima vrednost "BREZ POŠKODBE" -> Po pregledu bomo obravnavali prazne vnose kot "BREZ POŠKODBE"*
- **VplivAlkohola** - Ali je bila oseba pod vplivom alkohola
- **VplivMamil** - Ali je bila oseba pod vplivom mamil
<br>*DA ali NE, NN pomeni da ni bil opravljen test*
- **OrganiziranaZdruzba** - Ali je bila oseba del kriminalne združbe
- **Skoda** - Povzročena škoda v € oz. oznaka "BREZ"

## Predprocesiranje

Opazili smo, da imamo med atributi 3 vrste podatkov.
- Številske podatke kot so ID-ji ter letnice smo pretvorili v tip int.
- Besedilne podatke, kot so oznake kaznivih dejanj, uporabljeni predmeti, idr. smo spremenili v tip string.
- Atributi ki so vsebovali samo dve vrednosti smo nastavili na tip bool.

Glede na to da je bilo napačnih in manjkajočih vnosov zelo malo, smo le te odstranili, saj to ne bo bistveno vplivalo na končne rezultate. Razbrati je bilo možno tudi določene atribute, kjer pa smo lahko sklepali, da je manjkajoč zapis predstavljal eno izmed dveh drugih zapisanih vrednsti(navadno negacijo atributa).
