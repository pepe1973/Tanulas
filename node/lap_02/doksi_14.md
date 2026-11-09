# Növelő és csökkentő operátorok JavaScriptben

## 1. Az operátorok szerepe

A növelő és csökkentő operátorok segítségével egy változó numerikus értékét tudjuk eggyel növelni vagy csökkenteni.

- Növelő operátor (`++`): eggyel növeli a változó értékét.
- Csökkentő operátor (`--`): eggyel csökkenti a változó értékét.

Ezek az operátorok különösen gyakran fordulnak elő ciklusokban, számlálóknál és olyan programrészekben, ahol egy értéket lépésenként kell módosítani.

## 2. Növelő operátor (`++`)

A növelő operátor eggyel növeli a változó aktuális értékét.

```javascript
let szamlalo = 5;

szamlalo++;

console.log(szamlalo); // 6
```

A `szamlalo++` utasítás ugyanazt eredményezi, mint:

```javascript
let szamlalo = 5;

szamlalo = szamlalo + 1;

console.log(szamlalo); // 6
```

A növelő operátor tehát egy rövidebb megoldást biztosít az eggyel történő növelésre.

## 3. Csökkentő operátor (`--`)

A csökkentő operátor eggyel csökkenti a változó aktuális értékét.

```javascript
let szamlalo = 5;

szamlalo--;

console.log(szamlalo); // 4
```

A következő kódrészlet ugyanazt az eredményt adja:

```javascript
let szamlalo = 5;

szamlalo = szamlalo - 1;

console.log(szamlalo); // 4
```

A `--` operátort például visszaszámlálásnál, készletcsökkentésnél vagy egy számláló értékének csökkentésénél használhatjuk.

## 4. Prefix és postfix forma

A növelő és csökkentő operátorok kétféleképpen használhatók:

- Prefix forma: az operátor a változó előtt szerepel.
- Postfix forma: az operátor a változó után szerepel.

A két forma közötti különbség akkor válik fontossá, amikor az operátort egy kifejezés részeként használjuk.

### 4.1. Prefix növelés (`++valtozo`)

Prefix esetén először megtörténik a változó értékének növelése, majd a kifejezés az új értéket adja vissza.

```javascript
let szamlalo = 5;

let eredmeny = ++szamlalo;

console.log(szamlalo); // 6
console.log(eredmeny); // 6
```

A művelet lépései:

1. A `szamlalo` értéke kezdetben `5`.
2. A `++szamlalo` növeli az értéket `6`-ra.
3. Az `eredmeny` változó megkapja a `6` értéket.

### 4.2. Postfix növelés (`valtozo++`)

Postfix esetén először a változó eredeti értéke kerül felhasználásra, majd megtörténik a növelés.

```javascript
let szamlalo = 5;

let eredmeny = szamlalo++;

console.log(szamlalo); // 6
console.log(eredmeny); // 5
```

A művelet lépései:

1. A `szamlalo` értéke kezdetben `5`.
2. Az `eredmeny` változó megkapja a régi értéket, vagyis `5`-öt.
3. A `szamlalo` értéke ezután `6`-ra növekszik.

### 4.3. Prefix és postfix összehasonlítása

| Művelet      | Eredeti érték | A változó új értéke | A kifejezés eredménye |
| ------------ | ------------- | ------------------- | --------------------- |
| `++szamlalo` | 5             | 6                   | 6                     |
| `szamlalo++` | 5             | 6                   | 5                     |
| `--szamlalo` | 5             | 4                   | 4                     |
| `szamlalo--` | 5             | 4                   | 5                     |

Fontos: önálló utasításként a prefix és postfix forma általában ugyanazt a változást eredményezi. A különbség akkor jelentkezik, ha az operátor eredményét egy másik kifejezésben is felhasználjuk.

## 5. Prefix és postfix csökkentés

A csökkentő operátornál is ugyanaz a működési különbség figyelhető meg.

Prefix csökkentés:

```javascript
let eletkor = 20;

let eredmeny = --eletkor;

console.log(eletkor); // 19
console.log(eredmeny); // 19
```

Postfix csökkentés:

```javascript
let eletkor = 20;

let eredmeny = eletkor--;

console.log(eletkor); // 19
console.log(eredmeny); // 20
```

Prefix esetén az új érték, postfix esetén a régi érték kerül visszaadásra.

## 6. Növelő és csökkentő operátorok ciklusokban

A növelő operátorok egyik leggyakoribb felhasználási területe a `for` ciklus.

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

A ciklus működése:

1. Létrejön az `i` változó `1` kezdőértékkel.
2. A program ellenőrzi, hogy az `i <= 5` feltétel igaz-e.
3. Ha igaz, végrehajtja a ciklus törzsét.
4. Az `i++` növeli a változó értékét.
5. A program ismét ellenőrzi a feltételt.
6. A ciklus akkor fejeződik be, amikor a feltétel hamissá válik.

A kimenet:

```
1
2
3
4
5
```

A csökkentő operátorral visszafelé is végiglépkedhetünk egy számsoron:

```javascript
for (let i = 5; i >= 1; i--) {
    console.log(i);
}
```

A kimenet:

```
5
4
3
2
1
```

## 7. Gyakorlati példák

### 7.1. Látogatók számának növelése

Egy weboldalon minden új látogatáskor növelhetjük a látogatók számát.

```javascript
let latogatok = 100;

latogatok++;

console.log(`Látogatók száma: ${latogatok}`);
```

Eredmény:

```
Látogatók száma: 101
```

### 7.2. Készlet csökkentése

Egy termék eladásakor csökkenthetjük a raktárkészlet értékét.

```javascript
let keszlet = 25;

keszlet--;

console.log(`Raktáron maradt: ${keszlet} db`);
```

Eredmény:

```
Raktáron maradt: 24 db
```

### 7.3. Visszaszámlálás

```javascript
let masodperc = 5;

while (masodperc > 0) {
    console.log(masodperc);
    masodperc--;
}

console.log('Lejárt az idő!');
```

A program öttől egyig számol vissza, majd kiírja a befejező üzenetet.

### 7.4. Tömb elemeinek bejárása

A növelő operátor segítségével egy tömb minden elemét elérhetjük.

```javascript
const gyumolcsok = ['alma', 'körte', 'barack'];

for (let i = 0; i < gyumolcsok.length; i++) {
    console.log(gyumolcsok[i]);
}
```

A ciklusváltozó minden ismétlésnél eggyel növekszik, így a tömb következő elemére lép.

## 8. Gyakori hibák és fontos tudnivalók

### 8.1. Nem megfelelő változótípus

A növelő és csökkentő operátorokat numerikus értékek módosítására használjuk.

```javascript
let szamlalo = 10;

szamlalo++;

console.log(szamlalo); // 11
```

Szöveges értékeknél nem érdemes ezekre az operátorokra támaszkodni. A `++` és `--` műveletek a változó értékét számmá alakíthatják, ha az átalakítás lehetséges.

### 8.2. A `const` változó nem módosítható új értékadással

A `const` kulcsszóval deklarált változóhoz nem rendelhetünk új értéket. Ezért a növelő és csökkentő operátor sem használható rajta.

```javascript
const szamlalo = 5;

// Hibát eredményez:
szamlalo++;
```

Ha a változó értékét módosítani szeretnénk, használjunk `let` deklarációt.

### 8.3. Prefix és postfix összekeverése

Az alábbi két utasítás nem ugyanazt az eredményt adja:

```javascript
let a = 5;
let b = ++a;

console.log(b); // 6
```

```javascript
let a = 5;
let b = a++;

console.log(b); // 5
```

Mindkét esetben `a` értéke végül `6` lesz, de `b` értéke eltér.

### 8.4. Többszörös növelés egy kifejezésben

Kerüljük a nehezen követhető kifejezéseket:

```javascript
let szamlalo = 5;

let eredmeny = szamlalo++ + ++szamlalo;

console.log(eredmeny);
console.log(szamlalo);
```

Az ilyen kifejezések nehezebben olvashatók és könnyebben vezetnek hibához. Célszerű a változtatásokat külön utasításokban elvégezni.

## 9. Összefoglalás

| Operátor | Elnevezés          | Működés                                        |
| -------- | ------------------ | ---------------------------------------------- |
| `++x`    | Prefix növelés     | Előbb növel, majd visszaadja az új értéket     |
| `x++`    | Postfix növelés    | Előbb visszaadja a régi értéket, majd növel    |
| `--x`    | Prefix csökkentés  | Előbb csökkent, majd visszaadja az új értéket  |
| `x--`    | Postfix csökkentés | Előbb visszaadja a régi értéket, majd csökkent |

A növelő és csökkentő operátorok egyszerű és rövid megoldást biztosítanak egy változó értékének eggyel történő módosítására. Leggyakrabban számlálók, ciklusok, visszaszámlálások és készletkezelési feladatok során találkozhatunk velük.

# 10. Ellenőrző kérdések

1. Mire szolgál a növelő (`++`) operátor JavaScriptben?
2. Mire szolgál a csökkentő (`--`) operátor?
3. Mi a különbség a prefix és a postfix forma között?
4. Mit jelent a `++szamlalo` kifejezés?
5. Mit jelent a `szamlalo++` kifejezés?
6. Milyen értéket kap az `eredmeny` változó az alábbi kódban?
    ```javascript
    let szamlalo = 8;
    let eredmeny = szamlalo++;
    ```
7. Milyen értéket kap az `eredmeny` változó az alábbi kódban?
    ```javascript
    let szamlalo = 8;
    let eredmeny = --szamlalo;
    ```
8. Miért használjuk gyakran a növelő operátort `for` ciklusokban?
9. Miért nem alkalmazható a növelő operátor egy `const` változón?
10. Milyen gyakorlati programozási feladatokban használhatjuk a növelő és csökkentő operátorokat?

# 11. Gyakorlati feladatok

Az alábbi feladatokat JavaScriptben, megoldás nélkül készítsd el!

1. Számláló növelése: Hozz létre egy `szamlalo` nevű változót `10` kezdőértékkel. Növeld meg az értékét háromszor a növelő operátor segítségével, majd írd ki a végeredményt!
2. Számláló csökkentése: Hozz létre egy `keszlet` nevű változót `50` kezdőértékkel. Csökkentsd az értékét ötször a csökkentő operátor segítségével, majd jelenítsd meg az eredményt!
3. Prefix növelés: Hozz létre egy `a` változót `7` értékkel. A `++a` segítségével növeld meg az értékét, és az új értéket tárold el egy `b` változóban. Írd ki mindkét változó értékét!
4. Postfix növelés: Hozz létre egy `a` változót `7` értékkel. A `a++` segítségével növeld meg az értékét, és az operátor eredményét tárold el egy `b` változóban. Írd ki mindkét változó értékét!
5. Prefix csökkentés: Hozz létre egy `pontszam` változót `100` értékkel. Csökkentsd prefix operátorral az értékét, és az eredményt tárold el egy másik változóban!
6. Postfix csökkentés: Hozz létre egy `eletkor` változót `25` értékkel. Csökkentsd postfix operátorral az értékét, és vizsgáld meg, milyen értéket kap az eredményt tároló változó!
7. Növekvő ciklus: Készíts `for` ciklust, amely `1`-től `20`-ig írja ki a számokat. A ciklusváltozó növeléséhez használd a `++` operátort!
8. Csökkenő ciklus: Készíts `for` ciklust, amely `10`-től `1`-ig írja ki a számokat. A ciklusváltozó csökkentéséhez használd a `--` operátort!
9. Visszaszámlálás: Hozz létre egy `masodperc` változót `10` kezdőértékkel. Egy `while` ciklus segítségével számolj vissza nulláig, és minden lépésben jelenítsd meg az aktuális értéket!
10. Tömb bejárása: Hozz létre egy legalább 8 elemből álló, szöveges értékeket tartalmazó tömböt. Egy `for` ciklussal jelenítsd meg az összes elemet. A ciklusváltozó növeléséhez használd a `++` operátort!
