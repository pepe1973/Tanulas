# Implicit és explicit konverzió JavaScriptben

## 1. Mit jelent a típuskonverzió?

A típuskonverzió (típusátalakítás) azt jelenti, hogy egy érték adattípusát egy másik adattípussá alakítjuk.

JavaScriptben erre két alapvető lehetőségünk van:

1. Implicit konverzió: a JavaScript automatikusan alakítja át az érték típusát.
2. Explicit konverzió: a programozó közvetlenül utasítja a JavaScriptet az átalakításra.

A két módszer közötti legfontosabb különbség az, hogy ki kezdeményezi a típusátalakítást.

Például:

```javascript
// Implicit konverzió
let eredmeny1 = 10 + '5';

console.log(eredmeny1); // "105"

// Explicit konverzió
let eredmeny2 = 10 + Number('5');

console.log(eredmeny2); // 15
```

Az első esetben a JavaScript automatikusan szöveggé alakítja a számot. A második esetben a programozó a `Number()` segítségével számmá alakítja a szöveget.

## 2. Implicit konverzió

Az implicit konverzió során a JavaScript automatikusan módosítja az értékek típusát egy művelet végrehajtásakor.

A programozónak nem kell külön átalakító függvényt meghívnia. A JavaScript a művelet szabályai alapján dönti el, hogy szükséges-e a típusátalakítás.

### 2.1. Szám és szöveg összeadása

A `+` operátor számok esetén matematikai összeadást, szövegek esetén pedig összefűzést végez.

Ha az egyik operandus szöveg, akkor a JavaScript gyakran szöveggé alakítja a másik operandust is.

```javascript
let a = 10;
let b = '20';

let eredmeny = a + b;

console.log(eredmeny); // "1020"
console.log(typeof eredmeny); // "string"
```

A művelet lépései:

1. Az `a` változó értéke `10`, típusa `number`.
2. A `b` változó értéke `"20"`, típusa `string`.
3. A JavaScript a `10` értéket szöveggé alakítja.
4. A két szöveget összefűzi.
5. Az eredmény `"1020"` lesz.

### 2.2. Szöveg kivonása számból

A kivonás (`-`) esetében a JavaScript megpróbálja számmá alakítani a szöveges értéket.

```javascript
let a = 30;
let b = '10';

let eredmeny = a - b;

console.log(eredmeny); // 20
console.log(typeof eredmeny); // "number"
```

A `"10"` szöveg számmá alakul, ezért a művelet matematikai kivonásként hajtódik végre.

### 2.3. Szorzás és osztás

A szorzás és az osztás esetében is automatikus számmá alakítás történhet.

```javascript
let a = '12';
let b = 3;

console.log(a * b); // 36
console.log(a / b); // 4
```

A JavaScript a `"12"` értéket számmá alakítja, majd végrehajtja a műveletet.

### 2.4. Szám és logikai érték

A JavaScript matematikai műveleteknél a logikai értékeket is számmá alakíthatja.

| Logikai érték | Számmá alakított érték |
| ------------- | ---------------------- |
| `true`        | `1`                    |
| `false`       | `0`                    |

Például:

```javascript
console.log(10 + true); // 11
console.log(10 + false); // 10
console.log(true * 5); // 5
console.log(false + 8); // 8
```

A `true` értéket a JavaScript `1`-ként, a `false` értéket pedig `0`-ként kezeli ezekben a műveletekben.

### 2.5. Szöveg és logikai érték összeadása

Ha szöveget és logikai értéket adunk össze, akkor a `+` operátor szöveg-összefűzést végez.

```javascript
let nev = 'Anna';
let aktiv = true;

let eredmeny = nev + aktiv;

console.log(eredmeny); // "Annatrue"
```

A logikai érték szöveges formában kerül az eredménybe.

### 2.6. Null és undefined konverziója

A `null` és az `undefined` különböző módon viselkedhetnek az automatikus konverzió során.

Matematikai műveleteknél:

```javascript
console.log(10 + null); // 10
console.log(10 + undefined); // NaN
```

A `null` számmá alakítva `0` értéket jelent, míg az `undefined` számmá alakításakor `NaN` keletkezik.

### 2.7. Érvénytelen konverzió és NaN

Ha a JavaScript nem tud egy értéket megfelelő számmá alakítani, akkor az eredmény `NaN` lehet.

A `NaN` jelentése: Not a Number, vagyis nem szám.

```javascript
let a = 20;
let b = 'alma';

let eredmeny = a - b;

console.log(eredmeny); // NaN
```

A `NaN` típusa a `typeof` szerint `number`.

```javascript
console.log(typeof NaN); // "number"
```

Az ilyen érték ellenőrzésére a `Number.isNaN()` használható.

```javascript
if (Number.isNaN(eredmeny)) {
    console.log('Az eredmény nem érvényes szám.');
}
```

## 3. Explicit konverzió

Az explicit konverzió során a programozó közvetlenül meghatározza, hogy egy értéket milyen adattípussá szeretne alakítani.

Ez általában átláthatóbbá teszi a program működését, mert a típusátalakítás egyértelműen látható a kódban.

A legfontosabb átalakító függvények:

| Függvény       | Feladat                           |
| -------------- | --------------------------------- |
| `Number()`     | Átalakítás számmá                 |
| `String()`     | Átalakítás szöveggé               |
| `Boolean()`    | Átalakítás logikai értékké        |
| `parseInt()`   | Egész szám kiolvasása szövegből   |
| `parseFloat()` | Tizedes szám kiolvasása szövegből |

### 3.1. Szöveg átalakítása számmá – Number()

A `Number()` segítségével egy szöveges értéket számmá alakíthatunk.

```javascript
let szoveg = '125';

let szam = Number(szoveg);

console.log(szam); // 125
console.log(typeof szam); // "number"
```

Tizedes szám esetén is működik:

```javascript
let szoveg = '12.75';

let szam = Number(szoveg);

console.log(szam); // 12.75
```

Ha a szöveg nem alakítható számmá, akkor az eredmény `NaN` lesz.

```javascript
let szoveg = 'JavaScript';

let szam = Number(szoveg);

console.log(szam); // NaN
```

### 3.2. Szöveg átalakítása egész számmá – parseInt()

A `parseInt()` egy szöveg elejéről próbál egész számot kiolvasni.

```javascript
let adat = '125px';

let szam = parseInt(adat);

console.log(szam); // 125
```

A függvény a szám után következő, nem feldolgozható karaktereknél befejezi a kiolvasást.

Másik példa:

```javascript
let adat = '45.89';

let szam = parseInt(adat);

console.log(szam); // 45
```

A `parseInt()` csak az egész számrészt olvassa ki.

A függvény második paraméterében megadhatjuk a számrendszert is:

```javascript
let szam = parseInt('1010', 2);

console.log(szam); // 10
```

Ebben a példában a `"1010"` bináris számként értelmeződik.

### 3.3. Szöveg átalakítása tizedes számmá – parseFloat()

A `parseFloat()` a szöveg elejéről tizedes számot próbál kiolvasni.

```javascript
let adat = '45.89kg';

let szam = parseFloat(adat);

console.log(szam); // 45.89
```

A `parseFloat()` a tizedes részt is megtartja.

### 3.4. Érték átalakítása szöveggé – String()

A `String()` segítségével számokat, logikai értékeket és más adattípusokat alakíthatunk szöveggé.

```javascript
let szam = 250;

let szoveg = String(szam);

console.log(szoveg); // "250"
console.log(typeof szoveg); // "string"
```

Logikai értékkel:

```javascript
let aktiv = true;

let szoveg = String(aktiv);

console.log(szoveg); // "true"
```

`null` értékkel:

```javascript
let adat = null;

let szoveg = String(adat);

console.log(szoveg); // "null"
```

### 3.5. Érték átalakítása logikai értékké – Boolean()

A `Boolean()` segítségével egy értéket `true` vagy `false` típusúvá alakíthatunk.

```javascript
let szam = 1;

let logikai = Boolean(szam);

console.log(logikai); // true
console.log(typeof logikai); // "boolean"
```

A JavaScriptben vannak olyan értékek, amelyek logikai környezetben hamisnak számítanak. Ezeket falsy értékeknek nevezzük.

| Érték       | `Boolean()` eredménye |
| ----------- | --------------------- |
| `false`     | `false`               |
| `0`         | `false`               |
| `-0`        | `false`               |
| `0n`        | `false`               |
| `""`        | `false`               |
| `null`      | `false`               |
| `undefined` | `false`               |
| `NaN`       | `false`               |

Minden más érték truthy, vagyis igaznak tekinthető.

```javascript
console.log(Boolean('JavaScript')); // true
console.log(Boolean('0')); // true
console.log(Boolean(100)); // true
console.log(Boolean([])); // true
console.log(Boolean({})); // true
```

Fontos: az üres szöveg falsy, de az üres tömb és az üres objektum truthy.

## 4. Az implicit és explicit konverzió összehasonlítása

| Szempont                  | Implicit konverzió        | Explicit konverzió      |
| ------------------------- | ------------------------- | ----------------------- |
| Ki végzi?                 | JavaScript                | Programozó kezdeményezi |
| Automatikus?              | Igen                      | Nem                     |
| Külön függvény szükséges? | Nem                       | Általában igen          |
| Átláthatóság              | Néha nehezen felismerhető | Egyértelműbb            |
| Példa                     | `"10" * 2`                | `Number("10") * 2`      |

Nézzünk egy összehasonlító példát:

```javascript
let adat = '10';

// Implicit konverzió
let eredmeny1 = adat * 2;

// Explicit konverzió
let eredmeny2 = Number(adat) * 2;

console.log(eredmeny1); // 20
console.log(eredmeny2); // 20
```

Mindkét esetben ugyanaz az eredmény, de eltérő módon történik a típusátalakítás.

Az explicit változatban egyértelműen látható, hogy a szöveget számmá alakítjuk.

## 5. Az implicit konverzió és a műveleti sorrend

A JavaScriptben fontos megérteni, hogy az automatikus típuskonverzió hogyan befolyásolja a műveletek eredményét.

Például:

```javascript
let a = '10';
let b = 5;
let c = 2;

let eredmeny = a + b * c;

console.log(eredmeny); // "1010"
```

A művelet a következőképpen hajtódik végre:

1. Először a szorzás történik meg: `5 * 2 = 10`.
2. Ezután következik az összeadás: `"10" + 10`.
3. A JavaScript szöveggé alakítja a számot.
4. A két szöveget összefűzi.
5. Az eredmény `"1010"` lesz.

Ha matematikai összeadást szeretnénk, akkor használjunk explicit konverziót:

```javascript
let a = '10';
let b = 5;
let c = 2;

let eredmeny = Number(a) + b * c;

console.log(eredmeny); // 20
```

## 6. Konverzió összehasonlításkor

A típuskonverzió az összehasonlító operátorok működését is befolyásolhatja.

### 6.1. Laza összehasonlítás – `==`

A `==` operátor bizonyos esetekben automatikusan átalakítja az értékeket összehasonlítás előtt.

```javascript
console.log(10 == '10'); // true
console.log(1 == true); // true
console.log(0 == false); // true
```

A különböző típusú értékek az automatikus konverzió után egyenlőnek bizonyulhatnak.

### 6.2. Szigorú összehasonlítás – `===`

A `===` operátor nem végez automatikus típuskonverziót.

```javascript
console.log(10 === '10'); // false
console.log(1 === true); // false
console.log(0 === false); // false
```

A szigorú összehasonlítás során az értéknek és a típusnak is egyeznie kell.

Ajánlás: a legtöbb esetben használjuk a `===` és a `!==` operátorokat.

## 7. Típuskonverzió a felhasználói adatok feldolgozásakor

A felhasználói adatok kezelése során gyakran találkozunk típuskonverzióval.

A `prompt()` függvény például szöveges értéket ad vissza, még akkor is, ha a felhasználó számot ír be.

```javascript
let elsoSzam = prompt('Add meg az első számot!');
let masodikSzam = prompt('Add meg a második számot!');

console.log(elsoSzam + masodikSzam);
```

Ha a felhasználó `10` és `20` értékeket ad meg, az eredmény nem `30`, hanem `"1020"` lesz.

Ennek oka, hogy mindkét változó szöveget tartalmaz, ezért a `+` operátor összefűzést végez.

Helyes megoldás:

```javascript
let elsoSzam = Number(prompt('Add meg az első számot!'));
let masodikSzam = Number(prompt('Add meg a második számot!'));

let eredmeny = elsoSzam + masodikSzam;

console.log(eredmeny); // 30
```

### 7.1. A kapott adatok ellenőrzése

A típusátalakítás önmagában nem garantálja, hogy érvényes adatot kaptunk.

```javascript
let adat = prompt('Adj meg egy számot!');

let szam = Number(adat);

if (Number.isNaN(szam)) {
    console.log('Nem érvényes számot adtál meg!');
} else {
    console.log('A megadott szám: ' + szam);
}
```

Érdemes az üres szöveget is külön ellenőrizni, mert a `Number("")` eredménye `0`.

```javascript
let adat = prompt('Adj meg egy számot!');

if (adat.trim() === '') {
    console.log('Nem adtál meg értéket!');
} else {
    let szam = Number(adat);

    if (Number.isNaN(szam)) {
        console.log('Érvénytelen szám!');
    } else {
        console.log('A megadott szám: ' + szam);
    }
}
```

## 8. Mikor melyik konverziót használjuk?

A megfelelő konverziós módszer kiválasztása a program feladatától függ.

| Helyzet                                 | Ajánlott megoldás   |
| --------------------------------------- | ------------------- |
| Szöveges szám teljes átalakítása számmá | `Number()`          |
| Egész szám kiolvasása szövegből         | `parseInt()`        |
| Tizedes szám kiolvasása szövegből       | `parseFloat()`      |
| Szám vagy más érték szöveggé alakítása  | `String()`          |
| Érték logikai formára alakítása         | `Boolean()`         |
| Automatikus konverzió elkerülése        | Explicit átalakítás |
| Típusazonos összehasonlítás             | `===`               |

A programozás során általában érdemes az explicit konverziót előnyben részesíteni, amikor egy érték típusát egyértelműen meg szeretnénk változtatni.

Ez olvashatóbbá és könnyebben hibakereshetővé teszi a programot.

## 9. Összefoglalás

Az implicit és explicit konverzió a JavaScript típuskezelésének két alapvető módszere.

Implicit konverzió:

- A JavaScript automatikusan végzi.
- A műveletek során az operandusok típusa megváltozhat.
- A `+` operátor szöveg-összefűzést vagy összeadást is végezhet.
- A `-`, `*` és `/` operátorok általában számmá alakítják az operandusokat.
- Nem megfelelő átalakítás esetén `NaN` keletkezhet.

Explicit konverzió:

- A programozó kezdeményezi.
- A `Number()` számmá alakít.
- A `String()` szöveggé alakít.
- A `Boolean()` logikai értékké alakít.
- A `parseInt()` egész számot olvas ki.
- A `parseFloat()` tizedes számot olvas ki.

A legfontosabb cél, hogy a programban mindig tisztában legyünk azzal, milyen típusú értékekkel dolgozunk, és szükség esetén tudatosan alakítsuk át őket.

# 10. Ellenőrző kérdések

1. Mit jelent az implicit konverzió JavaScriptben?
2. Mit jelent az explicit konverzió?
3. Mi a legfontosabb különbség az implicit és az explicit konverzió között?
4. Mi lesz a `"10" + 5` kifejezés eredménye, és miért?
5. Miért ad a `"10" - 5` kifejezés `5` eredményt?
6. Mire használjuk a `Number()`, a `String()` és a `Boolean()` függvényeket?
7. Mi a különbség a `parseInt()` és a `parseFloat()` között?
8. Miért fontos ellenőrizni a `Number()` segítségével átalakított értékeket?
9. Mi a különbség a `==` és a `===` operátor között?
10. Miért ajánlott az explicit konverzió használata a felhasználótól érkező adatok feldolgozásakor?

# 11. Gyakorlati feladatok

A feladatokat JavaScriptben oldd meg! A megoldásokhoz használj változókat, típusátalakító függvényeket, feltételeket és szükség esetén függvényeket. A feladatokhoz nem tartozik előre megadott megoldás.

1\. Implicit konverzió vizsgálata

Hozz létre két változót:

- `a = 15`
- `b = "25"`

Végezd el a következő műveleteket:

- Összeadás.
- Kivonás.
- Szorzás.
- Osztás.

Jelenítsd meg az eredményeket és azok típusát is! Magyarázd meg, miért különbözik az összeadás eredménye a többi műveletétől!

2\. Explicit konverzió használata

Hozz létre egy `"150"` értékű szöveges változót! Alakítsd át számmá a `Number()` segítségével! Ezután adj hozzá 50-et, és jelenítsd meg az eredményt!

3\. Különböző konverziós módszerek

Hozz létre egy `"45.89kg"` értékű változót! Próbáld meg átalakítani a `Number()`, a `parseInt()` és a `parseFloat()` segítségével! Jelenítsd meg az eredményeket, majd magyarázd meg a különbségeket!

4\. Logikai értékek konverziója

Hozz létre legalább nyolc különböző értéket tároló változót! Legyen közöttük `0`, `1`, `""`, `"Hello"`, `null`, `undefined`, egy üres tömb és egy üres objektum! Alakítsd át mindegyiket `Boolean()` segítségével, majd jelenítsd meg az eredményeket!

5\. Implicit és explicit konverzió összehasonlítása

Hozz létre egy `"20"` értékű szöveges változót és egy `10` értékű számot! Végezd el az összeadást először implicit, majd explicit konverzióval! Hasonlítsd össze a két eredményt és azok típusát!

6\. Hibás típuskonverzió felismerése

Hozz létre három szöveges változót:

- `"125"`
- `"12.5"`
- `"alma"`

Alakítsd át mindegyiket számmá! A `Number.isNaN()` segítségével ellenőrizd, hogy melyik átalakítás volt sikeres!

7\. Felhasználói adatok feldolgozása

Kérj be két számot a felhasználótól a `prompt()` segítségével! Alakítsd át őket számmá, majd ellenőrizd, hogy mindkét érték érvényes-e! Ha igen, végezd el az összeadást, kivonást, szorzást és osztást! Osztás esetén ellenőrizd, hogy a második szám nem nulla-e!

8\. Konverziós függvény készítése

Készíts egy `konvertal()` nevű függvényt, amely két paramétert kap:

- Az első paraméter az átalakítandó érték.
- A második paraméter az elvárt típus neve (`"number"`, `"string"` vagy `"boolean"`).

A függvény a megadott típusnak megfelelően alakítsa át az értéket, és adja vissza az eredményt! Nem támogatott típus esetén adjon vissza megfelelő hibaüzenetet!

9\. Életkor ellenőrzése

Kérd be a felhasználó életkorát szöveges formában! Alakítsd át számmá, majd ellenőrizd:

- Üres-e a megadott érték.
- Sikerült-e a számmá alakítás.
- Nem negatív-e az életkor.
- Nem nagyobb-e 120-nál.

A megfelelő feltételek alapján jeleníts meg üzenetet!

10\. Egyszerű adatfeldolgozó program

Hozz létre egy programot, amely három adatot kér be a felhasználótól:

- A felhasználó neve.
- Az életkora.
- A havi jövedelme.

A program:

- A nevet kezelje szövegként.
- Az életkort és a jövedelmet alakítsa számmá.
- Ellenőrizze, hogy az átalakítás sikeres volt-e.
- Ellenőrizze, hogy az életkor és a jövedelem nem negatív-e.
- Érvényes adatok esetén jelenítse meg az összes adatot és azok típusát.
- Hibás adatok esetén jelenítsen meg megfelelő hibaüzenetet.
