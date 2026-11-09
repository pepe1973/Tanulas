# Dinamikus típusosság JavaScriptben

## 1. Mit jelent a dinamikus típusosság?

A dinamikus típusosság azt jelenti, hogy egy változó típusa a program futása során változhat. JavaScriptben a változó deklarálásakor nem kell előre meghatározni, hogy milyen típusú adatot fog tárolni.

Például ugyanaz a változó először számot, később szöveget, majd logikai értéket is tárolhat.

```javascript
let adat = 25;

console.log(adat); // 25

adat = 'JavaScript';

console.log(adat); // JavaScript

adat = true;

console.log(adat); // true
```

A változó neve (`adat`) nem változik, de a benne tárolt érték típusa igen.

Fontos: JavaScriptben nem a változónak van rögzített típusa, hanem az aktuálisan tárolt értéknek.

## 2. Dinamikus és statikus típusosság összehasonlítása

A programozási nyelvek típusosság szempontjából többek között dinamikus és statikus típusosságú nyelvekre oszthatók.

| Szempont            | Dinamikus típusosság    | Statikus típusosság           |
| ------------------- | ----------------------- | ----------------------------- |
| Típus meghatározása | Futás közben            | Általában fordításkor         |
| Változó típusa      | Változhat               | Általában előre meghatározott |
| Típusellenőrzés     | Jellemzően futás közben | Jellemzően fordításkor        |
| Példák              | JavaScript, Python      | C#, Java, C++                 |

JavaScriptben:

```javascript
let ertek = 100;

ertek = 'Száz';

ertek = false;
```

A fenti kód szabályos, mert a JavaScript lehetővé teszi, hogy ugyanaz a változó különböző típusú értékeket tároljon.

Egy statikusan típusos nyelvben, például C#-ban, egy `int` típusú változó nem kaphat közvetlenül szöveges értéket:

```csharp
int ertek = 100;

ertek = "Száz"; // Típushiba
```

## 3. A változó típusa és az érték típusa

Fontos különbséget tenni a változó és az általa tárolt érték között.

JavaScriptben a változó egy értékre hivatkozik, az értéknek pedig van típusa.

```javascript
let eredmeny = 42;

console.log(typeof eredmeny); // "number"

eredmeny = 'Sikeres';

console.log(typeof eredmeny); // "string"
```

A `typeof` operátor segítségével megvizsgálhatjuk, hogy egy érték milyen típusú.

Néhány példa:

```javascript
let szam = 10;
let szoveg = 'Hello';
let logikai = true;
let ures = null;
let nincsErtek = undefined;

console.log(typeof szam); // "number"
console.log(typeof szoveg); // "string"
console.log(typeof logikai); // "boolean"
console.log(typeof nincsErtek); // "undefined"
console.log(typeof ures); // "object"
```

A `null` esetében a `typeof` eredménye `"object"`. Ez a JavaScript egyik régi, történelmi sajátossága, nem pedig azt jelenti, hogy a `null` valóban objektum.

## 4. Egy változó többféle értéket is tárolhat

Dinamikus típusosság esetén egy változó különböző típusú értékeket kaphat a program különböző pontjain.

```javascript
let felhasznaloAdat = 25;

console.log(typeof felhasznaloAdat); // "number"

felhasznaloAdat = 'Péter';

console.log(typeof felhasznaloAdat); // "string"

felhasznaloAdat = {
    nev: 'Péter',
    eletkor: 25,
};

console.log(typeof felhasznaloAdat); // "object"
```

Ez különösen hasznos lehet olyan esetekben, amikor egy változó értéke a program működése során eltérő formátumú lehet.

Ugyanakkor figyelni kell arra, hogy a változó mindig az adott művelethez megfelelő típusú értéket tartalmazzon.

## 5. Dinamikus típusosság és a műveletek

A JavaScript a műveletek végrehajtásakor figyelembe veszi az operandusok típusát.

Ezért ugyanaz a művelet különböző eredményt adhat attól függően, hogy milyen típusú értékekkel dolgozunk.

### 5.1. Összeadás számokkal

Ha mindkét operandus szám, akkor az összeadás matematikai összeadást jelent.

```javascript
let a = 10;
let b = 20;

let eredmeny = a + b;

console.log(eredmeny); // 30
```

### 5.2. Összeadás szövegekkel

Ha az egyik operandus szöveg, akkor a `+` operátor szöveg-összefűzést is végezhet.

```javascript
let a = 10;
let b = '20';

let eredmeny = a + b;

console.log(eredmeny); // "1020"
```

A JavaScript a számot szöveggé alakítja, majd összefűzi a két értéket.

### 5.3. Kivonás szöveges számmal

A kivonás esetében a JavaScript megpróbálja számmá alakítani a szöveges értéket.

```javascript
let a = 30;
let b = '10';

let eredmeny = a - b;

console.log(eredmeny); // 20
```

Ez azért működik, mert a `"10"` szöveg számmá alakítható.

### 5.4. Nem átalakítható értékek

Ha a JavaScript nem tud egy értéket megfelelő típussá alakítani, akkor az eredmény lehet `NaN`.

A `NaN` jelentése: Not a Number, vagyis nem szám.

```javascript
let szam = 20;
let szoveg = 'alma';

let eredmeny = szam - szoveg;

console.log(eredmeny); // NaN
```

A `NaN` típusa a `typeof` operátor szerint `number`.

```javascript
console.log(typeof NaN); // "number"
```

## 6. Implicit típuskonverzió

A dinamikus típusossághoz szorosan kapcsolódik az implicit típuskonverzió.

Ez azt jelenti, hogy a JavaScript bizonyos műveletek során automatikusan átalakítja az értékek típusát.

Például:

```javascript
let szam = 10;
let szoveg = '5';

console.log(szam + szoveg); // "105"
console.log(szam - szoveg); // 5
console.log(szam * szoveg); // 50
console.log(szam / szoveg); // 2
```

A különböző műveletek eltérő típuskonverziót eredményezhetnek.

| Kifejezés    | Eredmény | Magyarázat         |
| ------------ | -------- | ------------------ |
| `10 + "5"`   | `"105"`  | Szöveg-összefűzés  |
| `10 - "5"`   | `5`      | Számmá alakítás    |
| `10 * "5"`   | `50`     | Számmá alakítás    |
| `10 / "5"`   | `2`      | Számmá alakítás    |
| `10 + true`  | `11`     | A `true` értéke 1  |
| `10 + false` | `10`     | A `false` értéke 0 |

Az implicit típuskonverzió kényelmes, de bizonyos esetekben nehezen felismerhető hibákat okozhat.

## 7. Explicit típuskonverzió

A típuskonverziót nemcsak a JavaScript végezheti el automatikusan, hanem a programozó is kezdeményezheti.

Ezt explicit típuskonverziónak nevezzük.

### 7.1. Szöveg átalakítása számmá

A `Number()` segítségével egy értéket számmá alakíthatunk.

```javascript
let szoveg = '125';

let szam = Number(szoveg);

console.log(szam); // 125
console.log(typeof szam); // "number"
```

Ha az átalakítás nem lehetséges, az eredmény `NaN` lesz.

```javascript
let szoveg = 'alma';

let szam = Number(szoveg);

console.log(szam); // NaN
```

### 7.2. Szöveg átalakítása egész számmá

A `parseInt()` egy szövegből egész számot próbál kiolvasni.

```javascript
let szoveg = '125px';

let szam = parseInt(szoveg);

console.log(szam); // 125
```

### 7.3. Szöveg átalakítása tizedes számmá

A `parseFloat()` tizedes számot is képes kiolvasni.

```javascript
let szoveg = '12.75kg';

let szam = parseFloat(szoveg);

console.log(szam); // 12.75
```

### 7.4. Érték átalakítása szöveggé

A `String()` segítségével egy értéket szöveggé alakíthatunk.

```javascript
let szam = 250;

let szoveg = String(szam);

console.log(szoveg); // "250"
console.log(typeof szoveg); // "string"
```

### 7.5. Érték átalakítása logikai értékké

A `Boolean()` egy értéket `true` vagy `false` értékké alakít.

```javascript
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false
console.log(Boolean('Hello')); // true
console.log(Boolean('')); // false
```

## 8. Truthy és falsy értékek

JavaScriptben minden érték felhasználható logikai feltételként.

Bizonyos értékek `true`-ként, mások `false`-ként viselkednek.

Ezeket az értékeket két csoportba soroljuk:

- Truthy: logikai környezetben igaznak tekintett értékek.
- Falsy: logikai környezetben hamisnak tekintett értékek.

A legfontosabb falsy értékek:

| Érték       | Jelentés            |
| ----------- | ------------------- |
| `false`     | Logikai hamis       |
| `0`         | Nulla               |
| `-0`        | Negatív nulla       |
| `0n`        | BigInt nulla        |
| `""`        | Üres szöveg         |
| `null`      | Nincs érték         |
| `undefined` | Nem definiált érték |
| `NaN`       | Nem szám            |

Minden más érték truthy, például:

```javascript
Boolean('JavaScript'); // true
Boolean(100); // true
Boolean(-5); // true
Boolean([]); // true
Boolean({}); // true
```

Fontos, hogy az üres tömb (`[]`) és az üres objektum (`{}`) is truthy érték.

### Példa feltételben

```javascript
let nev = '';

if (nev) {
    console.log('A név meg van adva.');
} else {
    console.log('A név üres.');
}
```

Mivel az üres szöveg falsy érték, a program az `else` ágat hajtja végre.

## 9. A dinamikus típusosság előnyei

A dinamikus típusosság több előnnyel jár:

1. Rugalmas változóhasználat: ugyanaz a változó különböző típusú értékeket tárolhat.
2. Kevesebb típusdeklaráció: nem szükséges minden változó típusát előre megadni.
3. Gyorsabb kezdeti fejlesztés: egyszerűbb lehet kisebb programok és prototípusok elkészítése.
4. Rugalmas adatkezelés: különböző forrásokból érkező adatok feldolgozása könnyebb lehet.

## 10. A dinamikus típusosság hátrányai

A dinamikus típusosság bizonyos problémákat is okozhat.

1. Futásidejű hibák: a típusproblémák nem feltétlenül derülnek ki a program írásakor.
2. Váratlan típuskonverzió: a JavaScript automatikus átalakításai meglepő eredményeket adhatnak.
3. Nehezebb hibakeresés: nagyobb programokban nehezebb lehet követni, hogy egy változó éppen milyen értéket tartalmaz.
4. Kevésbé egyértelmű kód: ha egy változó sokféle típust tárol, a kód nehezebben értelmezhető.

Például:

```javascript
function duplaz(ertek) {
    return ertek * 2;
}

console.log(duplaz(10)); // 20
console.log(duplaz('10')); // 20
console.log(duplaz('alma')); // NaN
```

A függvény különböző típusú értékeket is elfogad, de nem minden bemenettel működik értelmesen.

## 11. Hogyan kezeljük biztonságosan a dinamikus típusosságot?

A dinamikus típusosság előnyeit úgy használhatjuk ki, hogy közben csökkentjük a típushibák lehetőségét.

### 11.1. Használjunk egyértelmű változóneveket

A változó neve utaljon arra, milyen adatot tárol.

```javascript
let felhasznaloNev = 'Anna';
let felhasznaloKor = 25;
let aktivFelhasznalo = true;
```

### 11.2. Ellenőrizzük az értékek típusát

A `typeof` operátorral ellenőrizhetjük az egyszerű értékek típusát.

```javascript
let eletkor = 25;

if (typeof eletkor === 'number') {
    console.log('Az életkor szám.');
}
```

Tömb ellenőrzésére használjuk az `Array.isArray()` metódust, mert a `typeof` a tömbökre is `"object"` eredményt ad.

```javascript
let adatok = [10, 20, 30];

console.log(Array.isArray(adatok)); // true
```

### 11.3. Használjunk szigorú összehasonlítást

A `===` operátor az értéket és a típust is ellenőrzi.

```javascript
console.log(10 == '10'); // true
console.log(10 === '10'); // false
```

A `==` összehasonlítás előtt típuskonverziót végezhet, míg a `===` nem végez ilyen automatikus átalakítást.

Ezért a legtöbb esetben a `===` használata ajánlott.

### 11.4. Ellenőrizzük a felhasználótól érkező adatokat

A `prompt()` például szöveges értéket ad vissza, még akkor is, ha a felhasználó számot ír be.

```javascript
let eletkor = prompt('Hány éves vagy?');

eletkor = Number(eletkor);

if (Number.isNaN(eletkor)) {
    console.log('Érvénytelen életkor!');
} else {
    console.log('A megadott életkor: ' + eletkor);
}
```

A `Number.isNaN()` segítségével ellenőrizhetjük, hogy az érték `NaN`-e.

## 12. Összefoglalás

A JavaScript dinamikusan típusos programozási nyelv. Ez azt jelenti, hogy egy változó a program futása során különböző típusú értékeket is tárolhat.

A dinamikus típusosság fontos jellemzői:

- A változó típusát nem kell előre deklarálni.
- A változó által tárolt érték típusa megváltozhat.
- A JavaScript bizonyos műveleteknél automatikus típuskonverziót végez.
- A programozó explicit módon is átalakíthatja az értékek típusát.
- A `typeof` segítségével megvizsgálható egy érték típusa.
- A `Boolean()` segítségével megállapítható, hogy egy érték truthy vagy falsy.
- A `===` használata segít elkerülni a nem kívánt típuskonverzióból eredő összehasonlítási hibákat.

# 13. Ellenőrző kérdések

1. Mit jelent a dinamikus típusosság JavaScriptben?
2. Mi a különbség a dinamikus és a statikus típusosság között?
3. Megváltozhat-e egy JavaScript-változó által tárolt érték típusa a program futása során?
4. Mire használjuk a `typeof` operátort?
5. Miért ad a `typeof null` kifejezés `"object"` eredményt?
6. Mit jelent az implicit típuskonverzió?
7. Mi a különbség a `Number()` és a `parseInt()` között?
8. Mit jelent a truthy és a falsy kifejezés?
9. Mi a különbség a `==` és a `===` operátor között?
10. Milyen előnyei és hátrányai vannak a dinamikus típusosságnak?

# 14. Gyakorlati feladatok

A feladatokat JavaScriptben oldd meg! A megoldásokhoz használj változókat, feltételeket, típusellenőrzést és típuskonverziót. A feladatokhoz nem tartozik előre megadott megoldás.

1\. Változó típusának változtatása

Hozz létre egy `adat` nevű változót, amely kezdetben egy számot tárol. Ezután módosítsd úgy, hogy először szöveget, majd logikai értéket tároljon. Minden módosítás után jelenítsd meg az értékét és a típusát a konzolon.

2\. Típusellenőrzés

Hozz létre három változót: egy számot, egy szöveget és egy logikai értéket. A `typeof` operátor segítségével jelenítsd meg mindhárom változó típusát.

3\. Automatikus típuskonverzió

Hozz létre két változót:

- Az első értéke legyen `25`.
- A második értéke legyen `"15"`.

Végezd el rajtuk az összeadás, kivonás, szorzás és osztás műveletét! Jelenítsd meg az eredményeket és magyarázd meg a különbségeket.

4\. Szöveg átalakítása számmá

Hozz létre egy `"150"` értékű szöveges változót. Alakítsd át számmá a `Number()` segítségével, majd ellenőrizd az új változó típusát.

5\. Érvénytelen szám felismerése

Hozz létre egy `"alma"` értékű változót. Próbáld meg számmá alakítani, majd a `Number.isNaN()` segítségével ellenőrizd, hogy sikerült-e az átalakítás.

6\. Truthy és falsy értékek vizsgálata

Hozz létre legalább nyolc változót különböző értékekkel. Legyen közöttük `0`, `false`, üres szöveg, `null`, `undefined`, egy nem üres szöveg, egy üres tömb és egy üres objektum. Vizsgáld meg a `Boolean()` segítségével, hogy mely értékek truthy és melyek falsy értékek.

7\. Összehasonlító operátorok

Vizsgáld meg az alábbi kifejezések eredményét:

```
10 == "10"
10 === "10"
0 == false
0 === false
```

Jelenítsd meg az eredményeket, majd magyarázd meg, miért térhetnek el egymástól.

8\. Felhasználói adat átalakítása

Kérd be a felhasználó életkorát a `prompt()` segítségével. Alakítsd át számmá, majd ellenőrizd, hogy érvényes számot adott-e meg. Érvénytelen adat esetén jeleníts meg hibaüzenetet.

9\. Egyszerű típusellenőrző függvény

Készíts egy `tipusEllenorzes()` nevű függvényt, amely paraméterként egy értéket kap. A függvény jelenítse meg a konzolon az értéket és annak típusát. Próbáld ki számmal, szöveggel, logikai értékkel, tömbbel és objektummal is.

10\. Egyszerű adatfeldolgozó program

Hozz létre egy változót, amely kezdetben szöveges formában tárol egy számot. Alakítsd át számmá, majd ellenőrizd az eredményt. Ha az érték érvényes szám, számítsd ki a kétszeresét és a felét. Ha nem érvényes szám, jeleníts meg megfelelő hibaüzenetet.
