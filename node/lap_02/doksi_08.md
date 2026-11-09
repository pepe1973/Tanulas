# Konverzió és típusátalakítás JavaScriptben

## 1. Mit jelent a konverzió és a típusátalakítás?

A konverzió, más néven típusátalakítás, azt jelenti, hogy egy adott érték adattípusát egy másik adattípussá alakítjuk.

JavaScriptben erre gyakran azért van szükség, mert a program különböző forrásokból származó adatokat dolgoz fel. Például a felhasználó által megadott adatok, a HTML-űrlapokból érkező értékek vagy a szerverről letöltött adatok sok esetben szöveges formában állnak rendelkezésre.

Ha egy szövegként kapott értékkel matematikai műveletet szeretnénk végezni, akkor szükség lehet arra, hogy először számmá alakítsuk.

```javascript
let eletkor = '25';

console.log(typeof eletkor); // "string"

eletkor = Number(eletkor);

console.log(typeof eletkor); // "number"
```

A JavaScriptben két alapvető típusátalakítási módszert különböztetünk meg:

1. Implicit konverzió: a JavaScript automatikusan alakítja át az érték típusát.
2. Explicit konverzió: a programozó határozza meg, hogy milyen típusúvá szeretné alakítani az értéket.

## 2. Implicit típuskonverzió

Az implicit típuskonverzió során a JavaScript automatikusan átalakítja az egyik vagy mindkét operandus típusát egy művelet végrehajtása előtt.

Ez a folyamat a programozó külön utasítása nélkül történik.

### 2.1. Szám és szöveg összeadása

A `+` operátor kétféle feladatot is elláthat:

- Számok esetén matematikai összeadást végez.
- Ha valamelyik operandus szöveg, akkor szöveg-összefűzést végezhet.

```javascript
let a = 10;
let b = '20';

let eredmeny = a + b;

console.log(eredmeny); // "1020"
console.log(typeof eredmeny); // "string"
```

A JavaScript a számot szöveggé alakítja, majd összefűzi a két értéket.

### 2.2. Szöveg használata kivonásnál

A kivonás (`-`) esetében a JavaScript megpróbálja számmá alakítani a szöveges operandust.

```javascript
let a = 30;
let b = '10';

let eredmeny = a - b;

console.log(eredmeny); // 20
console.log(typeof eredmeny); // "number"
```

A `"10"` szöveg számmá alakul, így a művelet matematikai kivonásként hajtódik végre.

### 2.3. Szorzás és osztás

A szorzás és az osztás esetében is megtörténhet az automatikus számmá alakítás.

```javascript
let a = '5';
let b = 4;

console.log(a * b); // 20
console.log(a / b); // 1.25
```

A JavaScript a `"5"` értéket számmá alakítja.

### 2.4. Szám és logikai érték

A JavaScript bizonyos matematikai műveleteknél a logikai értékeket is számmá alakítja:

- `true` → `1`
- `false` → `0`

```javascript
console.log(10 + true); // 11
console.log(10 + false); // 10
console.log(true * 5); // 5
```

### 2.5. Érvénytelen konverzió

Ha egy szöveg nem alakítható át érvényes számmá, a matematikai művelet eredménye gyakran `NaN` lesz.

A `NaN` jelentése: Not a Number, vagyis nem szám.

```javascript
let szam = 20;
let szoveg = 'alma';

let eredmeny = szam - szoveg;

console.log(eredmeny); // NaN
```

A `NaN` típusa a `typeof` szerint `number`.

```javascript
console.log(typeof NaN); // "number"
```

## 3. Explicit típuskonverzió

Explicit típuskonverzió esetén a programozó közvetlenül utasítja a JavaScriptet az átalakításra.

Ez általában átláthatóbb és kiszámíthatóbb kódot eredményez, mint az automatikus típuskonverzióra hagyatkozás.

A leggyakrabban használt átalakító függvények:

| Függvény       | Feladat                           |
| -------------- | --------------------------------- |
| `Number()`     | Érték átalakítása számmá          |
| `String()`     | Érték átalakítása szöveggé        |
| `Boolean()`    | Érték átalakítása logikai értékké |
| `parseInt()`   | Egész szám kiolvasása szövegből   |
| `parseFloat()` | Tizedes szám kiolvasása szövegből |

## 4. Értékek átalakítása számmá – `Number()`

A `Number()` segítségével különböző típusú értékeket alakíthatunk számmá.

### 4.1. Szöveg átalakítása számmá

```javascript
let szoveg = '125';

let szam = Number(szoveg);

console.log(szam); // 125
console.log(typeof szam); // "number"
```

A `"125"` szöveges értékből `125` szám lesz.

### 4.2. Tizedes szám átalakítása

```javascript
let szoveg = '12.75';

let szam = Number(szoveg);

console.log(szam); // 12.75
```

A `Number()` a tizedes értéket is képes számmá alakítani.

JavaScriptben a tizedeselválasztó a pont, nem a vessző.

### 4.3. Üres szöveg átalakítása

```javascript
let szoveg = '';

let szam = Number(szoveg);

console.log(szam); // 0
```

Az üres szöveg `Number()` segítségével történő átalakításakor az eredmény nulla.

A csak szóközöket tartalmazó szöveg esetében is nulla az eredmény.

```javascript
console.log(Number('   ')); // 0
```

### 4.4. Logikai érték átalakítása

```javascript
console.log(Number(true)); // 1
console.log(Number(false)); // 0
```

### 4.5. Nem átalakítható szöveg

```javascript
let szoveg = 'JavaScript';

let szam = Number(szoveg);

console.log(szam); // NaN
```

A szöveg nem tartalmaz érvényes számot, ezért az eredmény `NaN`.

## 5. Egész szám kiolvasása – `parseInt()`

A `parseInt()` egy szöveg elejéről próbál egész számot kiolvasni.

```javascript
let szoveg = '125';

let szam = parseInt(szoveg);

console.log(szam); // 125
```

A függvény akkor is képes számot kiolvasni, ha a szám után további szöveg található.

```javascript
let adat = '125px';

let eredmeny = parseInt(adat);

console.log(eredmeny); // 125
```

A `parseInt()` a szám után következő, nem feldolgozható karaktereknél befejezi a kiolvasást.

Ha a szöveg nem kezdődik feldolgozható számmal, az eredmény `NaN` lesz.

```javascript
console.log(parseInt('alma125')); // NaN
```

### 5.1. A számrendszer megadása

A `parseInt()` második paramétereként megadhatjuk, hogy milyen számrendszerben értelmezze a szöveget.

```javascript
let szam = parseInt('1010', 2);

console.log(szam); // 10
```

A fenti példában a `"1010"` bináris számként értelmeződik, amelynek decimális értéke 10.

## 6. Tizedes szám kiolvasása – `parseFloat()`

A `parseFloat()` egy szöveg elejéről próbál tizedes számot kiolvasni.

```javascript
let szoveg = '12.75';

let szam = parseFloat(szoveg);

console.log(szam); // 12.75
```

A szám után további szöveg is szerepelhet:

```javascript
let adat = '12.75kg';

let eredmeny = parseFloat(adat);

console.log(eredmeny); // 12.75
```

Ha a szöveg nem kezdődik érvényes számmal, akkor `NaN` lesz az eredmény.

```javascript
console.log(parseFloat('alma12.75')); // NaN
```

## 7. A `Number()`, `parseInt()` és `parseFloat()` összehasonlítása

Mindhárom függvény alkalmas szöveges adatok feldolgozására, de eltérő módon működnek.

| Kifejezés               | Eredmény | Magyarázat                          |
| ----------------------- | -------- | ----------------------------------- |
| `Number("125")`         | `125`    | A teljes szöveget számmá alakítja   |
| `Number("125px")`       | `NaN`    | A teljes szöveg nem érvényes szám   |
| `parseInt("125px")`     | `125`    | Egész számot olvas ki az elejéről   |
| `parseFloat("12.75kg")` | `12.75`  | Tizedes számot olvas ki az elejéről |
| `parseInt("12.75")`     | `12`     | Csak az egész részt olvassa ki      |
| `parseFloat("12.75")`   | `12.75`  | A tizedes részt is megtartja        |

Fontos különbség:

- A `Number()` a teljes értéket próbálja számmá alakítani.
- A `parseInt()` a szöveg elejéről egész számot olvas ki.
- A `parseFloat()` a szöveg elejéről tizedes számot olvas ki.

## 8. Értékek átalakítása szöveggé – `String()`

A `String()` segítségével különböző típusú értékeket alakíthatunk szöveggé.

```javascript
let szam = 250;

let szoveg = String(szam);

console.log(szoveg); // "250"
console.log(typeof szoveg); // "string"
```

### 8.1. Logikai érték átalakítása

```javascript
let aktiv = true;

let szoveg = String(aktiv);

console.log(szoveg); // "true"
```

### 8.2. Null átalakítása

```javascript
let adat = null;

let szoveg = String(adat);

console.log(szoveg); // "null"
```

### 8.3. Undefined átalakítása

```javascript
let adat;

let szoveg = String(adat);

console.log(szoveg); // "undefined"
```

### 8.4. Tömb átalakítása szöveggé

A `String()` tömb esetén is használható.

```javascript
let gyumolcsok = ['alma', 'körte', 'barack'];

let szoveg = String(gyumolcsok);

console.log(szoveg); // "alma,körte,barack"
```

A tömb elemei vesszővel elválasztva kerülnek a szövegbe.

## 9. Értékek átalakítása logikai értékké – `Boolean()`

A `Boolean()` segítségével egy értéket `true` vagy `false` logikai értékké alakíthatunk.

```javascript
let szam = 1;

let logikai = Boolean(szam);

console.log(logikai); // true
console.log(typeof logikai); // "boolean"
```

A JavaScript minden értéket képes logikai értékként értelmezni.

### 9.1. Falsy értékek

Az alábbi értékek `false` eredményt adnak:

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

Példa:

```javascript
console.log(Boolean(0)); // false
console.log(Boolean('')); // false
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN)); // false
```

### 9.2. Truthy értékek

Minden más érték `true` eredményt ad.

```javascript
console.log(Boolean(10)); // true
console.log(Boolean(-5)); // true
console.log(Boolean('Hello')); // true
console.log(Boolean('0')); // true
console.log(Boolean([])); // true
console.log(Boolean({})); // true
```

Fontos: a `"0"` szöveg truthy érték, míg a `0` szám falsy érték.

Ugyanígy az üres tömb (`[]`) és az üres objektum (`{}`) is truthy.

## 10. Típusátalakítás a `+` operátorral

A JavaScriptben a `+` operátor nemcsak összeadásra, hanem szöveg-összefűzésre is használható.

Ha az egyik operandus szöveg, akkor a másik operandus is szöveggé alakulhat.

```javascript
let eletkor = 25;

let szoveg = 'Az életkor: ' + eletkor;

console.log(szoveg); // "Az életkor: 25"
```

A `+` operátor mellett létezik az összes többi matematikai operátor is, amelyek általában számmá alakítják az operandusokat.

```javascript
let a = '10';
let b = '5';

console.log(a + b); // "105"
console.log(a - b); // 5
console.log(a * b); // 50
console.log(a / b); // 2
```

Ezért fontos, hogy a műveletek előtt tisztában legyünk az értékek típusaival.

## 11. Típusátalakítás összehasonlításkor

A JavaScriptben az összehasonlító operátorok is kapcsolatban állhatnak a típuskonverzióval.

### 11.1. Laza összehasonlítás – `==`

A `==` operátor összehasonlítás előtt bizonyos esetekben automatikus típuskonverziót végez.

```javascript
console.log(10 == '10'); // true
console.log(1 == true); // true
console.log(0 == false); // true
```

A JavaScript a különböző típusú értékeket megpróbálja összehasonlítható formára alakítani.

### 11.2. Szigorú összehasonlítás – `===`

A `===` operátor nem végez ilyen automatikus típuskonverziót.

```javascript
console.log(10 === '10'); // false
console.log(1 === true); // false
console.log(0 === false); // false
```

A szigorú összehasonlítás az érték mellett a típust is figyelembe veszi.

Ajánlás: a legtöbb esetben használjuk a `===` és a `!==` operátorokat, hogy elkerüljük a nem kívánt típuskonverziókat.

## 12. Típusátalakítás felhasználói adatok esetén

A típusátalakítás egyik leggyakoribb alkalmazási területe a felhasználói adatok feldolgozása.

A HTML-űrlapokból és a `prompt()` segítségével érkező adatok általában szöveges értékek.

Példa egy életkor bekérésére:

```javascript
let eletkor = prompt('Hány éves vagy?');

eletkor = Number(eletkor);

if (Number.isNaN(eletkor)) {
    console.log('Érvénytelen életkor!');
} else {
    console.log('A megadott életkor: ' + eletkor);
}
```

A program működése:

1. A `prompt()` bekéri a felhasználó életkorát.
2. A kapott szöveget a `Number()` számmá alakítja.
3. A `Number.isNaN()` ellenőrzi, hogy az eredmény `NaN`-e.
4. Érvényes szám esetén a program megjeleníti az értéket.
5. Érvénytelen adat esetén hibaüzenetet jelenít meg.

### 12.1. További ellenőrzés

A `Number()` önmagában nem ellenőrzi, hogy a megadott életkor értelmes-e. Például a negatív szám is érvényes számnak számít.

Ezért további feltételeket is alkalmazhatunk:

```javascript
let eletkor = Number(prompt('Hány éves vagy?'));

if (Number.isNaN(eletkor)) {
    console.log('Nem számot adtál meg.');
} else if (eletkor < 0) {
    console.log('Az életkor nem lehet negatív.');
} else if (eletkor > 120) {
    console.log('Ellenőrizd a megadott életkort.');
} else {
    console.log('Elfogadott életkor: ' + eletkor);
}
```

A típusellenőrzés és az értéktartomány ellenőrzése két külön feladat:

- Típusellenőrzés: megfelelő típusú adatot kaptunk-e?
- Értékellenőrzés: az adat értéke megfelel-e az elvárásoknak?

## 13. Gyakori hibák a típusátalakítás során

### 13.1. Szövegek összeadása számok helyett

```javascript
let a = '10';
let b = '20';

console.log(a + b); // "1020"
```

Ha matematikai összeadást szeretnénk, előbb alakítsuk számmá az értékeket:

```javascript
let a = Number('10');
let b = Number('20');

console.log(a + b); // 30
```

### 13.2. A `parseInt()` használata tizedes számoknál

```javascript
let szam = parseInt('12.85');

console.log(szam); // 12
```

A `parseInt()` elhagyja a tizedes részt.

Ha a tizedes részt is meg szeretnénk tartani, használjuk a `parseFloat()` vagy a `Number()` függvényt.

```javascript
console.log(parseFloat('12.85')); // 12.85
console.log(Number('12.85')); // 12.85
```

### 13.3. Az üres szöveg számmá alakítása

```javascript
let adat = '';

console.log(Number(adat)); // 0
```

Ez különösen fontos felhasználói adatok feldolgozásakor. Az üres mezőből kapott érték nem feltétlenül jelent valódi, megadott nullát.

Ezért az átalakítás előtt érdemes ellenőrizni, hogy a felhasználó valóban megadott-e értéket.

```javascript
let adat = '';

if (adat.trim() === '') {
    console.log('Nem adtál meg értéket.');
} else {
    console.log(Number(adat));
}
```

### 13.4. A `NaN` helytelen ellenőrzése

A következő ellenőrzés nem megfelelő:

```javascript
let szam = Number('alma');

if (szam === NaN) {
    console.log('Nem érvényes szám.');
}
```

A `NaN` sajátossága, hogy még önmagával sem egyenlő.

Helyesen:

```javascript
let szam = Number('alma');

if (Number.isNaN(szam)) {
    console.log('Nem érvényes szám.');
}
```

## 14. Összefoglalás

A konverzió és a típusátalakítás a JavaScript egyik fontos alapfogalma.

A legfontosabb tudnivalók:

- A típusátalakítás során egy érték adattípusát változtatjuk meg.
- Az implicit konverziót a JavaScript automatikusan végzi.
- Az explicit konverziót a programozó kezdeményezi.
- A `Number()` értékeket alakít számmá.
- A `String()` értékeket alakít szöveggé.
- A `Boolean()` értékeket alakít logikai típussá.
- A `parseInt()` egész számot olvas ki egy szövegből.
- A `parseFloat()` tizedes számot olvas ki egy szövegből.
- A sikertelen számmá alakítás eredménye gyakran `NaN`.
- A `Number.isNaN()` segítségével ellenőrizhetjük a `NaN` értéket.
- A `==` automatikus típuskonverziót végezhet, a `===` nem.
- Felhasználói adatok feldolgozásakor érdemes ellenőrizni az adat típusát és értékét is.

# 15. Ellenőrző kérdések

1. Mit jelent a konverzió vagy típusátalakítás JavaScriptben?
2. Mi a különbség az implicit és az explicit típuskonverzió között?
3. Mi történik a `10 + "20"` kifejezés végrehajtásakor?
4. Milyen eredményt ad a `Number("125px")`, és miért?
5. Mi a különbség a `Number()` és a `parseInt()` között?
6. Mire használjuk a `parseFloat()` függvényt?
7. Milyen eredményt ad a `Boolean(0)`, a `Boolean("0")` és a `Boolean("")`?
8. Milyen típusú értéket ad vissza a `String(true)`?
9. Mi a különbség a `==` és a `===` operátor között?
10. Miért fontos ellenőrizni a felhasználótól érkező adatokat a típusátalakítás után?

# 16. Gyakorlati feladatok

A feladatokat JavaScriptben oldd meg! A megoldásokhoz használj változókat, típusátalakító függvényeket, feltételeket és szükség esetén függvényeket.

1\. Szöveg átalakítása számmá

Hozz létre egy `szoveg` nevű változót, amely a `"250"` értéket tárolja. Alakítsd át számmá a `Number()` segítségével! Jelenítsd meg az eredményt és az új érték típusát!

2\. Különböző konverziók összehasonlítása

Hozz létre egy `"125.75"` értékű szöveges változót! Alakítsd át az értékét a `Number()`, a `parseInt()` és a `parseFloat()` segítségével! Jelenítsd meg mindhárom eredményt, és figyeld meg a különbségeket!

3\. Szöveg átalakítása logikai értékké

Hozz létre több változót az alábbi értékekkel:

- `""`
- `"Hello"`
- `"0"`
- `0`
- `1`
- `null`
- `undefined`

Alakítsd át mindegyiket a `Boolean()` segítségével! Jelenítsd meg az eredményeket!

4\. Automatikus típuskonverzió vizsgálata

Hozz létre két változót:

```javascript
let a = '15';
let b = 5;
```

Végezd el a következő műveleteket:

- Összeadás.
- Kivonás.
- Szorzás.
- Osztás.

Minden eredmény után jelenítsd meg annak típusát is!

5\. Érvénytelen szám felismerése

Hozz létre három szöveges változót:

- `"125"`
- `"12.5"`
- `"alma"`

Alakítsd át mindegyiket számmá! A `Number.isNaN()` segítségével ellenőrizd, hogy melyik átalakítás eredményezett érvénytelen számot!

6\. Egész és tizedes szám feldolgozása

Hozz létre egy `"45.89kg"` értékű változót! Próbáld feldolgozni a `parseInt()` és a `parseFloat()` segítségével! Jelenítsd meg az eredményeket, és magyarázd meg a különbséget!

7\. Felhasználói adatok feldolgozása

Kérd be a felhasználó életkorát a `prompt()` segítségével! Alakítsd át számmá, majd ellenőrizd, hogy:

- Érvényes számot adott-e meg.
- Nem negatív-e az érték.
- Nem nagyobb-e 120-nál.

A feltételeknek megfelelően jeleníts meg üzenetet!

8\. Egyszerű számológép

Kérj be két értéket a felhasználótól! Alakítsd át mindkettőt számmá! Ha mindkét érték érvényes szám, végezd el az összeadás, kivonás, szorzás és osztás műveletét! Osztás esetén ellenőrizd, hogy a második szám nem nulla-e!

9\. Konverziós függvény készítése

Készíts egy `konvertal()` nevű függvényt, amely két paramétert kap:

- Az első paraméter az átalakítandó érték.
- A második paraméter az elvárt típus neve (`"number"`, `"string"` vagy `"boolean"`).

A függvény a megadott típusnak megfelelően alakítsa át az értéket, majd adja vissza az eredményt! Ha nem támogatott típust kap, jelenítsen meg hibaüzenetet!

10\. Összetett adatfeldolgozó program

Készíts egy programot, amely három adatot kér be a felhasználótól:

- A nevét.
- Az életkorát.
- A havi jövedelmét.

A program:

- A nevet szövegként kezelje.
- Az életkort alakítsa számmá.
- A jövedelmet alakítsa számmá.
- Ellenőrizze, hogy az életkor és a jövedelem érvényes szám-e.
- Ellenőrizze, hogy egyik érték sem negatív.
- Érvényes adatok esetén jelenítse meg a felhasználó adatait és azok típusát.
- Hibás adatok esetén jelenítsen meg megfelelő hibaüzenetet.
