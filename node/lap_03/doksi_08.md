# JavaScript – `break` és `continue`

## 1. Mi a `break` és a `continue`?

A `break` és a `continue` olyan vezérlési utasítások, amelyekkel befolyásolhatjuk a ciklusok működését.

Segítségükkel nemcsak azt határozhatjuk meg, hogy egy ciklus hányszor fusson le, hanem azt is, hogy bizonyos feltételek teljesülésekor mi történjen az ismétlésekkel.

- A `break` teljesen megszakítja a ciklus végrehajtását.
- A `continue` kihagyja az aktuális ismétlés hátralévő részét, majd a ciklus folytatódik a következő ismétléssel.

Mindkét utasítás használható a következő ciklusokban:

- `for`
- `while`
- `do...while`
- `for...of`
- `for...in`

A következőkben külön-külön megvizsgáljuk a működésüket.

## 2. A `break` utasítás

A `break` utasítás segítségével idő előtt megszakíthatjuk egy ciklus végrehajtását.

Amikor a program eléri a `break` utasítást, kilép az aktuális ciklusból. A ciklus utáni programkód végrehajtása folytatódik.

Alapvető szintaxis:

```javascript
break;
```

Példa:

```javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);

    if (i === 5) {
        break;
    }
}

console.log('A ciklus véget ért.');
```

Kimenet:

```
1
2
3
4
5
A ciklus véget ért.
```

A ciklus eredetileg tízszer futna le, de amikor az `i` értéke 5 lesz, a `break` megszakítja a végrehajtást.

Fontos megfigyelni, hogy az 5-ös szám még megjelenik, mert a `console.log(i)` a `break` előtt található.

## 3. A `break` használata `for` ciklusban

Gyakori felhasználási területe, amikor egy tömbben keresünk egy adott értéket.

Ha megtaláltuk a keresett elemet, nincs szükség a további elemek vizsgálatára.

```javascript
const szamok = [12, 25, 38, 47, 59, 64];

for (let i = 0; i < szamok.length; i++) {
    if (szamok[i] === 47) {
        console.log('A keresett szám megtalálható!');
        break;
    }

    console.log('Vizsgált szám:', szamok[i]);
}
```

Kimenet:

```
Vizsgált szám: 12
Vizsgált szám: 25
Vizsgált szám: 38
A keresett szám megtalálható!
```

Amikor a ciklus eléri a 47-es számot, a program kiírja a megfelelő üzenetet, majd a `break` segítségével kilép a ciklusból.

A 59 és 64 értékeket már nem vizsgálja meg.

## 4. A `break` használata `while` ciklusban

A `break` nemcsak a `for`, hanem a `while` ciklusban is használható.

```javascript
let szam = 1;

while (szam <= 10) {
    console.log(szam);

    if (szam === 6) {
        break;
    }

    szam++;
}
```

Kimenet:

```
1
2
3
4
5
6
```

Amikor a `szam` értéke 6 lesz, a `break` megszakítja a ciklust.

Ebben a példában a `szam++` már nem hajtódik végre a hatodik ismétlésben, mert a program előbb találkozik a `break` utasítással.

## 5. A `break` használata `for...of` ciklusban

A `for...of` ciklus esetén is megszakíthatjuk az elemek bejárását.

```javascript
const nevek = ['Anna', 'Béla', 'Csilla', 'Dávid', 'Erika'];

for (let nev of nevek) {
    if (nev === 'Csilla') {
        console.log('A keresett név megvan!');
        break;
    }

    console.log(nev);
}
```

Kimenet:

```
Anna
Béla
A keresett név megvan!
```

A ciklus a Csilla nevű elemnél megszakad, ezért a Dávid és az Erika már nem kerül feldolgozásra.

## 6. A `continue` utasítás

A `continue` utasítás nem szakítja meg teljesen a ciklust.

Ehelyett kihagyja az aktuális ismétlés hátralévő részét, majd a következő ismétléssel folytatja a végrehajtást.

Alapvető szintaxis:

```javascript
continue;
```

Példa:

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

Kimenet:

```
1
2
4
5
```

Amikor az `i` értéke 3 lesz, a `continue` kihagyja az aktuális ismétlés hátralévő részét.

Ezért a `console.log(i)` nem hajtódik végre a harmadik ismétlésben.

A ciklus azonban nem áll le, hanem folytatódik a 4-es értékkel.

## 7. A `continue` használata páros és páratlan számoknál

A `continue` különösen hasznos, ha bizonyos elemeket nem szeretnénk feldolgozni.

Például kiírhatjuk egy tömb páratlan számait úgy, hogy a páros számokat kihagyjuk.

```javascript
const szamok = [1, 2, 3, 4, 5, 6, 7, 8];

for (let szam of szamok) {
    if (szam % 2 === 0) {
        continue;
    }

    console.log(szam);
}
```

Kimenet:

```
1
3
5
7
```

A `%` operátor segítségével megvizsgáljuk, hogy a szám páros-e.

Ha a szám páros, a `continue` kihagyja az aktuális ismétlést. Ha páratlan, a program végrehajtja a `console.log()` utasítást.

## 8. A `continue` használata `while` ciklusban

A `while` ciklusban különösen figyelni kell a ciklusváltozó módosítására.

```javascript
let szam = 0;

while (szam < 6) {
    szam++;

    if (szam === 3) {
        continue;
    }

    console.log(szam);
}
```

Kimenet:

```
1
2
4
5
6
```

A ciklus a 3-as értéket kihagyja, de a többi számot megjeleníti.

Ebben a példában a `szam++` a `continue` előtt szerepel, ezért a ciklusváltozó minden ismétlésben növekszik.

Fontos: ha a ciklusváltozó növelése a `continue` után található, akkor előfordulhat, hogy a ciklus végtelenné válik.

Hibás példa:

```javascript
let szam = 0;

while (szam < 5) {
    if (szam === 2) {
        continue;
    }

    console.log(szam);
    szam++;
}
```

Amikor a `szam` értéke 2 lesz, a `continue` miatt a `szam++` már nem hajtódik végre. A változó értéke így folyamatosan 2 marad, a feltétel pedig mindig igaz lesz.

A ciklus ezért végtelenül ismétlődik.

## 9. A `break` és a `continue` használata egymással

A két utasítást ugyanabban a ciklusban is használhatjuk.

```javascript
for (let i = 1; i <= 10; i++) {
    if (i === 3) {
        continue;
    }

    if (i === 8) {
        break;
    }

    console.log(i);
}
```

Kimenet:

```
1
2
4
5
6
7
```

A működés:

1. Az 1 és 2 értékek megjelennek.
2. A 3-as értéknél a `continue` kihagyja a kiírást.
3. A 4, 5, 6 és 7 értékek megjelennek.
4. A 8-as értéknél a `break` megszakítja a ciklust.
5. A 9 és 10 értékek feldolgozása már nem történik meg.

## 10. A `break` és a `continue` használata beágyazott ciklusokban

A beágyazott ciklus azt jelenti, hogy egy cikluson belül egy másik ciklust helyezünk el.

Ilyenkor fontos tudni, hogy a `break` és a `continue` alapértelmezés szerint csak azt a legbelső ciklust befolyásolja, amelyben szerepel.

Példa:

```javascript
for (let i = 1; i <= 3; i++) {
    console.log('Külső ciklus:', i);

    for (let j = 1; j <= 5; j++) {
        if (j === 3) {
            break;
        }

        console.log('Belső ciklus:', j);
    }
}
```

Kimenet:

```
Külső ciklus: 1
Belső ciklus: 1
Belső ciklus: 2
Külső ciklus: 2
Belső ciklus: 1
Belső ciklus: 2
Külső ciklus: 3
Belső ciklus: 1
Belső ciklus: 2
```

A belső ciklus minden alkalommal a 3-as értéknél megszakad, de a külső ciklus tovább folytatódik.

A `continue` hasonlóan csak a legbelső ciklus aktuális ismétlését hagyja ki.

## 11. Címkézett `break` és `continue`

A JavaScript lehetőséget biztosít címkézett utasítások használatára is.

Ezekkel beágyazott ciklusok esetén nemcsak a legbelső ciklusra hivatkozhatunk.

A címke egy tetszőleges azonosító, amelyet kettőspont követ.

Példa címkézett `break` használatára:

```javascript
kulsoCiklus: for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 5; j++) {
        if (i === 2 && j === 3) {
            break kulsoCiklus;
        }

        console.log(i, j);
    }
}
```

Amikor az `i` értéke 2 és a `j` értéke 3 lesz, a `break kulsoCiklus` megszakítja a teljes, címkével megjelölt külső ciklust is.

Példa címkézett `continue` használatára:

```javascript
kulsoCiklus: for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        if (j === 2) {
            continue kulsoCiklus;
        }

        console.log(i, j);
    }
}
```

A `continue kulsoCiklus` a külső ciklus következő ismétlésére ugrik. Emiatt az adott külső ciklusban a belső ciklus további ismétlései kimaradnak.

A címkézett utasítások ritkábban használatosak, de összetettebb ciklusoknál hasznosak lehetnek.

## 12. A `break` és a `continue` összehasonlítása

| Szempont                    | `break`                       | `continue`                              |
| --------------------------- | ----------------------------- | --------------------------------------- |
| Teljes ciklus megszakítása  | Igen                          | Nem                                     |
| Aktuális ismétlés kihagyása | A ciklus megszűnik            | Igen                                    |
| Következő ismétlés          | Nem történik meg              | Végrehajtódik                           |
| Ciklus utáni kód            | Végrehajtódik                 | A ciklus befejezése után hajtódik végre |
| Tipikus felhasználás        | Keresés megszakítása, kilépés | Nem kívánt elemek kihagyása             |

A legfontosabb különbség:

```javascript
// break: a ciklus teljesen leáll
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }

    console.log(i);
}
```

```javascript
// continue: csak a 3-as érték kimarad
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

## 13. Mikor használjuk őket?

A `break` használata javasolt például:

- ha egy keresett elemet megtaláltunk;
- ha egy ciklusnak egy bizonyos feltételnél le kell állnia;
- ha egy menüből ki szeretnénk lépni;
- ha egy hibás vagy nem megfelelő állapot miatt nem szükséges folytatni a feldolgozást.

A `continue` használata javasolt például:

- ha bizonyos elemeket ki szeretnénk hagyni;
- ha csak meghatározott értékeket szeretnénk feldolgozni;
- ha egy tömbből csak a megfelelő elemeket szeretnénk megjeleníteni;
- ha egy feltétel teljesülésekor az aktuális ismétlés további műveleteire nincs szükség.

# 14. Ellenőrző kérdések

1\. Mire használjuk a `break` utasítást?

A) A ciklus újraindítására.\
B) A ciklus teljes megszakítására.\
C) Az aktuális változó törlésére.\
D) A következő ismétlés kihagyására.

2\. Mire használjuk a `continue` utasítást?

A) A teljes ciklus megszakítására.\
B) A program leállítására.\
C) Az aktuális ismétlés hátralévő részének kihagyására.\
D) A ciklusváltozó automatikus törlésére.

3\. Mi lesz az alábbi kód kimenete?

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }

    console.log(i);
}
```

A) `1 2 3 4 5`\
B) `1 2`\
C) `1 2 4 5`\
D) `3 4 5`

4\. Mi lesz az alábbi kód kimenete?

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

A) `1 2 3 4 5`\
B) `1 2`\
C) `1 2 4 5`\
D) `3 4 5`

5\. Melyik utasítás alkalmas arra, hogy egy keresett elem megtalálásakor befejezzük a keresést?

A) `continue`\
B) `break`\
C) `return` minden esetben\
D) `skip`

6\. Mi történik, ha egy `while` ciklusban a `continue` miatt kimarad a ciklusváltozó növelése?

A) A ciklus automatikusan befejeződik.\
B) A ciklusváltozó nullára áll.\
C) Végtelen ciklus alakulhat ki.\
D) A ciklus automatikusan új értéket kap.

7\. Mi történik az alábbi kódban?

```javascript
for (let i = 1; i <= 5; i++) {
    if (i % 2 === 0) {
        continue;
    }

    console.log(i);
}
```

A) Csak a páros számok jelennek meg.\
B) Csak a páratlan számok jelennek meg.\
C) Minden szám megjelenik.\
D) Egyetlen szám sem jelenik meg.

8\. Mit szakít meg alapértelmezés szerint a `break` egy beágyazott ciklusban?

A) Az összes ciklust.\
B) Csak a külső ciklust.\
C) A legbelső ciklust.\
D) A teljes JavaScript-programot.

9\. Melyik állítás igaz a `continue` utasításra?

A) Véglegesen megszakítja a ciklust.\
B) Kihagyja az aktuális ismétlés hátralévő részét.\
C) Mindig újraindítja a teljes programot.\
D) Törli a ciklusváltozót.

10\. Melyik kódrészlet írja ki az 1, 2, 4 és 5 számokat?

A)

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }
    console.log(i);
}
```

B)

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }
    console.log(i);
}
```

C)

```javascript
for (let i = 1; i <= 5; i++) {
    if (i !== 3) {
        break;
    }
    console.log(i);
}
```

D)

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
    break;
}
```

# 15. Gyakorló feladatok

1\. Ciklus megszakítása adott értéknél

Hozz létre egy `for` ciklust, amely 1-től 20-ig számol.

A feladatod:

- Írd ki a számokat a konzolra!
- Ha a ciklusváltozó értéke eléri a 12-t, szakítsd meg a ciklust `break` segítségével!
- A ciklus után jelenítsd meg a következő üzenetet: „A ciklus befejeződött.”

2\. Páros számok kihagyása

Hozz létre egy `for` ciklust, amely 1-től 30-ig halad.

A feladatod:

- A `continue` segítségével hagyd ki a páros számokat!
- Csak a páratlan számokat írd ki!
- Minden szám külön sorban jelenjen meg!

3\. Keresés tömbben

Hozz létre egy legalább tíz elemből álló számtömböt.

A feladatod:

- Kérj be egy számot a felhasználótól a `prompt()` segítségével!
- Járd be a tömböt egy `for` ciklussal!
- Ha megtalálod a keresett számot, jelenítsd meg a „Találat!” üzenetet!
- A találat után a `break` segítségével állítsd le a keresést!
- Ha nincs találat, jelenítsd meg a „Nincs ilyen szám a tömbben!” üzenetet!

4\. Csak a megfelelő osztályzatok megjelenítése

Hozz létre egy `osztalyzatok` nevű tömböt, amely 1 és 5 közötti értékeket tartalmaz.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- A `continue` segítségével hagyd ki az 1-es és 2-es osztályzatokat!
- A többi osztályzatot írd ki!

5\. Pozitív számok összeadása

Hozz létre egy tömböt, amely pozitív, negatív és nulla értékeket is tartalmaz.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- A negatív számokat hagyd ki `continue` segítségével!
- A nulla értéket se add hozzá az összeghez!
- A pozitív számokat add össze!
- A végén írd ki az eredményt!

6\. Jelszó ellenőrzése

Készíts egy egyszerű jelszóellenőrző programot!

A feladatod:

- Tárolj egy előre meghatározott jelszót egy változóban!
- Kérj be jelszót a felhasználótól!
- Amíg a felhasználó nem adja meg a helyes jelszót, ismételd a bekérést!
- Helyes jelszó esetén a `break` segítségével lépj ki a ciklusból!
- A kilépés után jelenítsd meg a „Sikeres bejelentkezés!” üzenetet!

7\. Számok keresése több feltétellel

Hozz létre egy 1-től 50-ig terjedő számtömböt.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- A 3-mal osztható számokat hagyd ki `continue` segítségével!
- Ha elérsz egy 40-nél nagyobb számot, szakítsd meg a ciklust `break` segítségével!
- A többi számot írd ki!

8\. Termékek feldolgozása

Hozz létre egy `termekek` nevű tömböt, amely legalább nyolc termék nevét tartalmazza.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- Egy előre meghatározott terméknév esetén szakítsd meg a ciklust `break` segítségével!
- Egy másik terméknév esetén hagyd ki az aktuális ismétlést `continue` segítségével!
- A többi termék nevét írd ki!

9\. Beágyazott ciklus megszakítása

Hozz létre két egymásba ágyazott `for` ciklust.

A feladatod:

- A külső ciklus 1-től 5-ig fusson!
- A belső ciklus szintén 1-től 5-ig fusson!
- Írd ki mindkét ciklusváltozó értékét!
- Ha a belső ciklusváltozó értéke 3, használd a `break` utasítást!
- Figyeld meg, hogy a külső ciklus folytatódik-e!

10\. Egyszerű számkitaláló játék

Készíts egy számkitaláló programot!

A feladatod:

- Tárolj egy titkos számot egy változóban!
- A felhasználó próbálja meg kitalálni a számot!
- Használj `while` ciklust a bekérések ismétlésére!
- Ha a megadott szám kisebb a titkos számnál, jelenítsd meg: „A keresett szám nagyobb!”
- Ha nagyobb, jelenítsd meg: „A keresett szám kisebb!”
- Ha eltalálta, jelenítsd meg: „Gratulálok, eltaláltad!”
- A helyes találat után a `break` segítségével lépj ki a ciklusból!

## 16. Összefoglalás

A `break` és a `continue` a ciklusok vezérlésére szolgáló utasítások.

| Utasítás   | Feladata                                        |
| ---------- | ----------------------------------------------- |
| `break`    | Megszakítja a teljes aktuális ciklust.          |
| `continue` | Kihagyja az aktuális ismétlés hátralévő részét. |

A legfontosabb tudnivalók:

- Mindkét utasítás használható a JavaScript ciklusaiban.
- A `break` után a program a ciklus utáni utasításokkal folytatódik.
- A `continue` után a ciklus a következő ismétlésre lép.
- Beágyazott ciklusoknál alapértelmezés szerint csak a legbelső ciklust befolyásolják.
- `while` ciklusban a `continue` használatakor figyelni kell a ciklusváltozó módosítására, nehogy végtelen ciklus alakuljon ki.
