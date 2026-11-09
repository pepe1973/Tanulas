# A `for` ciklus JavaScriptben

## 1. Mi az a ciklus?

A programozásban gyakran előfordul, hogy egy vagy több utasítást többször szeretnénk végrehajtani. Ilyenkor ciklusokat használunk.

Például, ha a konzolon egymás után tízszer szeretnénk megjeleníteni egy szöveget, nem szükséges tízszer leírnunk ugyanazt a `console.log()` utasítást. Egy ciklus segítségével rövidebben és áttekinthetőbben megoldhatjuk.

A JavaScriptben többféle ciklus létezik:

- `for`
- `while`
- `do...while`
- `for...of`
- `for...in`

Ebben a témakörben a hagyományos `for` ciklussal foglalkozunk.

## 2. A `for` ciklus alapvető felépítése

A `for` ciklust akkor használjuk, amikor általában előre tudjuk, hányszor szeretnénk végrehajtani egy utasítást vagy utasításcsoportot.

Alapvető szintaxisa:

```javascript
for (kezdőérték; feltétel; léptetés) {
    // Ismétlődő utasítások
}
```

A `for` ciklus három fontos részből áll:

1. Kezdőérték: létrehozza és kezdőértékkel látja el a ciklusváltozót.
2. Feltétel: meghatározza, hogy a ciklus folytatódhat-e.
3. Léptetés: módosítja a ciklusváltozó értékét minden ismétlés után.

A három részt pontosvessző (`;`) választja el egymástól.

## 3. Egyszerű `for` ciklus

Nézzünk egy példát, amely 1-től 5-ig kiírja a számokat!

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
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

- `let i = 1`: létrehozza az `i` változót, amelynek kezdőértéke 1.
- `i <= 5`: a ciklus addig fut, amíg az `i` értéke legfeljebb 5.
- `i++`: minden ismétlés után eggyel növeli az `i` értékét.
- `console.log(i)`: kiírja az aktuális értéket.

A ciklus működését lépésenként:

| Ismétlés | `i` értéke | `i <= 5` | Eredmény          |
| -------- | ---------- | -------- | ----------------- |
| 1.       | 1          | igaz     | 1 kiírása         |
| 2.       | 2          | igaz     | 2 kiírása         |
| 3.       | 3          | igaz     | 3 kiírása         |
| 4.       | 4          | igaz     | 4 kiírása         |
| 5.       | 5          | igaz     | 5 kiírása         |
| 6.       | 6          | hamis    | A ciklus véget ér |

Amikor a feltétel hamissá válik, a ciklus nem hajtódik végre újra.

## 4. A ciklusváltozó szerepe

A `for` ciklusban általában egy változó segítségével követjük nyomon az ismétlések számát.

Ezt a változót ciklusváltozónak nevezzük.

A példákban gyakran az `i` betűt használjuk, de más változónév is megfelelő:

```javascript
for (let szamlalo = 1; szamlalo <= 5; szamlalo++) {
    console.log(szamlalo);
}
```

A ciklusváltozó deklarálásához leggyakrabban a `let` kulcsszót használjuk.

A `let` azért megfelelő, mert a ciklusváltozó értéke ismétlésenként megváltozik.

Fontos: Ha a ciklus fejlécében `let` segítségével hozzuk létre a változót, akkor annak hatóköre a ciklusra korlátozódik. A cikluson kívül nem érhető el.

## 5. A növelés és csökkentés

A ciklusváltozót nemcsak növelhetjük, hanem csökkenthetjük is.

Növelés egyesével:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Eredmény: 1, 2, 3, 4, 5.

Csökkentés egyesével:

```javascript
for (let i = 5; i >= 1; i--) {
    console.log(i);
}
```

Eredmény: 5, 4, 3, 2, 1.

A leggyakrabban használt rövidített operátorok:

| Operátor | Jelentés                            |
| -------- | ----------------------------------- |
| `i++`    | Az `i` értékének növelése 1-gyel    |
| `i--`    | Az `i` értékének csökkentése 1-gyel |
| `i += 2` | Az `i` értékének növelése 2-vel     |
| `i -= 2` | Az `i` értékének csökkentése 2-vel  |

## 6. A ciklus léptetése többesével

A ciklusváltozót nem kötelező egyesével módosítani.

Például kiírhatjuk a páros számokat 2-től 10-ig:

```javascript
for (let i = 2; i <= 10; i += 2) {
    console.log(i);
}
```

Eredmény:

```
2
4
6
8
10
```

A ciklusváltozó minden ismétlés után kettővel növekszik.

Hasonlóan kiírhatjuk a páratlan számokat is:

```javascript
for (let i = 1; i <= 9; i += 2) {
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

## 7. A `for` ciklus és a tömbök

A `for` ciklus egyik leggyakoribb felhasználási területe a tömbök elemeinek feldolgozása.

Tegyük fel, hogy rendelkezünk egy neveket tartalmazó tömbbel:

```javascript
const nevek = ['Anna', 'Béla', 'Csilla', 'Dávid'];

for (let i = 0; i < nevek.length; i++) {
    console.log(nevek[i]);
}
```

A konzol eredménye:

```
Anna
Béla
Csilla
Dávid
```

Nézzük meg a ciklus részeit:

- `let i = 0`: a tömb első elemének indexe 0.
- `i < nevek.length`: a ciklus addig fut, amíg az index kisebb a tömb hosszánál.
- `i++`: minden ismétlés után a következő elem indexére lépünk.
- `nevek[i]`: lekérjük a tömb aktuális elemét.

Miért használjuk az `i < nevek.length` feltételt?

A tömbök indexelése 0-tól kezdődik. Ha egy tömb négy elemet tartalmaz, akkor az érvényes indexek:

```
0, 1, 2, 3
```

A tömb hossza viszont 4. Ezért a ciklus feltétele `i < nevek.length`, nem pedig `i <= nevek.length`.

Ha egyenlőséget is megengednénk, a ciklus megpróbálná elérni a `nevek[4]` elemet, amely nem létezik.

## 8. A `break` utasítás használata ciklusban

A `break` utasítással idő előtt megszakíthatjuk a ciklus végrehajtását.

Például keressük meg az első 7-tel osztható számot 1 és 20 között!

```javascript
for (let i = 1; i <= 20; i++) {
    if (i % 7 === 0) {
        console.log('Megtaláltuk:', i);
        break;
    }
}
```

Eredmény:

```
Megtaláltuk: 7
```

A `break` hatására a ciklus azonnal befejeződik, ezért a 8–20 közötti számokat már nem vizsgálja meg.

A `break` tehát akkor hasznos, ha egy adott feltétel teljesülése után nincs szükség további ismétlésekre.

## 9. A `continue` utasítás használata ciklusban

A `continue` utasítás segítségével kihagyhatjuk az aktuális ismétlés hátralévő utasításait, és a ciklus a következő ismétléssel folytatódik.

Például írjuk ki az 1 és 10 közötti számokat, de a páros számokat hagyjuk ki!

```javascript
for (let i = 1; i <= 10; i++) {
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

A `i % 2 === 0` feltétel azt vizsgálja, hogy a szám páros-e.

Ha a feltétel igaz, a `continue` átugorja a `console.log(i)` utasítást, és a következő ismétlésre lép.

A `break` és a `continue` közötti különbség:

| Utasítás   | Működés                                                            |
| ---------- | ------------------------------------------------------------------ |
| `break`    | Teljesen megszakítja a ciklust.                                    |
| `continue` | Csak az aktuális ismétlést szakítja meg, majd folytatja a ciklust. |

## 10. Egymásba ágyazott `for` ciklusok

Előfordulhat, hogy egy cikluson belül egy másik ciklust is szeretnénk futtatni. Ezt egymásba ágyazott ciklusnak nevezzük.

Például készítsünk egy egyszerű szorzótáblát!

```javascript
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        console.log(i + ' * ' + j + ' = ' + i * j);
    }
}
```

A program eredménye:

```
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
2 * 1 = 2
2 * 2 = 4
2 * 3 = 6
3 * 1 = 3
3 * 2 = 6
3 * 3 = 9
```

A működés lépései:

1. A külső ciklus elindul, és az `i` értéke 1 lesz.
2. Elindul a belső ciklus, amely a `j` változót 1-től 3-ig növeli.
3. A belső ciklus mindhárom ismétlése végrehajtódik.
4. A belső ciklus befejeződik.
5. A külső ciklus növeli az `i` értékét 2-re.
6. A belső ciklus ismét lefut háromszor.
7. A folyamat addig ismétlődik, amíg a külső ciklus is befejeződik.

A belső ciklus minden külső ciklusbeli ismétlésnél teljesen lefut.

Mikor használunk egymásba ágyazott ciklusokat?

- Szorzótáblák készítésénél.
- Kétdimenziós tömbök feldolgozásánál.
- Táblázatok sorainak és oszlopainak bejárásánál.
- Összetettebb ismétlődő feladatok megoldásánál.

## 11. Gyakori hibák a `for` ciklus használatakor

A ciklusok használatakor néhány tipikus hibára érdemes figyelni.

1\. Végtelen ciklus

```javascript
for (let i = 1; i <= 5; ) {
    console.log(i);
}
```

Ebben a példában a ciklusváltozó nem változik, ezért a feltétel mindig igaz marad.

A ciklus soha nem fejeződik be magától.

Helyesen:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

2\. Hibás feltétel tömb feldolgozásakor

```javascript
const szamok = [10, 20, 30];

for (let i = 0; i <= szamok.length; i++) {
    console.log(szamok[i]);
}
```

A ciklus az utolsó érvényes index után is végrehajtódik. A `szamok[3]` értéke `undefined` lesz.

Helyesen:

```javascript
for (let i = 0; i < szamok.length; i++) {
    console.log(szamok[i]);
}
```

3\. Hibás kezdőérték

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Ez a ciklus 1-től 5-ig írja ki a számokat. Ha viszont egy tömb elemeit szeretnénk feldolgozni, általában 0-ról kell indítani az indexet.

4\. A `break` és a `continue` összekeverése

A `break` az egész ciklust befejezi, a `continue` viszont csak az aktuális ismétlést hagyja ki.

5\. Rosszul megválasztott léptetés

Ha a feltétel növekvő értékeket vár, de a változót folyamatosan csökkentjük, a ciklus könnyen végtelenné válhat.

Például:

```javascript
for (let i = 1; i <= 5; i--) {
    console.log(i);
}
```

Az `i` értéke folyamatosan csökken, így soha nem lesz nagyobb 5-nél.

# 12. Ellenőrző kérdések

1\. Mire használjuk a `for` ciklust?

A) Változók törlésére.

B) Utasítások ismételt végrehajtására.

C) Függvények deklarálására.

D) Objektumok létrehozására.

2\. Hány fő részből áll a `for` ciklus fejléce?

A) Egyből.

B) Kettőből.

C) Háromból.

D) Négyből.

3\. Mit jelent a következő kódrészlet?

```javascript
let i = 1;
```

A) A ciklus azonnal befejeződik.

B) A változó értéke 1 lesz.

C) A változó értéke 0 lesz.

D) A változó minden ismétlésnél csökken.

4\. Mit csinál az `i++` utasítás?

A) Eggyel csökkenti az `i` értékét.

B) Kettővel növeli az `i` értékét.

C) Eggyel növeli az `i` értékét.

D) Nullára állítja az `i` értékét.

5\. Mit jelent az `i < 5` feltétel?

A) Az `i` értéke nagyobb 5-nél.

B) Az `i` értéke kisebb 5-nél.

C) Az `i` értéke pontosan 5.

D) Az `i` értéke nem lehet 5.

6\. Melyik utasítás szakítja meg teljesen a ciklust?

A) `continue`

B) `return`

C) `break`

D) `skip`

7\. Mi történik a `continue` utasítás használatakor?

A) A ciklus teljesen leáll.

B) A program újraindul.

C) Az aktuális ismétlés hátralévő része kimarad.

D) A ciklusváltozó törlődik.

8\. Miért használjuk általában a `i < tomb.length` feltételt egy tömb bejárásakor?

A) Mert a tömb indexelése 1-től kezdődik.

B) Mert így elkerüljük a tömb határain túli indexelést.

C) Mert így minden elem kétszer jelenik meg.

D) Mert a `length` mindig nullát ad vissza.

9\. Mit ír ki az alábbi kód?

```javascript
for (let i = 2; i <= 6; i += 2) {
    console.log(i);
}
```

A) 1, 2, 3, 4, 5, 6

B) 2, 3, 4, 5, 6

C) 2, 4, 6

D) 2, 4, 6, 8

10\. Mit nevezünk egymásba ágyazott ciklusnak?

A) Amikor egy ciklus nem tartalmaz feltételt.

B) Amikor egy cikluson belül egy másik ciklus is található.

C) Amikor egy ciklus azonnal leáll.

D) Amikor két változó azonos értéket kap.

# 13. Gyakorlati feladatok

A következő feladatokat JavaScriptben oldd meg! A megoldások során elsősorban a `for` ciklust használd.

1\. Számok kiírása

Írj programot, amely 1-től 20-ig kiírja az egész számokat a konzolra.

2\. Visszaszámlálás

Készíts egy ciklust, amely 10-től 1-ig visszafelé számol.

A számok kiírása után jelenjen meg a következő szöveg:

```
Indulás!
```

3\. Páros számok

Írd ki a 2 és 50 közötti páros számokat!

A feladatot úgy oldd meg, hogy a ciklusváltozó mindig kettővel növekedjen.

4\. Számok összege

Hozz létre egy `osszeg` nevű változót, amely kezdetben 0 értéket tartalmaz.

Egy `for` ciklus segítségével add össze az 1 és 100 közötti egész számokat!

A ciklus végén jelenítsd meg az összeget.

5\. Szorzótábla

Kérj le vagy hozz létre egy számot tároló változót.

Egy `for` ciklus segítségével jelenítsd meg a szám szorzótábláját 1-től 10-ig!

Például a 7-es szám esetén:

```
7 * 1 = 7
7 * 2 = 14
7 * 3 = 21
...
7 * 10 = 70
```

6\. Tömb elemeinek kiírása

Hozz létre egy legalább 5 elemből álló, számokat tartalmazó tömböt.

A `for` ciklus segítségével írd ki a tömb összes elemét!

A ciklus fejlécében a tömb `length` tulajdonságát használd.

7\. Tömb elemeinek összeadása

Hozz létre egy számokat tartalmazó tömböt.

A `for` ciklus segítségével számítsd ki a tömb elemeinek összegét!

Az eredményt a ciklus befejezése után jelenítsd meg.

8\. Pozitív és negatív számok megszámlálása

Hozz létre egy számokat tartalmazó tömböt, amely pozitív, negatív és nulla értékeket is tartalmaz.

A `for` ciklus és az `if` utasítás segítségével számold meg:

- Hány pozitív szám található a tömbben?
- Hány negatív szám található a tömbben?
- Hány nulla található a tömbben?

Az eredményeket külön változókban tárold.

9\. Keresés tömbben

Hozz létre egy számokat tartalmazó tömböt, valamint egy `keresettSzam` változót.

A `for` ciklus segítségével keresd meg, hogy a keresett szám megtalálható-e a tömbben!

Ha megtaláltad, jelenítsd meg az indexét is.

Használd a `break` utasítást, hogy a találat után a keresés befejeződjön.

10\. Szorzótábla egymásba ágyazott ciklusokkal

Két egymásba ágyazott `for` ciklus segítségével készítsd el az 1-től 10-ig terjedő szorzótáblát!

A külső ciklus határozza meg az első szorzótényezőt, a belső ciklus pedig a másodikat.

Minden szorzást külön sorban jeleníts meg.

# 14. Összefoglalás

A `for` ciklus segítségével egy utasítást vagy utasításcsoportot többször végrehajthatunk.

A ciklus három fő része:

| Rész       | Feladat                                    |
| ---------- | ------------------------------------------ |
| Kezdőérték | Beállítja a ciklusváltozó kezdeti értékét  |
| Feltétel   | Meghatározza, hogy folytatódhat-e a ciklus |
| Léptetés   | Módosítja a ciklusváltozó értékét          |

A legfontosabb utasítások:

- `i++`: növelés eggyel.
- `i--`: csökkentés eggyel.
- `i += 2`: növelés kettővel.
- `break`: a ciklus megszakítása.
- `continue`: az aktuális ismétlés kihagyása.

A `for` ciklus leggyakoribb felhasználási területei:

- Számok ismételt kiírása.
- Összegek és átlagok kiszámítása.
- Tömbök elemeinek feldolgozása.
- Keresés és számlálás.
- Egymásba ágyazott ismétlések végrehajtása.
