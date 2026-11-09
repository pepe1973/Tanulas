# Értékadó operátorok JavaScriptben

## 1. Mik azok az értékadó operátorok?

Az értékadó operátorok segítségével értékeket rendelhetünk a változókhoz, illetve módosíthatjuk a változókban tárolt értékeket.

A legegyszerűbb értékadó operátor az `=`, amely egy értéket rendel egy változóhoz.

Példa:

```javascript
let szam = 10;

console.log(szam); // 10
```

A példában a `10` értéket hozzárendeljük a `szam` nevű változóhoz.

Az értékadó operátorok segítségével azonban nemcsak új értéket adhatunk egy változónak, hanem a korábbi értékéből kiindulva matematikai műveleteket is végezhetünk.

Például:

```javascript
let szam = 10;

szam = szam + 5;

console.log(szam); // 15
```

A JavaScript ezt egyszerűbben is lehetővé teszi:

```javascript
let szam = 10;

szam += 5;

console.log(szam); // 15
```

Az értékadó operátorokat gyakran használjuk számlálók, összesítések, árak, mennyiségek és egyéb változó adatok módosításakor.

## 2. Egyszerű értékadás (`=`)

Az `=` operátor egy értéket rendel a bal oldalán szereplő változóhoz.

```javascript
let nev = 'Péter';
let eletkor = 25;
let aktiv = true;

console.log(nev);
console.log(eletkor);
console.log(aktiv);
```

Az értékadás jobb oldalán szerepelhet:

- konkrét érték;
- egy másik változó;
- matematikai kifejezés;
- függvény visszatérési értéke.

Példák:

```javascript
let a = 10;

let b = a;

let c = 5 + 3;

let d = Math.max(10, 20);

console.log(a); // 10
console.log(b); // 10
console.log(c); // 8
console.log(d); // 20
```

### 2.1. Egy változó értékének felülírása

Ha egy változónak új értéket adunk, akkor a korábban tárolt érték helyére az új érték kerül.

```javascript
let pontszam = 50;

console.log(pontszam); // 50

pontszam = 80;

console.log(pontszam); // 80
```

Fontos, hogy a változónak történő új értékadás nem jelent új változódeklarációt. Ezért nem kell újra használni a `let` kulcsszót.

## 3. Összetett értékadó operátorok

Az összetett értékadó operátorok egy matematikai műveletet és egy értékadást kapcsolnak össze.

Segítségükkel rövidebben írhatjuk le azokat a műveleteket, amelyek során egy változó aktuális értékét módosítjuk.

Például:

```javascript
let szam = 10;

szam += 5;
```

Ez ugyanazt jelenti, mint:

```javascript
let szam = 10;

szam = szam + 5;
```

A JavaScript többféle összetett értékadó operátort biztosít.

| Operátor | Jelentés                   | Hosszabb forma |
| -------- | -------------------------- | -------------- |
| `+=`     | Összeadás és értékadás     | `a = a + b`    |
| `-=`     | Kivonás és értékadás       | `a = a - b`    |
| `*=`     | Szorzás és értékadás       | `a = a * b`    |
| `/=`     | Osztás és értékadás        | `a = a / b`    |
| `%=`     | Maradékképzés és értékadás | `a = a % b`    |
| `**=`    | Hatványozás és értékadás   | `a = a ** b`   |

## 4. Összeadás és értékadás (`+=`)

A `+=` operátor hozzáad egy értéket a változó aktuális értékéhez, majd az eredményt visszaírja ugyanabba a változóba.

Példa:

```javascript
let szam = 10;

szam += 5;

console.log(szam); // 15
```

A művelet lépései:

1. A változó eredeti értéke 10.
2. Ehhez hozzáadjuk az 5-öt.
3. Az eredmény 15.
4. A változó új értéke 15 lesz.

Több egymást követő értékadás is lehetséges:

```javascript
let osszeg = 100;

osszeg += 20;
osszeg += 30;
osszeg += 50;

console.log(osszeg); // 200
```

### 4.1. Szövegek összefűzése a `+=` operátorral

A `+=` operátor szövegek összefűzésére is használható.

```javascript
let uzenet = 'Jó';

uzenet += ' reggelt!';

console.log(uzenet); // Jó reggelt!
```

A `+=` tehát nem kizárólag matematikai összeadásra alkalmas. A működése a változóban tárolt érték típusától is függ.

## 5. Kivonás és értékadás (`-=`)

A `-=` operátor kivon egy értéket a változó aktuális értékéből, majd az eredményt visszaírja a változóba.

```javascript
let egyenleg = 50000;

egyenleg -= 12000;

console.log(egyenleg); // 38000
```

A példában egy bankszámla egyenlegét módosítjuk egy levonás után.

További példa:

```javascript
let keszlet = 100;

keszlet -= 5;
keszlet -= 10;
keszlet -= 15;

console.log(keszlet); // 70
```

A készlet értéke minden kivonás után csökken.

## 6. Szorzás és értékadás (`*=`)

A `*=` operátor megszorozza a változó aktuális értékét egy másik értékkel, majd az eredményt visszaírja.

```javascript
let ar = 1000;

ar *= 2;

console.log(ar); // 2000
```

A művelet ugyanaz, mint:

```javascript
let ar = 1000;

ar = ar * 2;

console.log(ar); // 2000
```

Példa egy mennyiség többszörözésére:

```javascript
let termekDarab = 5;

termekDarab *= 3;

console.log(termekDarab); // 15
```

## 7. Osztás és értékadás (`/=`)

A `/=` operátor elosztja a változó aktuális értékét egy másik értékkel, majd az eredményt visszaírja.

```javascript
let osszeg = 12000;

osszeg /= 4;

console.log(osszeg); // 3000
```

A példában egy összeget négy egyenlő részre osztunk.

Fontos, hogy az osztás eredménye nem feltétlenül egész szám.

```javascript
let szam = 10;

szam /= 3;

console.log(szam); // 3.3333333333333335
```

A nullával történő osztás itt is speciális eredményt adhat:

```javascript
let szam = 10;

szam /= 0;

console.log(szam); // Infinity
```

## 8. Maradékképzés és értékadás (`%=`)

A `%=` operátor kiszámítja a változó aktuális értékének és egy másik számnak az osztási maradékát, majd az eredményt visszaírja a változóba.

```javascript
let szam = 17;

szam %= 5;

console.log(szam); // 2
```

A 17-et 5-tel osztva a maradék 2.

Példa:

```javascript
let szam = 20;

szam %= 3;

console.log(szam); // 2
```

A `%=` operátor például akkor hasznos, ha egy szám maradékát szeretnénk eltárolni, vagy egy ismétlődő számlálási feladatban dolgozunk.

## 9. Hatványozás és értékadás (`**=`)

A `**=` operátor a változó aktuális értékét a megadott kitevőre emeli, majd az eredményt visszaírja.

```javascript
let szam = 3;

szam **= 2;

console.log(szam); // 9
```

A művelet ugyanaz, mint:

```javascript
let szam = 3;

szam = szam ** 2;

console.log(szam); // 9
```

További példa:

```javascript
let alap = 2;

alap **= 4;

console.log(alap); // 16
```

## 10. Növelő és csökkentő operátorok (`++`, `--`)

A növelő és csökkentő operátorok speciális értékmódosító operátorok. Egy változó értékét eggyel növelik vagy csökkentik.

### 10.1. Növelés eggyel (`++`)

```javascript
let szamlalo = 5;

szamlalo++;

console.log(szamlalo); // 6
```

Ez ugyanazt az eredményt adja, mint:

```javascript
let szamlalo = 5;

szamlalo += 1;

console.log(szamlalo); // 6
```

### 10.2. Csökkentés eggyel (`--`)

```javascript
let szamlalo = 5;

szamlalo--;

console.log(szamlalo); // 4
```

Ez ugyanazt jelenti, mint:

```javascript
let szamlalo = 5;

szamlalo -= 1;

console.log(szamlalo); // 4
```

### 10.3. Prefix és postfix változat

A növelő és csökkentő operátorokat a változó előtt vagy után is használhatjuk.

Postfix:

```javascript
let szam = 5;

let eredmeny = szam++;

console.log(eredmeny); // 5
console.log(szam); // 6
```

A postfix forma először a változó eredeti értékét adja vissza, és csak utána növeli meg.

Prefix:

```javascript
let szam = 5;

let eredmeny = ++szam;

console.log(eredmeny); // 6
console.log(szam); // 6
```

A prefix forma először növeli meg a változót, és az új értéket adja vissza.

## 11. Értékadó operátorok használata a gyakorlatban

Az értékadó operátorok különösen hasznosak olyan programokban, ahol egy változó értéke folyamatosan módosul.

### 11.1. Bevásárlókosár végösszege

```javascript
let vegosszeg = 0;

vegosszeg += 2500;
vegosszeg += 1800;
vegosszeg += 3200;

console.log('Fizetendő összeg: ' + vegosszeg + ' Ft');
```

A program minden új termék árát hozzáadja a korábbi végösszeghez.

### 11.2. Raktárkészlet kezelése

```javascript
let keszlet = 100;

// Új termékek érkeznek.
keszlet += 25;

console.log('Aktuális készlet: ' + keszlet);

// Termékeket értékesítünk.
keszlet -= 40;

console.log('Aktuális készlet: ' + keszlet);
```

A készlet először növekszik, majd az értékesítés miatt csökken.

### 11.3. Pontszám kezelése

```javascript
let pontszam = 0;

pontszam += 10;
pontszam += 15;
pontszam += 20;

console.log('Elért pontszám: ' + pontszam);
```

A program minden teljesített feladat után hozzáadja a megszerzett pontokat az összesített pontszámhoz.

### 11.4. Számláló kezelése ciklusban

Az értékadó operátorokat gyakran használjuk ciklusokban is.

```javascript
let szamlalo = 0;

for (let i = 1; i <= 5; i++) {
    szamlalo += i;
}

console.log(szamlalo); // 15
```

A ciklus minden ismétléskor hozzáadja az aktuális `i` értékét a `szamlalo` változóhoz.

## 12. Gyakori hibák az értékadó operátorok használatakor

### 12.1. Az értékadás és az összehasonlítás összekeverése

Az `=` értékadást végez, míg a `===` két értéket hasonlít össze.

```javascript
let szam = 10;

szam = 20; // Új érték hozzárendelése

console.log(szam === 20); // true
```

### 12.2. Nem megfelelő változódeklaráció

A `const` kulcsszóval deklarált változóhoz nem rendelhetünk új értéket.

Hibás példa:

```javascript
const szam = 10;

szam += 5; // Hiba!
```

A `const` változó értékét nem lehet újra hozzárendeléssel módosítani.

Ha egy változó értékét később módosítani szeretnénk, használjunk `let` kulcsszót:

```javascript
let szam = 10;

szam += 5;

console.log(szam); // 15
```

### 12.3. A `+=` operátor szövegekkel

A `+=` operátor szövegek összefűzésére is használható.

```javascript
let szam = 10;

szam += '5';

console.log(szam); // "105"
```

Ez nem matematikai összeadás, hanem szöveg-összefűzés.

### 12.4. A műveletek sorrendjének figyelmen kívül hagyása

Az összetett értékadó operátorok esetén is érvényesek a matematikai műveletek végrehajtási szabályai.

```javascript
let szam = 10;

szam += 5 * 2;

console.log(szam); // 20
```

Először a szorzás történik meg, majd az eredményt hozzáadjuk a változó aktuális értékéhez.

# 13. Ellenőrző kérdések

1. Mire szolgálnak az értékadó operátorok JavaScriptben?
2. Mit jelent az egyszerű értékadás (`=`)?
3. Mi a különbség az `=` és a `===` operátor között?
4. Mit jelent a `+=` operátor, és hogyan működik?
5. Milyen műveletet végez a `-=` operátor?
6. Mi a különbség a `*=` és a `/=` operátor között?
7. Mire használjuk a `%=` és a `**=` operátorokat?
8. Milyen műveletet végez a `++` és a `--` operátor?
9. Mi a különbség a prefix és a postfix növelés között?
10. Miért nem használhatunk új értékadást egy `const` kulcsszóval deklarált változónál?

# 14. Gyakorlati feladatok

1\. feladat – Egyszerű értékadás

Hozz létre három változót:

- `nev`;
- `eletkor`;
- `varos`.

Rendelj hozzájuk tetszőleges értékeket, majd jelenítsd meg a változók tartalmát a konzolon.

2\. feladat – Változó értékének módosítása

Hozz létre egy `szam` nevű változót 20-as kezdőértékkel. Módosítsd az értékét egy új értékadás segítségével 50-re, majd jelenítsd meg a konzolon.

3\. feladat – Összeadás és értékadás

Hozz létre egy `osszeg` nevű változót 100-as kezdőértékkel. Adj hozzá egymás után három különböző számot a `+=` operátorral. Minden módosítás után jelenítsd meg az aktuális értéket.

4\. feladat – Kivonás és értékadás

Hozz létre egy `egyenleg` nevű változót 50 000-es kezdőértékkel. Végezz rajta három különböző levonást a `-=` operátor segítségével. A végén jelenítsd meg a fennmaradó összeget.

5\. feladat – Szorzás és osztás

Hozz létre egy `szam` nevű változót 12-es kezdőértékkel. Szorozd meg 5-tel, majd oszd el 3-mal az összetett értékadó operátorok segítségével. Jelenítsd meg az eredményt.

6\. feladat – Maradékképzés

Hozz létre egy `szam` nevű változót 47-es kezdőértékkel. Használd a `%=` operátort, hogy meghatározd a 47 és 6 osztási maradékát. Jelenítsd meg az eredményt.

7\. feladat – Hatványozás

Hozz létre egy `alap` nevű változót 3-as kezdőértékkel. Használd a `**=` operátort a változó négyzetre emeléséhez, majd jelenítsd meg az eredményt.

8\. feladat – Számláló készítése

Hozz létre egy `szamlalo` nevű változót 0-s kezdőértékkel. Növeld az értékét ötször a `++` operátorral, majd csökkentsd kétszer a `--` operátorral. Jelenítsd meg a végeredményt.

9\. feladat – Bevásárlókosár

Hozz létre egy `vegosszeg` nevű változót 0-s kezdőértékkel. Adj hozzá legalább öt különböző termékárat a `+=` operátor segítségével. Ezután vonj le a végösszegből egy kedvezményt a `-=` operátorral. Jelenítsd meg a fizetendő összeget.

10\. feladat – Pontszámkezelő program

Készíts egy egyszerű pontszámkezelő programot. Hozz létre egy `pontszam` nevű változót 0-s kezdőértékkel.

- Három feladat teljesítésekor adj hozzá különböző pontértékeket.
- Egy hibás válasz esetén vonj le pontot.
- Egy bónuszfeladat teljesítésekor duplázd meg a pontszámot.
- A végén jelenítsd meg az összesített pontszámot.

A műveletekhez használj összetett értékadó operátorokat.
