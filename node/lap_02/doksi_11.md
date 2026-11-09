# Összehasonlító operátorok JavaScriptben

## 1. Mik azok az összehasonlító operátorok?

Az összehasonlító operátorok segítségével két értéket hasonlíthatunk össze JavaScriptben. A művelet eredménye minden esetben egy logikai érték, vagyis `true` (igaz) vagy `false` (hamis).

Ezeket az operátorokat leggyakrabban feltételek megfogalmazásakor használjuk, például:

- Egy szám nagyobb-e egy másik számnál?
- Két változó értéke megegyezik-e?
- Egy felhasználó betöltötte-e a szükséges életkort?
- Egy termék ára kisebb-e egy meghatározott összegnél?

Például:

```javascript
let a = 10;
let b = 5;

console.log(a > b); // true
console.log(a < b); // false
```

Az első összehasonlítás eredménye `true`, mert a 10 nagyobb, mint az 5. A második eredménye `false`, mert a 10 nem kisebb az 5-nél.

## 2. Az összehasonlító operátorok típusai

A JavaScriptben a következő összehasonlító operátorokat használhatjuk:

| Operátor | Jelentés              | Példa       | Eredmény |
| -------- | --------------------- | ----------- | -------- |
| `==`     | Egyenlő érték         | `5 == 5`    | `true`   |
| `===`    | Szigorúan egyenlő     | `5 === 5`   | `true`   |
| `!=`     | Nem egyenlő érték     | `5 != 3`    | `true`   |
| `!==`    | Szigorúan nem egyenlő | `5 !== "5"` | `true`   |
| `>`      | Nagyobb               | `10 > 5`    | `true`   |
| `<`      | Kisebb                | `3 < 8`     | `true`   |
| `>=`     | Nagyobb vagy egyenlő  | `10 >= 10`  | `true`   |
| `<=`     | Kisebb vagy egyenlő   | `5 <= 8`    | `true`   |

## 3. Egyenlőségvizsgálat

Az egyenlőségvizsgálatnak két fontos formája van JavaScriptben: a laza és a szigorú egyenlőség.

### 3.1. Laza egyenlőség (`==`)

A `==` operátor két értéket hasonlít össze. Az összehasonlítás előtt szükség esetén automatikus típusátalakítást végez.

Példa:

```javascript
console.log(5 == 5); // true
console.log(5 == '5'); // true
console.log(10 == 5); // false
```

A második összehasonlítás eredménye azért `true`, mert a JavaScript a szövegként megadott `"5"` értéket a vizsgálat során számmá alakítja.

További példák:

```javascript
console.log(1 == true); // true
console.log(0 == false); // true
console.log(null == undefined); // true
```

A laza egyenlőség használata bizonyos helyzetekben nehezen kiszámítható eredményekhez vezethet, ezért általában érdemes kerülni.

### 3.2. Szigorú egyenlőség (`===`)

A `===` operátor nemcsak az értékeket, hanem az adattípusokat is összehasonlítja.

Ahhoz, hogy az eredmény `true` legyen, mindkét értéknek és azok típusának is meg kell egyeznie.

```javascript
console.log(5 === 5); // true
console.log(5 === '5'); // false
console.log(10 === 5); // false
```

Az első összehasonlítás eredménye `true`, mert mindkét érték szám, és az értékük is azonos.

A második eredménye `false`, mert az egyik érték szám, a másik pedig szöveg.

További példák:

```javascript
console.log(1 === true); // false
console.log(0 === false); // false
console.log('alma' === 'alma'); // true
```

Fontos: JavaScriptben a `===` használata általában ajánlott, mert elkerülhetők vele a nem kívánt automatikus típusátalakításból eredő meglepetések.

## 4. Nem egyenlőségvizsgálat

A JavaScriptben kétféle operátort használhatunk annak ellenőrzésére, hogy két érték különbözik-e egymástól.

### 4.1. Laza nem egyenlőség (`!=`)

A `!=` operátor azt vizsgálja, hogy két érték nem egyenlő-e. Az összehasonlítás előtt szükség esetén automatikus típusátalakítás történhet.

```javascript
console.log(5 != 3); // true
console.log(5 != 5); // false
console.log(5 != '5'); // false
```

Az utolsó példában az eredmény `false`, mert a JavaScript az értékeket típusátalakítás után egyenlőnek tekinti.

### 4.2. Szigorú nem egyenlőség (`!==`)

A `!==` operátor azt vizsgálja, hogy két érték vagy azok típusa különbözik-e.

```javascript
console.log(5 !== 3); // true
console.log(5 !== 5); // false
console.log(5 !== '5'); // true
```

Az utolsó példában az eredmény `true`, mert az egyik érték szám, a másik pedig szöveg.

## 5. Relációs operátorok

A relációs operátorok két érték nagyság szerinti összehasonlítására szolgálnak.

### 5.1. Nagyobb (`>`)

A `>` operátor akkor ad `true` eredményt, ha a bal oldali érték nagyobb a jobb oldalinál.

```javascript
let eletkor = 25;

console.log(eletkor > 18); // true
console.log(eletkor > 30); // false
```

### 5.2. Kisebb (`<`)

A `<` operátor akkor ad `true` eredményt, ha a bal oldali érték kisebb a jobb oldalinál.

```javascript
let pontszam = 65;

console.log(pontszam < 100); // true
console.log(pontszam < 50); // false
```

### 5.3. Nagyobb vagy egyenlő (`>=`)

A `>=` operátor akkor ad `true` eredményt, ha a bal oldali érték nagyobb a jobb oldalinál, vagy megegyezik vele.

```javascript
let eletkor = 18;

console.log(eletkor >= 18); // true
console.log(eletkor >= 21); // false
```

Ez az operátor akkor is `true` eredményt ad, ha a két érték pontosan megegyezik.

### 5.4. Kisebb vagy egyenlő (`<=`)

A `<=` operátor akkor ad `true` eredményt, ha a bal oldali érték kisebb a jobb oldalinál, vagy megegyezik vele.

```javascript
let homerseklet = 20;

console.log(homerseklet <= 25); // true
console.log(homerseklet <= 20); // true
console.log(homerseklet <= 15); // false
```

## 6. Szövegek összehasonlítása

Az összehasonlító operátorok nemcsak számok, hanem szövegek esetén is használhatók.

A JavaScript a szövegeket lexikografikus sorrendben hasonlítja össze. Ez alapvetően a karakterek Unicode-kódpontjai alapján történik, balról jobbra haladva.

Például:

```javascript
console.log('alma' === 'alma'); // true
console.log('alma' === 'körte'); // false
```

A nagyobb és kisebb operátorokkal sorrendet is vizsgálhatunk:

```javascript
console.log('alma' < 'körte'); // true
console.log('zebra' > 'alma'); // true
```

A szövegek összehasonlításakor fontos figyelembe venni, hogy a kis- és nagybetűk eltérő karakterek.

```javascript
console.log('alma' === 'Alma'); // false
console.log('A' === 'a'); // false
```

Fontos: a szövegek sorrend szerinti összehasonlítása nem feltétlenül követi a magyar ábécé szerinti rendezést. Ha nyelvhelyes rendezésre van szükség, használható az `Intl.Collator` objektum.

```javascript
const rendezo = new Intl.Collator('hu');

console.log(rendezo.compare('alma', 'körte') < 0); // true
```

## 7. Összehasonlító operátorok használata feltételekben

Az összehasonlító operátorokat gyakran az `if` szerkezettel együtt használjuk.

Az `if` segítségével a program egy feltétel teljesülése esetén végrehajthat bizonyos utasításokat.

Példa:

```javascript
let eletkor = 20;

if (eletkor >= 18) {
    console.log('A felhasználó nagykorú.');
}
```

A program megvizsgálja, hogy az `eletkor` értéke legalább 18-e.

Ha a feltétel eredménye `true`, akkor végrehajtja a kapcsos zárójelek között található utasításokat.

### 7.1. Két lehetséges ág (`if...else`)

Az `else` segítségével akkor is megadhatunk végrehajtandó utasítást, ha a feltétel nem teljesül.

```javascript
let pontszam = 45;

if (pontszam >= 50) {
    console.log('Sikeres teljesítés.');
} else {
    console.log('Sikertelen teljesítés.');
}
```

### 7.2. Több feltétel vizsgálata (`else if`)

Ha több különböző esetet szeretnénk kezelni, használhatjuk az `else if` szerkezetet.

```javascript
let pontszam = 85;

if (pontszam >= 90) {
    console.log('Jeles eredmény.');
} else if (pontszam >= 70) {
    console.log('Jó eredmény.');
} else if (pontszam >= 50) {
    console.log('Megfelelő eredmény.');
} else {
    console.log('Elégtelen eredmény.');
}
```

A program felülről lefelé vizsgálja a feltételeket. Az első igaz feltételhez tartozó kód fut le, a többi ágat már nem vizsgálja tovább.

## 8. Több összehasonlítás együttes használata

Gyakran nem elegendő egyetlen feltételt megvizsgálni. Ilyenkor több összehasonlító kifejezést is használhatunk.

Például ellenőrizhetjük, hogy egy szám egy adott tartományba esik-e.

```javascript
let eletkor = 25;

if (eletkor >= 18 && eletkor <= 65) {
    console.log('Az életkor a megadott tartományban van.');
}
```

Ebben a példában a program azt vizsgálja, hogy az életkor legalább 18 és legfeljebb 65 éves-e.

A `&&` logikai ÉS operátor azt jelenti, hogy mindkét feltételnek igaznak kell lennie.

Másik példa:

```javascript
let nap = 'szombat';

if (nap === 'szombat' || nap === 'vasárnap') {
    console.log('Hétvége van.');
}
```

A `||` logikai VAGY operátor esetén elegendő, ha legalább az egyik feltétel igaz.

A logikai operátorok részletesebb tárgyalása egy külön témakör része.

## 9. Összetett példák

### 9.1. Életkor ellenőrzése

```javascript
let eletkor = 17;

if (eletkor >= 18) {
    console.log('Belépés engedélyezve.');
} else {
    console.log('Belépés megtagadva.');
}
```

### 9.2. Két szám összehasonlítása

```javascript
let a = 25;
let b = 30;

if (a > b) {
    console.log('Az első szám nagyobb.');
} else if (a < b) {
    console.log('A második szám nagyobb.');
} else {
    console.log('A két szám egyenlő.');
}
```

### 9.3. Jelszó hosszának ellenőrzése

```javascript
let jelszo = 'javascript123';

if (jelszo.length >= 8) {
    console.log('A jelszó megfelelő hosszúságú.');
} else {
    console.log('A jelszó túl rövid.');
}
```

A `length` tulajdonság a szöveg hosszát adja vissza.

### 9.4. Kedvezmény vizsgálata

```javascript
let vasarlasOsszege = 25000;

if (vasarlasOsszege >= 20000) {
    console.log('A vásárló kedvezményre jogosult.');
} else {
    console.log('A vásárló nem jogosult kedvezményre.');
}
```

## 10. Gyakori hibák az összehasonlító operátorok használatakor

### 10.1. Az `=` és az `==` összekeverése

A `=` értékadásra szolgál, míg a `==` összehasonlítást végez.

```javascript
let szam = 10; // Értékadás

console.log(szam == 10); // Összehasonlítás
```

A két operátor eltérő feladatot lát el.

### 10.2. A `==` és a `===` összekeverése

```javascript
console.log(10 == '10'); // true
console.log(10 === '10'); // false
```

A `==` automatikus típusátalakítást végezhet, a `===` viszont az adattípust is figyelembe veszi.

### 10.3. A nagyobb és kisebb operátorok felcserélése

```javascript
let eletkor = 16;

console.log(eletkor >= 18); // false
console.log(eletkor <= 18); // true
```

A két kifejezés eltérő feltételt vizsgál.

### 10.4. A tartományellenőrzés hibás megfogalmazása

JavaScriptben az alábbi kifejezés nem a matematikában megszokott módon működik:

```javascript
let szam = 15;

console.log(10 <= szam <= 20);
```

Ez nem azt jelenti, hogy a szám 10 és 20 között van. A JavaScript balról jobbra kiértékeli a két összehasonlítást.

A helyes megoldás:

```javascript
let szam = 15;

console.log(szam >= 10 && szam <= 20); // true
```

### 10.5. A kis- és nagybetűk figyelmen kívül hagyása

```javascript
let nev = 'Péter';

console.log(nev === 'péter'); // false
```

A két szöveg nem teljesen azonos, mert az első karakterük eltérő kis- és nagybetű.

# 11. Ellenőrző kérdések

1. Mire szolgálnak az összehasonlító operátorok JavaScriptben?
2. Milyen értékeket adhat vissza egy összehasonlító művelet?
3. Mi a különbség a `==` és a `===` operátor között?
4. Mi a különbség a `!=` és a `!==` operátor között?
5. Mit jelent a `>=` és a `<=` operátor?
6. Hogyan hasonlítja össze a JavaScript a szöveges értékeket?
7. Mi történik, ha egy `if` feltétel eredménye `true`?
8. Mire használjuk az `else if` szerkezetet?
9. Hogyan ellenőrizhető, hogy egy szám két érték közé esik-e?
10. Mi a különbség az értékadást végző `=` és az összehasonlítást végző `==` operátor között?

# 12. Gyakorlati feladatok

1\. feladat – Két szám összehasonlítása

Hozz létre két változót, amelyek különböző egész számokat tárolnak. Hasonlítsd össze őket a `>`, `<` és `===` operátorokkal. Az eredményeket jelenítsd meg a konzolon.

2\. feladat – Egyenlőségvizsgálat

Hozz létre egy számot és egy szöveget tároló változót. Vizsgáld meg a két értéket a `==` és a `===` operátorokkal. Figyeld meg az eredmények közötti különbséget.

3\. feladat – Páros vagy páratlan szám

Hozz létre egy változót, amely egy egész számot tárol. A maradékképző operátor és egy összehasonlító operátor segítségével döntsd el, hogy a szám páros vagy páratlan.

4\. feladat – Életkor ellenőrzése

Kérj be egy életkort a felhasználótól. Vizsgáld meg, hogy a felhasználó betöltötte-e a 18. életévét. Az eredménynek megfelelően jeleníts meg üzenetet.

5\. feladat – Két szám közül a nagyobb

Kérj be két számot a felhasználótól. Hasonlítsd össze őket, majd jelenítsd meg, hogy melyik a nagyobb. Ha egyenlők, azt is jelezd.

6\. feladat – Osztályzat meghatározása

Hozz létre egy változót, amely egy 0 és 100 közötti pontszámot tárol. Az `if...else if...else` szerkezet segítségével határozd meg az eredményhez tartozó osztályzatot:

- 0–49 pont: elégtelen;
- 50–64 pont: elégséges;
- 65–79 pont: közepes;
- 80–89 pont: jó;
- 90–100 pont: jeles.

7\. feladat – Tartományellenőrzés

Kérj be egy számot a felhasználótól. Ellenőrizd, hogy a szám 10 és 50 közé esik-e. A határértékeket is fogadd el.

8\. feladat – Jelszó ellenőrzése

Hozz létre egy változót, amely egy jelszót tárol. Vizsgáld meg, hogy a jelszó legalább 8 karakter hosszú-e. Jeleníts meg megfelelő üzenetet.

9\. feladat – Kedvezmény ellenőrzése

Hozz létre egy változót, amely egy vásárlás összegét tárolja. Ha az összeg eléri a 20 000 Ft-ot, a vásárló 10% kedvezményt kapjon. Számítsd ki és jelenítsd meg a fizetendő összeget.

10\. feladat – Belépési feltételek ellenőrzése

Hozz létre két változót: az egyik tárolja a felhasználó életkorát, a másik azt, hogy rendelkezik-e érvényes belépővel (`true` vagy `false`). A `&&` és az összehasonlító operátorok segítségével ellenőrizd, hogy a felhasználó beléphet-e. A belépés feltétele, hogy legalább 18 éves legyen, és rendelkezzen érvényes belépővel.
