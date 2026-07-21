# Memóriajáték

A játék egy egyszerű memóriajáték megvalósítása. A játékmező egy 4x4-es tábla, amely 8 különböző párt (kártyát) tartalmaz. A kártyák nagybetűkkel vannak jelölve. 
A játék célja az összes pár megtalálása. Minden körben két kártyát fordíthat fel a játékos. Ha a kártyák megegyeznek, felfedve maradnak, ha nem, visszafordulnak.
Akkor győz a játékos, ha megtalálta az összes párt.

## Elindítás lépései

- Futtasd az alkalmazást a(z) `src`  mappából a `python3 main.py` paranccsal.

## Implementáladnó feature-ök

Az alapmegvalósítás a következő funkciókkal bővíthető/bővítendő:

### I. Mentés/Betöltés

Valósítsd meg a mentés-betöltés funkciót!

A mentéstől elvárt, hogy a lemezen, tetszőleges fájlformátumban tárolja el a játék aktuális állását. A betöltés funkció meg az így eltárolt fájlt legyen képes beolvasni és az alapján elindítani a játékot a megfelelő _game state_-el.

### II. Pályaméret módosítása

A játékos legyen képes a játék elején a pálya méretét megadni. A pálya mérete legyen legalább 2x2-es, maximum 10x10-es. A pálya mérete alatt értjük a sorok és oszlopok számát.

_Figyelj rá, hogy módosított pályaméret mellett is megfelelően jelenjenek meg a sorok és oszlopok jelzései! Függően a további funkciók megvalósításától, ha egy funkció megköveteli a jelzések megjelenítésének módosítását._

### III. Párok helyett "csoportok"

A játékosnak a játék elején legyen lehetősége kiválasztani, hogy a pályán a kártyák párokban vagy "csoportokban" (mivel több, mint 2, ezért már nem pár) legyenek-e. A csoportok mérete legyen legalább 2, mert kevesebbnek nincs értelme, mivel akkor párok sem lennének.

- Legyen lehetőség választani csoportméretet, amely legalább 2 legyen
- A csoportméret legfeljebb a pálya méretének (kártyák számának) fele legyen (4x4-es pálya esetén maximum 8 legyen egy csoportban, mert ha több lenne, akkor nem egyeznének a csoportokban lévő kártyák száma, pl. 10-6 aránynál az egyikből többet kellene kiválasztani, mint a másikból)
- A koordináták megadásánál figyelj arra, hogy annyi koordinátát kelljen megadni, ahány kártya van egy csoportban

_A további funkciók megvalósításától függően készíts hibakezelést, ha szükséges, mert például egy 3x3-as pályán egy 4-es méretű csoport nem egészen lesz valid koncepció, mivel abban az esetben lenne egy kártya, aminek nincs párja, vagy nem egyeznének meg a csoportméretek._

### IV. Saját kártyák használata

A játékosnak legyen lehetősége az alaptól eltérő, nagyobb kártyákkal játszani, pl. 3x3-as kártyákkal.

- A játék elején legyen lehetőség a kártyák méretének megadására
- A kártyák mérete legyen legalább 2x2-es, mivel az 1x1-es méret már létezik a játékban

_Figyelj rá, hogy a változtatott méretű kártyák és a hozzájuk tartozó jelölések (sor, oszlop koordináták) is megfelelően jelenek meg!_

#### Alap pálya megjelenése:

```
    1 2 3 4
    -------
1 | * * * *
2 | * * * *
3 | * * * *
4 | * * * *
```

#### Példák nagyobb méretű kártyákra:
2x2-es pályán, 3x3-as kártyák:

```
      1   2
    --------
  | AAA  BBB
1 | AAA  BBB
  | AAA  BBB
  |
  | BBB  AAA
2 | BBB  AAA
  | BBB  AAA
```

```
     1   2
    --------
  | TTT  X X
1 |  T    X 
  |  T   X X
  |
  | X X  TTT
2 |  X    T 
  | X X   T
```

3x3-as pályán, 3x3-as kártyák (3-as csoportokkal):

```
     1    2    3
    -------------
  | AAA  BBB  CCC
1 | AAA  BBB  CCC
  | AAA  BBB  CCC
  |
  | BBB  CCC  AAA
2 | BBB  CCC  AAA
  | BBB  CCC  AAA
  |
  | CCC  AAA  BBB
3 | CCC  AAA  BBB
  | CCC  AAA  BBB
```

```
     1    2    3
    -------------
  | TTT  X X  CCC
1 |  T    X   C
  |  T   X X  CCC
  |
  | X X  CCC  TTT
2 |  X   C     T
  | X X  CCC  TTT
  |
  | CCC  TTT  X X
3 | C     T    X
  | CCC  TTT  X X
```

### V. Ranglista és játékos nevek

A játék végén a játékosnak legyen lehetősége megadni a nevét, amelyet a játék a pontszámával együtt elment. A ranglistán a játékosok pontszám szerint legyenek rendezve.

- Számold meg, hogy mennyi próbálkozásból találta meg az összes párt a játékos
- Ha már játszott a játékos korábban és szerepel a ranglistán, akkor a játék végén a pontszámát növeld meg az új pontszámmal
- A játék végén jelenjen meg a ranglista, amely tartalmazza a 10 legjobb játékosok nevét és pontszámát.
- A ranglistát a játék indításakor lehessen törölni.

_Határozd meg a játékos pontszámát az alapján, hogy hány tippelésből nyerte meg az adott játékot és mekkora pályán játszott és mennyi kártya volt egy csoportban:_

```pontszám = ( (pálya mérete) * (pálya mérete) * (csoportméret) ) / (tippelések száma)```

## Követelmények
- venv (opcionális)
- Python 3.10 vagy magasabb
