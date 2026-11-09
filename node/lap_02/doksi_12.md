# Logikai operátorok JavaScriptben

## 1. Mik azok a logikai operátorok?

A logikai operátorok segítségével logikai értékeket (`true` és `false`) kapcsolhatunk össze, illetve módosíthatjuk egy feltétel igazságértékét.

Leggyakrabban akkor használjuk őket, amikor egy programban több feltételt szeretnénk egyszerre megvizsgálni.

Például:

- A felhasználó elmúlt 18 éves és rendelkezik érvényes belépővel.
- A felhasználó adminisztrátor vagy moderátor.
- A felhasználó nem rendelkezik megfelelő jogosultsággal.

A JavaScript három alapvető logikai operátort biztosít:

| Operátor | Elnevezés         | Jelentés                                           |
| -------- | ----------------- | -------------------------------------------------- |
| `&&`     | Logikai ÉS (AND)  | Mindkét feltételnek igaznak kell lennie.           |
| `\|\| `  | Logikai VAGY (OR) | Legalább az egyik feltételnek igaznak kell lennie. |
| `!`      | Logikai NEM (NOT) | Megfordítja a logikai értéket.                     |

## 2. Logikai ÉS operátor (`&&`)

A `&&` operátor akkor ad `true` eredményt, ha mindkét feltétel igaz.

Ha akár az egyik feltétel hamis, akkor a teljes kifejezés eredménye `false` lesz.

Példa:

```javascript
let eletkor = 25;
let vanJogositvany = true;

let vezethet = eletkor >= 18 && vanJogositvany;

console.log(vezethet); // true
```

A példában két feltételt vizsgálunk:

1. A felhasználó legalább 18 éves-e?
2. Rendelkezik-e jogosítvánnyal?

Mivel mindkét feltétel igaz, a teljes kifejezés eredménye is `true`.

### 2.1. A logikai ÉS igazságtáblája

Az igazságtábla bemutatja, hogy a különböző bemeneti értékek esetén milyen eredményt ad az operátor.

| Első feltétel | Második feltétel | Eredmény |
| ------------- | ---------------- | -------- |
| `true`        | `true`           | `true`   |
| `true`        | `false`          | `false`  |
| `false`       | `true`           | `false`  |
| `false`       | `false`          | `false`  |

### 2.2. Több feltétel összekapcsolása

A `&&` operátorral kettőnél több feltételt is összekapcsolhatunk.

```javascript
let eletkor = 25;
let vanJogositvany = true;
let vanAuto = true;

if (eletkor >= 18 && vanJogositvany && vanAuto) {
    console.log('A felhasználó vezethet.');
} else {
    console.log('A felhasználó nem vezethet.');
}
```

A program csak akkor jeleníti meg a pozitív üzenetet, ha mindhárom feltétel teljesül.

## 3. Logikai VAGY operátor (`||`)

A `||` operátor akkor ad `true` eredményt, ha legalább az egyik feltétel igaz.

Csak akkor lesz az eredmény `false`, ha minden feltétel hamis.

Példa:

```javascript
let nap = 'szombat';

let hetvege = nap === 'szombat' || nap === 'vasarnap';

console.log(hetvege); // true
```

A program két feltételt vizsgál:

- A nap szombat?
- A nap vasárnap?

Mivel a nap szombat, az egyik feltétel igaz, ezért a teljes kifejezés eredménye `true`.

### 3.1. A logikai VAGY igazságtáblája

| Első feltétel | Második feltétel | Eredmény |
| ------------- | ---------------- | -------- |
| `true`        | `true`           | `true`   |
| `true`        | `false`          | `true`   |
| `false`       | `true`           | `true`   |
| `false`       | `false`          | `false`  |

### 3.2. Több feltétel összekapcsolása

```javascript
let szerepkor = 'admin';

if (szerepkor === 'admin' || szerepkor === 'moderator') {
    console.log('A felhasználó kezelheti a tartalmakat.');
} else {
    console.log('A felhasználónak nincs megfelelő jogosultsága.');
}
```

A program akkor engedélyezi a műveletet, ha a felhasználó adminisztrátor vagy moderátor.

## 4. Logikai NEM operátor (`!`)

A `!` operátor megfordítja egy logikai kifejezés eredményét.

- Ha az eredeti érték `true`, akkor az eredmény `false`.
- Ha az eredeti érték `false`, akkor az eredmény `true`.

Példa:

```javascript
let aktiv = true;

console.log(!aktiv); // false
```

Egy másik példa:

```javascript
let bejelentkezett = false;

if (!bejelentkezett) {
    console.log('Kérjük, jelentkezzen be!');
}
```

A `!bejelentkezett` kifejezés azt jelenti, hogy a felhasználó nincs bejelentkezve.

### 4.1. A logikai NEM igazságtáblája

| Eredeti érték | Negált érték |
| ------------- | ------------ |
| `true`        | `false`      |
| `false`       | `true`       |

### 4.2. Összehasonlító kifejezés tagadása

A `!` operátort nemcsak változók, hanem teljes összehasonlító kifejezések előtt is használhatjuk.

```javascript
let eletkor = 16;

console.log(!(eletkor >= 18)); // true
```

A zárójelben lévő feltétel eredménye `false`, mert a 16 nem nagyobb vagy egyenlő 18-cal. A `!` ezt az értéket megfordítja.

A következő két feltétel logikai szempontból egyenértékű:

```javascript
!(eletkor >= 18);
```

```javascript
eletkor < 18;
```

## 5. A logikai operátorok együttes használata

A gyakorlatban gyakran előfordul, hogy egy feltételben többféle logikai operátort is használunk.

Példa:

```javascript
let eletkor = 25;
let vanJogositvany = true;
let alkoholFogyasztas = false;

if (eletkor >= 18 && vanJogositvany && !alkoholFogyasztas) {
    console.log('A feltételek teljesülnek.');
} else {
    console.log('A feltételek nem teljesülnek.');
}
```

A program három feltételt vizsgál:

1. A felhasználó legalább 18 éves.
2. Rendelkezik jogosítvánnyal.
3. Nem fogyasztott alkoholt.

A harmadik feltételnél a `!` operátor megfordítja az `alkoholFogyasztas` változó értékét.

## 6. A logikai operátorok végrehajtási sorrendje

Ha egy kifejezésben többféle logikai operátort használunk, fontos figyelembe venni azok végrehajtási sorrendjét.

A JavaScriptben az alapvető sorrend:

1. `!` – Logikai NEM.
2. `&&` – Logikai ÉS.
3. `||` – Logikai VAGY.

Példa:

```javascript
let a = true;
let b = false;
let c = true;

let eredmeny = a || (b && c);

console.log(eredmeny); // true
```

A `&&` operátor magasabb precedenciával rendelkezik, ezért előbb hajtódik végre:

1. `b && c` → `false && true` → `false`
2. `a || false` → `true || false` → `true`

### 6.1. Zárójelek használata

A zárójelek segítségével egyértelművé tehetjük, hogy melyik műveletet szeretnénk először végrehajtani.

```javascript
let a = true;
let b = false;
let c = true;

let eredmeny = (a || b) && c;

console.log(eredmeny); // true
```

A zárójelekben lévő kifejezés értékelődik ki először.

Javaslat: összetettebb logikai feltételeknél használj zárójeleket, még akkor is, ha a műveleti sorrend egyébként egyértelmű. Így a kód könnyebben olvasható és értelmezhető.

## 7. Rövidzáras kiértékelés (Short-circuit evaluation)

A JavaScript logikai operátorai rövidzáras kiértékelést alkalmaznak. Ez azt jelenti, hogy bizonyos esetekben a programnak nem kell minden feltételt kiértékelnie ahhoz, hogy meghatározza a teljes kifejezés eredményét.

### 7.1. Rövidzáras kiértékelés a `&&` operátornál

Ha az első feltétel `false`, akkor a teljes ÉS kifejezés már nem lehet `true`. Ezért a JavaScript nem értékeli ki a második feltételt.

```javascript
let eredmeny = false && console.log('Ez nem fut le.');

console.log(eredmeny); // false
```

Mivel az első érték `false`, a második kifejezés végrehajtása elmarad.

### 7.2. Rövidzáras kiértékelés a `||` operátornál

Ha az első érték `true`, akkor a teljes VAGY kifejezés eredménye már biztosan `true`. Ezért a JavaScript nem értékeli ki a második feltételt.

```javascript
let eredmeny = true || console.log('Ez nem fut le.');

console.log(eredmeny); // true
```

### 7.3. Gyakorlati példa

A rövidzáras kiértékelés segítségével például ellenőrizhetjük, hogy egy objektum létezik-e, mielőtt valamelyik tulajdonságát megvizsgálnánk.

```javascript
let felhasznalo = null;

if (felhasznalo && felhasznalo.aktiv) {
    console.log('Aktív felhasználó.');
} else {
    console.log('A felhasználó nem érhető el vagy nem aktív.');
}
```

A JavaScript az első feltétel kiértékelésekor megállapítja, hogy a `felhasznalo` értéke `null`. Emiatt nem próbálja meg lekérdezni a `felhasznalo.aktiv` tulajdonságot, így elkerülhető a hibás tulajdonságelérés.

## 8. A logikai operátorok és a nem logikai értékek

A JavaScript logikai operátorai nem minden esetben kizárólag `true` vagy `false` értéket adnak vissza.

A `&&` és a `||` operátorok bizonyos esetekben az eredeti operandusok egyikét adják vissza.

Példa:

```javascript
console.log('alma' && 'körte'); // "körte"
console.log(0 && 'körte'); // 0

console.log('alma' || 'körte'); // "alma"
console.log(0 || 'körte'); // "körte"
```

Ennek megértéséhez fontos ismerni a truthy és falsy értékeket.

### 8.1. Falsy értékek

A JavaScript bizonyos értékeket hamisnak tekint, amikor logikai környezetben vizsgálja őket.

A legfontosabb falsy értékek:

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
- `[]`
- `{}`
- `42`

### 8.2. Az `&&` és a `||` visszatérési értéke

A `&&` operátor az első falsy értéket adja vissza, vagy ha minden operandus truthy, akkor az utolsót.

```javascript
console.log(10 && 20); // 20
console.log(10 && 0 && 30); // 0
```

A `||` operátor az első truthy értéket adja vissza, vagy ha minden operandus falsy, akkor az utolsót.

```javascript
console.log(0 || 10); // 10
console.log(0 || '' || 20); // 20
```

Ez a működés gyakran használható alapértelmezett érték megadásakor.

```javascript
let nev = '';

let megjelenitendoNev = nev || 'Ismeretlen felhasználó';

console.log(megjelenitendoNev); // Ismeretlen felhasználó
```

Ha a `nev` változó üres szöveget tartalmaz, akkor a program az alapértelmezett szöveget használja.

## 9. Nullish coalescing operátor (`??`)

A `??` operátor szorosan kapcsolódik a logikai operátorokhoz, de nem azonos a `||` operátorral.

Akkor adja vissza a jobb oldali értéket, ha a bal oldali érték `null` vagy `undefined`.

Példa:

```javascript
let nev = null;

let megjelenitendoNev = nev ?? 'Ismeretlen';

console.log(megjelenitendoNev); // Ismeretlen
```

A `??` és a `||` közötti különbség:

```javascript
let darabszam = 0;

console.log(darabszam || 10); // 10
console.log(darabszam ?? 10); // 0
```

A `||` a `0` értéket falsy értéknek tekinti, ezért a jobb oldali értéket adja vissza.

A `??` viszont csak a `null` és az `undefined` értékeket kezeli hiányzóként, ezért a `0` értéket megtartja.

## 10. Gyakori hibák a logikai operátorok használatakor

### 10.1. A `&&` és a `||` összekeverése

```javascript
let eletkor = 25;

if (eletkor >= 18 || eletkor <= 65) {
    console.log('A feltétel teljesül.');
}
```

Ez a feltétel nem megfelelő, ha azt szeretnénk ellenőrizni, hogy az életkor 18 és 65 közé esik-e.

A helyes megoldás:

```javascript
if (eletkor >= 18 && eletkor <= 65) {
    console.log('Az életkor megfelelő.');
}
```

### 10.2. A feltétel megismétlésének elfelejtése

Hibás megoldás:

```javascript
let szam = 15;

if (szam === 10 || 20) {
    console.log('A feltétel teljesül.');
}
```

A `20` önmagában truthy érték, ezért a feltétel mindig igaz lesz.

Helyes megoldás:

```javascript
if (szam === 10 || szam === 20) {
    console.log('A szám 10 vagy 20.');
}
```

### 10.3. A tagadás helytelen használata

```javascript
let aktiv = true;

if (!aktiv) {
    console.log('A felhasználó nem aktív.');
}
```

A `!aktiv` kifejezés az `aktiv` változó értékének ellentétét vizsgálja. Mivel a változó értéke `true`, a feltétel hamis lesz.

### 10.4. A zárójelek hiánya összetett feltételeknél

```javascript
let admin = false;
let moderator = true;
let aktiv = true;

let jogosult = admin || (moderator && aktiv);
```

A JavaScript először a `moderator && aktiv` részt értékeli ki, majd az eredményt kapcsolja össze az `admin` értékével.

A könnyebb olvashatóság érdekében célszerű egyértelmű zárójeleket használni:

```javascript
let jogosult = admin || (moderator && aktiv);
```

# 11. Ellenőrző kérdések

1. Mire használjuk a logikai operátorokat JavaScriptben?
2. Mikor ad `true` eredményt a `&&` operátor?
3. Mikor ad `true` eredményt a `||` operátor?
4. Mit csinál a `!` operátor?
5. Milyen eredményt ad a `true && false` kifejezés?
6. Milyen eredményt ad a `false || true` kifejezés?
7. Milyen sorrendben hajtódnak végre a `!`, `&&` és `||` operátorok?
8. Mit jelent a rövidzáras kiértékelés?
9. Mi a különbség a `||` és a `??` operátor között?
10. Mit jelent a falsy kifejezés, és melyek a legfontosabb falsy értékek JavaScriptben?

# 12. Gyakorlati feladatok

1\. feladat – Logikai ÉS

Hozz létre két logikai változót. Az egyik értéke legyen `true`, a másiké `false`. Kapcsold össze őket a `&&` operátorral, majd jelenítsd meg az eredményt.

2\. feladat – Logikai VAGY

Hozz létre két logikai változót. Vizsgáld meg a `||` operátor segítségével, hogy legalább az egyik változó értéke igaz-e. Próbáld ki mind a négy lehetséges értékkombinációt.

3\. feladat – Logikai NEM

Hozz létre egy `aktiv` nevű logikai változót. Használd a `!` operátort az értékének megfordítására, majd jelenítsd meg az eredményt.

4\. feladat – Életkor ellenőrzése

Kérj be egy életkort a felhasználótól. A `&&` operátor segítségével ellenőrizd, hogy az életkor legalább 18 és legfeljebb 65 év-e. Jeleníts meg megfelelő üzenetet.

5\. feladat – Hétvége ellenőrzése

Hozz létre egy `nap` nevű változót. Vizsgáld meg a `||` operátor segítségével, hogy a változó értéke szombat vagy vasárnap-e. Ha igen, jelenítsd meg, hogy hétvége van.

6\. feladat – Jogosultság ellenőrzése

Hozz létre három változót:

- `bejelentkezett`;
- `admin`;
- `aktiv`.

A `&&` és a `||` operátorok segítségével ellenőrizd, hogy a felhasználó bejelentkezett és aktív-e, továbbá adminisztrátori jogosultsággal rendelkezik-e. A jogosultság feltétele legyen, hogy a felhasználó aktív és bejelentkezett legyen, vagy adminisztrátor legyen.

7\. feladat – Szám vizsgálata

Kérj be egy számot a felhasználótól. Ellenőrizd, hogy a szám kisebb-e 10-nél vagy nagyobb-e 100-nál. Ha egyik feltétel sem teljesül, jelenítsd meg, hogy a szám a megadott tartományban van.

8\. feladat – Negatív feltétel vizsgálata

Hozz létre egy `karbantartas` nevű logikai változót. A `!` operátor segítségével vizsgáld meg, hogy nincs-e karbantartás. Ha nincs, jelenítsd meg, hogy a rendszer használható.

9\. feladat – Alapértelmezett érték megadása

Hozz létre egy `felhasznalonev` nevű változót, amely kezdetben üres szöveget tartalmaz. A `||` operátor segítségével adj neki alapértelmezett értéket, ha a változó üres. Ezután próbáld ki ugyanezt a feladatot a `??` operátorral is, és figyeld meg a különbséget.

10\. feladat – Összetett belépési feltétel

Készíts egy programot, amely három változót használ:

- `eletkor`;
- `vanJegy`;
- `kitiltva`.

A felhasználó akkor léphet be, ha legalább 18 éves, rendelkezik érvényes jeggyel, és nincs kitiltva. A feltételek vizsgálatához használd a `&&` és a `!` operátorokat. A program jelenítse meg, hogy a belépés engedélyezett vagy megtagadott.
