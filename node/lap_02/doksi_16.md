# Nullish coalescing operátor (`??`) JavaScriptben

## 1. Mi az a nullish coalescing operátor?

A nullish coalescing operátor (`??`) a JavaScript egyik speciális operátora, amely segítségével alapértelmezett értéket rendelhetünk egy változóhoz vagy kifejezéshez, ha annak értéke `null` vagy `undefined`.

Magyarul gyakran nullérték-összefésülő operátornak is nevezik.

A legfontosabb tulajdonsága, hogy kizárólag két értéket tekint hiányzónak:

- `null`
- `undefined`

Ha a bal oldali érték nem `null` és nem `undefined`, akkor azt adja vissza, egyébként a jobb oldali értéket.

### Általános szintaxis

```javascript
valtozo ?? alapertelmezettErtek;
```

Működése:

- Ha a `valtozo` értéke `null` vagy `undefined`, akkor az `alapertelmezettErtek` kerül felhasználásra.
- Minden más esetben a `valtozo` eredeti értékét kapjuk.

## 2. A nullish coalescing operátor alapvető működése

Nézzünk egy egyszerű példát!

```javascript
let nev = null;

let megjelenitendoNev = nev ?? 'Ismeretlen';

console.log(megjelenitendoNev);
```

Kimenet:

```
Ismeretlen
```

A `nev` változó értéke `null`, ezért a `??` operátor a jobb oldalon található `"Ismeretlen"` szöveget adja vissza.

Ha a változó értéke nem hiányzó érték, akkor az eredeti érték marad érvényben.

```javascript
let nev = 'Anna';

let megjelenitendoNev = nev ?? 'Ismeretlen';

console.log(megjelenitendoNev);
```

Kimenet:

```
Anna
```

Mivel a `nev` változó értéke nem `null` és nem `undefined`, a jobb oldali alapértelmezett érték nem kerül felhasználásra.

## 3. A `null` és az `undefined` közötti különbség

A `??` operátor működésének megértéséhez fontos ismerni a `null` és az `undefined` jelentését.

### 3.1. `null`

A `null` azt jelenti, hogy egy változónak szándékosan nincs értéke.

```javascript
let felhasznaloNev = null;

console.log(felhasznaloNev);
```

A változó létezik, de jelenleg nincs hozzárendelve konkrét érték.

### 3.2. `undefined`

Az `undefined` azt jelenti, hogy egy érték még nincs meghatározva vagy hozzárendelve.

```javascript
let felhasznaloNev;

console.log(felhasznaloNev);
```

Kimenet:

```
undefined
```

A változót deklaráltuk, de nem adtunk neki kezdőértéket.

### 3.3. Mindkét eset kezelése a `??` operátorral

A nullish coalescing operátor mindkét értéket azonos módon kezeli.

```javascript
let nev1 = null;
let nev2 = undefined;

let eredmeny1 = nev1 ?? 'Nincs megadva';
let eredmeny2 = nev2 ?? 'Nincs megadva';

console.log(eredmeny1);
console.log(eredmeny2);
```

Kimenet:

```
Nincs megadva
Nincs megadva
```

## 4. A `??` és a logikai VAGY (`||`) operátor összehasonlítása

A nullish coalescing operátort gyakran hasonlítjuk össze a logikai VAGY (`||`) operátorral.

Mindkettő használható alapértelmezett érték megadására, azonban eltérően működnek.

A `||` operátor nemcsak a `null` és az `undefined` értékeket tekinti hamisnak, hanem minden olyan értéket is, amely a JavaScriptben falsy értéknek számít.

Ilyenek például:

- `false`
- `0`
- `-0`
- `""` (üres szöveg)
- `null`
- `undefined`
- `NaN`

A `??` operátor ezzel szemben kizárólag a `null` és az `undefined` értékeket kezeli hiányzó értékként.

### Példa a különbségre

```javascript
let darabszam = 0;

let eredmeny1 = darabszam || 10;
let eredmeny2 = darabszam ?? 10;

console.log(eredmeny1);
console.log(eredmeny2);
```

Kimenet:

```
10
0
```

Miért kapunk eltérő eredményt?

- A `||` operátor a `0` értéket hamisnak tekinti, ezért a `10` értéket adja vissza.
- A `??` operátor a `0` értéket érvényes értéknek tekinti, ezért megtartja.

### Összehasonlító táblázat

| Bal oldali érték | `ertek   \|\| 10` | `ertek ?? 10` |
| ---------------- | ----------------- | ------------- |
| `null`           | 10                | 10            |
| `undefined`      | 10                | 10            |
| `0`              | 10                | 0             |
| `false`          | 10                | false         |
| `""`             | 10                | `""`          |
| `25`             | 25                | 25            |
| `"Anna"`         | `"Anna"`          | `"Anna"`      |

Fontos: ha a `0`, a `false` vagy az üres szöveg érvényes adat lehet, akkor a `??` operátor általában megfelelőbb választás.

## 5. Alapértelmezett értékek megadása változóknál

A `??` operátort gyakran használjuk olyan esetekben, amikor egy változó értéke nem feltétlenül ismert.

Példa:

```javascript
let felhasznaloKor = undefined;

let kor = felhasznaloKor ?? 18;

console.log(kor);
```

Kimenet:

```
18
```

Ha a felhasználó életkora nem áll rendelkezésre, akkor a program a 18-as alapértelmezett értéket használja.

Másik példa:

```javascript
let termekAr = null;

let ar = termekAr ?? 0;

console.log(`A termék ára: ${ar} Ft`);
```

Kimenet:

```
A termék ára: 0 Ft
```

## 6. A nullish coalescing operátor használata objektumoknál

A `??` operátor objektumok tulajdonságainak kezelésénél is hasznos lehet.

Tegyük fel, hogy egy felhasználói objektumban nem minden adat szerepel.

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    eletkor: 25,
    telefonszam: null,
};

let telefon = felhasznalo.telefonszam ?? 'Nincs telefonszám';

console.log(telefon);
```

Kimenet:

```
Nincs telefonszám
```

A `telefonszam` tulajdonság értéke `null`, ezért a program az alapértelmezett szöveget jeleníti meg.

### Hiányzó objektumtulajdonság kezelése

Ha egy objektum nem tartalmazza a keresett tulajdonságot, annak értéke `undefined` lesz.

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
};

let email = felhasznalo.email ?? 'Nincs megadva';

console.log(email);
```

Kimenet:

```
Nincs megadva
```

A `??` operátor tehát a nem létező objektumtulajdonságok kezelésében is segítséget nyújt.

## 7. A nullish coalescing operátor függvényekben

Függvények paramétereinek vagy visszatérési értékeinek kezelésére is használhatjuk.

Példa:

```javascript
function koszont(nev) {
    let megjelenitendoNev = nev ?? 'Vendég';

    return `Szia, ${megjelenitendoNev}!`;
}

console.log(koszont('Anna'));
console.log(koszont(null));
console.log(koszont());
```

Kimenet:

```
Szia, Anna!
Szia, Vendég!
Szia, Vendég!
```

Ha a függvény nem kap paramétert, akkor a `nev` értéke `undefined` lesz. Ebben az esetben a `??` operátor a `"Vendég"` szöveget választja.

## 8. A nullish coalescing operátor és a ternáris operátor

A két operátor különböző feladatokra használható.

### Nullish coalescing (`??`)

Akkor használjuk, ha csak azt szeretnénk ellenőrizni, hogy egy érték `null` vagy `undefined`-e.

```javascript
let nev = null;

let eredmeny = nev ?? 'Ismeretlen';
```

### Ternáris operátor (`? :`)

Akkor használjuk, ha egy tetszőleges feltétel alapján két érték közül szeretnénk választani.

```javascript
let eletkor = 20;

let eredmeny = eletkor >= 18 ? 'Felnőtt' : 'Kiskorú';
```

### Összehasonlítás

| Szempont      | `??`                       | `? :`                               |
| ------------- | -------------------------- | ----------------------------------- |
| Elnevezés     | Nullish coalescing         | Ternáris operátor                   |
| Feladata      | Hiányzó érték kezelése     | Feltételes választás                |
| Vizsgált eset | `null`, `undefined`        | Bármilyen logikai feltétel          |
| Eredménye     | Bal vagy jobb oldali érték | Igaz vagy hamis ághoz tartozó érték |

## 9. A nullish coalescing operátor és a nullish coalescing assignment (`??=`)

A JavaScriptben létezik a `??=` értékadó operátor is.

Ez a `??` operátorhoz kapcsolódik, de közvetlenül módosítja a változó értékét.

A `??=` csak akkor rendel hozzá új értéket a változóhoz, ha annak jelenlegi értéke `null` vagy `undefined`.

Példa:

```javascript
let nev = null;

nev ??= 'Ismeretlen';

console.log(nev);
```

Kimenet:

```
Ismeretlen
```

A művelet ugyanazt az eredményt adja, mint:

```javascript
let nev = null;

nev = nev ?? 'Ismeretlen';

console.log(nev);
```

Ha a változó már rendelkezik érvényes értékkel, akkor a `??=` nem módosítja azt.

```javascript
let nev = 'Anna';

nev ??= 'Ismeretlen';

console.log(nev);
```

Kimenet:

```
Anna
```

## 10. Gyakori hibák és fontos tudnivalók

### 10.1. A `0` érték téves kezelése

Gyakori hiba, hogy a `||` operátort használjuk akkor is, amikor a nulla érvényes érték.

```javascript
let mennyiseg = 0;

let eredmeny = mennyiseg || 1;

console.log(eredmeny); // 1
```

Ha a nulla értéket is meg szeretnénk tartani, használjunk `??` operátort:

```javascript
let mennyiseg = 0;

let eredmeny = mennyiseg ?? 1;

console.log(eredmeny); // 0
```

### 10.2. A `false` érték megőrzése

A `false` is lehet érvényes adat, például egy beállítás vagy engedélyezési állapot esetén.

```javascript
let aktiv = false;

let allapot = aktiv ?? true;

console.log(allapot); // false
```

A program megőrzi a `false` értéket, mert az nem `null` és nem `undefined`.

### 10.3. Az üres szöveg megőrzése

```javascript
let felhasznaloNev = '';

let nev = felhasznaloNev ?? 'Ismeretlen';

console.log(nev); // ""
```

Az üres szöveg nem számít hiányzó értéknek a `??` operátor számára.

### 10.4. A `??` és a `||` közvetlen keverése

A JavaScriptben a `??` operátor nem használható közvetlenül a `&&` vagy a `||` operátorral ugyanabban a kifejezésben, zárójelezés nélkül.

Hibás példa:

```javascript
let eredmeny = a || b ?? c;
```

Helyes megoldás:

```javascript
let eredmeny = (a || b) ?? c;
```

Vagy:

```javascript
let eredmeny = a || (b ?? c);
```

A zárójelezés egyértelművé teszi a műveletek sorrendjét.

## 11. Összefoglalás

A nullish coalescing operátor (`??`) segítségével alapértelmezett értéket adhatunk meg olyan esetekre, amikor egy változó vagy kifejezés értéke `null` vagy `undefined`.

Általános szintaxisa:

```javascript
valtozo ?? alapertelmezettErtek;
```

A legfontosabb tudnivalók:

- A `??` kizárólag a `null` és az `undefined` értékeket tekinti hiányzónak.
- A `0`, `false` és `""` értékeket érvényes adatként kezeli.
- Gyakran használjuk alapértelmezett értékek megadására.
- Hasznos objektumok tulajdonságainak és függvényparamétereknek a kezelésénél.
- A `||` operátortól eltérően nem utasítja el a falsy értékeket.
- A `??=` operátor segítségével közvetlenül módosíthatjuk a változót, ha annak értéke `null` vagy `undefined`.

# 12. Ellenőrző kérdések

1. Mi a nullish coalescing operátor, és milyen feladat megoldására használjuk?
2. Milyen jelet használunk a nullish coalescing operátorhoz?
3. Melyik két értéket tekinti hiányzónak a `??` operátor?
4. Mi történik, ha a `??` operátor bal oldalán `null` érték szerepel?
5. Mi történik, ha a bal oldali érték `0`?
6. Mi a különbség a `??` és a `||` operátor működése között?
7. Miért lehet hasznos a `??` operátor objektumok tulajdonságainak kezelésénél?
8. Hogyan használhatjuk a `??` operátort függvények paramétereinél?
9. Mi a különbség a `??` és a ternáris (`? :`) operátor között?
10. Mire szolgál a `??=` operátor, és mikor módosítja a változó értékét?

# 13. Gyakorlati feladatok

Az alábbi feladatokat JavaScriptben, megoldás nélkül készítsd el!

1. Alapértelmezett név: Hozz létre egy `nev` változót `null` értékkel. A `??` operátor segítségével adj neki `"Ismeretlen"` alapértelmezett értéket, majd jelenítsd meg az eredményt!
2. Hiányzó életkor: Hozz létre egy `eletkor` változót `undefined` értékkel. Ha nincs megadva az életkor, használj `18` alapértelmezett értéket!
3. Nulla érték kezelése: Hozz létre egy `mennyiseg` változót `0` értékkel. A `??` operátor segítségével rendelj hozzá `10` alapértelmezett értéket! Ellenőrizd, hogy a nulla megmarad-e!
4. Logikai érték kezelése: Hozz létre egy `aktiv` változót `false` értékkel. A `??` operátor segítségével adj neki `true` alapértelmezett értéket! Jelenítsd meg az eredményt!
5. Üres szöveg kezelése: Hozz létre egy `felhasznaloNev` változót üres szöveggel. A `??` operátor segítségével adj neki `"Vendég"` alapértelmezett értéket! Vizsgáld meg az eredményt!
6. Objektum tulajdonságainak kezelése: Hozz létre egy `felhasznalo` objektumot, amely tartalmazza a `nev`, `eletkor` és `email` tulajdonságokat. Az `email` értéke legyen `null`. A `??` operátor segítségével jeleníts meg egy `"Nincs megadva"` szöveget, ha nincs e-mail-cím!
7. Függvény alapértelmezett paraméterrel: Készíts egy `koszont` nevű függvényt, amely egy nevet kap paraméterként. Ha a paraméter értéke `null` vagy `undefined`, a függvény a `"Vendég"` nevet használja. A függvény adjon vissza egy köszönő szöveget!
8. `??` és `||` összehasonlítása: Hozz létre egy `pontszam` változót `0` értékkel. Készíts két különböző eredményváltozót: az egyiknél használd a `||`, a másiknál a `??` operátort. Jelenítsd meg mindkét eredményt, és figyeld meg a különbséget!
9. Nullish coalescing assignment: Hozz létre egy `orszag` változót `null` értékkel. A `??=` operátor segítségével rendelj hozzá `"Magyarország"` értéket! Ezután ismételd meg a feladatot egy `"Ausztria"` kezdőértékű változóval!
10. Termékadatok kezelése: Hozz létre egy `termek` objektumot a következő tulajdonságokkal: `nev`, `ar`, `keszlet` és `leiras`. Legalább két tulajdonság értéke legyen `null`. A `??` operátor segítségével biztosíts alapértelmezett értékeket a hiányzó adatokhoz, majd jelenítsd meg a teljes termékinformációt!
