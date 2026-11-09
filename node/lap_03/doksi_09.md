# JavaScript – Beágyazott ciklusok

## 1. Mi az a beágyazott ciklus?

Beágyazott ciklusnak nevezzük azt a programozási szerkezetet, amikor egy cikluson belül egy másik ciklust helyezünk el.

A külső ciklus minden egyes ismétlésekor a belső ciklus is végrehajtódik.

A beágyazott ciklusokat akkor használjuk, amikor több szinten kell ismétlődő műveleteket végrehajtanunk.

Például:

- táblázatok sorainak és oszlopainak feldolgozásakor;
- szorzótábla előállításakor;
- kétdimenziós tömbök bejárásakor;
- több elem kombinációinak előállításakor;
- különböző mintázatok és alakzatok kirajzolásakor.

A beágyazott ciklusok használhatók `for`, `while`, `do...while`, `for...of` és `for...in` ciklusokkal is.

## 2. A beágyazott `for` ciklus felépítése

A legegyszerűbb beágyazott ciklus két egymásba helyezett `for` ciklusból áll.

```javascript
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 4; j++) {
        console.log(i, j);
    }
}
```

A kimenet:

```
1 1
1 2
1 3
1 4
2 1
2 2
2 3
2 4
3 1
3 2
3 3
3 4
```

A példában:

- Az `i` a külső ciklus változója.
- A `j` a belső ciklus változója.
- A külső ciklus háromszor fut le.
- A belső ciklus minden külső ismétlésben négyszer fut le.

Ez összesen 3 × 4, vagyis 12 belső ciklusbeli ismétlést jelent.

## 3. Hogyan működik a beágyazott ciklus?

Nézzük meg részletesebben az előző példát!

```javascript
for (let i = 1; i <= 3; i++) {
    console.log('Külső ciklus:', i);

    for (let j = 1; j <= 3; j++) {
        console.log('Belső ciklus:', j);
    }
}
```

A végrehajtás sorrendje:

1. A külső ciklus elindul, `i = 1`.
2. A belső ciklus elindul, `j = 1`.
3. A belső ciklus végrehajtódik `j = 2` értéknél.
4. A belső ciklus végrehajtódik `j = 3` értéknél.
5. A belső ciklus befejeződik.
6. A külső ciklus továbblép, `i = 2`.
7. A belső ciklus ismét elindul `j = 1` értékkel.
8. A folyamat megismétlődik.
9. A harmadik külső ismétlés után a teljes szerkezet befejeződik.

Fontos: a belső ciklus minden új külső ismétlésnél elölről indul.

## 4. Szorzótábla készítése beágyazott ciklussal

A beágyazott ciklusok egyik klasszikus felhasználási területe a szorzótábla előállítása.

```javascript
for (let i = 1; i <= 10; i++) {
    for (let j = 1; j <= 10; j++) {
        console.log(i + ' * ' + j + ' = ' + i * j);
    }
}
```

A program minden számhoz kiszámolja az 1 és 10 közötti számokkal való szorzatot.

A kimenet eleje:

```
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
...
1 * 10 = 10
2 * 1 = 2
2 * 2 = 4
...
```

A külső ciklus kiválasztja az első szorzót, a belső ciklus pedig végigmegy a második szorzón.

## 5. Táblázat létrehozása

A beágyazott ciklusokkal egyszerű szöveges táblázatot is előállíthatunk.

```javascript
for (let sor = 1; sor <= 3; sor++) {
    let szoveg = '';

    for (let oszlop = 1; oszlop <= 4; oszlop++) {
        szoveg += '* ';
    }

    console.log(szoveg);
}
```

Kimenet:

```
* * * *
* * * *
* * * *
```

A működés:

- A külső ciklus három sort hoz létre.
- A belső ciklus minden sorban négy csillagot helyez el.
- A belső ciklus végén a teljes sor kiírásra kerül.

Ez a megoldás jól szemlélteti, hogyan lehet sorokat és oszlopokat előállítani ciklusok segítségével.

## 6. Háromszög alakzat készítése

A beágyazott ciklusokkal változó hosszúságú sorokat is létrehozhatunk.

```javascript
for (let sor = 1; sor <= 5; sor++) {
    let szoveg = '';

    for (let oszlop = 1; oszlop <= sor; oszlop++) {
        szoveg += '* ';
    }

    console.log(szoveg);
}
```

Kimenet:

```
*
* *
* * *
* * * *
* * * * *
```

Ebben a példában a belső ciklus futásainak száma a külső ciklus változójától függ.

- Az első sorban egy csillag jelenik meg.
- A második sorban kettő.
- A harmadik sorban három.
- A negyedik sorban négy.
- Az ötödik sorban öt.

A `oszlop <= sor` feltétel biztosítja, hogy minden sorban eggyel több csillag legyen.

## 7. Beágyazott ciklusok és tömbök

A beágyazott ciklusok különösen hasznosak kétdimenziós tömbök feldolgozásakor.

A kétdimenziós tömb olyan adatszerkezet, amelyben a tömb elemei maguk is tömbök.

Példa:

```javascript
const adatok = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90],
];
```

A tömb három belső tömböt tartalmaz. Mindegyik belső tömb három számot tárol.

Az elemek bejárása:

```javascript
for (let i = 0; i < adatok.length; i++) {
    for (let j = 0; j < adatok[i].length; j++) {
        console.log(adatok[i][j]);
    }
}
```

Kimenet:

```
10
20
30
40
50
60
70
80
90
```

A változók jelentése:

- `i`: a külső tömb aktuális indexe;
- `j`: az aktuális belső tömb indexe;
- `adatok[i]`: a kiválasztott belső tömb;
- `adatok[i][j]`: a kétdimenziós tömb aktuális eleme.

## 8. Kétdimenziós tömb sorainak feldolgozása

A beágyazott ciklusokkal nemcsak az egyes elemeket, hanem a sorok összegét is kiszámíthatjuk.

```javascript
const eredmenyek = [
    [10, 20, 30],
    [15, 25, 35],
    [5, 10, 15],
];

for (let i = 0; i < eredmenyek.length; i++) {
    let osszeg = 0;

    for (let j = 0; j < eredmenyek[i].length; j++) {
        osszeg += eredmenyek[i][j];
    }

    console.log('A(z) ' + (i + 1) + '. sor összege: ' + osszeg);
}
```

Kimenet:

```
A(z) 1. sor összege: 60
A(z) 2. sor összege: 75
A(z) 3. sor összege: 30
```

Minden külső ciklusban létrehozunk egy új `osszeg` változót. A belső ciklus összeadja az adott sor elemeit.

## 9. Beágyazott `for...of` ciklusok

A kétdimenziós tömbök feldolgozására a `for...of` ciklus is alkalmas.

```javascript
const adatok = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90],
];

for (let sor of adatok) {
    for (let ertek of sor) {
        console.log(ertek);
    }
}
```

A működés:

- A külső `for...of` ciklus egy-egy belső tömböt ad vissza.
- A belső `for...of` ciklus az adott tömb elemein halad végig.
- A program minden számot külön kiír.

Ez a megoldás akkor különösen kényelmes, ha nincs szükségünk az elemek indexére.

## 10. `break` használata beágyazott ciklusokban

A `break` utasítás alapértelmezés szerint csak azt a ciklust szakítja meg, amelyben közvetlenül szerepel.

```javascript
for (let i = 1; i <= 3; i++) {
    console.log('Külső:', i);

    for (let j = 1; j <= 5; j++) {
        if (j === 3) {
            break;
        }

        console.log('Belső:', j);
    }
}
```

Kimenet:

```
Külső: 1
Belső: 1
Belső: 2
Külső: 2
Belső: 1
Belső: 2
Külső: 3
Belső: 1
Belső: 2
```

A belső ciklus minden alkalommal a 3-as értéknél megszakad, de a külső ciklus tovább folytatódik.

## 11. `continue` használata beágyazott ciklusokban

A `continue` szintén csak azt a ciklust befolyásolja, amelyben szerepel.

```javascript
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 4; j++) {
        if (j === 2) {
            continue;
        }

        console.log(i, j);
    }
}
```

A kimenet:

```
1 1
1 3
1 4
2 1
2 3
2 4
3 1
3 3
3 4
```

Minden külső ciklusban kimarad a belső ciklus második ismétlése.

## 12. Címkézett `break` és `continue`

Ha egy beágyazott ciklusban a külső ciklust is szeretnénk megszakítani, címkézett `break` utasítást használhatunk.

```javascript
kulso: for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 5; j++) {
        if (i === 2 && j === 3) {
            break kulso;
        }

        console.log(i, j);
    }
}
```

A `break kulso` megszakítja a címkével megjelölt külső ciklust is.

A címkézett `continue` segítségével a külső ciklus következő ismétlésére ugorhatunk:

```javascript
kulso: for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        if (j === 2) {
            continue kulso;
        }

        console.log(i, j);
    }
}
```

Ez az adott külső ismétlés hátralévő részét is kihagyja, és a külső ciklus következő értékével folytatja.

## 13. Háromszintű beágyazott ciklusok

Nemcsak két, hanem akár három vagy több ciklust is egymásba ágyazhatunk.

```javascript
for (let i = 1; i <= 2; i++) {
    for (let j = 1; j <= 3; j++) {
        for (let k = 1; k <= 2; k++) {
            console.log(i, j, k);
        }
    }
}
```

A külső ciklus kétszer fut le, a középső ciklus minden külső ismétlésben háromszor, a legbelső pedig minden középső ismétlésben kétszer.

Az összes belső végrehajtás száma:

\\[ 2 * 3 * 2 = 12 \\]

A háromszintű ciklusok hasznosak lehetnek összetett adatszerkezetek feldolgozásakor, de a túl sok egymásba ágyazott ciklus nehezebben olvashatóvá teheti a programot.

## 14. A beágyazott ciklusok teljesítménye

A beágyazott ciklusoknál fontos figyelembe venni, hogy a belső ciklus hányszor fut le.

Például:

```javascript
for (let i = 0; i < 100; i++) {
    for (let j = 0; j < 100; j++) {
        console.log(i, j);
    }
}
```

A külső ciklus 100-szor fut le, a belső ciklus pedig minden alkalommal 100-szor.

Ez összesen:

\\[ 100 * 100 = 10,000 \\]

végrehajtást jelent.

Ha mindkét ciklus 1000-szer fut le, akkor már 1 000 000 belső végrehajtással kell számolnunk.

A beágyazott ciklusok használatakor ezért érdemes figyelni:

- a feldolgozandó adatok mennyiségére;
- a ciklusok ismétlésszámára;
- a felesleges műveletek elkerülésére;
- arra, hogy valóban szükség van-e minden belső ismétlésre.

## 15. Gyakori hibák

1\. A ciklusváltozók összekeverése

A külső és belső ciklushoz külön változót használjunk.

Helyes:

```javascript
for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 4; j++) {
        console.log(i, j);
    }
}
```

2\. Hibás tömbindexelés

Kétdimenziós tömbnél figyelni kell arra, hogy a külső és a belső indexet is helyesen használjuk.

```javascript
const adatok = [
    [10, 20],
    [30, 40],
];

console.log(adatok[1][0]);
```

A kimenet `30`, mert először a második belső tömböt választjuk ki, majd annak első elemét.

3\. Rosszul megválasztott ciklusfeltétel

Ha a belső ciklus feltétele nem megfelelő, előfordulhat, hogy a ciklus nem fut le, vagy túl sokszor ismétlődik.

4\. A `break` félreértése

A `break` alapértelmezés szerint csak a közvetlenül körülötte lévő ciklust szakítja meg, nem az összes beágyazott ciklust.

5\. Túl sok egymásba ágyazott ciklus

A túlzott beágyazás nehezen olvasható és lassú programot eredményezhet. Érdemes a bonyolultabb feldolgozási részeket külön függvényekbe szervezni.

# 16. Ellenőrző kérdések

1\. Mit nevezünk beágyazott ciklusnak?

A) Olyan ciklust, amely soha nem fejeződik be.\
B) Olyan ciklust, amelyen belül egy másik ciklus található.\
C) Olyan ciklust, amely csak egyszer fut le.\
D) Olyan ciklust, amely nem tartalmaz ciklusváltozót.

2\. Hányszor fut le a belső ciklus az alábbi példában?

```javascript
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 4; j++) {
        console.log(i, j);
    }
}
```

A) 3 alkalommal.\
B) 4 alkalommal.\
C) 7 alkalommal.\
D) 12 alkalommal.

3\. Mi történik a belső ciklussal, amikor a külső ciklus újabb ismétlésre lép?

A) A belső ciklus folytatja az előző ismétléstől.\
B) A belső ciklus újra elindul.\
C) A belső ciklus végleg leáll.\
D) A belső ciklus változói automatikusan törlődnek.

4\. Mit jelent az alábbi kifejezés?

```javascript
adatok[i][j];
```

A) A tömb teljes hosszát.\
B) Az `i` és `j` változók összegét.\
C) A kétdimenziós tömb adott sorának adott elemét.\
D) A tömb első elemét.

5\. Mi lesz az alábbi kód kimenete?

```javascript
for (let i = 1; i <= 2; i++) {
    for (let j = 1; j <= 3; j++) {
        console.log(i, j);
    }
}
```

A) 3 sor.\
B) 5 sor.\
C) 6 sor.\
D) 9 sor.

6\. Mit szakít meg alapértelmezés szerint a belső ciklusban elhelyezett `break`?

A) Az összes ciklust.\
B) Csak a belső ciklust.\
C) Csak a külső ciklust.\
D) A teljes JavaScript-programot.

7\. Mire használható a `continue` beágyazott ciklusban?

A) A teljes program leállítására.\
B) Az összes ciklus megszakítására.\
C) Az aktuális ciklusismétlés hátralévő részének kihagyására.\
D) A külső ciklus automatikus újraindítására.

8\. Melyik ciklusváltozó jelöli általában a kétdimenziós tömb sorát az alábbi kódban?

```javascript
for (let i = 0; i < adatok.length; i++) {
    for (let j = 0; j < adatok[i].length; j++) {
        console.log(adatok[i][j]);
    }
}
```

A) `i`\
B) `j`\
C) Mindkettő kizárólag az oszlopot jelöli.\
D) Egyik sem.

9\. Hány belső ciklusvégrehajtás történik az alábbi kódban?

```javascript
for (let i = 0; i < 4; i++) {
    for (let j = 0; j < 5; j++) {
        console.log(i, j);
    }
}
```

A) 9\
B) 15\
C) 20\
D) 25

10\. Miért lehet problémás a túl sok egymásba ágyazott ciklus használata?

A) Mert a JavaScript nem támogatja a három ciklust.\
B) Mert a ciklusváltozók nem módosíthatók.\
C) Mert a program nehezebben olvasható és lassabb lehet.\
D) Mert a belső ciklus mindig végtelen lesz.

# 17. Gyakorló feladatok

1\. Téglalap kirajzolása

Készíts két egymásba ágyazott `for` ciklust!

A feladatod:

- A külső ciklus 5 sort hozzon létre.
- A belső ciklus minden sorban 8 csillagot helyezzen el.
- A csillagokat egyetlen sorban jelenítsd meg.
- Minden sor végén használj `console.log()` utasítást!

Elvárt kimenet:

```
* * * * * * * *
* * * * * * * *
* * * * * * * *
* * * * * * * *
* * * * * * * *
```

2\. Számpiramis készítése

Készíts egy számpiramist beágyazott ciklusok segítségével!

A feladatod:

- A külső ciklus 1-től 5-ig fusson.
- A belső ciklus minden sorban az aktuális sorszámot írja ki.
- A számok között legyen szóköz!

Elvárt kimenet:

```
1
2 2
3 3 3
4 4 4 4
5 5 5 5 5
```

3\. Szorzótábla elkészítése

Készíts 10 × 10-es szorzótáblát!

A feladatod:

- Használj két egymásba ágyazott `for` ciklust.
- A külső ciklus határozza meg az első szorzót.
- A belső ciklus határozza meg a második szorzót.
- Minden szorzási eredményt jeleníts meg!
- A kimenet legyen jól áttekinthető.

4\. Kétdimenziós tömb bejárása

Hozz létre egy háromsoros, soronként négy elemet tartalmazó kétdimenziós tömböt!

A feladatod:

- Használj két egymásba ágyazott `for` ciklust.
- Járd be a teljes tömböt!
- Minden elemet külön sorban írj ki!
- A kiírás során jelenítsd meg az elem sor- és oszlopindexét is!

5\. Soronkénti összeg kiszámítása

Hozz létre egy kétdimenziós tömböt, amely legalább négy sort tartalmaz, soronként négy számmal.

A feladatod:

- A külső ciklus haladjon végig a sorokon.
- A belső ciklus adja össze az aktuális sor elemeit.
- Minden sor összegét külön jelenítsd meg!
- A végén számold ki a teljes tömbben található számok összegét is!

6\. Páros számok keresése kétdimenziós tömbben

Hozz létre egy kétdimenziós tömböt pozitív egész számokkal!

A feladatod:

- Járd be a tömb minden elemét beágyazott ciklusokkal.
- A `%` operátor segítségével vizsgáld meg, hogy a szám páros-e.
- Csak a páros számokat jelenítsd meg!
- Számold meg, hány páros szám található a tömbben!

7\. Háromszög alakzat készítése

Készíts egy növekvő és egy csökkenő csillagmintát!

A feladatod:

- Az első külső ciklus 1-től 5-ig fusson, és növekvő számú csillagot jelenítsen meg.
- A második külső ciklus 5-től 1-ig fusson, és csökkenő számú csillagot jelenítsen meg.
- Mindkét esetben használj belső ciklust!
- A két alakzat között jeleníts meg egy üres sort!

Elvárt kimenet:

```
*
* *
* * *
* * * *
* * * * *

* * * * *
* * * *
* * *
* *
*
```

8\. Két tömb elemeinek összehasonlítása

Hozz létre két különálló tömböt, amelyek számokat tartalmaznak!

A feladatod:

- Használj két egymásba ágyazott `for` ciklust.
- A külső ciklus az első tömb elemein haladjon végig.
- A belső ciklus a második tömb elemein haladjon végig.
- Jelenítsd meg azokat az értékpárokat, amelyeknél a két szám egyenlő!

9\. Címkézett ciklus használata

Készíts két egymásba ágyazott `for` ciklust!

A feladatod:

- A külső ciklus 1-től 5-ig fusson.
- A belső ciklus szintén 1-től 5-ig fusson.
- Jelenítsd meg mindkét ciklusváltozó értékét!
- Ha a külső változó értéke 3, a belső változó értéke pedig 2, a `break` segítségével szakítsd meg a külső ciklust is!
- A feladatot címkézett ciklussal oldd meg!

10\. Egyszerű ülésrend kezelése

Készíts egy kétdimenziós tömböt, amely egy terem ülésrendjét tárolja!

Például:

```javascript
const ulesrend = [
    ['Anna', 'Béla', 'Csilla'],
    ['Dávid', 'Erika', 'Ferenc'],
    ['Gábor', 'Hanna', 'István'],
];
```

A feladatod:

- Járd be a teljes ülésrendet beágyazott ciklusokkal!
- Jelenítsd meg minden tanuló nevét a sor- és oszlopszámával együtt!
- Számold meg, hány tanuló található a teremben!
- Kérj be egy tanulónevet a `prompt()` segítségével!
- Keresd meg a tanulót a kétdimenziós tömbben!
- Ha megtaláltad, jelenítsd meg a helyét, majd címkézett `break` segítségével lépj ki mindkét ciklusból!
- Ha nem található meg, jeleníts meg egy megfelelő üzenetet!

## 18. Összefoglalás

A beágyazott ciklus olyan ciklusszerkezet, amelyben egy másik ciklus található.

A legfontosabb tudnivalók:

- A külső ciklus minden ismétlésekor a belső ciklus is végrehajtódik.
- A belső ciklus minden új külső ismétlésnél újra elindul.
- A beágyazott ciklusok alkalmasak kétdimenziós tömbök feldolgozására.
- Segítségükkel táblázatok, szorzótáblák és különböző mintázatok készíthetők.
- A `break` és a `continue` alapértelmezés szerint csak a legbelső ciklusra hat.
- Címkézett utasításokkal a külső ciklus is vezérelhető.
- A ciklusok számának növekedésével a végrehajtások száma jelentősen emelkedhet.

Fontos összefüggés:

Ha a külső ciklus 5-ször, a belső ciklus pedig minden alkalommal 4-szer fut le, akkor a belső ciklus összesen 20-szor hajtódik végre.
