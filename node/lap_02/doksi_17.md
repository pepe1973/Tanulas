# Optional chaining operátor (`?.`) JavaScriptben

## 1. Mi az az optional chaining operátor?

Az optional chaining operátor (`?.`) segítségével biztonságosan érhetjük el objektumok tulajdonságait, tömbök elemeit vagy függvényeket akkor is, ha az adott objektum vagy érték esetleg `null` vagy `undefined`.

Magyarul opcionális láncolásnak is nevezik.

A hagyományos tulajdonságelérésnél problémát okozhat, ha egy objektum nem létezik, vagy valamelyik köztes tulajdonsága hiányzik.

Például:

```javascript
const felhasznalo = null;

console.log(felhasznalo.nev);
```

A fenti kód futásidejű hibát eredményez, mert a `null` értéknek nem lehet lekérdezni a `nev` tulajdonságát.

Az optional chaining operátorral elkerülhetjük ezt:

```javascript
const felhasznalo = null;

console.log(felhasznalo?.nev);
```

Kimenet:

```
undefined
```

A program nem áll le hibával. Ha a bal oldali érték `null` vagy `undefined`, akkor az opcionális láncolás eredménye `undefined` lesz.

## 2. Az optional chaining alapvető szintaxisa

Az operátor általános felépítése:

```javascript
objektum?.tulajdonsag;
```

A működése:

- Ha az objektum létezik, akkor a program lekéri a megadott tulajdonságot.
- Ha az objektum értéke `null` vagy `undefined`, akkor a kifejezés eredménye `undefined` lesz.
- A program nem dob hibát az opcionális láncolás által védett hozzáférés miatt.

Példa:

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    eletkor: 25,
};

console.log(felhasznalo?.nev);
console.log(felhasznalo?.eletkor);
console.log(felhasznalo?.email);
```

Kimenet:

```
Kovács Anna
25
undefined
```

Az első két tulajdonság létezik, ezért a program visszaadja az értéküket. Az `email` tulajdonság nem szerepel az objektumban, ezért az eredmény `undefined`.

## 3. Beágyazott objektumok tulajdonságainak elérése

Az optional chaining különösen hasznos akkor, ha egy objektum több egymásba ágyazott objektumot tartalmaz.

Tegyük fel, hogy egy felhasználó adatai között a lakcím is szerepel.

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    cim: {
        varos: 'Budapest',
        iranyitoszam: 1111,
    },
};

console.log(felhasznalo.cim.varos);
```

Kimenet:

```
Budapest
```

A probléma akkor jelentkezik, ha a `cim` tulajdonság nem létezik, vagy értéke `null`.

A hagyományos hozzáférés hibát okozhat:

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    cim: null,
};

console.log(felhasznalo.cim.varos);
```

Optional chaining használatával biztonságosabbá tehetjük a hozzáférést:

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    cim: null,
};

console.log(felhasznalo.cim?.varos);
```

Kimenet:

```
undefined
```

Fontos: a `?.` operátort minden olyan ponton alkalmazni kell, ahol az előző érték `null` vagy `undefined` lehet.

Például:

```javascript
const felhasznalo = null;

console.log(felhasznalo?.cim?.varos);
```

A láncolás mindkét hozzáférést biztonságossá teszi.

## 4. Tömbök elemeinek elérése optional chaining segítségével

Az optional chaining tömbök esetében is használható.

Példa:

```javascript
const felhasznalok = ['Anna', 'Péter', 'János'];

console.log(felhasznalok?.[0]);
console.log(felhasznalok?.[1]);
```

Kimenet:

```
Anna
Péter
```

A `?.[index]` forma akkor különösen hasznos, ha maga a tömb is lehet `null` vagy `undefined`.

```javascript
const felhasznalok = null;

console.log(felhasznalok?.[0]);
```

Kimenet:

```
undefined
```

Hagyományos tömbindexelés esetén a `null` vagy `undefined` értéken történő indexelés hibát eredményezne.

### 4.1. Tömb egy elemének tulajdonsága

A tömb elemeinek tulajdonságait is elérhetjük optional chaining segítségével.

```javascript
const felhasznalok = [
    {
        nev: 'Anna',
        eletkor: 25,
    },
    {
        nev: 'Péter',
        eletkor: 30,
    },
];

console.log(felhasznalok?.[0]?.nev);
console.log(felhasznalok?.[1]?.eletkor);
```

Kimenet:

```
Anna
30
```

Ha a tömb vagy annak valamelyik eleme hiányzik, az opcionális láncolás megakadályozza a hozzáférésből eredő hibát.

## 5. Függvények meghívása optional chaining segítségével

Az optional chaining segítségével egy függvény meghívását is biztonságossá tehetjük.

Ehhez a `?.()` szintaxist használjuk.

Példa:

```javascript
const felhasznalo = {
    nev: 'Anna',
    koszont: function () {
        console.log('Szia!');
    },
};

felhasznalo.koszont?.();
```

Kimenet:

```
Szia!
```

Ha a `koszont` függvény nem létezik, akkor a program nem próbálja meg meghívni, hanem `undefined` értéket ad vissza.

```javascript
const felhasznalo = {
    nev: 'Anna',
};

felhasznalo.koszont?.();

console.log('A program folytatódik.');
```

Kimenet:

```
A program folytatódik.
```

### 5.1. Fontos különbség: hiányzó függvény és nem függvény típusú érték

A `?.()` akkor védi meg a kódot a hibától, ha a meghívni kívánt érték `null` vagy `undefined`.

Ha az érték létezik, de nem függvény, akkor továbbra is hibát kapunk.

```javascript
const felhasznalo = {
    koszont: 'Szia!',
};

felhasznalo.koszont?.();
```

Ez a kód hibát eredményez, mert a `koszont` értéke szöveg, nem pedig meghívható függvény.

## 6. Dinamikus tulajdonságnevek kezelése

Az objektumok tulajdonságait nemcsak ponttal, hanem szögletes zárójellel is elérhetjük.

Az optional chaining ezt a formát is támogatja.

```javascript
const felhasznalo = {
    nev: 'Anna',
    eletkor: 25,
};

let tulajdonsag = 'nev';

console.log(felhasznalo?.[tulajdonsag]);
```

Kimenet:

```
Anna
```

A `?.[tulajdonsag]` akkor hasznos, ha a tulajdonság neve egy változóban található, és az objektum esetleg nem létezik.

```javascript
const felhasznalo = null;

let tulajdonsag = 'nev';

console.log(felhasznalo?.[tulajdonsag]);
```

Kimenet:

```
undefined
```

## 7. Optional chaining és nullish coalescing együtt

Az optional chaining (`?.`) és a nullish coalescing (`??`) operátorokat gyakran együtt használjuk.

A két operátor különböző feladatot lát el:

- A `?.` biztonságosan eléri az objektum tulajdonságát.
- A `??` alapértelmezett értéket biztosít, ha az eredmény `null` vagy `undefined`.

Példa:

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    cim: null,
};

let varos = felhasznalo.cim?.varos ?? 'Nincs megadva';

console.log(varos);
```

Kimenet:

```
Nincs megadva
```

A program először megpróbálja elérni a `cim` objektum `varos` tulajdonságát. Mivel a `cim` értéke `null`, az optional chaining eredménye `undefined` lesz.

Ezután a `??` operátor a `"Nincs megadva"` értéket választja.

Másik példa:

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    cim: {
        varos: 'Budapest',
    },
};

let varos = felhasznalo.cim?.varos ?? 'Nincs megadva';

console.log(varos);
```

Kimenet:

```
Budapest
```

Ebben az esetben a `varos` tulajdonság létezik, ezért az eredeti értéket kapjuk meg.

## 8. Optional chaining használata gyakorlati programozási helyzetekben

### 8.1. Felhasználói adatok megjelenítése

Egy alkalmazásban előfordulhat, hogy a felhasználó nem tölt ki minden adatot.

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    profil: {
        telefonszam: null,
        email: 'anna@example.com',
    },
};

let telefonszam = felhasznalo.profil?.telefonszam ?? 'Nincs telefonszám';
let email = felhasznalo.profil?.email ?? 'Nincs e-mail-cím';

console.log(telefonszam);
console.log(email);
```

Kimenet:

```
Nincs telefonszám
anna@example.com
```

### 8.2. Szerverről érkező adatok kezelése

Egy webalkalmazásban az adatokat gyakran egy API-tól kapjuk meg. Nem garantált, hogy minden adatmező szerepel a válaszban.

```javascript
const valasz = {
    felhasznalo: {
        nev: 'Péter',
        cim: {
            varos: 'Szeged',
        },
    },
};

let varos = valasz.felhasznalo?.cim?.varos ?? 'Ismeretlen város';

console.log(varos);
```

Kimenet:

```
Szeged
```

Ha a szerver nem küldene `cim` vagy `felhasznalo` adatot, a program akkor sem állna le ennél a hozzáférésnél.

### 8.3. Opcionális eseménykezelő meghívása

Előfordulhat, hogy egy függvény meghívása nem kötelező, mert csak bizonyos helyzetekben érhető el.

```javascript
function feldolgozas(callback) {
    console.log('Feldolgozás elkezdődött.');

    callback?.();

    console.log('Feldolgozás befejeződött.');
}

feldolgozas(() => {
    console.log('A visszahívási függvény lefutott.');
});

feldolgozas();
```

Kimenet:

```
Feldolgozás elkezdődött.
A visszahívási függvény lefutott.
Feldolgozás befejeződött.
Feldolgozás elkezdődött.
Feldolgozás befejeződött.
```

A második függvényhívásnál nem adtunk át callbacket, ezért az optional chaining miatt nem történik függvényhívás, és nem keletkezik hiba.

## 9. Az optional chaining korlátai és gyakori hibák

### 9.1. Nem minden hibát akadályoz meg

Az optional chaining kizárólag a `null` és `undefined` értékekből eredő hozzáférési hibák egy részét kezeli.

Nem ellenőrzi például, hogy egy objektum tulajdonsága megfelelő típusú-e.

```javascript
const felhasznalo = {
    cim: 'Budapest',
};

console.log(felhasznalo.cim?.varos);
```

A `cim` értéke létezik, de szöveg, ezért a `varos` tulajdonság értéke `undefined` lesz. Ez nem feltétlenül okoz hibát, de nem is biztos, hogy a program a kívánt eredményt kapja.

### 9.2. Nem használható értékadás bal oldalán

Az optional chaining nem használható közvetlenül értékadás bal oldalán.

Hibás példa:

```javascript
let felhasznalo = {};

felhasznalo?.nev = 'Anna';
```

A JavaScript szintaktikai hibát jelez.

Helyes megoldás:

```javascript
let felhasznalo = {};

if (felhasznalo !== null && felhasznalo !== undefined) {
    felhasznalo.nev = 'Anna';
}
```

### 9.3. Nem helyettesíti az összes ellenőrzést

Az optional chaining kényelmesebbé teszi az adatok elérését, de nem jelenti azt, hogy minden adatot ellenőrzés nélkül használhatunk.

Például:

```javascript
const felhasznalo = null;

let nev = felhasznalo?.nev;

console.log(nev.toUpperCase());
```

Ez a kód hibát okoz, mert a `nev` értéke `undefined`, és azon nem hívható meg a `toUpperCase()` metódus.

Biztonságosabb megoldás:

```javascript
const felhasznalo = null;

let nev = felhasznalo?.nev;

console.log(nev?.toUpperCase() ?? 'Nincs név megadva');
```

Kimenet:

```
Nincs név megadva
```

### 9.4. Az optional chaining és a nullish coalescing nem ugyanaz

A két operátor együtt is használható, de eltérő feladatot látnak el.

| Operátor | Feladat                                                                    |
| -------- | -------------------------------------------------------------------------- |
| `?.`     | Biztonságos tulajdonság-, elem- vagy függvényelérés                        |
| `??`     | Alapértelmezett érték megadása `null` vagy `undefined` esetén              |
| `??=`    | Alapértelmezett érték hozzárendelése, ha a változó `null` vagy `undefined` |

## 10. Összefoglalás

Az optional chaining operátor (`?.`) segítségével biztonságosan érhetjük el objektumok tulajdonságait, tömbök elemeit és függvényeket akkor is, ha az adott érték esetleg `null` vagy `undefined`.

A legfontosabb formái:

| Szintaxis               | Jelentés                                      |
| ----------------------- | --------------------------------------------- |
| `objektum?.nev`         | Opcionális tulajdonságelérés                  |
| `tomb?.[0]`             | Opcionális tömbelem-elérés                    |
| `objektum.fuggveny?.()` | Opcionális függvényhívás                      |
| `objektum?.[kulcs]`     | Opcionális elérés dinamikus tulajdonságnévvel |

Fontos tudnivalók:

- A `?.` megakadályozza a `null` és `undefined` értékeken történő védett hozzáférésből eredő hibát.
- Ha a láncolás során hiányzó értéket talál, az eredmény `undefined` lesz.
- Többszintű objektumoknál több helyen is használható.
- Tömbök és függvények kezelésére is alkalmas.
- A `??` operátorral együtt alapértelmezett értékeket is megadhatunk.
- Nem használható közvetlenül értékadás bal oldalán.
- Nem helyettesíti az adatok típusának és tartalmának ellenőrzését.

# 11. Ellenőrző kérdések

1. Mi az optional chaining operátor, és milyen problémát old meg?
2. Milyen jelet használunk az optional chaining operátorhoz?
3. Mi történik, ha egy objektum értéke `null`, és a tulajdonságát `?.` segítségével próbáljuk elérni?
4. Mi a különbség a hagyományos `objektum.nev` és az `objektum?.nev` kifejezés között?
5. Hogyan használhatjuk az optional chaining operátort tömbök elemeinek elérésére?
6. Mire szolgál a `?.()` szintaxis?
7. Hogyan érhetünk el biztonságosan egy több szintből álló, beágyazott objektumtulajdonságot?
8. Mi a különbség az optional chaining (`?.`) és a nullish coalescing (`??`) operátor között?
9. Miért nem használható az optional chaining közvetlenül egy értékadás bal oldalán?
10. Miért nem helyettesíti az optional chaining az adatok típusának és tartalmának ellenőrzését?

# 12. Gyakorlati feladatok

Az alábbi feladatokat JavaScriptben, megoldás nélkül készítsd el!

1. Egyszerű objektumtulajdonság elérése: Hozz létre egy `felhasznalo` objektumot `nev` és `eletkor` tulajdonságokkal. Az optional chaining operátor segítségével jelenítsd meg mindkét tulajdonság értékét!
2. Hiányzó objektum kezelése: Hozz létre egy `felhasznalo` változót `null` értékkel. Próbáld meg az optional chaining segítségével elérni a `nev` tulajdonságát! Jelenítsd meg az eredményt!
3. Beágyazott objektum: Hozz létre egy `felhasznalo` objektumot, amely tartalmaz egy `cim` nevű beágyazott objektumot. A `cim` objektum tartalmazza a `varos` és az `utca` tulajdonságokat. Az optional chaining segítségével jelenítsd meg a város nevét!
4. Hiányzó beágyazott objektum: Hozz létre egy `felhasznalo` objektumot, amelynek `cim` tulajdonsága `null`. Optional chaining segítségével próbáld meg elérni a `cim.varos` értékét! A program ne okozzon futásidejű hibát!
5. Tömb elemének elérése: Hozz létre egy legalább három elemből álló tömböt, amely felhasználók neveit tartalmazza. Az optional chaining segítségével jelenítsd meg a tömb első és második elemét!
6. Hiányzó tömb kezelése: Hozz létre egy `termekek` változót `undefined` értékkel. Az optional chaining segítségével próbáld meg elérni a tömb első elemét!
7. Opcionális függvényhívás: Hozz létre egy `felhasznalo` objektumot, amely tartalmaz egy `koszont` nevű függvényt. Hívd meg a függvényt a `?.()` operátor segítségével! Ezután próbáld meg ugyanezt egy olyan objektummal, amely nem tartalmazza ezt a függvényt!
8. Dinamikus tulajdonságelérés: Hozz létre egy `felhasznalo` objektumot `nev`, `eletkor` és `varos` tulajdonságokkal. Egy külön változóban tárold el a tulajdonság nevét, majd optional chaining segítségével jelenítsd meg az adott értéket!
9. Optional chaining és nullish coalescing együtt: Hozz létre egy `felhasznalo` objektumot, amelynek `profil` tulajdonsága tartalmaz egy `bemutatkozas` mezőt. Ha a profil vagy a bemutatkozás hiányzik, jelenítsd meg a `"Nincs bemutatkozás"` szöveget. Használd együtt a `?.` és a `??` operátorokat!
10. Termékadatok feldolgozása: Hozz létre egy `termek` objektumot, amely tartalmazza a termék nevét, árát és egy `gyarto` nevű beágyazott objektumot. A gyártó objektum tartalmazza a gyártó nevét és országát. Készíts olyan megoldást, amely optional chaining segítségével biztonságosan eléri a gyártó adatait, és `??` operátorral alapértelmezett értéket ad, ha valamelyik adat hiányzik!
