# A `while` ciklus JavaScriptben

## 1. Mi az a `while` ciklus?

A `while` ciklus segítségével egy vagy több utasítást ismételten végrehajthatunk mindaddig, amíg egy megadott feltétel igaz.

A `while` ciklus különösen akkor hasznos, amikor előre nem tudjuk pontosan, hányszor kell megismételni egy műveletet. A ciklus addig fut, amíg a feltétel teljesül.

Például:

- Addig kérünk be adatokat, amíg a felhasználó nem ad meg egy érvényes értéket.
- Addig keresünk egy tömbben, amíg meg nem találjuk a keresett elemet.
- Addig növelünk egy számlálót, amíg el nem ér egy meghatározott értéket.
- Egy játékban addig ismételjük a játék menetét, amíg a játék véget nem ér.

A JavaScriptben a `while` a feltételvizsgálós ciklusok közé tartozik.

## 2. A `while` ciklus alapvető felépítése

A `while` ciklus szintaxisa:

```javascript
while (feltetel) {
    // Ismétlődő utasítások
}
```

A működés részei:

1. A JavaScript megvizsgálja a feltételt.
2. Ha a feltétel igaz (`true`), végrehajtja a ciklus törzsében található utasításokat.
3. A ciklus végén visszatér a feltétel vizsgálatához.
4. Ha a feltétel hamis (`false`), a ciklus befejeződik, és a program a ciklus utáni utasításokkal folytatódik.

A `while` ciklus tehát minden ismétlés előtt ellenőrzi a feltételt.

## 3. Egyszerű `while` ciklus

Nézzünk egy példát, amely 1-től 5-ig kiírja a számokat!

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
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

- `let i = 1`: létrehozzuk a ciklusváltozót, amelynek kezdőértéke 1.
- `while (i <= 5)`: a ciklus addig fut, amíg az `i` értéke legfeljebb 5.
- `console.log(i)`: kiírjuk az aktuális értéket.
- `i++`: növeljük a változó értékét eggyel.

Amikor az `i` értéke 6 lesz, a `i <= 5` feltétel hamissá válik, ezért a ciklus befejeződik.

## 4. A ciklusváltozó szerepe

A `while` ciklusban gyakran használunk egy változót, amelynek értékét a ciklus minden ismétlése során módosítjuk.

Ezt ciklusváltozónak nevezzük.

Például:

```javascript
let szamlalo = 0;

while (szamlalo < 4) {
    console.log('Ismétlés:', szamlalo);
    szamlalo++;
}
```

Eredmény:

```
Ismétlés: 0
Ismétlés: 1
Ismétlés: 2
Ismétlés: 3
```

A ciklusváltozó segítségével szabályozzuk az ismétlések számát.

Fontos: A `while` ciklus fejlécében nem kötelező deklarálni a ciklusváltozót. A változót általában a ciklus előtt hozzuk létre, majd a ciklus törzsében módosítjuk.

## 5. A `while` ciklus növeléssel és csökkentéssel

A ciklusváltozó értékét növelhetjük vagy csökkenthetjük.

Növelés:

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```

Eredmény: 1, 2, 3, 4, 5.

Csökkentés:

```javascript
let i = 5;

while (i >= 1) {
    console.log(i);
    i--;
}
```

Eredmény: 5, 4, 3, 2, 1.

Léptetés többesével:

```javascript
let i = 2;

while (i <= 10) {
    console.log(i);
    i += 2;
}
```

Eredmény: 2, 4, 6, 8, 10.

A léptetés irányának és mértékének mindig összhangban kell lennie a ciklus feltételével.

## 6. A `while` ciklus és a tömbök

A `while` ciklussal tömbök elemeit is feldolgozhatjuk.

Például:

```javascript
const nevek = ['Anna', 'Béla', 'Csilla', 'Dávid'];

let i = 0;

while (i < nevek.length) {
    console.log(nevek[i]);
    i++;
}
```

Eredmény:

```
Anna
Béla
Csilla
Dávid
```

A működés:

- A `nevek` tömb négy nevet tartalmaz.
- Az `i` változó kezdetben 0.
- A ciklus addig fut, amíg az index kisebb a tömb hosszánál.
- A `nevek[i]` kifejezéssel elérjük az aktuális elemet.
- Az `i++` segítségével továbblépünk a következő elemre.

A tömbök indexelése 0-tól kezdődik, ezért a ciklusváltozó értékét is 0-ról indítjuk.

Fontos: A feltételben itt is `i < nevek.length` szerepel. Így elkerüljük, hogy a ciklus a tömbön kívüli indexet próbáljon elérni.

## 7. A `break` utasítás használata `while` ciklusban

A `break` utasítás segítségével a ciklust idő előtt megszakíthatjuk, függetlenül attól, hogy a ciklus feltétele egyébként igaz lenne-e.

Például keressük meg az első 7-tel osztható számot 1 és 20 között!

```javascript
let i = 1;

while (i <= 20) {
    if (i % 7 === 0) {
        console.log('Megtaláltuk:', i);
        break;
    }

    i++;
}
```

Eredmény:

```
Megtaláltuk: 7
```

A program működése:

1. A ciklus elindul 1-es kezdőértékkel.
2. Megvizsgálja, hogy az aktuális szám osztható-e 7-tel.
3. Ha nem osztható, növeli a változó értékét.
4. Ha megtalálja a megfelelő számot, végrehajtja a `break` utasítást.
5. A ciklus azonnal befejeződik.

A `break` különösen hasznos keresési feladatoknál, amikor a keresett elem megtalálása után nincs szükség további vizsgálatokra.

## 8. A `continue` utasítás használata `while` ciklusban

A `continue` utasítás az aktuális ismétlés hátralévő részét kihagyja, majd a ciklus a következő feltételvizsgálattal folytatódik.

Például írjuk ki az 1 és 10 közötti páratlan számokat!

```javascript
let i = 0;

while (i < 10) {
    i++;

    if (i % 2 === 0) {
        continue;
    }

    console.log(i);
}
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

- A ciklus növeli az `i` értékét.
- Megvizsgálja, hogy a szám páros-e.
- Ha páros, a `continue` kihagyja a `console.log()` utasítást.
- Ha páratlan, a program kiírja a számot.

Fontos: A `continue` használatakor különösen figyelni kell a ciklusváltozó módosítására. Ha a növelés a `continue` után szerepelne, a páros számoknál kimaradna, és a ciklus akár végtelenné is válhatna.

## 9. Végtelen ciklus

Végtelen ciklusnak nevezzük azt a ciklust, amelynek feltétele soha nem válik hamissá, ezért a ciklus nem fejeződik be magától.

Például:

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
}
```

Ebben a példában az `i` értéke mindig 1 marad, mert nem növeljük meg.

Ezért az `i <= 5` feltétel mindig igaz lesz.

A program folyamatosan ezt írja ki:

```
1
1
1
1
...
```

A helyes változat:

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```

A ciklusváltozó megfelelő módosítása biztosítja, hogy a feltétel egy idő után hamissá váljon.

Mikor lehet szándékos a végtelen ciklus?

Bizonyos programokban előfordul, hogy a ciklusnak folyamatosan futnia kell, például egy szerver vagy egy játék működése során. Ilyenkor a kilépést általában valamilyen esemény vagy `break` utasítás szabályozza.

## 10. A `while` és a `for` ciklus összehasonlítása

Mindkét ciklust ismétlődő feladatok végrehajtására használjuk, de a felépítésük és a tipikus alkalmazásuk eltér.

`for` ciklus:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

A kezdőérték, a feltétel és a léptetés egyetlen sorban található.

`while` ciklus:

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```

A kezdőértéket a ciklus előtt adjuk meg, a léptetés pedig a ciklus törzsében szerepel.

| Szempont          | `for`               | `while`                      |
| ----------------- | ------------------- | ---------------------------- |
| Kezdőérték        | A ciklus fejlécében | Általában a ciklus előtt     |
| Feltétel          | A ciklus fejlécében | A ciklus fejlécében          |
| Léptetés          | A ciklus fejlécében | Általában a ciklus törzsében |
| Tipikus használat | Ismert ismétlésszám | Feltételtől függő ismétlés   |
| Tömb bejárása     | Igen                | Igen                         |

Mikor melyiket használjuk?

- `for`: ha az ismétlések száma előre ismert, vagy jól meghatározható.
- `while`: ha a ciklus addig fusson, amíg egy feltétel teljesül, és az ismétlések száma nem feltétlenül ismert előre.

Mindkét ciklussal sok esetben ugyanaz a feladat is megoldható. A választást elsősorban a feladat jellege és az áttekinthetőség határozza meg.

## 11. Összetettebb példa: számok keresése tömbben

Készítsünk egy programot, amely megkeres egy adott számot egy tömbben!

```javascript
const szamok = [12, 25, 8, 42, 17, 31];
const keresettSzam = 42;

let i = 0;
let megtalalva = false;

while (i < szamok.length) {
    if (szamok[i] === keresettSzam) {
        megtalalva = true;
        break;
    }

    i++;
}

if (megtalalva) {
    console.log('A keresett szám indexe:', i);
} else {
    console.log('A keresett szám nem található.');
}
```

Eredmény:

```
A keresett szám indexe: 3
```

A program működése:

1. Létrehozzuk a számokat tartalmazó tömböt.
2. Megadjuk a keresett számot.
3. Az `i` változóval követjük az aktuális tömbindexet.
4. A ciklus megvizsgálja a tömb elemeit.
5. Ha megtalálja a keresett számot, a `megtalalva` változó értékét `true` értékre állítja.
6. A `break` megszakítja a ciklust.
7. A ciklus után egy `if` utasítás ellenőrzi, hogy megtaláltuk-e a számot.

Ez a példa jól szemlélteti, hogyan használható együtt a `while`, az `if` és a `break`.

# 12. Ellenőrző kérdések

1\. Mire használjuk a `while` ciklust?

A) Változók deklarálására.

B) Utasítások ismételt végrehajtására, amíg egy feltétel igaz.

C) Függvények létrehozására.

D) Tömbök rendezésére.

2\. Mikor ellenőrzi a `while` ciklus a feltételt?

A) Minden ismétlés előtt.

B) Minden ismétlés után.

C) Csak a ciklus végén.

D) Csak egyszer, a program indulásakor.

3\. Mi történik, ha a `while` ciklus feltétele már kezdetben hamis?

A) A ciklus legalább egyszer lefut.

B) A program hibát jelez.

C) A ciklus törzse egyszer sem hajtódik végre.

D) A ciklus végtelenné válik.

4\. Mit csinál az alábbi kódrészlet?

```javascript
let i = 1;

while (i <= 3) {
    console.log(i);
    i++;
}
```

A) Kiírja az 1, 2, 3 számokat.

B) Kiírja az 0, 1, 2 számokat.

C) Csak a 3-as számot írja ki.

D) Végtelen ciklust hoz létre.

5\. Mi okozhat végtelen ciklust?

A) Ha a ciklusváltozó megfelelően növekszik.

B) Ha a ciklus feltétele soha nem válik hamissá.

C) Ha a ciklusban `console.log()` szerepel.

D) Ha a ciklusváltozó kezdeti értéke 0.

6\. Melyik utasítás szakítja meg teljesen a ciklust?

A) `continue`

B) `break`

C) `skip`

D) `next`

7\. Mi a `continue` utasítás feladata?

A) Teljesen leállítja a programot.

B) Új ciklust indít.

C) Kihagyja az aktuális ismétlés hátralévő részét.

D) Törli a ciklusváltozót.

8\. Melyik állítás igaz a `while` és a `for` ciklusra?

A) A `while` csak számokkal használható.

B) A `for` nem használható tömbökkel.

C) Mindkettő alkalmas ismétlődő utasítások végrehajtására.

D) A `while` ciklus mindig legalább egyszer lefut.

9\. Mit ír ki az alábbi kód?

```javascript
let i = 2;

while (i <= 6) {
    console.log(i);
    i += 2;
}
```

A) 2, 3, 4, 5, 6

B) 2, 4, 6

C) 1, 2, 3, 4, 5, 6

D) 2, 4, 6, 8

10\. Miért használjuk a `i < tomb.length` feltételt tömb bejárásakor?

A) Mert a tömb utolsó indexe a hosszánál eggyel kisebb.

B) Mert így minden elemet kihagyunk.

C) Mert a `length` mindig 0 értéket ad vissza.

D) Mert a tömbök indexelése 1-től kezdődik.

# 13. Gyakorlati feladatok

A következő feladatokat JavaScriptben oldd meg! A megoldások során elsősorban a `while` ciklust használd.

1\. Számok kiírása

Írj programot, amely 1-től 20-ig kiírja az egész számokat a konzolra!

2\. Visszaszámlálás

Készíts egy `while` ciklust, amely 10-től 1-ig visszafelé számol.

A számok kiírása után jelenjen meg a következő szöveg:

```
Indulás!
```

3\. Páros számok

Írd ki a 2 és 50 közötti páros számokat!

A ciklusváltozó minden ismétlés után kettővel növekedjen.

4\. Számok összege

Hozz létre egy `osszeg` nevű változót, amely kezdetben 0 értéket tartalmaz.

A `while` ciklus segítségével add össze az 1 és 100 közötti egész számokat!

A ciklus befejezése után jelenítsd meg az eredményt.

5\. Szorzótábla

Hozz létre egy `szam` nevű változót.

A `while` ciklus segítségével jelenítsd meg a változóban tárolt szám szorzótábláját 1-től 10-ig!

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

A `while` ciklus segítségével írd ki a tömb összes elemét!

A ciklus feltételében használd a tömb `length` tulajdonságát.

7\. Tömb elemeinek összeadása

Hozz létre egy számokat tartalmazó tömböt.

A `while` ciklus segítségével számítsd ki a tömb elemeinek összegét!

Az eredményt a ciklus befejezése után jelenítsd meg.

8\. Pozitív és negatív számok megszámlálása

Hozz létre egy számokat tartalmazó tömböt, amely pozitív, negatív és nulla értékeket is tartalmaz.

A `while` ciklus és az `if` utasítás segítségével számold meg:

- Hány pozitív szám található a tömbben?
- Hány negatív szám található a tömbben?
- Hány nulla található a tömbben?

Az eredményeket külön változókban tárold.

9\. Keresés tömbben

Hozz létre egy számokat tartalmazó tömböt, valamint egy `keresettSzam` változót.

A `while` ciklus segítségével keresd meg, hogy a keresett szám megtalálható-e a tömbben!

Ha megtaláltad, jelenítsd meg az indexét is.

Használd a `break` utasítást, hogy a találat után a keresés befejeződjön.

10\. Számok vizsgálata

Készíts egy `while` ciklust, amely 1-től 30-ig vizsgálja a számokat.

- Ha a szám osztható 3-mal, írd ki: `"Hárommal osztható"`.
- Ha a szám osztható 5-tel, írd ki: `"Öttel osztható"`.
- Ha mindkettővel osztható, írd ki: `"Hárommal és öttel is osztható"`.
- Egyébként írd ki magát a számot.

Ügyelj arra, hogy a mindkét feltételnek megfelelő számokat csak egyszer kezeld!

# 14. Összefoglalás

A `while` ciklus segítségével egy vagy több utasítást addig hajthatunk végre ismételten, amíg a megadott feltétel igaz.

A legfontosabb tudnivalók:

- A `while` ciklus minden ismétlés előtt ellenőrzi a feltételt.
- Ha a feltétel már kezdetben hamis, a ciklus egyszer sem fut le.
- A ciklusváltozó módosításáról általában nekünk kell gondoskodnunk.
- A `break` megszakítja a ciklust.
- A `continue` kihagyja az aktuális ismétlés hátralévő részét.
- A `while` ciklus tömbök feldolgozására és keresési feladatokra is alkalmas.
- Ha nem módosítjuk megfelelően a ciklusváltozót, végtelen ciklust hozhatunk létre.
