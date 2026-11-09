# Értékadás és inicializálás JavaScriptben

## 1. Mit jelent az inicializálás?

Az inicializálás egy változó első értékének megadása. Amikor létrehozunk egy változót, lehetőségünk van arra, hogy már a deklarálásakor értéket rendeljünk hozzá.

JavaScriptben a változók deklarálására három kulcsszót használhatunk:

- `var`
- `let`
- `const`

Például:

```javascript
let nev = 'Péter';
const eletkor = 25;
var varos = 'Budapest';
```

A fenti példában mindhárom változó deklarálása és inicializálása egyszerre történik.

| Kifejezés           | Jelentés                              |
| ------------------- | ------------------------------------- |
| `let nev`           | Változó deklarálása                   |
| `nev = "Péter"`     | Értékadás                             |
| `let nev = "Péter"` | Deklarálás és inicializálás egyszerre |

Az inicializálás tehát az első érték hozzárendelését jelenti.

## 2. Mit jelent az értékadás?

Az értékadás során egy változóhoz értéket rendelünk, vagy megváltoztatjuk a korábban eltárolt értékét.

Az értékadáshoz az egyenlőségjelet (`=`) használjuk.

```javascript
let szam;

szam = 10;

console.log(szam);
```

A program működése:

1. Létrejön a `szam` nevű változó.
2. A változó még nem kapott konkrét értéket.
3. A `szam = 10` utasítás értéket rendel hozzá.
4. A `console.log()` megjeleníti a változó értékét.

Az eredmény:

```
10
```

Fontos, hogy az egyenlőségjel JavaScriptben nem matematikai egyenlőséget jelent, hanem értékadást.

## 3. Deklarálás és inicializálás külön-külön

A `let` és a `var` használatakor a deklarálás és az inicializálás külön utasításban is történhet.

```javascript
let pontszam;

pontszam = 50;
```

A két utasítás jelentése:

- `let pontszam;` – létrehozza a változót.
- `pontszam = 50;` – értéket rendel hozzá.

Természetesen a két művelet egyetlen sorban is elvégezhető:

```javascript
let pontszam = 50;
```

Ez a megoldás gyakran áttekinthetőbb, mert a változó már a létrehozásakor megkapja a kezdőértékét.

## 4. A `let` változók inicializálása és módosítása

A `let` kulcsszóval deklarált változók értéke később megváltoztatható.

```javascript
let ar = 1000;

console.log(ar);

ar = 1500;

console.log(ar);
```

Eredmény:

```
1000
1500
```

A változó először `1000` értéket kapott, majd az értékét `1500`-ra módosítottuk.

A `let` változókat deklarálhatjuk értékadás nélkül is:

```javascript
let eredmeny;

eredmeny = 85;
```

Ha egy deklarált `let` változónak még nem adtunk értéket, akkor az értéke `undefined`.

```javascript
let eredmeny;

console.log(eredmeny);
```

Eredmény:

```
undefined
```

Az `undefined` azt jelenti, hogy a változó létezik, de még nincs hozzárendelve konkrét érték.

## 5. A `const` változók inicializálása

A `const` kulcsszóval deklarált változóknak a deklarálás pillanatában értéket kell adnunk.

Helyes használat:

```javascript
const PI = 3.14159;
const nev = 'Anna';
```

Hibás használat:

```javascript
const PI;

PI = 3.14159;
```

A fenti kód hibát eredményez, mert a `const` változót nem lehet értékadás nélkül deklarálni.

A `const` változóhoz később nem rendelhetünk új értéket:

```javascript
const orszag = 'Magyarország';

orszag = 'Ausztria'; // Hiba
```

A `const` tehát olyan változó deklarálására szolgál, amelynek az értékét nem szeretnénk új értékkel felülírni.

## 6. A `var` változók inicializálása

A `var` kulcsszóval deklarált változók szintén inicializálhatók a deklaráláskor, de értékadás nélkül is létrehozhatók.

```javascript
var termek = 'Laptop';

console.log(termek);
```

Külön deklarálás és értékadás:

```javascript
var termek;

termek = 'Laptop';
```

Ha egy `var` változót deklarálunk, de nem adunk neki értéket, akkor az értéke szintén `undefined` lesz.

```javascript
var termek;

console.log(termek);
```

Eredmény:

```
undefined
```

A `var` változók értéke később módosítható:

```javascript
var darab = 5;

darab = 10;

console.log(darab);
```

Eredmény:

```
10
```

A `var` használata újabb JavaScript-kódban általában nem ajánlott. Helyette legtöbbször a `let` és a `const` használata javasolt.

## 7. Az inicializálás és az `undefined` kapcsolata

Ha egy `let` vagy `var` változót deklarálunk, de nem inicializálunk, akkor a JavaScript automatikusan az `undefined` értéket rendeli hozzá.

```javascript
let nev;
var kor;

console.log(nev);
console.log(kor);
```

Eredmény:

```
undefined
undefined
```

Az `undefined` egy JavaScript-adatérték, amely azt jelzi, hogy egy változóhoz még nem tartozik meghatározott érték.

Fontos különbség, hogy az `undefined` nem ugyanaz, mint a `null`.

```javascript
let elso;
let masodik = null;

console.log(elso);
console.log(masodik);
```

Eredmény:

```
undefined
null
```

| Érték       | Jelentés                                                    |
| ----------- | ----------------------------------------------------------- |
| `undefined` | A változóhoz még nincs meghatározott érték rendelve.        |
| `null`      | A programozó szándékosan üres értéket rendelt a változóhoz. |

A `null` tehát tudatosan megadott érték, míg az `undefined` gyakran az érték hiányát jelzi.

## 8. Többszöri értékadás

Egy `let` vagy `var` változóhoz a program futása során többször is rendelhetünk új értéket.

```javascript
let allapot = 'Előkészítés';

console.log(allapot);

allapot = 'Folyamatban';

console.log(allapot);

allapot = 'Befejezve';

console.log(allapot);
```

Eredmény:

```
Előkészítés
Folyamatban
Befejezve
```

Minden új értékadás felülírja a változó korábbi értékét.

Ez különösen hasznos például:

- számlálók esetében;
- felhasználói adatok módosításakor;
- programállapotok követésekor;
- számítások eredményének tárolásakor.

## 9. Értékadás számítás eredményével

Nemcsak közvetlenül megadott értéket rendelhetünk egy változóhoz, hanem egy kifejezés eredményét is.

```javascript
let a = 10;
let b = 20;

let osszeg = a + b;

console.log(osszeg);
```

Eredmény:

```
30
```

A JavaScript először kiszámítja az `a + b` kifejezést, majd az eredményt eltárolja az `osszeg` változóban.

Más műveleteket is használhatunk:

```javascript
let szam1 = 20;
let szam2 = 5;

let kulonbseg = szam1 - szam2;
let szorzat = szam1 * szam2;
let hanyados = szam1 / szam2;

console.log(kulonbseg);
console.log(szorzat);
console.log(hanyados);
```

Eredmény:

```
15
100
4
```

## 10. Összetett értékadó operátorok

A JavaScript lehetőséget biztosít rövidített értékadási műveletek használatára is.

Például:

```javascript
let szam = 10;

szam = szam + 5;
```

A fenti művelet rövidebben is megadható:

```javascript
let szam = 10;

szam += 5;
```

Mindkét esetben a változó értéke `15` lesz.

A leggyakrabban használt összetett értékadó operátorok:

| Operátor | Jelentés                      | Példa        |
| -------- | ----------------------------- | ------------ |
| `+=`     | Hozzáadás és értékadás        | `szam += 5`  |
| `-=`     | Kivonás és értékadás          | `szam -= 5`  |
| `*=`     | Szorzás és értékadás          | `szam *= 5`  |
| `/=`     | Osztás és értékadás           | `szam /= 5`  |
| `%=`     | Maradékos osztás és értékadás | `szam %= 5`  |
| `**=`    | Hatványozás és értékadás      | `szam **= 2` |

Példa:

```javascript
let eredmeny = 10;

eredmeny += 5; // 15
eredmeny *= 2; // 30
eredmeny -= 10; // 20
eredmeny /= 4; // 5

console.log(eredmeny);
```

Eredmény:

```
5
```

## 11. Értékadás és adattípusok

A JavaScript dinamikusan típusos programozási nyelv. Ez azt jelenti, hogy egy változóhoz különböző adattípusú értékeket is rendelhetünk a program futása során.

```javascript
let adat = 100;

console.log(typeof adat);

adat = 'Szöveges adat';

console.log(typeof adat);
```

Eredmény:

```
number
string
```

A `typeof` operátor segítségével megvizsgálhatjuk egy érték típusát.

Például:

```javascript
let szam = 25;
let szoveg = 'JavaScript';
let logikai = true;

console.log(typeof szam);
console.log(typeof szoveg);
console.log(typeof logikai);
```

Eredmény:

```
number
string
boolean
```

Fontos, hogy a `let` változó értékének módosításakor az adattípus is megváltozhat. A `const` változó esetében új érték nem rendelhető hozzá.

## 12. Gyakori hibák értékadáskor és inicializáláskor

### 12.1. `const` változó inicializálásának elmulasztása

```javascript
const nev;

nev = 'Anna';
```

Hiba, mert a `const` változónak már a deklaráláskor értéket kell adni.

### 12.2. `const` változó újraértékadása

```javascript
const kor = 20;

kor = 25;
```

Hiba, mert a `const` változóhoz nem rendelhető új érték.

### 12.3. Nem deklarált változó használata

```javascript
nev = 'Péter';

console.log(nev);
```

Szigorú módban vagy ES-modulban ez hibát okoz, mert a `nev` változót előzetesen nem deklaráltuk.

Helyesen:

```javascript
let nev = 'Péter';

console.log(nev);
```

### 12.4. Az értékadás és az összehasonlítás összekeverése

Az egyenlőségjel (`=`) értékadásra szolgál, míg az összehasonlító operátorok két érték összehasonlítására használhatók.

```javascript
let szam = 10; // Értékadás

console.log(szam === 10); // Összehasonlítás
```

Az eredmény:

```
true
```

### 12.5. Változó újradeklarálása `let` használatával

```javascript
let nev = 'Anna';

let nev = 'Péter';
```

Ez ugyanabban a hatókörben hibát okoz. A meglévő változó értékét egyszerű értékadással kell módosítani:

```javascript
let nev = 'Anna';

nev = 'Péter';
```

# 13. Összefoglalás

| Jellemző                                 | `var`               | `let`                         | `const`                               |
| ---------------------------------------- | ------------------- | ----------------------------- | ------------------------------------- |
| Deklarálható értékadás nélkül            | Igen                | Igen                          | Nem                                   |
| Inicializálás kötelező                   | Nem                 | Nem                           | Igen                                  |
| Érték később módosítható                 | Igen                | Igen                          | Nem                                   |
| Újradeklarálható ugyanabban a hatókörben | Igen                | Nem                           | Nem                                   |
| Használata új kódban                     | Általában kerülendő | Ajánlott, ha módosul az érték | Ajánlott, ha nem kell új értéket adni |

A legfontosabb szabályok:

- Az inicializálás a változó első értékének megadása.
- Az értékadás egy változó értékének megadása vagy módosítása.
- A `let` változó értéke később módosítható.
- A `const` változót kötelező inicializálni, és később nem adható neki új érték.
- A `var` és a `let` változó inicializálás nélkül is deklarálható.
- A nem inicializált `var` és `let` változók értéke `undefined`.

# 14. Ellenőrző kérdések

1. Mit jelent a változó inicializálása?
2. Mi a különbség a deklarálás és az értékadás között?
3. Melyik operátort használjuk értékadásra JavaScriptben?
4. Milyen értéket kap egy inicializálatlan `let` változó?
5. Kötelező-e inicializálni a `const` változókat?
6. Megváltoztatható-e egy `let` változó értéke a deklarálás után?
7. Mi történik, ha egy `const` változóhoz új értéket rendelünk?
8. Mi a különbség az `undefined` és a `null` között?
9. Mit jelent a `+=` operátor?
10. Milyen célt szolgál a `typeof` operátor?

# 15. Gyakorlati feladatok

A feladatokat JavaScriptben oldd meg! A megoldások során használj változódeklarálást, inicializálást és értékadást. A feladatokhoz nem tartozik megoldás.

1\. feladat – Változók inicializálása

Hozz létre három változót:

- `nev` – egy tetszőleges névvel;
- `kor` – egy egész számmal;
- `varos` – egy város nevével.

Mindhárom változót már a deklaráláskor inicializáld, majd jelenítsd meg az értékeiket a konzolon.

2\. feladat – Különálló értékadás

Hozz létre egy `pontszam` nevű `let` változót értékadás nélkül!

Ezután külön utasításban rendelj hozzá egy tetszőleges számot, majd jelenítsd meg az értékét.

3\. feladat – Változó értékének módosítása

Hozz létre egy `ar` nevű változót `let` használatával, és adj neki `1500` értéket!

Ezután módosítsd az értékét `2000`-re, majd jelenítsd meg mindkét értéket a konzolon.

4\. feladat – `const` változó használata

Hozz létre három `const` változót:

- `PI` – értéke `3.14159`;
- `orszag` – értéke `Magyarország`;
- `aktiv` – értéke `true`.

Jelenítsd meg mindhárom változó értékét!

5\. feladat – Számítás eredményének eltárolása

Hozz létre két változót `a` és `b` néven, majd rendelj hozzájuk két tetszőleges számot!

Egy harmadik változóban tárold el a két szám összegét, majd jelenítsd meg az eredményt.

6\. feladat – Többszöri értékadás

Hozz létre egy `allapot` nevű változót!

A program során három különböző értéket adj neki egymás után:

- `Előkészítés`
- `Folyamatban`
- `Befejezve`

Minden értékadás után jelenítsd meg a változó aktuális értékét.

7\. feladat – Összetett értékadó operátorok

Hozz létre egy `szam` nevű változót `10` kezdőértékkel!

Végezd el az alábbi műveleteket:

- Adj hozzá `5`-öt a `+=` operátorral!
- Szorozd meg `2`-vel a `*=` operátorral!
- Vonj ki belőle `4`-et a `-=` operátorral!
- Oszd el `2`-vel a `/=` operátorral!

Minden művelet után jelenítsd meg az aktuális értéket.

8\. feladat – Adattípus megváltoztatása

Hozz létre egy `adat` nevű `let` változót `100` értékkel!

Ezután:

1. Jelenítsd meg az értékét és az adattípusát!
2. Módosítsd az értékét a következő szövegre: `JavaScript`.
3. Ismét jelenítsd meg az értékét és az adattípusát!

A típus meghatározásához használd a `typeof` operátort.

9\. feladat – `undefined` és `null`

Hozz létre két változót:

- `elso` – deklaráld, de ne inicializáld;
- `masodik` – inicializáld `null` értékkel.

Jelenítsd meg mindkét változó értékét, majd vizsgáld meg az adattípusukat a `typeof` operátorral!

10\. feladat – Egyszerű számológép

Hozz létre két `let` változót két tetszőleges számmal!

Ezután külön változókban tárold el:

- a két szám összegét;
- a két szám különbségét;
- a két szám szorzatát;
- a két szám hányadosát.

A program végén jelenítsd meg az összes számítás eredményét a konzolon.
