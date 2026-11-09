# Feltételes elágazás JavaScriptben (`if`, `else if`, `else`)

## 1. A feltételes elágazás fogalma

A programozás során gyakran előfordul, hogy egy adott műveletet csak bizonyos feltételek teljesülése esetén szeretnénk végrehajtani.

Például:

- Ha egy szám pozitív, írjuk ki, hogy pozitív.
- Ha egy felhasználó elmúlt 18 éves, engedélyezzük a regisztrációt.
- Ha egy termék ára meghaladja a 10 000 Ft-ot, adjunk kedvezményt.
- Ha egy jelszó megfelelő hosszúságú, engedjük tovább a felhasználót.

Ezeket a döntési helyzeteket feltételes elágazásokkal tudjuk megvalósítani.

A JavaScript három fontos utasítást biztosít erre:

- `if` – egy feltétel vizsgálata.
- `else if` – további feltételek vizsgálata.
- `else` – minden más eset kezelése.

A feltételes elágazás segítségével a program futása különböző irányokba haladhat attól függően, hogy egy adott feltétel igaz vagy hamis.

## 2. Az if utasítás

Az `if` utasítás segítségével megvizsgálhatunk egy feltételt.

Ha a feltétel igaz (`true`), akkor végrehajtódik az `if` utasítás blokkja.

Ha a feltétel hamis (`false`), akkor a blokkban található utasítások kimaradnak.

Alapszintaxis:

```javascript
if (feltetel) {
    // Végrehajtandó utasítások
}
```

Példa:

```javascript
let eletkor = 20;

if (eletkor >= 18) {
    console.log('Nagykorú vagy!');
}
```

A program működése:

1. Létrehozunk egy `eletkor` változót.
2. Értéke 20.
3. Az `if` megvizsgálja, hogy az életkor legalább 18-e.
4. Mivel a feltétel igaz, végrehajtódik a blokk.
5. A konzolon megjelenik a következő szöveg:

```
Nagykorú vagy!
```

Mi történik, ha az életkor 16?

```javascript
let eletkor = 16;

if (eletkor >= 18) {
    console.log('Nagykorú vagy!');
}
```

Ebben az esetben a feltétel hamis, ezért a program nem ír ki semmit.

## 3. Az else utasítás

Az `else` segítségével megadhatjuk, hogy mi történjen akkor, ha az `if` feltétele nem teljesül.

Az `else` mindig egy `if` vagy `else if` után következik.

Alapszintaxis:

```javascript
if (feltetel) {
    // Ha a feltétel igaz
} else {
    // Ha a feltétel hamis
}
```

Példa:

```javascript
let eletkor = 16;

if (eletkor >= 18) {
    console.log('Nagykorú vagy!');
} else {
    console.log('Még nem vagy nagykorú!');
}
```

A program működése:

- Ha az életkor legalább 18, az első blokk hajtódik végre.
- Ha az életkor kisebb 18-nál, az `else` blokk hajtódik végre.

A program eredménye:

```
Még nem vagy nagykorú!
```

Fontos: az `else` nem tartalmaz feltételt. Akkor hajtódik végre, ha az előtte álló feltételes ágak egyike sem teljesült.

## 4. Az else if utasítás

Előfordulhat, hogy nemcsak két lehetőség közül kell választanunk, hanem több különböző esetet is kezelni szeretnénk.

Erre használjuk az `else if` utasítást.

Az `else if` lehetővé teszi, hogy több feltételt egymás után vizsgáljunk.

Alapszintaxis:

```javascript
if (elso_feltetel) {
    // Első eset
} else if (masodik_feltetel) {
    // Második eset
} else if (harmadik_feltetel) {
    // Harmadik eset
} else {
    // Egyik feltétel sem teljesült
}
```

Példa – osztályzat meghatározása:

```javascript
let pontszam = 85;

if (pontszam >= 90) {
    console.log('Jeles');
} else if (pontszam >= 80) {
    console.log('Jó');
} else if (pontszam >= 70) {
    console.log('Közepes');
} else if (pontszam >= 60) {
    console.log('Elégséges');
} else {
    console.log('Elégtelen');
}
```

A program eredménye:

```
Jó
```

A működés magyarázata:

1. Megvizsgálja, hogy a pontszám legalább 90-e. Nem igaz.
2. Megvizsgálja, hogy a pontszám legalább 80-e. Igaz.
3. Végrehajtja a második feltételhez tartozó blokkot.
4. A további feltételeket már nem vizsgálja.

A `85` pontszámhoz tehát a `Jó` eredmény tartozik.

## 5. A feltételek kiértékelésének sorrendje

Az `if` és `else if` utasítások kiértékelése felülről lefelé történik.

A JavaScript az első igaz feltételnél végrehajtja a hozzá tartozó kódblokkot, majd kilép az egész feltételes szerkezetből.

Ezért nagyon fontos a feltételek megfelelő sorrendje.

Helyes megoldás:

```javascript
let eletkor = 15;

if (eletkor >= 18) {
    console.log('Felnőtt');
} else if (eletkor >= 14) {
    console.log('Tinédzser');
} else {
    console.log('Gyermek');
}
```

Eredmény:

```
Tinédzser
```

Hibás megoldás:

```javascript
let eletkor = 15;

if (eletkor >= 14) {
    console.log('Tinédzser');
} else if (eletkor >= 18) {
    console.log('Felnőtt');
} else {
    console.log('Gyermek');
}
```

Ebben az esetben a program már az első feltételnél megáll, mert a 15 nagyobb 14-nél.

A második feltétel soha nem kerül ellenőrzésre, így a program nem tudja megfelelően kezelni a felnőtt kategóriát.

Tanulság: az egymást átfedő feltételeket úgy kell sorrendbe állítani, hogy a specifikusabb vagy szigorúbb feltételek kerüljenek előre.

## 6. Összehasonlító operátorok használata

A feltételes elágazásokban gyakran használunk összehasonlító operátorokat.

| Operátor | Jelentés                  | Példa      |
| -------- | ------------------------- | ---------- |
| `==`     | Érték szerinti egyenlőség | `a == 10`  |
| `===`    | Szigorú egyenlőség        | `a === 10` |
| `!=`     | Nem egyenlő               | `a != 10`  |
| `!==`    | Szigorúan nem egyenlő     | `a !== 10` |
| `>`      | Nagyobb                   | `a > 10`   |
| `<`      | Kisebb                    | `a < 10`   |
| `>=`     | Nagyobb vagy egyenlő      | `a >= 10`  |
| `<=`     | Kisebb vagy egyenlő       | `a <= 10`  |

Példa:

```javascript
let szam = 10;

if (szam === 10) {
    console.log('A szám pontosan 10.');
}
```

A `===` operátor az értéket és az adattípust is ellenőrzi.

Például:

```javascript
console.log(10 == '10'); // true
console.log(10 === '10'); // false
```

JavaScriptben általában a `===` és `!==` használata ajánlott, mert ezek elkerülik a nem kívánt automatikus típuskonverziókat.

## 7. Logikai operátorok feltételes elágazásokban

Előfordulhat, hogy egy feltétel teljesüléséhez több feltételnek is igaznak kell lennie.

Erre a logikai operátorokat használjuk.

Három fontos logikai operátor:

| Operátor | Jelentés | Működés                                       |
| -------- | -------- | --------------------------------------------- |
| `&&`     | ÉS       | Minden feltételnek igaznak kell lennie.       |
| `\|\| `  | VAGY     | Legalább egy feltételnek igaznak kell lennie. |
| `!`      | NEM      | Megfordítja a logikai értéket.                |

Példa – ÉS operátor:

```javascript
let eletkor = 25;
let vanJogositvany = true;

if (eletkor >= 18 && vanJogositvany === true) {
    console.log('Vezethetsz autót!');
}
```

Mindkét feltételnek teljesülnie kell.

Példa – VAGY operátor:

```javascript
let nap = 'szombat';

if (nap === 'szombat' || nap === 'vasarnap') {
    console.log('Hétvége van!');
}
```

Már az egyik feltétel teljesülése is elegendő.

Példa – NEM operátor:

```javascript
let bejelentkezve = false;

if (!bejelentkezve) {
    console.log('Kérjük, jelentkezz be!');
}
```

A `!` megfordítja a logikai értéket, így a `!false` eredménye `true`.

## 8. Többszörös feltételes elágazások

Egy `if` blokkon belül további feltételes elágazásokat is elhelyezhetünk.

Ezt egymásba ágyazott feltételes elágazásnak nevezzük.

Példa:

```javascript
let eletkor = 22;
let vanJegy = true;

if (eletkor >= 18) {
    if (vanJegy === true) {
        console.log('Beléphetsz!');
    } else {
        console.log('Nincs jegyed!');
    }
} else {
    console.log('Nem vagy nagykorú!');
}
```

A program működése:

1. Először megvizsgálja az életkort.
2. Ha az életkor legalább 18, továbblép a belső feltételhez.
3. Megvizsgálja, hogy van-e jegy.
4. Ha van jegy, engedélyezi a belépést.
5. Ha nincs jegy, kiírja a megfelelő üzenetet.
6. Ha az életkor kisebb 18-nál, a belső feltétel már nem hajtódik végre.

Az egymásba ágyazott feltételek hasznosak lehetnek összetett döntési helyzetekben, de túlzott használatuk nehezebben olvasható kódot eredményezhet.

## 9. A feltételek és a truthy/falsy értékek kapcsolata

JavaScriptben az `if` feltételében nem kizárólag `true` és `false` értékek szerepelhetnek.

Más adattípusok értékeit is képes logikai értékként értelmezni.

Ezt nevezzük truthy és falsy működésnek.

Falsy értékek:

- `false`
- `0`
- `-0`
- `0n`
- `""` (üres szöveg)
- `null`
- `undefined`
- `NaN`

Minden más érték truthy, például:

- `"hello"`
- `"0"`
- `100`
- `-5`
- `[]`
- `{}`

Példa:

```javascript
let nev = '';

if (nev) {
    console.log('A név meg van adva.');
} else {
    console.log('A név üres!');
}
```

Eredmény:

```
A név üres!
```

A `nev` változó értéke üres szöveg, ezért falsy értéknek számít.

Másik példa:

```javascript
let felhasznalo = [];

if (felhasznalo) {
    console.log('Van felhasználói adat.');
} else {
    console.log('Nincs felhasználói adat.');
}
```

A program az első üzenetet írja ki, mert egy üres tömb is truthy érték.

Ezért fontos, hogy ne keverjük össze az üres tömböt az `undefined` vagy `null` értékkel.

## 10. Gyakori hibák a feltételes elágazások használatakor

1\. Egyenlőség helyett értékadás használata

Hibás példa:

```javascript
let szam = 10;

if ((szam = 5)) {
    console.log('Öt');
}
```

A `=` értékadást végez, nem összehasonlítást.

Helyes:

```javascript
if (szam === 5) {
    console.log('Öt');
}
```

2\. Rossz feltételsorrend

Ha egy általános feltétel megelőz egy szűkebb feltételt, előfordulhat, hogy a későbbi ág soha nem hajtódik végre.

3\. Kapcsos zárójelek elhagyása

Az `if` és az `else` blokkjainál a kapcsos zárójelek használata ajánlott, akkor is, ha csak egy utasítás található bennük.

4\. Logikai operátorok helytelen használata

Például az `&&` és az `||` felcserélése teljesen más működést eredményezhet.

5\. Nem megfelelő adattípus összehasonlítása

A szövegként tárolt szám és a valódi szám nem minden esetben viselkedik azonosan.

# 10 ellenőrző kérdés

A kérdések mindegyikénél egyetlen helyes választ kell kiválasztani.

1\. Mire használjuk az `if` utasítást?

A) Változók létrehozására.

B) Feltétel vizsgálatára.

C) Ciklusok létrehozására.

D) Függvények meghívására.

2\. Mikor hajtódik végre az `else` blokk?

A) Mindig.

B) Csak akkor, ha az `if` feltétele igaz.

C) Ha az előtte álló feltételek egyike sem teljesült.

D) Csak akkor, ha a változó értéke nulla.

3\. Mire használjuk az `else if` utasítást?

A) Új változó létrehozására.

B) További feltételek vizsgálatára.

C) Egy ciklus megszakítására.

D) Egy függvény visszatérési értékének módosítására.

4\. Mi történik, ha egy `if` feltétele hamis, és nincs hozzá `else` ág?

A) A program leáll.

B) Hiba keletkezik.

C) Az `if` blokk kimarad.

D) Az `if` blokk mindig végrehajtódik.

5\. Mit jelent a `===` operátor?

A) Csak az értékeket hasonlítja össze.

B) Értéket ad egy változónak.

C) Az értéket és az adattípust is összehasonlítja.

D) Megfordítja a logikai értéket.

6\. Mit jelent az `&&` operátor?

A) VAGY.

B) ÉS.

C) NEM.

D) Egyenlőség.

7\. Melyik érték számít falsy értéknek JavaScriptben?

A) `"0"`

B) `[]`

C) `0`

D) `{}`

8\. Mi lesz a következő kód eredménye?

```javascript
let szam = 15;

if (szam > 20) {
    console.log('A');
} else if (szam > 10) {
    console.log('B');
} else {
    console.log('C');
}
```

A) A

B) B

C) C

D) Nem jelenik meg semmi.

9\. Hány `else if` ágat használhatunk egy feltételes szerkezetben?

A) Legfeljebb egyet.

B) Legfeljebb kettőt.

C) Tetszőleges számút.

D) Egyet sem.

10\. Mi történik, ha az első `if` feltétel igaz egy többágú feltételes szerkezetben?

A) Az összes további ág végrehajtódik.

B) Csak az első igaz feltételhez tartozó blokk hajtódik végre.

C) Az `else` blokk hajtódik végre.

D) A program hibával leáll.

# 10 gyakorlati feladat

A feladatokat JavaScriptben, önállóan oldd meg! A megoldások során használj `if`, `else if` és `else` utasításokat.

## 1. Pozitív, negatív vagy nulla

Hozz létre egy `szam` nevű változót.

A program vizsgálja meg az értékét!

- Ha a szám pozitív, írja ki: `Pozitív szám`.
- Ha negatív, írja ki: `Negatív szám`.
- Ha nulla, írja ki: `A szám nulla`.

## 2. Páros vagy páratlan

Hozz létre egy egész számot tároló változót.

A program döntse el, hogy a szám páros vagy páratlan!

Segítség: használd a maradékos osztás (`%`) operátort.

## 3. Életkor szerinti besorolás

Hozz létre egy `eletkor` változót.

A program az alábbi kategóriák alapján sorolja be a felhasználót:

- 0–12 év: Gyermek.
- 13–17 év: Tinédzser.
- 18–64 év: Felnőtt.
- 65 évtől: Nyugdíjas korú.

A negatív életkort kezeld érvénytelen adatként!

## 4. Osztályzat meghatározása

Hozz létre egy `pontszam` változót, amely 0 és 100 közötti értéket tárol.

A program az alábbiak szerint határozza meg az osztályzatot:

| Pontszám | Osztályzat |
| -------- | ---------- |
| 0–49     | Elégtelen  |
| 50–64    | Elégséges  |
| 65–79    | Közepes    |
| 80–89    | Jó         |
| 90–100   | Jeles      |

Ha a pontszám kívül esik a megadott tartományon, jelenítsen meg hibaüzenetet!

## 5. Legnagyobb szám meghatározása

Hozz létre három változót:

```javascript
let a = 15;
let b = 28;
let c = 12;
```

A program határozza meg, hogy melyik szám a legnagyobb!

Az eredményt jelenítse meg a konzolon.

Az egyenlő értékek esetét is kezeld!

## 6. Egyszerű belépési rendszer

Hozz létre két változót:

```javascript
let felhasznalonev = 'admin';
let jelszo = 'titok123';
```

A program ellenőrizze a belépési adatokat!

- Ha mindkettő helyes, írja ki: `Sikeres bejelentkezés!`
- Ha a felhasználónév hibás, írja ki: `Hibás felhasználónév!`
- Ha a jelszó hibás, írja ki: `Hibás jelszó!`

## 7. Kedvezmény kiszámítása

Hozz létre egy `vasarlasOsszege` változót.

A program az alábbi kedvezményeket alkalmazza:

- 0–9999 Ft: nincs kedvezmény.
- 10000–29999 Ft: 5% kedvezmény.
- 30000–49999 Ft: 10% kedvezmény.
- 50000 Ft felett: 15% kedvezmény.

A program írja ki:

- Az eredeti vásárlási összeget.
- A kedvezmény mértékét.
- A fizetendő összeget.

A negatív összeget kezeld hibás adatként!

## 8. Hónap napjainak meghatározása

Hozz létre egy `honap` változót, amely 1 és 12 közötti számot tárol.

A program határozza meg a hónap nevét és napjainak számát!

Például:

- 1: Január – 31 nap.
- 2: Február – 28 vagy 29 nap.
- 4: Április – 30 nap.
- 12: December – 31 nap.

A február esetében egyelőre használj 28 napot.

Érvénytelen hónapszám esetén jeleníts meg hibaüzenetet!

## 9. Egyszerű számológép

Hozz létre három változót:

```javascript
let a = 20;
let b = 5;
let muvelet = '/';
```

A `muvelet` változó értéke alapján végezd el a megfelelő műveletet!

Lehetséges műveletek:

- `+` összeadás.
- `-` kivonás.
- `*` szorzás.
- `/` osztás.

Ha az osztásnál a második szám nulla, jeleníts meg hibaüzenetet!

Ismeretlen művelet esetén is jeleníts meg hibaüzenetet!

## 10. Épületek látogatószám szerinti besorolása

Hozz létre egy `latogatokSzama` változót.

A program az alábbi kategóriákba sorolja az épületeket:

- 0–1 000 000: Kevés látogató.
- 1 000 001–5 000 000: Közepes látogatottság.
- 5 000 001–10 000 000: Nagy látogatottság.
- 10 000 000 felett: Kiemelkedő látogatottság.

A program jelenítse meg a megfelelő kategóriát!

A negatív látogatószámot kezelje érvénytelen adatként.

## Összefoglalás

A feltételes elágazás a programozás egyik alapvető vezérlési szerkezete.

| Utasítás  | Feladata                      |
| --------- | ----------------------------- |
| `if`      | Egy feltétel vizsgálata       |
| `else if` | További feltételek vizsgálata |
| `else`    | Minden más eset kezelése      |

A feltételes elágazások segítségével a program képes döntéseket hozni, adatokat ellenőrizni, felhasználói műveleteket kezelni és különböző üzleti logikákat megvalósítani.
