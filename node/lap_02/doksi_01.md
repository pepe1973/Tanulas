# Változók deklarálása JavaScriptben (`var`, `let`, `const`)

## 1. Mi az a változó?

A változó a programozásban olyan névvel ellátott tárolóhely, amelyben adatokat tárolhatunk, majd ezeket az adatokat a program működése során felhasználhatjuk.

JavaScriptben változókat például az alábbi adatok tárolására használhatunk:

- Szövegek (`string`)
- Számok (`number`)
- Logikai értékek (`boolean`)
- Tömbök (`array`)
- Objektumok (`object`)
- Függvények (`function`)
- Egyéb adatok és értékek

Például:

```javascript
let nev = 'Péter';
let eletkor = 25;
let aktiv = true;

console.log(nev);
console.log(eletkor);
console.log(aktiv);
```

A változók deklarálásához JavaScriptben három kulcsszót használhatunk:

- `var`
- `let`
- `const`

Ezek különböző szabályok szerint működnek, elsősorban az érvényességi körükben (scope) és az újraértékadás lehetőségében térnek el egymástól.

## 2. Változók deklarálása a `var` kulcsszóval

A `var` a JavaScript régebbi változódeklarációs kulcsszava. A modern JavaScript-fejlesztés során általában már nem ajánlott a használata, mert bizonyos működési sajátosságai könnyen hibákhoz vezethetnek.

### 2.1. Alapvető használata

A `var` segítségével változót hozhatunk létre, amelynek később módosíthatjuk az értékét.

```javascript
var nev = 'Anna';

console.log(nev);

nev = 'Péter';

console.log(nev);
```

A változó értéke a program futása közben megváltoztatható.

### 2.2. Újradefiniálás

A `var` segítségével ugyanazon a hatókörön belül többször is deklarálhatjuk ugyanazt a változónevet.

```javascript
var szam = 10;

var szam = 20;

console.log(szam);
```

Eredmény:

```
20
```

Ez a működés problémát okozhat, mert egy véletlenül megismételt deklaráció felülírhatja a korábbi változó értékét.

### 2.3. A `var` függvényszintű hatóköre

A `var` kulcsszóval létrehozott változók függvényszintű hatókörrel rendelkeznek.

Ez azt jelenti, hogy egy függvényen belül deklarált `var` változó a teljes függvényen belül elérhető, akkor is, ha egy belső blokkban hoztuk létre.

```javascript
function teszt() {
    if (true) {
        var uzenet = 'Helló!';
    }

    console.log(uzenet);
}

teszt();
```

Eredmény:

```
Helló!
```

Az `if` blokk nem korlátozza a `var` változó érvényességét.

### 2.4. A `var` globális és függvényszintű működése

Ha egy `var` változót függvényen kívül deklarálunk, akkor az az adott környezet globális hatóköréhez kapcsolódik.

Böngészőben, hagyományos klasszikus script esetén a globális `var` deklaráció a `window` objektum tulajdonságaként is megjelenik.

```javascript
var oldalCim = 'Főoldal';

console.log(window.oldalCim);
```

Fontos, hogy ez a viselkedés nem minden JavaScript-környezetben azonos. Például modulokban a legfelső szinten deklarált `var` nem válik a `window` objektum tulajdonságává.

## 3. Változók deklarálása a `let` kulcsszóval

A `let` a modern JavaScript egyik alapvető változódeklarációs kulcsszava.

Akkor használjuk, amikor olyan változót szeretnénk létrehozni, amelynek értéke a program futása során később megváltozhat.

### 3.1. Alapvető használata

```javascript
let eletkor = 20;

console.log(eletkor);

eletkor = 21;

console.log(eletkor);
```

Eredmény:

```
20
21
```

A `let` változó értéke módosítható.

### 3.2. Újradefiniálás korlátozása

Ugyanazon a hatókörön belül egy `let` változót nem deklarálhatunk újra ugyanazzal a névvel.

```javascript
let nev = 'Anna';

// Ez hibát okoz:
let nev = 'Péter';
```

A JavaScript `SyntaxError` hibát jelez, mert az adott hatókörben már létezik ilyen nevű változó.

Az érték módosítása azonban megengedett:

```javascript
let nev = 'Anna';

nev = 'Péter';

console.log(nev);
```

Eredmény:

```
Péter
```

### 3.3. A `let` blokkhatóköre

A `let` egyik legfontosabb tulajdonsága, hogy blokkhatókörű (block scope).

Ez azt jelenti, hogy a változó csak azon a blokkterületen belül érhető el, ahol deklaráltuk.

A blokkot általában kapcsos zárójelek határolják.

```javascript
if (true) {
    let uzenet = 'Helló!';
    console.log(uzenet);
}

// Ez hibát okoz:
console.log(uzenet);
```

Az `uzenet` változó csak az `if` blokk belsejében használható.

A blokkhatókör nemcsak az `if` szerkezetekre, hanem például a ciklusokra és az önálló kapcsos zárójelpárral létrehozott blokkokra is érvényes.

### 3.4. Változó deklarálása értékadás nélkül

A `let` változót kezdeti érték nélkül is deklarálhatjuk.

```javascript
let eredmeny;

console.log(eredmeny);
```

Eredmény:

```
undefined
```

Az `undefined` azt jelenti, hogy a változó létezik, de még nem rendeltünk hozzá értéket.

Később természetesen megadhatjuk az értékét:

```javascript
let eredmeny;

eredmeny = 100;

console.log(eredmeny);
```

## 4. Változók deklarálása a `const` kulcsszóval

A `const` kulcsszóval olyan változót deklarálhatunk, amelynek a deklaráláskor kötelező kezdőértéket adni, és amelynek később nem adhatunk új értéket.

A `const` neve a constant, vagyis állandó szóból származik.

### 4.1. Alapvető használata

```javascript
const PI = 3.14159;

console.log(PI);
```

A `const` változót kötelező inicializálni:

```
// Ez hibát okoz:
const nev;
```

A JavaScript `SyntaxError` hibát jelez, mert a `const` deklarációhoz nem adtunk kezdőértéket.

### 4.2. Új érték hozzárendelésének tiltása

A `const` változóhoz később nem rendelhetünk új értéket.

```javascript
const eletkor = 25;

// Ez hibát okoz:
eletkor = 26;
```

A JavaScript `TypeError` hibát jelez.

Ezért a `const` olyan értékek esetén hasznos, amelyeket a változóhoz rendelt referencia szintjén nem szeretnénk megváltoztatni.

### 4.3. Objektumok használata `const` esetén

Fontos különbség, hogy a `const` nem teszi automatikusan módosíthatatlanná az objektumokat és a tömböket.

Azt akadályozza meg, hogy a változó egy másik objektumra vagy értékre mutasson.

Például:

```javascript
const felhasznalo = {
    nev: 'Anna',
    eletkor: 25,
};

felhasznalo.eletkor = 26;

console.log(felhasznalo);
```

Eredmény:

```
{
    nev: "Anna",
    eletkor: 26
}
```

Az objektum egyik tulajdonságát módosíthattuk, mert nem magát a `felhasznalo` változóhoz rendelt referenciát változtattuk meg.

Viszont az alábbi művelet hibát okoz:

```javascript
const felhasznalo = {
    nev: 'Anna',
};

// Ez hibát okoz:
felhasznalo = {
    nev: 'Péter',
};
```

### 4.4. Tömbök használata `const` esetén

A `const` kulcsszóval deklarált tömb elemei módosíthatók.

```javascript
const szamok = [10, 20, 30];

szamok.push(40);

console.log(szamok);
```

Eredmény:

```
[10, 20, 30, 40]
```

A tömb egy eleme is módosítható:

```javascript
const szamok = [10, 20, 30];

szamok[0] = 100;

console.log(szamok);
```

Eredmény:

```
[100, 20, 30]
```

A tömb egészének lecserélése viszont nem megengedett:

```javascript
const szamok = [10, 20, 30];

// Ez hibát okoz:
szamok = [40, 50, 60];
```

Ha az objektum vagy tömb tartalmának módosíthatóságát is meg szeretnénk akadályozni, további megoldásokat, például az `Object.freeze()` metódust használhatjuk.

```javascript
const felhasznalo = Object.freeze({
    nev: 'Anna',
    eletkor: 25,
});

felhasznalo.eletkor = 30;

console.log(felhasznalo.eletkor);
```

Az objektum tulajdonsága nem módosul. Az `Object.freeze()` azonban csak sekély szinten fagyasztja be az objektumot, vagyis a benne található további objektumok alapértelmezés szerint nem válnak automatikusan módosíthatatlanná.

## 5. A `var`, `let` és `const` összehasonlítása

A három deklarációs kulcsszó között több fontos különbség van.

| Tulajdonság                                | `var`                    | `let`         | `const`       |
| ------------------------------------------ | ------------------------ | ------------- | ------------- |
| Új érték hozzárendelhető?                  | Igen                     | Igen          | Nem           |
| Újra deklarálható ugyanabban a hatókörben? | Igen                     | Nem           | Nem           |
| Hatókör                                    | Függvényszintű           | Blokkhatókörű | Blokkhatókörű |
| Kezdőérték kötelező?                       | Nem                      | Nem           | Igen          |
| Inicializálás előtti használat             | `undefined` értékű lehet | Hibát okoz    | Hibát okoz    |

### 5.1. A változók újraértékadása

```javascript
var a = 10;
a = 20;

let b = 10;
b = 20;

const c = 10;
// c = 20; // Hiba

console.log(a);
console.log(b);
console.log(c);
```

A `var` és a `let` változók értéke módosítható, a `const` változóhoz viszont nem rendelhetünk új értéket.

### 5.2. Azonos nevű változók különböző blokkokban

A `let` és a `const` blokkhatóköre lehetővé teszi, hogy különböző blokkokban azonos nevű változókat használjunk.

```javascript
let nev = 'Külső változó';

if (true) {
    let nev = 'Belső változó';

    console.log(nev);
}

console.log(nev);
```

Eredmény:

```
Belső változó
Külső változó
```

A két változó egymástól független, mert különböző hatókörben deklaráltuk őket.

## 6. A változók inicializálása és a Temporal Dead Zone

A változó deklarálása és inicializálása két különböző művelet.

- Deklarálás: létrehozzuk a változót a megadott névvel.
- Inicializálás: megadjuk a változó első értékét.

A `var`, `let` és `const` eltérően viselkedik a deklaráció előtti használat esetén.

### 6.1. A `var` működése

A `var` változók deklarációja a hatókör elejére kerül a feldolgozás során. Ezt hoistingnak nevezzük.

```javascript
console.log(szam);

var szam = 10;
```

Eredmény:

```
undefined
```

A változó deklarációja előre kerül, de az értékadás az eredeti helyén marad.

A fenti kód működése leegyszerűsítve:

```javascript
var szam;

console.log(szam);

szam = 10;
```

### 6.2. A `let` és `const` működése

A `let` és a `const` deklarációk szintén részt vesznek a hoisting folyamatában, de az inicializálásukig nem használhatók.

Ezt az időszakot Temporal Dead Zone-nak (TDZ), magyarul időbeli holttérnek nevezzük.

```javascript
console.log(szam);

let szam = 10;
```

A kód `ReferenceError` hibát eredményez, mert a változót az inicializálása előtt próbáltuk használni.

Ugyanez érvényes a `const` esetén is.

```javascript
console.log(PI);

const PI = 3.14159;
```

Ez szintén `ReferenceError` hibát okoz.

Fontos: a `let` és a `const` változókat mindig a deklarálásuk és inicializálásuk után használjuk.

## 7. Változók elnevezésének szabályai

JavaScriptben a változók neveire meghatározott szabályok vonatkoznak.

### 7.1. Érvényes változónevek

A változónév:

- Tartalmazhat betűket.
- Tartalmazhat számokat, de nem kezdődhet számmal.
- Tartalmazhat aláhúzásjelet (`_`).
- Tartalmazhat dollárjelet (`$`).
- Nem tartalmazhat szóközt.
- Nem lehet JavaScript-foglalt kulcsszó.
- Kis- és nagybetűérzékeny.

Példák:

```
let nev = "Anna";
let felhasznaloNev = "peter";
let eletkor2 = 25;
let _eredmeny = 100;
let $ar = 500;
```

### 7.2. Érvénytelen változónevek

```javascript
// Hibás, mert számmal kezdődik:
let 2nev = "Anna";

// Hibás, mert szóközt tartalmaz:
let felhasznalo nev = "Péter";

// Hibás, mert foglalt kulcsszó:
let let = 10;
```

### 7.3. Kis- és nagybetűk megkülönböztetése

A JavaScript megkülönbözteti a kis- és nagybetűket.

```javascript
let nev = 'Anna';
let Nev = 'Péter';
let NEV = 'Katalin';

console.log(nev);
console.log(Nev);
console.log(NEV);
```

A három változó különbözőnek számít.

### 7.4. Elnevezési konvenciók

JavaScriptben általában a camelCase elnevezési formát használjuk.

Ennek lényege, hogy az első szó kisbetűvel kezdődik, a további szavak pedig nagybetűvel.

```javascript
let felhasznaloNev = 'Anna';
let aktualisDatum = '2026-10-31';
let rendelesOsszeg = 15000;
let termekDarabszam = 5;
```

A `const` változóknál gyakran használunk nagybetűs neveket, ha valóban állandó, programon belül nem változó értéket tárolunk.

```javascript
const PI = 3.14159;
const MAX_PROBA = 5;
const API_URL = 'https://pelda.hu/api';
```

Ez azonban elnevezési konvenció, nem kötelező JavaScript-szabály. A `const` változók neve általában ugyanúgy lehet camelCase is.

## 8. Melyik deklarációs kulcsszót használjuk?

A modern JavaScript-fejlesztés során általában az alábbi szabályokat érdemes követni:

1\. Elsőként használjunk `const` kulcsszót.

Ha egy változóhoz a deklarálás után nem szeretnénk új értéket rendelni, akkor a `const` a megfelelő választás.

```javascript
const felhasznaloNev = 'Anna';
const termekAr = 12000;
```

2\. Használjunk `let` kulcsszót, ha az érték változni fog.

Például számlálóknál, ciklusoknál vagy módosítható állapotoknál.

```javascript
let szamlalo = 0;

szamlalo++;
szamlalo++;

console.log(szamlalo);
```

3\. Új kódban lehetőleg kerüljük a `var` használatát.

A `var` régebbi JavaScript-kódokban gyakran előfordul, ezért fontos megérteni a működését, de új programokban általában a `let` és a `const` használata ajánlott.

## 9. Gyakori hibák és fontos tudnivalók

### 9.1. `const` használata kezdőérték nélkül

```javascript
const nev;
```

Ez szintaktikai hibát okoz. A `const` deklarálásakor mindig meg kell adni a kezdőértéket.

### 9.2. `let` vagy `const` újradefiniálása

```javascript
let nev = 'Anna';
let nev = 'Péter';
```

Ez ugyanabban a hatókörben hibás. Az érték módosításához nem kell újra deklarálni a változót.

Helyesen:

```javascript
let nev = 'Anna';
nev = 'Péter';
```

### 9.3. `const` változó értékének módosítása

```javascript
const szam = 10;
szam = 20;
```

Ez hibát okoz, mert a `const` változóhoz nem rendelhető új érték.

### 9.4. Blokkon kívüli változóhasználat

```javascript
if (true) {
    let uzenet = 'Szia!';
}

console.log(uzenet);
```

Ez hibás, mert az `uzenet` változó csak az `if` blokkon belül érhető el.

### 9.5. Változó használata inicializálás előtt

```javascript
console.log(nev);

let nev = 'Anna';
```

Ez `ReferenceError` hibát okoz a Temporal Dead Zone miatt.

## 10. Összefoglalás

A JavaScriptben három alapvető kulcsszóval deklarálhatunk változókat: `var`, `let` és `const`.

- A `var` a régebbi változódeklarációs forma, függvényszintű hatókörrel rendelkezik.
- A `let` blokkhatókörű változót hoz létre, amelynek értéke módosítható.
- A `const` blokkhatókörű változót hoz létre, amelyhez a deklarálás után nem rendelhetünk új értéket.
- A `let` és a `const` nem deklarálható újra ugyanabban a hatókörben.
- A `const` objektumok és tömbök tartalma módosítható, de maga a változó nem rendelhető hozzá másik objektumhoz vagy tömbhöz.
- A `let` és a `const` inicializálás előtti használata hibát okoz.
- Modern JavaScriptben általában a `const` használata az elsődleges, és csak akkor választunk `let`-et, ha az értéknek változnia kell.

## 11. Ellenőrző kérdések

1. Mi a változó szerepe a JavaScript-programozásban?
2. Milyen három kulcsszóval deklarálhatunk változókat JavaScriptben?
3. Mi a legfontosabb különbség a `var` és a `let` hatóköre között?
4. Módosítható-e egy `const` változó értéke a deklarálás után? Indokold a válaszodat!
5. Mi történik akkor, ha ugyanabban a hatókörben kétszer deklarálunk egy `let` változót ugyanazzal a névvel?
6. Mit jelent a blokkhatókör, és melyik két változódeklarációs kulcsszó használja ezt a működést?
7. Miért nem okoz feltétlenül hibát egy `const` változóhoz rendelt objektum egyik tulajdonságának módosítása?
8. Mit jelent a hoisting, és hogyan viselkedik a `var` változó esetében?
9. Mit nevezünk Temporal Dead Zone-nak (TDZ), és milyen hibát okoz a változó inicializálás előtti használata `let` esetén?
10. Mikor érdemes a `const`, és mikor a `let` kulcsszót használni a modern JavaScript-programozásban?

## 12. Gyakorlati feladatok

A következő feladatok célja, hogy a változók deklarálásával, módosításával, hatókörével és elnevezésével kapcsolatos ismereteket gyakorold.

A feladatokat JavaScriptben oldd meg! A megoldásokat külön fájlban vagy egy közös JavaScript-fájlban is elkészítheted.

### 1. feladat – Változók deklarálása

Hozz létre három változót a megfelelő deklarációs kulcsszavakkal!

- Egy `nev` nevű változót, amely egy személy nevét tárolja.
- Egy `eletkor` nevű változót, amely egy életkort tárol.
- Egy `aktiv` nevű változót, amely egy logikai értéket tárol.

Írasd ki mindhárom változó értékét a konzolra!

### 2. feladat – Értékek módosítása

Hozz létre egy `let` kulcsszóval deklarált `pontszam` változót, amelynek kezdeti értéke `10`.

- Növeld az értékét 5-tel!
- Ezután növeld további 15-tel!
- Végül írasd ki az eredményt!

### 3. feladat – A `const` használata

Hozz létre három `const` változót:

- `PI`: értéke `3.14159`.
- `MAX_ELETKOR`: értéke `120`.
- `WEBOLDAL_NEVE`: értéke egy általad választott weboldal neve.

Írasd ki az értékeket a konzolra!

### 4. feladat – Tömb módosítása `const` használatával

Hozz létre egy `const` kulcsszóval deklarált `gyumolcsok` nevű tömböt, amely három gyümölcs nevét tartalmazza!

- Adj hozzá egy negyedik gyümölcsöt a `push()` metódussal!
- Módosítsd a tömb első elemét!
- Írasd ki a teljes tömböt!

### 5. feladat – Objektum módosítása `const` használatával

Hozz létre egy `const` változót `auto` néven!

Az objektum az alábbi tulajdonságokat tartalmazza:

- `marka`
- `tipus`
- `evjarat`
- `ar`

Ezután módosítsd az autó árát, majd írasd ki az objektum teljes tartalmát!

### 6. feladat – A `var` és a `let` hatóköre

Készíts egy programot, amelyben:

- Egy `var` változót egy `if` blokkon belül deklarálsz.
- Egy `let` változót szintén az `if` blokkon belül deklarálsz.
- Mindkét változót próbáld meg kiírni az `if` blokkon belül!
- Ezután próbáld meg mindkét változót kiírni a blokkon kívül is!

Figyeld meg, hogy melyik változó érhető el a blokkon kívül! A két változó kiírását külön-külön vizsgáld, mert az egyik próbálkozás hibát okoz.

### 7. feladat – Változók újradefiniálása

Hozz létre egy `var` változót `szam` néven, majd ugyanazzal a névvel deklaráld újra!

Ezután végezd el ugyanezt a kísérletet `let` használatával is!

Figyeld meg, milyen különbség van a két deklaráció működése között!

### 8. feladat – Változónevek javítása

Az alábbi változódeklarációk között hibás elnevezések találhatók.

```javascript
let nev = "Anna";
let 2eletkor = 25;
let felhasznalo nev = "Péter";
let var = 10;
let aktualisDatum = "2026-10-31";
let termek-ar = 5000;
```

Feladatok:

- Keresd meg a hibás változóneveket!
- Javítsd ki az elnevezéseket!
- Ügyelj arra, hogy a nevek megfeleljenek a JavaScript szabályainak!

### 9. feladat – Számlálóprogram

Készíts egy egyszerű számlálóprogramot!

- Hozz létre egy `let` változót `szamlalo` néven, kezdeti értéke legyen `0`!
- Növeld az értékét egymás után ötször!
- Minden növelés után írasd ki az aktuális értéket!
- A program végén jelenítsd meg a végső értéket is!

### 10. feladat – Változók használata egy programban

Készíts egy egyszerű terméknyilvántartó programot!

Hozd létre az alábbi változókat:

- `const termekNev`: a termék neve.
- `let termekAr`: a termék ára.
- `let keszlet`: a rendelkezésre álló darabszám.
- `const penznem`: a pénznem megnevezése.

Ezután végezd el a következő műveleteket:

1. Írasd ki a termék nevét és eredeti árát!
2. Módosítsd a termék árát!
3. Csökkentsd a készlet mennyiségét 2-vel!
4. Írasd ki a módosított adatokat!
5. Próbálj új értéket rendelni a `termekNev` változóhoz! Figyeld meg, mi történik!
6. A program végén jelenítsd meg a termék teljes adatait!
