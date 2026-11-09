# A `typeof` operátor JavaScriptben

## 1. Mi az a `typeof` operátor?

A `typeof` egy JavaScript-operátor, amelynek segítségével megállapíthatjuk egy érték típusát.

A JavaScript dinamikusan típusos nyelv, ezért egy változó különböző időpontokban különböző típusú értékeket tárolhat. A `typeof` segítségével ellenőrizhetjük, hogy az adott pillanatban milyen típusú érték található benne.

Alapvető szintaxisa:

```javascript
typeof ertek;
```

Példa:

```javascript
let nev = 'Anna';
let eletkor = 25;
let aktiv = true;

console.log(typeof nev); // "string"
console.log(typeof eletkor); // "number"
console.log(typeof aktiv); // "boolean"
```

A `typeof` eredménye minden esetben egy szöveg (`string`), amely az érték típusának nevét tartalmazza.

## 2. A `typeof` által visszaadott típusok

A `typeof` különböző eredményt ad az egyes adattípusok esetén.

| Adattípus | Példa             | `typeof` eredménye |
| --------- | ----------------- | ------------------ |
| String    | `"Hello"`         | `"string"`         |
| Number    | `25`              | `"number"`         |
| Boolean   | `true`            | `"boolean"`        |
| Undefined | `undefined`       | `"undefined"`      |
| BigInt    | `100n`            | `"bigint"`         |
| Symbol    | `Symbol("id")`    | `"symbol"`         |
| Object    | `{ nev: "Anna" }` | `"object"`         |
| Function  | `function() {}`   | `"function"`       |

Példaprogram:

```javascript
let szoveg = 'JavaScript';
let szam = 100;
let logikai = false;
let nincsErtek;
let nagySzam = 12345678901234567890n;
let azonosito = Symbol('id');
let objektum = { nev: 'Anna' };
let tomb = [10, 20, 30];
let fuggveny = function () {};

console.log(typeof szoveg); // "string"
console.log(typeof szam); // "number"
console.log(typeof logikai); // "boolean"
console.log(typeof nincsErtek); // "undefined"
console.log(typeof nagySzam); // "bigint"
console.log(typeof azonosito); // "symbol"
console.log(typeof objektum); // "object"
console.log(typeof tomb); // "object"
console.log(typeof fuggveny); // "function"
```

## 3. A `typeof` használata változóknál

A `typeof` segítségével ellenőrizhetjük, hogy egy változó milyen típusú értéket tárol.

```javascript
let adat = 50;

console.log(typeof adat); // "number"

adat = 'Ötven';

console.log(typeof adat); // "string"

adat = true;

console.log(typeof adat); // "boolean"
```

A változó értékének megváltoztatásakor a `typeof` eredménye is megváltozhat.

Ez különösen hasznos lehet olyan programokban, ahol egy változó többféle típusú adatot is tárolhat.

## 4. A `typeof` és az `undefined`

Ha egy változót deklarálunk, de nem rendelünk hozzá értéket, akkor az értéke `undefined` lesz.

```javascript
let eredmeny;

console.log(eredmeny); // undefined
console.log(typeof eredmeny); // "undefined"
```

Az `undefined` azt jelzi, hogy a változó deklarálva van, de még nem kapott értéket.

Fontos különbség, hogy a deklarálatlan változó és a deklarált, de érték nélküli változó nem ugyanaz.

```javascript
let nev;

console.log(typeof nev); // "undefined"
console.log(typeof nemLetezo); // "undefined"
```

A `typeof` különlegessége, hogy egy nem deklarált azonosító esetén sem feltétlenül keletkezik hiba.

Más műveleteknél azonban a nem deklarált változó használata `ReferenceError` hibát okoz.

```javascript
console.log(nemLetezo); // ReferenceError
```

## 5. A `typeof null` sajátossága

A JavaScript egyik ismert sajátossága, hogy a `null` érték típusának ellenőrzésekor a `typeof` `"object"` eredményt ad.

```javascript
let adat = null;

console.log(typeof adat); // "object"
```

Ez nem azt jelenti, hogy a `null` valódi objektum.

A jelenség a JavaScript történetéből származó, megőrzött kompatibilitási sajátosság.

Ha kifejezetten azt szeretnénk ellenőrizni, hogy egy változó értéke `null`-e, akkor használjuk a szigorú összehasonlítást:

```javascript
let adat = null;

if (adat === null) {
    console.log('Az érték null.');
}
```

Fontos: a `typeof` önmagában nem alkalmas a `null` és az objektum megkülönböztetésére.

## 6. A `typeof` és a tömbök

A tömbök JavaScriptben objektumoknak számítanak.

Ezért a `typeof` egy tömb esetén is `"object"` eredményt ad.

```javascript
let szamok = [10, 20, 30];

console.log(typeof szamok); // "object"
```

Ha meg szeretnénk állapítani, hogy egy változó tömböt tartalmaz-e, akkor az `Array.isArray()` metódust kell használnunk.

```javascript
let szamok = [10, 20, 30];
let szemely = {
    nev: 'Anna',
    eletkor: 25,
};

console.log(Array.isArray(szamok)); // true
console.log(Array.isArray(szemely)); // false
```

A két ellenőrzés közötti különbség:

| Kifejezés               | Eredmény   | Jelentés               |
| ----------------------- | ---------- | ---------------------- |
| `typeof szamok`         | `"object"` | A tömb objektum típusú |
| `Array.isArray(szamok)` | `true`     | Az érték tömb          |

## 7. A `typeof` és a függvények

A JavaScriptben a függvények speciális objektumoknak tekinthetők.

A `typeof` azonban a függvények esetében külön `"function"` eredményt ad.

```javascript
function koszones() {
    console.log('Szia!');
}

console.log(typeof koszones); // "function"
```

Ez akkor is működik, ha a függvényt egy változóban tároljuk:

```javascript
const osszead = function (a, b) {
    return a + b;
};

console.log(typeof osszead); // "function"
```

A nyílfüggvények esetében is ugyanezt az eredményt kapjuk:

```javascript
const szoroz = (a, b) => a * b;

console.log(typeof szoroz); // "function"
```

## 8. A `typeof` használata feltételekben

A `typeof` gyakran szerepel `if` szerkezetekben, amikor egy változó típusától függően szeretnénk különböző műveleteket végrehajtani.

Példa:

```javascript
let adat = 25;

if (typeof adat === 'number') {
    console.log('A változó számot tartalmaz.');
} else if (typeof adat === 'string') {
    console.log('A változó szöveget tartalmaz.');
} else if (typeof adat === 'boolean') {
    console.log('A változó logikai értéket tartalmaz.');
} else {
    console.log('Más típusú adat.');
}
```

A program a változó aktuális típusának megfelelő üzenetet jeleníti meg.

### 8.1. Függvény paraméterének ellenőrzése

A függvények paramétereinek típusát is ellenőrizhetjük.

```javascript
function duplaz(ertek) {
    if (typeof ertek === 'number') {
        return ertek * 2;
    }

    return 'A paraméter nem szám!';
}

console.log(duplaz(10)); // 20
console.log(duplaz('alma')); // A paraméter nem szám!
```

Ez segít elkerülni, hogy egy függvény nem megfelelő típusú adatot dolgozzon fel.

## 9. A `typeof` és a szigorú összehasonlítás

A `typeof` eredménye egy szöveg, ezért az ellenőrzés során általában a `===` operátort használjuk.

```javascript
let eletkor = 25;

if (typeof eletkor === 'number') {
    console.log('Az életkor megfelelő típusú.');
}
```

A következő megoldás is működhet:

```javascript
if (typeof eletkor == 'number') {
    console.log('Az életkor szám.');
}
```

Azonban a szigorú összehasonlítás használata ajánlott, mert nem végez automatikus típuskonverziót.

## 10. Gyakori hibák a `typeof` használatakor

### 10.1. A `typeof` eredményének hibás összehasonlítása

Hibás:

```javascript
let szam = 25;

if (typeof szam === number) {
    console.log('Szám.');
}
```

A `number` itt nincs szövegként megadva, ezért a JavaScript változóként próbálja értelmezni.

Helyesen:

```javascript
let szam = 25;

if (typeof szam === 'number') {
    console.log('Szám.');
}
```

### 10.2. A tömbök hibás ellenőrzése

Nem megfelelő:

```javascript
let adatok = [10, 20, 30];

if (typeof adatok === 'array') {
    console.log('Tömb.');
}
```

A `typeof` nem ad `"array"` eredményt.

Helyesen:

```javascript
let adatok = [10, 20, 30];

if (Array.isArray(adatok)) {
    console.log('A változó tömböt tartalmaz.');
}
```

### 10.3. A `null` hibás ellenőrzése

Nem megfelelő:

```javascript
let adat = null;

if (typeof adat === 'null') {
    console.log('Az érték null.');
}
```

A `typeof null` eredménye `"object"`.

Helyesen:

```javascript
let adat = null;

if (adat === null) {
    console.log('Az érték null.');
}
```

### 10.4. A `NaN` hibás ellenőrzése

A `NaN` típusa `number`, ezért a `typeof` nem alkalmas annak megállapítására, hogy egy számérték érvényes-e.

```javascript
let eredmeny = Number('alma');

console.log(typeof eredmeny); // "number"
```

A `NaN` ellenőrzésére használjuk a `Number.isNaN()` metódust:

```javascript
if (Number.isNaN(eredmeny)) {
    console.log('Az eredmény nem érvényes szám.');
}
```

## 11. Összefoglalás

A `typeof` operátor a JavaScript egyik alapvető eszköze, amely az értékek típusának ellenőrzésére szolgál.

A legfontosabb tudnivalók:

- A `typeof` egy érték típusát adja vissza szövegként.
- Használható változók, literálok és kifejezések esetén.
- A tömbök esetében `"object"` eredményt ad.
- A `null` esetében szintén `"object"` az eredmény.
- A függvények esetében `"function"` eredményt ad.
- Az `undefined` érték esetében `"undefined"` az eredmény.
- Tömbök ellenőrzésére az `Array.isArray()` használható.
- `null` ellenőrzésére a `=== null` kifejezés alkalmas.
- `NaN` ellenőrzésére a `Number.isNaN()` használható.
- Feltételekben a `typeof` eredményét általában `===` operátorral hasonlítjuk össze.

# 12. Ellenőrző kérdések

1. Mire használjuk a `typeof` operátort JavaScriptben?
2. Milyen típusú értéket ad vissza a `typeof` operátor?
3. Mi lesz a `typeof "JavaScript"` kifejezés eredménye?
4. Miért ad a `typeof null` `"object"` eredményt?
5. Milyen eredményt ad a `typeof` egy tömb esetén?
6. Melyik metódussal ellenőrizhetjük, hogy egy változó tömböt tartalmaz-e?
7. Milyen eredményt ad a `typeof` egy függvény esetén?
8. Mi a különbség a deklarált, de érték nélküli változó és a nem deklarált változó között?
9. Miért nem alkalmas a `typeof` a `NaN` felismerésére?
10. Miért ajánlott a `typeof` eredményét `===` operátorral összehasonlítani?

# 13. Gyakorlati feladatok

A feladatokat JavaScriptben oldd meg! A megoldásokhoz használj változókat, `typeof` operátort, feltételeket és szükség esetén függvényeket.

1\. Egyszerű típusellenőrzés

Hozz létre öt változót az alábbi értékekkel:

- `"JavaScript"`
- `150`
- `false`
- `undefined`
- `100n`

A `typeof` segítségével jelenítsd meg mindegyik változó típusát a konzolon!

2\. Változó típusának változása

Hozz létre egy `adat` nevű változót, amely kezdetben egy számot tárol. Ezután módosítsd az értékét szövegre, majd logikai értékre! Minden módosítás után jelenítsd meg a változó típusát.

3\. Több változó ellenőrzése

Hozz létre egy számot, egy szöveget, egy objektumot és egy tömböt tároló változót! Ellenőrizd mindegyik típusát a `typeof` segítségével. Figyeld meg a tömb és az objektum eredményét!

4\. Tömb felismerése

Hozz létre három változót:

- Egy tömböt.
- Egy objektumot.
- Egy szöveget.

Az `Array.isArray()` segítségével állapítsd meg, hogy melyik változó tartalmaz tömböt!

5\. `null` érték ellenőrzése

Hozz létre egy `adat` nevű változót `null` értékkel! Vizsgáld meg a típusát a `typeof` segítségével, majd ellenőrizd a `=== null` kifejezéssel is!

6\. Függvény típusának vizsgálata

Hozz létre egy hagyományos függvényt és egy nyílfüggvényt! A `typeof` segítségével ellenőrizd mindkettő típusát.

7\. Típusellenőrző feltétel

Hozz létre egy `ertek` nevű változót! Készíts olyan feltételrendszert, amely a `typeof` segítségével megvizsgálja, hogy az érték szám, szöveg vagy logikai érték. Mindegyik esetben jelenítsen meg megfelelő üzenetet!

8\. Típusellenőrző függvény készítése

Készíts egy `tipusEllenorzes()` nevű függvényt, amely paraméterként egy értéket kap! A függvény a `typeof` segítségével állapítsa meg az érték típusát, majd jelenítse meg a konzolon az eredményt. Próbáld ki legalább öt különböző adattípussal!

9\. Szám ellenőrzése

Hozz létre egy `"125"` értékű szöveges változót! Alakítsd át számmá a `Number()` segítségével, majd ellenőrizd a `typeof` operátorral, hogy valóban szám lett-e az eredmény!

10\. Összetett típusellenőrző program

Készíts egy programot, amelyben legalább hat különböző típusú értéket tároló változó szerepel! A program mindegyik változónál:

- Jelenítse meg az értéket.
- Jelenítse meg a `typeof` által visszaadott típust.
- Ellenőrizze külön, hogy az érték tömb-e.
- Ha az érték `null`, azt külön ismerje fel.
- Az eredményeket jelenítse meg a konzolon.
