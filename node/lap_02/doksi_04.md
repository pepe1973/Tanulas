# Primitív adattípusok JavaScriptben

## 1. Mik azok az adattípusok?

A programozás során különböző adatokat tárolunk és dolgozunk fel. Ezek az adatok eltérő jellegűek lehetnek: számok, szövegek, logikai értékek vagy akár olyan speciális értékek, amelyek egy változó állapotát jelzik.

Az adattípus meghatározza, hogy egy érték milyen jellegű adatot képvisel, és milyen műveleteket végezhetünk vele.

JavaScriptben az adattípusokat két nagy csoportra oszthatjuk:

1. Primitív adattípusok
2. Összetett adattípusok

A primitív adattípusok egyszerű, önálló értékeket jelentenek. Nem objektumok, és közvetlenül egyetlen értéket képviselnek.

A JavaScript hét primitív adattípust különböztet meg:

| Adattípus   | Jelentése               | Példa                   |
| ----------- | ----------------------- | ----------------------- |
| `string`    | Szöveg                  | `"JavaScript"`          |
| `number`    | Szám                    | `25`, `3.14`            |
| `bigint`    | Nagy egész szám         | `12345678901234567890n` |
| `boolean`   | Logikai érték           | `true`, `false`         |
| `undefined` | Nem meghatározott érték | `undefined`             |
| `null`      | Szándékosan üres érték  | `null`                  |
| `symbol`    | Egyedi azonosító        | `Symbol("id")`          |

A következőkben részletesen megismerjük ezeket.

## 2. String – szöveges adattípus

A `string` adattípus szöveges adatok tárolására szolgál.

Ide tartoznak például:

- nevek;
- címek;
- települések;
- üzenetek;
- e-mail-címek;
- különböző szöveges azonosítók.

A szöveges értékeket idézőjelek közé kell írni.

JavaScriptben háromféle idézőjelet használhatunk:

- egyszeres idézőjel: `'...'`;
- dupla idézőjel: `"..."`;
- backtick, vagyis sablonliterál: `` `...` ``.

Példa:

```javascript
let nev = 'Kovács Anna';
let varos = 'Szeged';
let nyelv = `JavaScript`;

console.log(nev);
console.log(varos);
console.log(nyelv);
```

### 2.1. Szövegek összefűzése

A szöveges értékeket a `+` operátor segítségével összefűzhetjük.

```javascript
let vezetekNev = 'Kovács';
let keresztNev = 'Anna';

let teljesNev = vezetekNev + ' ' + keresztNev;

console.log(teljesNev);
```

Eredmény:

```
Kovács Anna
```

A `+` operátor ebben az esetben nem összeadást, hanem szövegösszefűzést végez.

### 2.2. Sablonliterálok

A backtick karakterrel létrehozott sablonliterálok lehetővé teszik, hogy változókat helyezzünk el egy szövegen belül.

A változókat `${}` közé kell írni.

```javascript
let nev = 'Anna';
let kor = 25;

let bemutatkozas = `A nevem ${nev}, és ${kor} éves vagyok.`;

console.log(bemutatkozas);
```

Eredmény:

```
A nevem Anna, és 25 éves vagyok.
```

A sablonliterálok különösen hasznosak összetettebb szövegek előállításakor.

### 2.3. A string hossza

A `length` tulajdonsággal meghatározhatjuk egy szöveg hosszát.

```javascript
let szoveg = 'JavaScript';

console.log(szoveg.length);
```

Eredmény:

```
10
```

### 2.4. Egyéb gyakori szövegkezelő műveletek

```javascript
let szoveg = 'JavaScript programozás';

console.log(szoveg.toUpperCase());
console.log(szoveg.toLowerCase());
console.log(szoveg.includes('programozás'));
console.log(szoveg.startsWith('Java'));
```

Eredmény:

```
JAVASCRIPT PROGRAMOZÁS
javascript programozás
true
true
```

Fontos, hogy a `string` értékek megváltoztathatatlanok (immutable). A szövegkezelő műveletek nem módosítják az eredeti szöveget, hanem új szöveges értéket adnak vissza.

## 3. Number – szám típus

A `number` adattípus egész és tizedes számok tárolására szolgál.

JavaScriptben nem külön adattípus az egész szám és a lebegőpontos szám. Mindkettő a `number` típusba tartozik.

Példák:

```javascript
let egeszSzam = 25;
let negativSzam = -10;
let tizedesSzam = 3.14;
let nulla = 0;

console.log(typeof egeszSzam);
console.log(typeof tizedesSzam);
```

Eredmény:

```
number
number
```

### 3.1. Matematikai műveletek

A `number` típusú értékekkel a szokásos matematikai műveleteket végezhetjük.

| Operátor | Művelet          | Példa    |
| -------- | ---------------- | -------- |
| `+`      | Összeadás        | `10 + 5` |
| `-`      | Kivonás          | `10 - 5` |
| `*`      | Szorzás          | `10 * 5` |
| `/`      | Osztás           | `10 / 5` |
| `%`      | Maradékos osztás | `10 % 3` |
| `**`     | Hatványozás      | `2 ** 3` |

Példa:

```javascript
let a = 10;
let b = 3;

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(a / b);
console.log(a % b);
console.log(a ** b);
```

Eredmény:

```
13
7
30
3.3333333333333335
1
1000
```

### 3.2. Speciális Number értékek

A `number` adattípushoz néhány speciális érték is tartozik.

NaN

A `NaN` jelentése: Not a Number. Olyan számítási eredményt jelöl, amely nem értelmezhető érvényes számként.

```javascript
let eredmeny = 'alma' / 2;

console.log(eredmeny);
console.log(Number.isNaN(eredmeny));
```

Eredmény:

```
NaN
true
```

Infinity és -Infinity

A `Infinity` pozitív, a `-Infinity` negatív végtelent jelöl.

```javascript
console.log(1 / 0);
console.log(-1 / 0);
```

Eredmény:

```
Infinity
-Infinity
```

### 3.3. Számok ellenőrzése

A `Number.isInteger()` segítségével ellenőrizhetjük, hogy egy érték egész szám-e.

```javascript
let szam1 = 10;
let szam2 = 10.5;

console.log(Number.isInteger(szam1));
console.log(Number.isInteger(szam2));
```

Eredmény:

```
true
false
```

A `Number.isFinite()` segítségével megvizsgálhatjuk, hogy egy érték véges szám-e.

```javascript
console.log(Number.isFinite(100));
console.log(Number.isFinite(Infinity));
```

Eredmény:

```
true
false
```

## 4. BigInt – nagy egész számok

A `bigint` adattípus olyan egész számok tárolására szolgál, amelyek túl nagyok lehetnek a `number` típus biztonságosan kezelhető egész számtartományához képest.

A JavaScript `number` típusának legnagyobb biztonságos egész száma:

```javascript
console.log(Number.MAX_SAFE_INTEGER);
```

Eredmény:

```
9007199254740991
```

Ha ennél nagyobb egész számokkal szeretnénk pontosan dolgozni, használhatjuk a `bigint` típust.

### 4.1. BigInt létrehozása

A BigInt értékeket kétféleképpen hozhatjuk létre.

Az első módszer az `n` karakter használata a szám végén:

```javascript
let nagySzam = 12345678901234567890n;

console.log(nagySzam);
console.log(typeof nagySzam);
```

Eredmény:

```
12345678901234567890n
bigint
```

A másik lehetőség a `BigInt()` függvény használata:

```javascript
let nagySzam = BigInt('12345678901234567890');

console.log(nagySzam);
```

### 4.2. BigInt műveletek

A BigInt értékekkel egész számokon végezhető matematikai műveleteket használhatunk.

```javascript
let a = 10000000000000000n;
let b = 20000000000000000n;

console.log(a + b);
console.log(a * b);
```

Eredmény:

```
30000000000000000n
200000000000000000000000000000000n
```

Fontos: a `number` és a `bigint` típusú értékeket nem lehet közvetlenül összeadni vagy más közös matematikai műveletben felhasználni.

Hibás példa:

```javascript
let szam = 10;
let nagySzam = 20n;

console.log(szam + nagySzam);
```

Ez `TypeError` hibát eredményez.

Ha szükséges, az egyik értéket át kell alakítani a másik típusra, figyelembe véve az esetleges pontosságvesztést.

## 5. Boolean – logikai adattípus

A `boolean` adattípus két lehetséges értéket vehet fel:

- `true` – igaz;
- `false` – hamis.

A logikai értékeket elsősorban feltételek, döntések és ellenőrzések során használjuk.

Példa:

```javascript
let aktiv = true;
let torolt = false;

console.log(aktiv);
console.log(torolt);
```

### 5.1. Összehasonlítások eredménye

A logikai értékeket gyakran összehasonlító operátorok eredményeként kapjuk.

```javascript
let kor = 20;

console.log(kor > 18);
console.log(kor < 18);
console.log(kor === 20);
console.log(kor !== 20);
```

Eredmény:

```
true
false
true
false
```

### 5.2. Logikai operátorok

A logikai operátorokkal több feltételt kapcsolhatunk össze.

| Operátor | Jelentés        | Példa             |
| -------- | --------------- | ----------------- |
| `&&`     | Logikai ÉS      | `true && false`   |
| `\|\| `  | Logikai VAGY    | `true \|\| false` |
| `!`      | Logikai tagadás | `!true`           |

Példa:

```javascript
let kor = 25;
let vanJogositvany = true;

let vezethet = kor >= 18 && vanJogositvany;

console.log(vezethet);
```

Eredmény:

```
true
```

### 5.3. Truthy és falsy értékek

JavaScriptben nemcsak a `true` és `false` értékek használhatók feltételekben. Más adattípusok értékei is átalakíthatók logikai értékké.

A truthy értékek igaznak tekinthetők, a falsy értékek pedig hamisnak.

A legfontosabb falsy értékek:

- `false`
- `0`
- `-0`
- `0n`
- `""` (üres szöveg)
- `null`
- `undefined`
- `NaN`

Példa:

```javascript
let nev = '';

if (nev) {
    console.log('Van megadott név.');
} else {
    console.log('A név üres.');
}
```

Eredmény:

```
A név üres.
```

A truthy és falsy értékek megértése különösen fontos a feltételes utasítások és az adatellenőrzések során.

## 6. Undefined – nem meghatározott érték

Az `undefined` egy speciális primitív adattípus, amely azt jelzi, hogy egy érték nincs meghatározva.

Leggyakrabban akkor találkozunk vele, amikor egy változót deklarálunk, de nem rendelünk hozzá értéket.

```javascript
let nev;

console.log(nev);
console.log(typeof nev);
```

Eredmény:

```
undefined
undefined
```

A `typeof` operátor eredménye is `"undefined"` szöveg.

### 6.1. Undefined függvényeknél

Ha egy függvény nem ad vissza kifejezetten értéket a `return` segítségével, akkor a visszatérési értéke `undefined`.

```javascript
function koszones() {
    console.log('Szia!');
}

let eredmeny = koszones();

console.log(eredmeny);
```

Eredmény:

```
Szia!
undefined
```

### 6.2. Hiányzó objektumtulajdonság

Ha egy objektum nem létező tulajdonságát próbáljuk lekérdezni, általában `undefined` értéket kapunk.

```javascript
let felhasznalo = {
    nev: 'Anna',
    kor: 25,
};

console.log(felhasznalo.nev);
console.log(felhasznalo.email);
```

Eredmény:

```
Anna
undefined
```

## 7. Null – szándékosan üres érték

A `null` olyan primitív érték, amellyel kifejezetten azt jelezzük, hogy egy változóhoz jelenleg nem tartozik érték.

Példa:

```javascript
let kivalasztottFelhasznalo = null;

console.log(kivalasztottFelhasznalo);
```

Eredmény:

```
null
```

A `null` és az `undefined` közötti különbség:

| `undefined`                              | `null`                                         |
| ---------------------------------------- | ---------------------------------------------- |
| Az érték nincs meghatározva.             | Az üres értéket szándékosan állítottuk be.     |
| Gyakran automatikusan jelenik meg.       | Általában a programozó rendeli hozzá.          |
| Például inicializálatlan változó esetén. | Például még ki nem választott objektum esetén. |

### 7.1. A typeof különlegessége

A `typeof` operátor a `null` értékre `"object"` eredményt ad.

```javascript
let adat = null;

console.log(typeof adat);
```

Eredmény:

```
object
```

Ez a JavaScript egyik történelmi sajátossága, nem jelenti azt, hogy a `null` valójában objektum lenne. A `null` továbbra is primitív adattípus.

Ha kifejezetten azt szeretnénk ellenőrizni, hogy egy érték `null`-e, használjunk szigorú összehasonlítást:

```javascript
let adat = null;

console.log(adat === null);
```

Eredmény:

```
true
```

## 8. Symbol – egyedi azonosító

A `symbol` adattípus egyedi és megváltoztathatatlan azonosítók létrehozására szolgál.

A Symbol értékeket a `Symbol()` függvénnyel hozzuk létre.

```javascript
let elso = Symbol();
let masodik = Symbol();

console.log(elso === masodik);
```

Eredmény:

```
false
```

A két Symbol különböző érték, még akkor is, ha ugyanazt a leírást adjuk meg nekik.

```javascript
let elso = Symbol('azonosito');
let masodik = Symbol('azonosito');

console.log(elso === masodik);
```

Eredmény:

```
false
```

### 8.1. Symbol használata objektumokban

A Symbol egyik felhasználási területe az objektumok egyedi tulajdonságainak létrehozása.

```javascript
let azonosito = Symbol('id');

let felhasznalo = {
    nev: 'Anna',
    [azonosito]: 123,
};

console.log(felhasznalo.nev);
console.log(felhasznalo[azonosito]);
```

Eredmény:

```
Anna
123
```

A Symbol tulajdonságok különösen hasznosak lehetnek akkor, amikor el szeretnénk kerülni, hogy az objektum tulajdonságnevei véletlenül ütközzenek egymással.

## 9. A primitív adattípusok ellenőrzése a typeof operátorral

A `typeof` operátor segítségével megvizsgálhatjuk egy érték adattípusát.

Példa:

```javascript
let nev = 'Anna';
let kor = 25;
let aktiv = true;
let adat;
let ures = null;
let nagySzam = 12345678901234567890n;
let azonosito = Symbol('id');

console.log(typeof nev);
console.log(typeof kor);
console.log(typeof aktiv);
console.log(typeof adat);
console.log(typeof ures);
console.log(typeof nagySzam);
console.log(typeof azonosito);
```

Eredmény:

```
string
number
boolean
undefined
object
bigint
symbol
```

A `typeof null` eredménye `"object"`, ami a JavaScript történelmi sajátossága.

### A typeof eredményeinek összefoglalása

| Érték          | `typeof` eredménye |
| -------------- | ------------------ |
| `"JavaScript"` | `"string"`         |
| `25`           | `"number"`         |
| `true`         | `"boolean"`        |
| `undefined`    | `"undefined"`      |
| `null`         | `"object"`         |
| `123n`         | `"bigint"`         |
| `Symbol("id")` | `"symbol"`         |

## 10. Primitív értékek megváltoztathatatlansága

A primitív értékek egyik fontos tulajdonsága, hogy megváltoztathatatlanok (immutable).

Ez azt jelenti, hogy maga a primitív érték nem módosítható. Ha egy változóhoz új értéket rendelünk, akkor a változó már az új értéket tárolja.

Példa:

```javascript
let szoveg = 'Hello';

szoveg.toUpperCase();

console.log(szoveg);
```

Eredmény:

```
Hello
```

A `toUpperCase()` nem módosította az eredeti szöveget, hanem egy új szöveges értéket adott vissza.

Ha az eredményt meg szeretnénk őrizni, újra értéket kell adnunk a változónak:

```javascript
let szoveg = 'Hello';

szoveg = szoveg.toUpperCase();

console.log(szoveg);
```

Eredmény:

```
HELLO
```

Ez a viselkedés a többi primitív adattípusra is jellemző.

## 11. Primitív és összetett adattípusok közötti különbség

A JavaScriptben a primitív adattípusok mellett összetett adattípusokat is használunk.

Az összetett adattípusok több értéket vagy tulajdonságot foghatnak össze.

Példák:

- objektum (`object`);
- tömb (`Array`);
- függvény (`Function`);
- dátum (`Date`);
- térkép (`Map`);
- halmaz (`Set`).

Példa primitív értékre:

```javascript
let nev = 'Anna';
```

Példa összetett értékre:

```
let felhasznalo = {
    nev: "Anna",
    kor: 25,
    aktiv: true
};
```

A két kategória közötti egyik fontos különbség az értékek kezelése.

Primitív értékek esetén az érték másolódik:

```javascript
let a = 10;
let b = a;

b = 20;

console.log(a);
console.log(b);
```

Eredmény:

```
10
20
```

Objektumok esetén a változók ugyanarra az objektumra hivatkozhatnak:

```javascript
let elso = {
    nev: 'Anna',
};

let masodik = elso;

masodik.nev = 'Péter';

console.log(elso.nev);
console.log(masodik.nev);
```

Eredmény:

```
Péter
Péter
```

Ez a különbség fontos a változók másolásának, az objektumok kezelésének és a függvényeknek a megértéséhez.

# 12. Összefoglalás

A JavaScript hét primitív adattípussal rendelkezik:

| Adattípus   | Felhasználási terület   | Példa                   |
| ----------- | ----------------------- | ----------------------- |
| `string`    | Szövegek tárolása       | `"Szia"`                |
| `number`    | Egész és tizedes számok | `25`, `3.14`            |
| `bigint`    | Nagy egész számok       | `12345678901234567890n` |
| `boolean`   | Logikai értékek         | `true`, `false`         |
| `undefined` | Nem meghatározott érték | `undefined`             |
| `null`      | Szándékosan üres érték  | `null`                  |
| `symbol`    | Egyedi azonosítók       | `Symbol("id")`          |

A legfontosabb tudnivalók:

- A primitív adattípusok egyszerű, önálló értékeket képviselnek.
- A `string` szövegek, a `number` számok tárolására szolgál.
- A `bigint` nagy egész számok pontos kezelését teszi lehetővé.
- A `boolean` két értéke a `true` és a `false`.
- Az `undefined` és a `null` nem ugyanazt jelentik.
- A `symbol` egyedi azonosítók létrehozására alkalmas.
- A `typeof` operátorral megvizsgálhatjuk az értékek típusát.
- A primitív értékek megváltoztathatatlanok.

# 13. Ellenőrző kérdések

1. Mit nevezünk primitív adattípusnak JavaScriptben?
2. Hány primitív adattípust különböztetünk meg JavaScriptben, és melyek ezek?
3. Milyen értékeket tárolhatunk a `string` adattípussal?
4. Mi a különbség a `number` és a `bigint` között?
5. Milyen két értéket vehet fel a `boolean` adattípus?
6. Mi a különbség az `undefined` és a `null` között?
7. Mire használható a `Symbol()` függvény?
8. Milyen célt szolgál a `typeof` operátor?
9. Miért adja vissza a `typeof null` az `"object"` értéket?
10. Mit jelent az, hogy a primitív értékek megváltoztathatatlanok?

# 14. Gyakorlati feladatok

A feladatokat JavaScriptben oldd meg! A megoldások során használj változódeklarálást, inicializálást, értékadást és szükség esetén típusellenőrzést. A feladatokhoz nem tartozik megoldás.

1\. feladat – String adattípus

Hozz létre három szöveges változót:

- `vezetekNev`
- `keresztNev`
- `varos`

Rendelj hozzájuk tetszőleges értékeket!

Ezután:

- Jelenítsd meg a teljes nevet egyetlen szövegként!
- Jelenítsd meg a lakóhelyet egy mondatban!
- Írd ki a teljes név karaktereinek számát!

2\. feladat – Szövegkezelés

Hozz létre egy `mondat` nevű változót a következő értékkel:

`A JavaScript egy programozási nyelv.`

Végezd el az alábbi műveleteket:

- Jelenítsd meg nagybetűkkel!
- Jelenítsd meg kisbetűkkel!
- Ellenőrizd, hogy tartalmazza-e a `JavaScript` szót!
- Ellenőrizd, hogy a `A JavaScript` szöveggel kezdődik-e!

3\. feladat – Number adattípus

Hozz létre két szám típusú változót `a` és `b` néven!

Végezd el és jelenítsd meg:

- az összeadás eredményét;
- a kivonás eredményét;
- a szorzás eredményét;
- az osztás eredményét;
- a maradékos osztás eredményét;
- az első szám négyzetét!

4\. feladat – Speciális számértékek

Hozz létre olyan változókat, amelyek segítségével előállítod a következő értékeket:

- `NaN`
- `Infinity`
- `-Infinity`

Jelenítsd meg az értékeket, majd vizsgáld meg a típusukat a `typeof` operátorral!

5\. feladat – BigInt adattípus

Hozz létre két nagy egész számot `bigint` adattípussal!

Ezután:

- Add össze őket!
- Szorozd össze őket!
- Vond ki az egyikből a másikat!
- Jelenítsd meg az eredményeket!
- Ellenőrizd az eredmények adattípusát!

6\. feladat – Boolean adattípus

Hozz létre két logikai változót:

- `aktiv`
- `engedelyezett`

Ezután:

- Vizsgáld meg, hogy mindkét változó értéke `true`-e!
- Vizsgáld meg, hogy legalább az egyik változó értéke `true`-e!
- Jelenítsd meg az `aktiv` változó ellentettjét!

A műveletekhez használd a `&&`, `||` és `!` operátorokat!

7\. feladat – Truthy és falsy értékek

Hozz létre egy-egy változót a következő értékekkel:

- `0`
- `""`
- `null`
- `undefined`
- `false`
- `"JavaScript"`
- `100`

Vizsgáld meg mindegyik értéket egy-egy `if...else` utasítással!

Jelenítsd meg, hogy az adott érték truthy vagy falsy.

8\. feladat – Undefined és null

Hozz létre három változót:

- `elso` – deklaráld, de ne inicializáld;
- `masodik` – inicializáld `null` értékkel;
- `harmadik` – inicializáld egy tetszőleges szöveggel.

Jelenítsd meg az értékeiket és az adattípusaikat!

Ezután ellenőrizd, hogy az első két változó értéke `undefined`, illetve `null`-e.

9\. feladat – Symbol adattípus

Hozz létre két Symbol értéket ugyanazzal a leírással:

```javascript
Symbol('azonosito');
```

Ezután:

- Hasonlítsd össze a két Symbol értéket!
- Jelenítsd meg az összehasonlítás eredményét!
- Ellenőrizd a típusukat a `typeof` operátorral!

10\. feladat – Primitív adattípusok összefoglaló vizsgálata

Hozz létre hét változót, amelyek mindegyike a JavaScript egy-egy primitív adattípusát képviseli!

A változók értékei legyenek tetszőlegesek, de feleljenek meg az adott típusnak.

Ezután:

- Jelenítsd meg az összes változó értékét!
- Jelenítsd meg az összes változó adattípusát a `typeof` operátorral!
- Külön ellenőrizd a `null` típusát!
- Készíts egy rövid szöveges összefoglalót arról, hogy melyik adattípust mire használjuk!
