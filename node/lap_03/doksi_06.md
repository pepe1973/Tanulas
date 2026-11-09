# JavaScript – `for...of` ciklus

## 1. Mi az a `for...of` ciklus?

A `for...of` ciklus a JavaScript egyik bejáró ciklusa. Segítségével egy iterálható adatszerkezet elemein haladhatunk végig úgy, hogy minden ismétlés során megkapjuk az aktuális elemet.

Leggyakrabban tömbök elemeinek feldolgozására használjuk, de más iterálható adatszerkezetekkel is működik, például:

- szövegekkel (`String`);
- tömbökkel (`Array`);
- halmazokkal (`Set`);
- térképekkel (`Map`);
- egyéb iterálható objektumokkal.

A `for...of` előnye, hogy nem kell külön indexváltozót létrehoznunk, nem szükséges a tömb hosszát lekérdeznünk, és nem kell kézzel növelnünk a ciklusváltozót.

## 2. A `for...of` ciklus felépítése

Általános szintaxisa:

```javascript
for (let elem of iterable) {
    // Ciklusmag
}
```

A részek jelentése:

| Elem       | Jelentés                                                        |
| ---------- | --------------------------------------------------------------- |
| `for`      | A ciklus kezdete.                                               |
| `let elem` | Az aktuális elem változója.                                     |
| `of`       | Jelzi, hogy az iterálható adatszerkezet elemein haladunk végig. |
| `iterable` | Az a bejárható adatszerkezet, amelynek elemeit feldolgozzuk.    |
| `{ }`      | A ciklusmag, amely minden elemnél végrehajtódik.                |

A ciklus minden ismétléskor az `iterable` következő elemét rendeli az `elem` változóhoz.

## 3. `for...of` ciklus használata tömbökkel

A `for...of` egyik leggyakoribb felhasználási területe a tömbök bejárása.

```javascript
const gyumolcsok = ['alma', 'körte', 'barack', 'szilva'];

for (let gyumolcs of gyumolcsok) {
    console.log(gyumolcs);
}
```

A kimenet:

```
alma
körte
barack
szilva
```

A ciklus működése:

1. Az első ismétlésben a `gyumolcs` értéke `"alma"`.
2. A második ismétlésben a `gyumolcs` értéke `"körte"`.
3. A harmadik ismétlésben a `gyumolcs` értéke `"barack"`.
4. A negyedik ismétlésben a `gyumolcs` értéke `"szilva"`.
5. Miután minden elemen végighaladt, a ciklus befejeződik.

## 4. Számok feldolgozása tömbben

A ciklus nemcsak szövegekkel, hanem számokkal is használható.

```javascript
const szamok = [10, 20, 30, 40, 50];

for (let szam of szamok) {
    console.log(szam);
}
```

A számok összegzésére is alkalmas:

```javascript
const szamok = [10, 20, 30, 40, 50];

let osszeg = 0;

for (let szam of szamok) {
    osszeg += szam;
}

console.log(osszeg);
```

Kimenet:

```
150
```

A ciklus minden elem értékét hozzáadja az `osszeg` változóhoz.

## 5. Feltételek használata a ciklusban

A `for...of` cikluson belül feltételeket is alkalmazhatunk.

Például megkereshetjük egy tömb páros számait:

```javascript
const szamok = [3, 8, 12, 15, 20, 23];

for (let szam of szamok) {
    if (szam % 2 === 0) {
        console.log(szam);
    }
}
```

Kimenet:

```
8
12
20
```

A `%` operátor a maradékos osztás eredményét adja vissza. Ha egy szám kettővel osztva nulla maradékot ad, akkor páros.

## 6. `break` használata

A `break` utasítással idő előtt megszakíthatjuk a ciklust.

```javascript
const szamok = [5, 10, 15, 20, 25];

for (let szam of szamok) {
    if (szam === 15) {
        break;
    }

    console.log(szam);
}
```

Kimenet:

```
5
10
```

Amikor a ciklus eléri a `15` értéket, a `break` megszakítja a teljes ciklust. A `15` és az utána következő elemek már nem kerülnek feldolgozásra.

## 7. `continue` használata

A `continue` utasítás az aktuális ismétlés hátralévő részét kihagyja, majd a ciklus a következő elemre lép.

```javascript
const szamok = [1, 2, 3, 4, 5, 6];

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
```

Ebben a példában a `continue` miatt a páros számok kiírása kimarad.

A `break` és a `continue` közötti különbség:

| Utasítás   | Működés                               |
| ---------- | ------------------------------------- |
| `break`    | Teljesen megszakítja a ciklust.       |
| `continue` | Csak az aktuális ismétlést hagyja ki. |

## 8. Szövegek bejárása `for...of` ciklussal

A szövegek is iterálható adatszerkezetek. A ciklus egyesével halad végig a szöveg karakterein.

```javascript
const szoveg = 'JavaScript';

for (let karakter of szoveg) {
    console.log(karakter);
}
```

Kimenet:

```
J
a
v
a
S
c
r
i
p
t
```

Ez például akkor lehet hasznos, ha egy szöveg karaktereit külön-külön szeretnénk feldolgozni.

## 9. `for...of` használata `Set` adatszerkezettel

A `Set` olyan adatszerkezet, amely egyedi értékeket tárol. Ugyanaz az érték csak egyszer szerepelhet benne.

```javascript
const szamok = new Set([10, 20, 20, 30, 30, 40]);

for (let szam of szamok) {
    console.log(szam);
}
```

Kimenet:

```
10
20
30
40
```

A `for...of` a `Set` egyedi elemein halad végig.

## 10. `for...of` használata `Map` adatszerkezettel

A `Map` kulcs-érték párokat tárol. A `for...of` ciklus minden ismétlésben egy kételemű tömböt ad vissza: az első elem a kulcs, a második az érték.

```javascript
const tanulo = new Map();

tanulo.set('nev', 'Kovács Anna');
tanulo.set('kor', 20);
tanulo.set('varos', 'Szeged');

for (let [kulcs, ertek] of tanulo) {
    console.log(kulcs, ertek);
}
```

Kimenet:

```
nev Kovács Anna
kor 20
varos Szeged
```

A szögletes zárójelek között szereplő változók segítségével közvetlenül különválaszthatjuk a kulcsot és az értéket.

## 11. `for...of` és a hagyományos `for` ciklus összehasonlítása

Mindkét ciklussal bejárhatunk egy tömböt, de eltérő módon működnek.

Hagyományos `for` ciklus:

```javascript
const gyumolcsok = ['alma', 'körte', 'barack'];

for (let i = 0; i < gyumolcsok.length; i++) {
    console.log(gyumolcsok[i]);
}
```

`for...of` ciklus:

```javascript
const gyumolcsok = ['alma', 'körte', 'barack'];

for (let gyumolcs of gyumolcsok) {
    console.log(gyumolcs);
}
```

| Szempont              | `for`                 | `for...of`           |
| --------------------- | --------------------- | -------------------- |
| Indexváltozó          | Általában szükséges   | Nem szükséges        |
| Tömbhossz lekérdezése | Gyakran szükséges     | Nem szükséges        |
| Aktuális elem elérése | Indexeléssel          | Közvetlenül          |
| Index kezelése        | Egyszerűen megoldható | Külön kell megoldani |
| Kód olvashatósága     | Több kódot igényelhet | Gyakran egyszerűbb   |

Ha csak az elemek értékére van szükségünk, általában a `for...of` a kényelmesebb választás. Ha az indexet is használni szeretnénk, a hagyományos `for` ciklus megfelelőbb lehet.

## 12. Fontos tudnivalók és gyakori hibák

1\. A `for...of` nem minden objektummal használható.

A `for...of` iterálható értékeket vár. Egy egyszerű objektum önmagában nem iterálható:

```javascript
const szemely = {
    nev: 'Anna',
    kor: 25,
};

// Ez hibát okoz:
for (let adat of szemely) {
    console.log(adat);
}
```

Egyszerű objektumok tulajdonságainak bejárására a `for...in`, illetve az `Object.keys()`, `Object.values()` és `Object.entries()` használható.

2\. A `for...of` közvetlenül az értékeket adja vissza, nem az indexeket.

```javascript
const nevek = ['Anna', 'Béla', 'Csilla'];

for (let nev of nevek) {
    console.log(nev);
}
```

A `nev` változó mindig az aktuális elem értékét tartalmazza.

3\. A ciklusváltozó új értéket kap minden ismétlésben.

A `let` használata általában megfelelő választás:

```javascript
for (let szam of [10, 20, 30]) {
    console.log(szam);
}
```

4\. A ciklus nem módosítja automatikusan a tömb elemeit.

```javascript
const szamok = [1, 2, 3];

for (let szam of szamok) {
    szam = szam * 2;
}

console.log(szamok);
```

A kimenet:

```
[1, 2, 3]
```

A `szam` változó az aktuális szám értékét kapja meg. Az átírása önmagában nem módosítja a tömb eredeti elemét.

Ha az eredeti tömb elemeit szeretnénk módosítani, használhatunk indexet:

```javascript
const szamok = [1, 2, 3];

for (let i = 0; i < szamok.length; i++) {
    szamok[i] *= 2;
}

console.log(szamok);
```

Kimenet:

```
[2, 4, 6]
```

# 13. Ellenőrző kérdések

1\. Mire használjuk a `for...of` ciklust?

A) Változók deklarálására.\
B) Iterálható adatszerkezetek elemeinek bejárására.\
C) Függvények létrehozására.\
D) Objektumok automatikus törlésére.

2\. Melyik a `for...of` ciklus helyes szintaxisa?

A)

```javascript
for (let elem inof adatok) {}
```

B)

```javascript
for (let elem of adatok) {
}
```

C)

```javascript
foreach (elem of adatok) {}
```

D)

```javascript
forof (elem in adatok) {}
```

3\. Mit tartalmaz az `elem` változó az alábbi példában?

```javascript
const szamok = [10, 20, 30];

for (let elem of szamok) {
    console.log(elem);
}
```

A) Mindig a tömb indexét.\
B) Mindig a tömb hosszát.\
C) Az aktuális tömbelemet.\
D) A teljes tömböt.

4\. Melyik adatszerkezettel használható a `for...of`?

A) Tömb (`Array`).\
B) Egyszerű objektum (`Object`) közvetlenül.\
C) Szám (`Number`).\
D) Logikai érték (`Boolean`).

5\. Mi történik a `break` utasítás végrehajtásakor?

A) A következő elemre lép.\
B) Újrakezdi a ciklust.\
C) Megszakítja a teljes ciklust.\
D) Kihagyja a feltételvizsgálatot.

6\. Mit csinál a `continue` utasítás?

A) Megállítja a programot.\
B) Kihagyja az aktuális ismétlés hátralévő részét.\
C) Törli az aktuális tömbelemet.\
D) Megszakítja a teljes ciklust.

7\. Mi lesz a kimenet?

```javascript
const szamok = [2, 4, 6];

for (let szam of szamok) {
    console.log(szam * 2);
}
```

A) `2, 4, 6`\
B) `4, 8, 12`\
C) `2, 8, 18`\
D) `6, 12, 18`

8\. Melyik állítás igaz a `for...of` ciklusra?

A) Mindig szüksége van indexváltozóra.\
B) Csak számokkal használható.\
C) Közvetlenül az aktuális elemet adja vissza.\
D) Csak objektumokkal használható.

9\. Mi történik az alábbi kód végrehajtásakor?

```javascript
const szamok = [1, 2, 3];

for (let szam of szamok) {
    szam = szam * 2;
}

console.log(szamok);
```

A) `[2, 4, 6]`\
B) `[1, 2, 3]`\
C) `[2, 2, 2]`\
D) Hiba keletkezik.

10\. Melyik ciklus használata célszerűbb, ha a tömb indexére is szükségünk van?

A) `while`\
B) `do...while`\
C) `for...of` minden esetben\
D) Hagyományos `for`

# 14. Gyakorló feladatok

1\. Tömb elemeinek kiírása

Hozz létre egy `varosok` nevű tömböt, amely öt város nevét tartalmazza.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- Minden város nevét írd ki a konzolra!
- Minden város külön sorban jelenjen meg!

2\. Számok összeadása

Hozz létre egy `szamok` nevű tömböt, amely legalább hat egész számot tartalmaz.

A feladatod:

- Hozz létre egy `osszeg` változót!
- A `for...of` ciklus segítségével add össze a tömb elemeit!
- A ciklus után írd ki az összeg eredményét!

3\. Páros számok kiválasztása

Hozz létre egy tömböt legalább tíz különböző egész számmal.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- Az `if` segítségével vizsgáld meg, hogy az aktuális szám páros-e!
- Csak a páros számokat írd ki!

4\. Páratlan számok összege

Hozz létre egy tömböt, amely pozitív és negatív egész számokat is tartalmaz.

A feladatod:

- A `for...of` segítségével járd be a tömböt!
- Csak a páratlan számokat add hozzá egy összegző változóhoz!
- A ciklus végén írd ki a páratlan számok összegét!

5\. Nevek keresése

Hozz létre egy `nevek` nevű tömböt legalább nyolc névvel.

A feladatod:

- Kérj be a felhasználótól egy keresendő nevet a `prompt()` segítségével!
- A `for...of` ciklussal keresd meg a nevet!
- Ha megtaláltad, írd ki, hogy a név szerepel a tömbben!
- Ha nem található meg, jelezd ezt is!
- A keresést `break` segítségével szakítsd meg, ha megtaláltad a nevet!

6\. Szöveg karaktereinek megszámolása

Hozz létre egy változót, amely egy tetszőleges szöveget tartalmaz.

A feladatod:

- Járd be a szöveget `for...of` ciklussal!
- Számold meg, hány karakterből áll a szöveg!
- A szóközöket ne számold bele!
- Az eredményt írd ki a konzolra!

7\. Legnagyobb szám megkeresése

Hozz létre egy legalább tíz elemből álló számtömböt.

A feladatod:

- A `for...of` segítségével járd be a tömböt!
- Keresd meg a legnagyobb számot!
- Ne használd a `Math.max()` metódust!
- Az eredményt írd ki a konzolra!

8\. Termékek árának összesítése

Hozz létre egy `arak` nevű tömböt, amely különböző termékárakat tartalmaz.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- Számold össze az árakat!
- Számold meg, hány termék ára haladja meg az 5000-et!
- Írd ki az összesített árat és a megfelelő termékek darabszámát!

9\. `Set` adatszerkezet bejárása

Hozz létre egy `Set` adatszerkezetet, amely több számot tartalmaz. Adj meg ismétlődő értékeket is a létrehozásakor.

A feladatod:

- Járd be a `Set` elemeit `for...of` ciklussal!
- Írd ki az egyedi értékeket!
- Számold meg, hány elem található a `Set` adatszerkezetben!

10\. Osztályzatok értékelése

Hozz létre egy `osztalyzatok` nevű tömböt, amely 1 és 5 közötti számokat tartalmaz.

A feladatod:

- Járd be a tömböt `for...of` ciklussal!
- Az `if...else if...else` segítségével értékeld az osztályzatokat!
- Az 1-es értékhez írd ki: „Elégtelen”.
- A 2-es értékhez írd ki: „Elégséges”.
- A 3-as értékhez írd ki: „Közepes”.
- A 4-es értékhez írd ki: „Jó”.
- Az 5-ös értékhez írd ki: „Jeles”.

## 15. Összefoglalás

A `for...of` ciklus az iterálható adatszerkezetek elemeinek egyszerű bejárására szolgál.

A legfontosabb tudnivalók:

- Nem szükséges hozzá külön indexváltozó.
- Minden ismétlésben az aktuális elemet kapjuk meg.
- Használható tömbökkel, szövegekkel, `Set` és `Map` adatszerkezetekkel.
- A `break` megszakítja a ciklust.
- A `continue` kihagyja az aktuális ismétlést.
- Egyszerű objektumok közvetlen bejárására nem alkalmas.
- Ha az indexre is szükségünk van, gyakran a hagyományos `for` ciklus a megfelelőbb.
