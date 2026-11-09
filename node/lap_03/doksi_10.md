# Igazságértékek JavaScriptben – `truthy` és `falsy` értékek

## 1. Mit jelent az igazságérték?

A JavaScriptben minden értékhez hozzárendelhető egy logikai igazságérték: `true` vagy `false`.

Ezeket az értékeket a programozási nyelv többek között feltételek kiértékelésekor használja. Például egy `if` utasítás eldönti, hogy végrehajtsa-e a hozzá tartozó kódblokkot.

```javascript
const szam = 10;

if (szam) {
    console.log('A feltétel igaz.');
}
```

Ebben az esetben a `szam` változó értéke `10`. A JavaScript ezt igaznak tekinti, ezért végrehajtja az `if` blokkot.

Fontos, hogy nem csak a `true` és `false` értékek használhatók feltételekben. Más típusú értékek is kiértékelhetők logikai értékként.

## 2. A `truthy` értékek

A `truthy` kifejezés azokat az értékeket jelöli, amelyeket a JavaScript logikai környezetben `true` értéknek tekint.

Ilyen például:

- minden nem nulla szám;
- minden nem üres szöveg;
- minden objektum;
- minden tömb;
- a `true` logikai érték.

Példák:

```javascript
if (10) {
    console.log('A 10 truthy érték.');
}

if ('JavaScript') {
    console.log('A szöveg truthy érték.');
}

if ([]) {
    console.log('Az üres tömb is truthy érték.');
}

if ({}) {
    console.log('Az üres objektum is truthy érték.');
}
```

Mind a négy feltétel igaznak számít.

Fontos: JavaScriptben az üres tömb (`[]`) és az üres objektum (`{}`) is `truthy`, annak ellenére, hogy nincs bennük elem vagy tulajdonság.

## 3. A `falsy` értékek

A `falsy` kifejezés azokat az értékeket jelöli, amelyeket a JavaScript logikai környezetben `false` értéknek tekint.

JavaScriptben pontosan az alábbi alapértékek számítanak `falsy` értéknek:

| Érték       | Jelentés                  |
| ----------- | ------------------------- |
| `false`     | Logikai hamis             |
| `0`         | Nulla                     |
| `-0`        | Negatív nulla             |
| `0n`        | BigInt nulla              |
| `""`        | Üres szöveg               |
| `null`      | Szándékosan hiányzó érték |
| `undefined` | Nem definiált érték       |
| `NaN`       | Nem szám érték            |

Példák:

```javascript
if (0) {
    console.log('Ez nem jelenik meg.');
}

if ('') {
    console.log('Ez sem jelenik meg.');
}

if (null) {
    console.log('Ez sem jelenik meg.');
}
```

Egyik üzenet sem jelenik meg, mert mindhárom feltétel `falsy`.

A `NaN` is `falsy`:

```javascript
const eredmeny = Number('alma');

if (eredmeny) {
    console.log('Érvényes szám.');
} else {
    console.log('Az érték falsy.');
}
```

A `Number("alma")` eredménye `NaN`, ezért az `else` ág fut le.

## 4. Az értékek logikai átalakítása: `Boolean()`

A `Boolean()` függvénnyel bármilyen értéket explicit módon logikai értékké alakíthatunk.

```javascript
console.log(Boolean(10)); // true
console.log(Boolean(0)); // false
console.log(Boolean('alma')); // true
console.log(Boolean('')); // false
console.log(Boolean([])); // true
console.log(Boolean(null)); // false
```

A függvény eredménye minden esetben `true` vagy `false`.

Ez hasznos lehet például adatok ellenőrzésekor vagy feltételek tesztelésekor.

## 5. A dupla tagadás: `!!`

Egy értéket a dupla tagadás operátorával (`!!`) is logikai értékké alakíthatunk.

Az első `!` megfordítja az érték logikai jelentését, a második pedig ismét megfordítja azt. Így az eredmény az eredeti érték logikai megfelelője lesz.

```javascript
console.log(!!10); // true
console.log(!!0); // false
console.log(!!'alma'); // true
console.log(!!''); // false
console.log(!!null); // false
```

A `Boolean()` és a `!!` ugyanazt az eredményt adja.

## 6. Igazságértékek használata az `if...else` szerkezetben

A `truthy` és `falsy` értékek segítségével egyszerűen ellenőrizhetjük, hogy egy változó rendelkezik-e használható értékkel.

```javascript
const felhasznalonev = 'Kata';

if (felhasznalonev) {
    console.log('A felhasználónév meg van adva.');
} else {
    console.log('Nincs megadva felhasználónév.');
}
```

Ha a `felhasznalonev` értéke üres szöveg lenne, akkor az `else` ág hajtódna végre.

```javascript
const felhasznalonev = '';

if (felhasznalonev) {
    console.log('A felhasználónév meg van adva.');
} else {
    console.log('Nincs megadva felhasználónév.');
}
```

Ez a megoldás rövid és gyakori, de figyelni kell arra, hogy minden `falsy` értéket hiányzó adatként kezel. Ha például a `0` érvényes adat lehet, akkor külön ellenőrzésre van szükség.

## 7. Igazságértékek használata a logikai operátorokkal

A `truthy` és `falsy` értékek a logikai operátorok működésében is fontos szerepet kapnak.

### Logikai VAGY: `||`

A `||` operátor az első `truthy` értéket adja vissza. Ha minden operandus `falsy`, akkor az utolsót adja vissza.

```javascript
const nev = '';

const megjelenitendoNev = nev || 'Vendég';

console.log(megjelenitendoNev); // Vendég
```

Ha a `nev` üres szöveg, akkor a program a `"Vendég"` értéket választja.

### Logikai ÉS: `&&`

A `&&` operátor az első `falsy` értéket adja vissza. Ha minden operandus `truthy`, akkor az utolsót adja vissza.

```javascript
const felhasznaloAktiv = true;

const uzenet = felhasznaloAktiv && 'A felhasználó aktív.';

console.log(uzenet); // A felhasználó aktív.
```

Ha a `felhasznaloAktiv` értéke `false`, akkor az eredmény is `false` lesz.

### Logikai tagadás: `!`

A `!` operátor egy érték logikai ellentétét adja vissza.

```javascript
const bejelentkezett = false;

if (!bejelentkezett) {
    console.log('A felhasználó nincs bejelentkezve.');
}
```

A `!bejelentkezett` kifejezés értéke `true`, ezért az `if` blokk végrehajtódik.

## 8. A `||` és a `??` közötti különbség

A két operátor hasonló célra használható, de nem ugyanazokat az értékeket tekinti hiányzónak.

- A `||` minden `falsy` értéknél a második operandust választja.
- A `??` (nullish coalescing) csak `null` vagy `undefined` esetén választja a második operandust.

Példa:

```javascript
const eletkor = 0;

const eredmeny1 = eletkor || 18;
const eredmeny2 = eletkor ?? 18;

console.log(eredmeny1); // 18
console.log(eredmeny2); // 0
```

A `0` `falsy`, ezért a `||` a `18` értéket adja vissza.

A `??` viszont csak a `null` és az `undefined` értéket kezeli hiányzóként, ezért a `0` megmarad.

Ez különösen fontos akkor, amikor a nulla vagy az üres szöveg érvényes adat lehet.

## 9. Gyakori hibák és félreértések

1\. Az üres tömb nem `falsy`.

```javascript
if ([]) {
    console.log('Ez a blokk végrehajtódik.');
}
```

2\. Az üres objektum sem `falsy`.

```javascript
if ({}) {
    console.log('Ez a blokk is végrehajtódik.');
}
```

3\. A `"0"` szöveg `truthy`.

```javascript
console.log(Boolean('0')); // true
```

A `"0"` nem nulla szám, hanem egy nem üres szöveg.

4\. A `"false"` szöveg is `truthy`.

```javascript
console.log(Boolean('false')); // true
```

A JavaScript nem a szöveg jelentését vizsgálja, hanem azt, hogy üres-e.

5\. A `0` és a `false` nem ugyanaz.

```javascript
console.log(0 === false); // false
```

Mindkettő `falsy`, de eltérő típusú és értékű adat.

## 10. Összefoglalás

| Fogalom     | Jelentés                                                          |
| ----------- | ----------------------------------------------------------------- |
| `truthy`    | Logikai környezetben `true` értéknek számít                       |
| `falsy`     | Logikai környezetben `false` értéknek számít                      |
| `Boolean()` | Explicit logikai átalakítás                                       |
| `!!`        | Kettős tagadással történő logikai átalakítás                      |
| `\|\| `     | Az első `truthy` értéket adja vissza                              |
| `&&`        | Az első `falsy` értéket adja vissza, vagy az utolsót              |
| `??`        | Csak `null` és `undefined` esetén választ alapértelmezett értéket |
| `!`         | Logikai tagadás                                                   |

A `truthy` és `falsy` értékek megértése alapvető fontosságú a feltételek, a logikai operátorok és az adatellenőrzések helyes használatához.

# 10 ellenőrző kérdés

1\. Mit jelent a `truthy` kifejezés?

A) Csak a `true` értéket jelenti.

B) Olyan értéket, amely logikai környezetben `true` értéknek számít.

C) Olyan értéket, amely mindig szám.

D) Olyan értéket, amely üres.

2\. Melyik érték `falsy`?

A) `"0"`

B) `[]`

C) `0`

D) `{}`

3\. Milyen logikai értéket ad vissza a `Boolean("JavaScript")`?

A) `false`

B) `null`

C) `undefined`

D) `true`

4\. Melyik állítás igaz az üres tömbre (`[]`)?

A) `falsy`

B) `truthy`

C) `undefined`

D) `null`

5\. Milyen eredményt ad a `Boolean("")`?

A) `true`

B) `false`

C) `0`

D) `undefined`

6\. Melyik érték nem tartozik a `falsy` értékek közé?

A) `NaN`

B) `undefined`

C) `"false"`

D) `null`

7\. Mit eredményez a `!!0` kifejezés?

A) `true`

B) `false`

C) `0`

D) `null`

8\. Mit ad vissza a `||` operátor, ha az első operandus `falsy`?

A) Mindig `true` értéket.

B) Mindig `false` értéket.

C) A második operandust.

D) Mindig `null` értéket.

9\. Mi a különbség a `||` és a `??` között?

A) Nincs különbség közöttük.

B) A `??` minden `falsy` értéket helyettesít.

C) A `||` csak `null` esetén működik.

D) A `??` csak `null` vagy `undefined` esetén választja a második operandust.

10\. Mi lesz az alábbi kód eredménye?

```javascript
const ertek = 0;
console.log(ertek || 10);
```

A) `0`

B) `10`

C) `true`

D) `false`

# 10 gyakorlati feladat

1\. feladat – `truthy` és `falsy` értékek

Hozz létre 8 változót különböző értékekkel:

- `true`
- `false`
- `0`
- `25`
- `""`
- `"JavaScript"`
- `null`
- `undefined`

Írd ki mindegyik változó `Boolean()` segítségével átalakított értékét.

2\. feladat – Feltételvizsgálat

Hozz létre egy `nev` változót üres szöveggel.

Egy `if...else` szerkezet segítségével vizsgáld meg, hogy a változó tartalmaz-e értéket. Ha igen, írd ki a nevet, ha nem, jeleníts meg egy megfelelő üzenetet.

3\. feladat – Szám ellenőrzése

Hozz létre egy `szam` változót `0` értékkel.

Vizsgáld meg `if...else` segítségével, hogy a változó `truthy` vagy `falsy` érték-e.

Ezután módosítsd a változó értékét `15`-re, és ismételd meg az ellenőrzést.

4\. feladat – Üres tömb és objektum

Hozz létre egy üres tömböt és egy üres objektumot.

Ellenőrizd mindkettőt `if...else` segítségével.

Írd ki, hogy a JavaScript milyen logikai értéknek tekinti őket.

5\. feladat – Dupla tagadás

Hozz létre 6 különböző értéket tartalmazó változót.

Mindegyiknél használd a `!!` operátort, és írd ki az eredményeket.

6\. feladat – Alapértelmezett név `||` operátorral

Hozz létre egy `felhasznalonev` változót üres szöveggel.

A `||` operátor segítségével állíts be `"Vendég"` alapértelmezett értéket.

Próbáld ki a programot egy valódi névvel is.

7\. feladat – `||` és `??` összehasonlítása

Hozz létre három változót:

```javascript
const eletkor = 0;
const nev = '';
const pontszam = null;
```

Mindegyik változónál készíts egy-egy alapértelmezett értéket `||` és `??` használatával.

Írd ki az eredményeket, majd magyarázd meg a különbségeket.

8\. feladat – Bejelentkezés ellenőrzése

Hozz létre egy `bejelentkezett` változót `false` értékkel.

A `!` operátor segítségével ellenőrizd, hogy a felhasználó nincs-e bejelentkezve.

Ha nincs bejelentkezve, jeleníts meg egy figyelmeztető üzenetet.

9\. feladat – Több feltétel vizsgálata

Hozz létre három változót:

```javascript
const nev = 'Anna';
const email = '';
const aktiv = true;
```

A `&&` operátor segítségével vizsgáld meg, hogy mindhárom változó `truthy` érték-e.

Készíts egy másik ellenőrzést `||` operátorral is, amely azt vizsgálja, hogy legalább az egyik változó `truthy` érték-e.

10\. feladat – Adatellenőrző program

Készíts egy egyszerű adatellenőrző programot az alábbi változókkal:

```javascript
const felhasznalonev = 'Bence';
const jelszo = '';
const eletkor = 0;
const elfogadtaFelteteleket = false;
```

A program vizsgálja meg:

- Meg van-e adva a felhasználónév?
- Meg van-e adva a jelszó?
- Megfelelő-e az életkor értéke?
- Elfogadta-e a felhasználó a feltételeket?

Minden ellenőrzéshez jeleníts meg megfelelő üzenetet. Figyelj arra, hogy a `0` életkor `falsy`, de az életkor ellenőrzésénél nem feltétlenül elegendő pusztán a `truthy` vagy `falsy` vizsgálata.
