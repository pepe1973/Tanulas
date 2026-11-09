# Matematikai operátorok JavaScriptben

## 1. Mik azok a matematikai operátorok?

A matematikai operátorok olyan speciális jelek, amelyek segítségével különböző matematikai műveleteket végezhetünk a JavaScriptben tárolt értékeken.

Segítségükkel például:

- összeadhatunk két számot;
- kivonhatunk egyik számból egy másikat;
- összeszorozhatunk értékeket;
- eloszthatunk két számot;
- meghatározhatjuk egy osztás maradékát;
- növelhetünk vagy csökkenthetünk egy változóban tárolt értéket.

A matematikai operátorokat gyakran aritmetikai operátoroknak is nevezzük.

## 2. Az alapvető matematikai operátorok

A JavaScript leggyakrabban használt matematikai operátorai:

| Operátor | Művelet       | Példa    | Eredmény |
| -------- | ------------- | -------- | -------- |
| `+`      | Összeadás     | `10 + 5` | `15`     |
| `-`      | Kivonás       | `10 - 5` | `5`      |
| `*`      | Szorzás       | `10 * 5` | `50`     |
| `/`      | Osztás        | `10 / 5` | `2`      |
| `%`      | Maradékképzés | `10 % 3` | `1`      |
| `**`     | Hatványozás   | `2 ** 3` | `8`      |

### 2.1. Összeadás (`+`)

A `+` operátor két számot ad össze.

```javascript
let a = 10;
let b = 5;

let eredmeny = a + b;

console.log(eredmeny); // 15
```

Az operátor nemcsak számok összeadására használható, hanem szövegek összefűzésére is.

```javascript
let nev = 'Péter';
let uzenet = 'Szia, ' + nev + '!';

console.log(uzenet); // Szia, Péter!
```

Ha mindkét operandus szám, akkor matematikai összeadás történik. Ha az egyik operandus szöveg, akkor az eredmény gyakran szöveg-összefűzés lesz.

### 2.2. Kivonás (`-`)

A `-` operátor két szám különbségét határozza meg.

```javascript
let a = 20;
let b = 8;

let eredmeny = a - b;

console.log(eredmeny); // 12
```

A művelet során a második értéket kivonjuk az elsőből.

### 2.3. Szorzás (`*`)

A `*` operátor két szám szorzatát számítja ki.

```javascript
let ar = 1500;
let darab = 4;

let osszeg = ar * darab;

console.log(osszeg); // 6000
```

A példában egy termék darabárát megszorozzuk a megvásárolt mennyiséggel.

### 2.4. Osztás (`/`)

A `/` operátor két szám hányadosát adja vissza.

```javascript
let osszeg = 100;
let darab = 4;

let eredmeny = osszeg / darab;

console.log(eredmeny); // 25
```

Fontos, hogy a JavaScriptben az osztás eredménye nem feltétlenül egész szám.

```javascript
console.log(10 / 3); // 3.3333333333333335
```

A JavaScript nem kerekíti automatikusan egész számra az osztás eredményét.

Nullával való osztás:

JavaScriptben a nullával történő osztás nem minden esetben okoz hibát.

```javascript
console.log(10 / 0); // Infinity
console.log(-10 / 0); // -Infinity
console.log(0 / 0); // NaN
```

Az `Infinity` végtelent, a `NaN` pedig nem értelmezhető számértéket jelent.

### 2.5. Maradékképzés (`%`)

A `%` operátor az osztás maradékát határozza meg.

```javascript
let eredmeny = 10 % 3;

console.log(eredmeny); // 1
```

A 10-et elosztva 3-mal az eredmény 3, a maradék pedig 1.

A maradékképzés különösen hasznos páros és páratlan számok vizsgálatakor.

```javascript
let szam = 8;

if (szam % 2 === 0) {
    console.log('A szám páros.');
} else {
    console.log('A szám páratlan.');
}
```

A feltétel azt vizsgálja, hogy a szám kettővel osztva nulla maradékot ad-e.

További példák:

```javascript
console.log(10 % 2); // 0
console.log(11 % 2); // 1
console.log(15 % 4); // 3
console.log(20 % 6); // 2
```

### 2.6. Hatványozás (`**`)

A `**` operátor segítségével egy számot egy másik szám hatványára emelhetünk.

```javascript
let eredmeny = 2 ** 3;

console.log(eredmeny); // 8
```

Ez azt jelenti, hogy a 2-t háromszor szorozzuk össze önmagával:

\\[ 2^3 = 2 * 2 * 2 = 8 \\]

További példák:

```javascript
console.log(3 ** 2); // 9
console.log(5 ** 2); // 25
console.log(2 ** 4); // 16
console.log(10 ** 3); // 1000
```

## 3. Értéknövelő és értékcsökkentő operátorok

A JavaScriptben léteznek olyan operátorok, amelyek egy változó értékét eggyel növelik vagy csökkentik.

### 3.1. Növelés eggyel (`++`)

A `++` operátor eggyel növeli a változó értékét.

```javascript
let szamlalo = 5;

szamlalo++;

console.log(szamlalo); // 6
```

A következő két megoldás ugyanazt az eredményt adja:

```javascript
let szamlalo = 5;

szamlalo = szamlalo + 1;

console.log(szamlalo); // 6
```

```javascript
let szamlalo = 5;

szamlalo++;

console.log(szamlalo); // 6
```

### 3.2. Csökkentés eggyel (`--`)

A `--` operátor eggyel csökkenti a változó értékét.

```javascript
let szamlalo = 10;

szamlalo--;

console.log(szamlalo); // 9
```

A következő kód ugyanezt a műveletet végzi:

```javascript
let szamlalo = 10;

szamlalo = szamlalo - 1;

console.log(szamlalo); // 9
```

### 3.3. Prefix és postfix használat

A növelő és csökkentő operátorok kétféleképpen használhatók:

- Prefix: az operátor a változó előtt szerepel.
- Postfix: az operátor a változó után szerepel.

A két változat közötti különbség akkor fontos, ha az operátort egy kifejezés részeként használjuk.

Postfix (`szamlalo++`):

A kifejezés először a változó eredeti értékét használja fel, és csak utána növeli meg a változót.

```javascript
let szamlalo = 5;

let eredmeny = szamlalo++;

console.log(eredmeny); // 5
console.log(szamlalo); // 6
```

Prefix (`++szamlalo`):

A változó először megnövekszik, és a kifejezés már az új értéket használja fel.

```javascript
let szamlalo = 5;

let eredmeny = ++szamlalo;

console.log(eredmeny); // 6
console.log(szamlalo); // 6
```

A különbség összefoglalva:

| Kifejezés    | Az eredményben használt érték | A változó új értéke |
| ------------ | ----------------------------- | ------------------- |
| `szamlalo++` | 5                             | 6                   |
| `++szamlalo` | 6                             | 6                   |
| `szamlalo--` | 5                             | 4                   |
| `--szamlalo` | 4                             | 4                   |

Ha önálló utasításként használjuk őket, például `szamlalo++`, akkor mindkét forma eggyel növeli a változót. A különbség a kifejezés eredményében jelenik meg.

## 4. Összetett értékadó matematikai operátorok

Gyakran előfordul, hogy egy változó aktuális értékét egy matematikai művelet eredményével szeretnénk módosítani.

Erre használhatók az összetett értékadó operátorok.

### 4.1. Összeadás és értékadás (`+=`)

```javascript
let szam = 10;

szam += 5;

console.log(szam); // 15
```

Ez ugyanazt jelenti, mint:

```javascript
let szam = 10;

szam = szam + 5;

console.log(szam); // 15
```

### 4.2. Kivonás és értékadás (`-=`)

```javascript
let szam = 20;

szam -= 5;

console.log(szam); // 15
```

### 4.3. Szorzás és értékadás (`*=`)

```javascript
let szam = 10;

szam *= 3;

console.log(szam); // 30
```

### 4.4. Osztás és értékadás (`/=`)

```javascript
let szam = 100;

szam /= 4;

console.log(szam); // 25
```

### 4.5. Maradékképzés és értékadás (`%=`)

```javascript
let szam = 17;

szam %= 5;

console.log(szam); // 2
```

### 4.6. Hatványozás és értékadás (`**=`)

```javascript
let szam = 3;

szam **= 2;

console.log(szam); // 9
```

Az összetett értékadó operátorok összefoglalása:

| Operátor | Jelentése                  | Példa        |
| -------- | -------------------------- | ------------ |
| `+=`     | Hozzáadás és értékadás     | `szam += 5`  |
| `-=`     | Kivonás és értékadás       | `szam -= 5`  |
| `*=`     | Szorzás és értékadás       | `szam *= 5`  |
| `/=`     | Osztás és értékadás        | `szam /= 5`  |
| `%=`     | Maradékképzés és értékadás | `szam %= 5`  |
| `**=`    | Hatványozás és értékadás   | `szam **= 5` |

## 5. A matematikai műveletek végrehajtási sorrendje

A JavaScript a matematikai műveleteket meghatározott sorrendben hajtja végre. Ezt műveleti precedenciának nevezzük.

Az alapvető sorrend:

1. Zárójelekben szereplő műveletek.
2. Hatványozás.
3. Szorzás, osztás és maradékképzés.
4. Összeadás és kivonás.

Példa:

```javascript
let eredmeny = 10 + 5 * 2;

console.log(eredmeny); // 20
```

A szorzás előbb történik meg:

1. `5 * 2 = 10`
2. `10 + 10 = 20`

Ha más sorrendben szeretnénk elvégezni a műveleteket, zárójeleket használhatunk.

```javascript
let eredmeny = (10 + 5) * 2;

console.log(eredmeny); // 30
```

Ebben az esetben először a zárójelben szereplő összeadás történik meg.

További példa:

```javascript
let eredmeny = (100 / (5 + 5)) * 2;

console.log(eredmeny); // 20
```

A zárójelek használatával a bonyolultabb kifejezések is könnyebben áttekinthetők.

## 6. Matematikai operátorok használata változókkal

A matematikai operátorokat általában változókban tárolt értékeken használjuk.

Például egy vásárlás végösszegének kiszámítása:

```javascript
let termekAra = 2500;
let darabszam = 3;

let vegosszeg = termekAra * darabszam;

console.log('Végösszeg: ' + vegosszeg + ' Ft');
```

Eredmény:

```
Végösszeg: 7500 Ft
```

Egy másik példa, amely egy kör kerületét számítja ki:

```javascript
const PI = 3.14159;
let sugar = 5;

let kerulet = 2 * sugar * PI;

console.log('A kör kerülete: ' + kerulet);
```

A kör kerületének képlete:

\\[ K = 2 * r * pi \\]

Ahol:

- `K` a kör kerülete;
- `r` a kör sugara;
- `PI` a pi közelítő értéke.

## 7. Matematikai műveletek a Math objektummal

A JavaScript beépített `Math` objektuma további matematikai műveleteket és függvényeket biztosít.

Ezek nem hagyományos aritmetikai operátorok, hanem előre elkészített matematikai eszközök.

### 7.1. Kerekítés (`Math.round()`)

A `Math.round()` a legközelebbi egész számra kerekít.

```javascript
console.log(Math.round(4.3)); // 4
console.log(Math.round(4.7)); // 5
console.log(Math.round(4.5)); // 5
```

### 7.2. Lefelé kerekítés (`Math.floor()`)

A `Math.floor()` a számnál nem nagyobb legnagyobb egész számot adja vissza.

```javascript
console.log(Math.floor(4.9)); // 4
console.log(Math.floor(4.1)); // 4
```

### 7.3. Felfelé kerekítés (`Math.ceil()`)

A `Math.ceil()` a számnál nem kisebb legkisebb egész számot adja vissza.

```javascript
console.log(Math.ceil(4.1)); // 5
console.log(Math.ceil(4.9)); // 5
```

### 7.4. Abszolút érték (`Math.abs()`)

A `Math.abs()` egy szám abszolút értékét határozza meg.

```javascript
console.log(Math.abs(-10)); // 10
console.log(Math.abs(10)); // 10
```

### 7.5. Legnagyobb és legkisebb érték

A `Math.max()` több szám közül a legnagyobbat adja vissza.

```javascript
console.log(Math.max(10, 25, 5, 40)); // 40
```

A `Math.min()` több szám közül a legkisebbet adja vissza.

```javascript
console.log(Math.min(10, 25, 5, 40)); // 5
```

### 7.6. Véletlenszám (`Math.random()`)

A `Math.random()` egy 0 és 1 közötti véletlenszerű számot ad vissza. A 0 előfordulhat, az 1 viszont nem.

```javascript
let veletlen = Math.random();

console.log(veletlen);
```

Ha 1 és 10 közötti egész számot szeretnénk előállítani:

```javascript
let veletlen = Math.floor(Math.random() * 10) + 1;

console.log(veletlen);
```

A `Math.random()` és a `Math.floor()` kombinációjával más egész számtartományok is előállíthatók.

## 8. Gyakori hibák a matematikai operátorok használatakor

### 8.1. Az összeadás és a szöveg-összefűzés összekeverése

```javascript
let a = 10;
let b = '5';

console.log(a + b); // "105"
```

Mivel az egyik operandus szöveg, a `+` operátor szöveg-összefűzést végez.

### 8.2. Az osztás eredményének egész számként kezelése

```javascript
let eredmeny = 10 / 3;

console.log(eredmeny); // 3.3333333333333335
```

Ha egész számra van szükségünk, külön kerekítést kell alkalmaznunk.

```javascript
let eredmeny = Math.round(10 / 3);

console.log(eredmeny); // 3
```

### 8.3. A maradékképzés félreértése

```javascript
console.log(10 / 3); // 3.3333333333333335
console.log(10 % 3); // 1
```

Az osztás hányadost, a maradékképzés pedig a maradékot adja vissza.

### 8.4. A műveleti sorrend figyelmen kívül hagyása

```javascript
let eredmeny = 5 + 3 * 2;

console.log(eredmeny); // 11
```

A szorzás előbb történik meg, mint az összeadás.

Ha először összeadni szeretnénk:

```javascript
let eredmeny = (5 + 3) * 2;

console.log(eredmeny); // 16
```

### 8.5. A prefix és postfix különbségének figyelmen kívül hagyása

```javascript
let szam = 5;

console.log(szam++); // 5
console.log(szam); // 6
```

A postfix forma először a régi értéket adja vissza, és csak utána növeli a változót.

# 9. Ellenőrző kérdések

1. Mire használjuk a matematikai operátorokat JavaScriptben?
2. Melyik operátorral végezhetünk összeadást, kivonást, szorzást és osztást?
3. Mi a különbség a `/` és a `%` operátor között?
4. Mit jelent a `**` operátor, és hogyan használható?
5. Mire szolgál a `++` és a `--` operátor?
6. Mi a különbség a prefix és a postfix növelés között?
7. Mit jelent a `+=` operátor, és hogyan működik?
8. Milyen sorrendben hajtja végre a JavaScript az alapvető matematikai műveleteket?
9. Mire használjuk a `Math.round()`, `Math.floor()` és `Math.ceil()` függvényeket?
10. Mi a különbség a `Math.max()` és a `Math.min()` függvények között?

# 10. Gyakorlati feladatok

1\. feladat – Alapműveletek

Hozz létre két változót, amelyek egész számokat tárolnak. Végezd el rajtuk az összeadás, kivonás, szorzás és osztás műveletét. Az eredményeket jelenítsd meg a konzolon.

2\. feladat – Maradékképzés

Hozz létre egy változót, amely egy tetszőleges egész számot tárol. Határozd meg, hogy a szám kettővel osztva mennyi maradékot ad.

3\. feladat – Páros vagy páratlan szám

Kérj be egy számot a felhasználótól, majd a maradékképző operátor segítségével döntsd el, hogy páros vagy páratlan számról van-e szó.

4\. feladat – Hatványozás

Hozz létre két változót. Az első tárolja az alapot, a második a kitevőt. Számítsd ki az első változó értékét a második változó hatványán.

5\. feladat – Számláló növelése és csökkentése

Hozz létre egy `szamlalo` nevű változót 10-es kezdőértékkel. Növeld meg háromszor, majd csökkentsd kétszer az értékét. Jelenítsd meg a végeredményt.

6\. feladat – Összetett értékadás

Hozz létre egy változót 100-as kezdőértékkel. Használd az `+=`, `-=`, `*=`, `/=` és `%=` operátorokat különböző értékekkel. Minden művelet után jelenítsd meg a változó aktuális értékét.

7\. feladat – Műveleti sorrend

Hozz létre egy olyan matematikai kifejezést, amely összeadást, kivonást, szorzást és osztást is tartalmaz. Számítsd ki az eredményét, majd zárójelek segítségével változtasd meg a műveletek végrehajtási sorrendjét.

8\. feladat – Vásárlás végösszege

Hozz létre két változót: az egyik tárolja egy termék árát, a másik a megvásárolt darabszámot. Számítsd ki a fizetendő összeget, majd jelenítsd meg egy szöveges üzenetben.

9\. feladat – Kerekítési műveletek

Hozz létre egy tizedes számot tároló változót. Alkalmazd rajta a `Math.round()`, `Math.floor()` és `Math.ceil()` függvényeket. Jelenítsd meg mindhárom eredményt.

10\. feladat – Véletlenszám-generátor

Készíts programot, amely véletlenszerű egész számot generál 1 és 100 között. Jelenítsd meg a kapott számot, majd döntsd el, hogy páros vagy páratlan-e.
