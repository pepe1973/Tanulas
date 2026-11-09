# A `do...while` ciklus JavaScriptben

## 1. Mi az a `do...while` ciklus?

A `do...while` ciklus segítségével egy vagy több utasítást ismételten végrehajthatunk mindaddig, amíg egy megadott feltétel igaz.

A `do...while` hasonlít a `while` ciklushoz, de van egy fontos különbség:

A `do...while` ciklus először végrehajtja az utasításokat, és csak ezután ellenőrzi a feltételt.

Ez azt jelenti, hogy a ciklus törzse legalább egyszer biztosan lefut, még akkor is, ha a feltétel már kezdetben hamis.

Például:

- Legalább egyszer megjelenítünk egy menüt.
- Egy játékban legalább egyszer végrehajtjuk a játék menetét.
- Legalább egyszer bekérünk egy adatot a felhasználótól.
- Egy műveletet addig ismétlünk, amíg a felhasználó nem választja a kilépést.

## 2. A `do...while` ciklus alapvető felépítése

A ciklus szintaxisa:

```javascript
do {
    // Ismétlődő utasítások
} while (feltetel);
```

A szerkezet részei:

- `do`: elindítja a ciklus törzsét.
- Kapcsos zárójelek (`{}`): tartalmazzák a végrehajtandó utasításokat.
- `while`: megadja a ciklus folytatásának feltételét.
- `feltetel`: egy logikai kifejezés, amelynek eredménye `true` vagy `false`.

Fontos: A `do...while` ciklus végén a `while` feltétel után pontosvesszőt (`;`) kell írni.

A végrehajtás sorrendje:

1. A JavaScript végrehajtja a `do` blokk utasításait.
2. Ellenőrzi a `while` feltételt.
3. Ha a feltétel igaz, újra végrehajtja a ciklus törzsét.
4. Ha a feltétel hamis, kilép a ciklusból.

## 3. Egyszerű `do...while` ciklus

Nézzünk egy példát, amely 1-től 5-ig kiírja a számokat!

```javascript
let i = 1;

do {
    console.log(i);
    i++;
} while (i <= 5);
```

A konzolon megjelenő eredmény:

```
1
2
3
4
5
```

A program működése:

- `let i = 1`: létrehozzuk a ciklusváltozót.
- `do`: elindul a ciklus törzse.
- `console.log(i)`: kiírjuk az aktuális értéket.
- `i++`: növeljük a változó értékét eggyel.
- `while (i <= 5)`: ellenőrizzük, hogy folytatódhat-e a ciklus.

Amikor az `i` értéke 6 lesz, a feltétel hamissá válik, ezért a ciklus befejeződik.

## 4. A `do...while` és a `while` közötti különbség

A két ciklus működése hasonló, de a feltétel ellenőrzésének időpontja eltér.

`while` ciklus:

```javascript
let i = 10;

while (i < 5) {
    console.log(i);
    i++;
}
```

Ebben az esetben a ciklus egyszer sem fut le, mert az `i < 5` feltétel már kezdetben hamis.

`do...while` ciklus:

```javascript
let i = 10;

do {
    console.log(i);
    i++;
} while (i < 5);
```

A konzol eredménye:

```
10
```

A `do...while` ciklus egyszer végrehajtja a törzsét, és csak utána ellenőrzi a feltételt.

| Szempont                 | `while`                    | `do...while`                           |
| ------------------------ | -------------------------- | -------------------------------------- |
| Feltétel ellenőrzése     | A ciklus előtt             | A ciklus után                          |
| Legalább egyszer lefut?  | Nem feltétlenül            | Igen                                   |
| Feltétel kezdetben hamis | Egyszer sem fut le         | Egyszer lefut                          |
| Tipikus használat        | Feltételtől függő ismétlés | Legalább egyszer végrehajtandó művelet |

A legfontosabb különbség: A `while` először ellenőrzi a feltételt, a `do...while` először végrehajtja a ciklus törzsét.

## 5. A ciklusváltozó szerepe

A `do...while` ciklusban is gyakran használunk egy változót az ismétlések számának követésére.

Például:

```javascript
let szamlalo = 0;

do {
    console.log('Ismétlés:', szamlalo);
    szamlalo++;
} while (szamlalo < 4);
```

Eredmény:

```
Ismétlés: 0
Ismétlés: 1
Ismétlés: 2
Ismétlés: 3
```

A `szamlalo` változó minden ismétlés során eggyel növekszik.

A ciklus akkor fejeződik be, amikor a változó értéke eléri a 4-et, mert ekkor a `szamlalo < 4` feltétel hamissá válik.

A ciklusváltozót általában a ciklus előtt hozzuk létre, és a ciklus törzsében módosítjuk.

## 6. A ciklusváltozó növelése és csökkentése

A `do...while` ciklusban ugyanazokat a növelő és csökkentő operátorokat használhatjuk, mint a `for` és a `while` ciklusoknál.

Növelés egyesével:

```javascript
let i = 1;

do {
    console.log(i);
    i++;
} while (i <= 5);
```

Eredmény: 1, 2, 3, 4, 5.

Csökkentés egyesével:

```javascript
let i = 5;

do {
    console.log(i);
    i--;
} while (i >= 1);
```

Eredmény: 5, 4, 3, 2, 1.

Növelés többesével:

```javascript
let i = 2;

do {
    console.log(i);
    i += 2;
} while (i <= 10);
```

Eredmény: 2, 4, 6, 8, 10.

A léptetésnek itt is összhangban kell lennie a feltétellel, különben a ciklus végtelenné válhat.

## 7. A `do...while` ciklus és a tömbök

A `do...while` ciklussal tömbök elemeit is feldolgozhatjuk.

Például:

```javascript
const nevek = ['Anna', 'Béla', 'Csilla', 'Dávid'];

let i = 0;

do {
    console.log(nevek[i]);
    i++;
} while (i < nevek.length);
```

Eredmény:

```
Anna
Béla
Csilla
Dávid
```

A működés:

1. Létrehozzuk a neveket tartalmazó tömböt.
2. Az `i` változó kezdeti értéke 0.
3. A ciklus kiírja az aktuális tömbelem értékét.
4. Az `i++` növeli az indexet.
5. A `while` ellenőrzi, hogy maradt-e még feldolgozható tömbelem.

Fontos: A `do...while` legalább egyszer lefut, ezért üres tömb esetén is megpróbálná elérni a `nevek[0]` elemet. Ennek értéke `undefined` lenne.

Ha a tömb üres is lehet, előtte ellenőrizzük a hosszát:

```javascript
const nevek = [];

if (nevek.length > 0) {
    let i = 0;

    do {
        console.log(nevek[i]);
        i++;
    } while (i < nevek.length);
} else {
    console.log('A tömb üres.');
}
```

## 8. A `break` utasítás használata

A `break` utasítással a `do...while` ciklust is idő előtt megszakíthatjuk.

Például keressük meg az első 7-tel osztható számot 1 és 20 között!

```javascript
let i = 1;

do {
    if (i % 7 === 0) {
        console.log('Megtaláltuk:', i);
        break;
    }

    i++;
} while (i <= 20);
```

Eredmény:

```
Megtaláltuk: 7
```

A `break` hatására a ciklus azonnal befejeződik. Nem várja meg, hogy a `while` feltétele hamissá váljon.

A `break` különösen hasznos keresési feladatoknál, amikor a keresett érték megtalálása után nincs szükség további ismétlésekre.

## 9. A `continue` utasítás használata

A `continue` utasítás kihagyja az aktuális ismétlés hátralévő részét, majd a ciklus folytatja a működését.

Például írjuk ki az 1 és 10 közötti páratlan számokat!

```javascript
let i = 0;

do {
    i++;

    if (i % 2 === 0) {
        continue;
    }

    console.log(i);
} while (i < 10);
```

Eredmény:

```
1
3
5
7
9
```

A program működése:

- Az `i++` növeli a változó értékét.
- Az `if` ellenőrzi, hogy az aktuális szám páros-e.
- Ha páros, a `continue` kihagyja a `console.log()` utasítást.
- Ha páratlan, a program kiírja a számot.
- A ciklus ezután ellenőrzi a folytatás feltételét.

Fontos: A `do...while` ciklusnál a `continue` után is a ciklus végén található `while` feltétel következik. Ezért a ciklusváltozó módosítását úgy kell elhelyezni, hogy a feltétel idővel hamissá válhasson.

## 10. Végtelen ciklus létrehozása

A `do...while` ciklus is végtelenné válhat, ha a feltétel soha nem lesz hamis.

Például:

```javascript
let i = 1;

do {
    console.log(i);
} while (i <= 5);
```

A változó értéke nem változik, ezért a feltétel mindig igaz marad.

A konzolon folyamatosan az 1-es szám jelenik meg.

A helyes megoldás:

```javascript
let i = 1;

do {
    console.log(i);
    i++;
} while (i <= 5);
```

A ciklusváltozó növelésével biztosítjuk, hogy a feltétel egy idő után hamissá váljon.

Mikor lehet szándékos a végtelen ciklus?

Például egy játék fő ciklusában vagy egy folyamatosan működő programban. Ilyenkor a ciklusból általában egy esemény vagy a `break` utasítás segítségével lépünk ki.

## 11. Összetettebb példa: menürendszer

A `do...while` egyik gyakori felhasználási területe a menürendszerek megvalósítása.

Készítsünk egy egyszerű menüt, amely legalább egyszer megjelenik, és addig ismétlődik, amíg a felhasználó a kilépést nem választja!

```javascript
let valasztas = 0;

do {
    console.log('----- MENÜ -----');
    console.log('1 - Felhasználók listázása');
    console.log('2 - Új felhasználó hozzáadása');
    console.log('3 - Felhasználó törlése');
    console.log('4 - Kilépés');

    valasztas = 4;

    switch (valasztas) {
        case 1:
            console.log('Felhasználók listázása');
            break;

        case 2:
            console.log('Új felhasználó hozzáadása');
            break;

        case 3:
            console.log('Felhasználó törlése');
            break;

        case 4:
            console.log('Kilépés a programból');
            break;

        default:
            console.log('Érvénytelen választás!');
    }
} while (valasztas !== 4);
```

A példában a `valasztas` értékét most közvetlenül 4-re állítjuk, ezért a menü csak egyszer jelenik meg.

Egy valódi, interaktív programban a választást például a `prompt()` segítségével kérhetnénk be:

```javascript
let valasztas;

do {
    valasztas = Number(
        prompt('1 - Listázás\n2 - Hozzáadás\n3 - Törlés\n4 - Kilépés'),
    );

    switch (valasztas) {
        case 1:
            console.log('Listázás');
            break;

        case 2:
            console.log('Hozzáadás');
            break;

        case 3:
            console.log('Törlés');
            break;

        case 4:
            console.log('Kilépés');
            break;

        default:
            console.log('Érvénytelen választás!');
    }
} while (valasztas !== 4);
```

Ebben a változatban a program minden alkalommal bekéri a választást, és addig jeleníti meg a menüt, amíg a felhasználó a 4-es lehetőséget nem választja.

A `Number()` a `prompt()` által visszaadott szöveget számmá alakítja, így a `switch` számmal tudja összehasonlítani a választást.

# 12. Ellenőrző kérdések

1\. Mire használjuk a `do...while` ciklust?

A) Változók deklarálására.

B) Utasítások ismételt végrehajtására egy feltétel alapján.

C) Függvények létrehozására.

D) Tömbök rendezésére.

2\. Mikor ellenőrzi a `do...while` ciklus a feltételt?

A) A ciklus előtt.

B) Minden utasítás előtt.

C) A ciklus törzsének végrehajtása után.

D) Csak a program végén.

3\. Hányszor fut le legalább a `do...while` ciklus törzse?

A) Egyszer sem.

B) Legalább egyszer.

C) Pontosan kétszer.

D) Csak akkor, ha a feltétel igaz.

4\. Mi történik, ha a ciklus feltétele már kezdetben hamis?

A) A ciklus egyszer lefut.

B) A ciklus végtelenné válik.

C) A program hibát jelez.

D) A ciklus azonnal, végrehajtás nélkül befejeződik.

5\. Melyik a `do...while` ciklus helyes szintaxisa?

A)

```javascript
while (feltetel) {
    // utasítások
}
```

B)

```javascript
do {
    // utasítások
} while (feltetel);
```

C)

```javascript
do while (feltetel) {
    // utasítások
}
```

D)

```javascript
do {
    // utasítások
} if (feltetel);
```

6\. Mi a különbség a `while` és a `do...while` ciklus között?

A) A `while` csak számokkal használható.

B) A `do...while` nem használhat ciklusváltozót.

C) A `while` először ellenőrzi a feltételt, a `do...while` pedig először végrehajtja a ciklus törzsét.

D) Nincs különbség közöttük.

7\. Melyik utasítás szakítja meg teljesen a ciklust?

A) `continue`

B) `break`

C) `skip`

D) `next`

8\. Mit csinál a `continue` utasítás?

A) Megszakítja a teljes programot.

B) Kihagyja az aktuális ismétlés hátralévő részét.

C) Új ciklust indít.

D) Törli a ciklusváltozót.

9\. Mit ír ki az alábbi kód?

```javascript
let i = 5;

do {
    console.log(i);
    i++;
} while (i < 5);
```

A) Semmit.

B) 5, 6, 7, 8...

C) 5

D) Végtelenül az 5-öst.

10\. Melyik esetben célszerű a `do...while` ciklust használni?

A) Ha egy műveletet legalább egyszer végre kell hajtani.

B) Ha egy változót szeretnénk deklarálni.

C) Ha egy tömböt szeretnénk létrehozni.

D) Ha egy függvényt szeretnénk meghívni.

# 13. Gyakorlati feladatok

A következő feladatokat JavaScriptben oldd meg! A megoldások során elsősorban a `do...while` ciklust használd.

1\. Számok kiírása

Írj programot, amely 1-től 10-ig kiírja az egész számokat a konzolra!

A ciklusváltozó minden ismétlés után növekedjen eggyel.

2\. Visszaszámlálás

Készíts egy `do...while` ciklust, amely 10-től 1-ig visszafelé számol.

A számok kiírása után jelenjen meg a következő szöveg:

```
Indulás!
```

3\. Páros számok

Írd ki a 2 és 30 közötti páros számokat!

A ciklusváltozó minden ismétlés után kettővel növekedjen.

4\. Számok összege

Hozz létre egy `osszeg` nevű változót, amely kezdetben 0 értéket tartalmaz.

A `do...while` ciklus segítségével add össze az 1 és 100 közötti egész számokat!

A ciklus befejezése után jelenítsd meg az eredményt.

5\. Szorzótábla

Hozz létre egy `szam` nevű változót.

A `do...while` ciklus segítségével jelenítsd meg a változóban tárolt szám szorzótábláját 1-től 10-ig!

Például a 7-es szám esetén:

```
7 * 1 = 7
7 * 2 = 14
7 * 3 = 21
...
7 * 10 = 70
```

6\. Tömb elemeinek kiírása

Hozz létre egy legalább 5 elemből álló, szöveges értékeket tartalmazó tömböt.

A `do...while` ciklus segítségével írd ki a tömb összes elemét!

A ciklus előtt ellenőrizd, hogy a tömb nem üres-e.

7\. Tömb elemeinek összeadása

Hozz létre egy számokat tartalmazó tömböt.

A `do...while` ciklus segítségével számítsd ki a tömb elemeinek összegét!

Az eredményt a ciklus befejezése után jelenítsd meg.

8\. Pozitív és negatív számok megszámlálása

Hozz létre egy számokat tartalmazó tömböt, amely pozitív, negatív és nulla értékeket is tartalmaz.

A `do...while` ciklus és az `if` utasítás segítségével számold meg:

- Hány pozitív szám található a tömbben?
- Hány negatív szám található a tömbben?
- Hány nulla található a tömbben?

Az eredményeket külön változókban tárold!

9\. Keresés tömbben

Hozz létre egy számokat tartalmazó tömböt, valamint egy `keresettSzam` változót.

A `do...while` ciklus segítségével keresd meg, hogy a keresett szám megtalálható-e a tömbben!

Ha megtaláltad, jelenítsd meg az indexét is.

Használd a `break` utasítást, hogy a találat után a keresés befejeződjön!

Ügyelj arra, hogy a tömb üres is lehet, ezért előtte ellenőrizd a hosszát.

10\. Menüvezérelt program

Készíts egy egyszerű menürendszert `do...while` ciklussal!

A lehetséges menüpontok:

- 1 – Felhasználók listázása
- 2 – Új felhasználó hozzáadása
- 3 – Felhasználó törlése
- 4 – Kilépés

A program:

- Jelenítse meg a menüt!
- Kérje be a felhasználó választását!
- A `switch` segítségével hajtsa végre a megfelelő műveletet!
- Ismeretlen választás esetén jelenítsen meg hibaüzenetet!
- A menü addig ismétlődjön, amíg a felhasználó a 4-es lehetőséget nem választja!

# 14. Összefoglalás

A `do...while` ciklus segítségével egy vagy több utasítást ismételten végrehajthatunk, miközben a ciklus feltételét minden ismétlés után ellenőrizzük.

A legfontosabb tudnivalók:

- A `do` indítja el a ciklus törzsét.
- A `while` határozza meg, hogy folytatódjon-e a ciklus.
- A ciklus törzse legalább egyszer végrehajtódik.
- A `break` megszakítja a ciklust.
- A `continue` kihagyja az aktuális ismétlés hátralévő részét.
- A ciklusváltozó megfelelő módosítására itt is figyelni kell.
- A `do...while` különösen hasznos menürendszerek és legalább egyszer végrehajtandó műveletek esetén.
- A `while` ciklustól az különbözteti meg, hogy a feltételt csak a ciklus törzsének végrehajtása után ellenőrzi.

A három eddig tanult ciklus rövid összehasonlítása:

| Ciklus       | Mikor ellenőrzi a feltételt? | Legalább egyszer lefut? |
| ------------ | ---------------------------- | ----------------------- |
| `for`        | A ciklus előtt               | Nem feltétlenül         |
| `while`      | A ciklus előtt               | Nem feltétlenül         |
| `do...while` | A ciklus után                | Igen                    |
