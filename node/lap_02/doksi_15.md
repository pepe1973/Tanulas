# Ternáris operátor JavaScriptben

## 1. Mi az a ternáris operátor?

A ternáris operátor egy rövidített feltételes kifejezés, amely segítségével egy feltétel alapján két lehetséges érték közül választhatunk.

A ternáris operátor a hagyományos `if...else` szerkezet egyszerűbb, tömörebb alternatívája lehet.

Az elnevezése arra utal, hogy három operandust használ:

1. Egy feltételt.
2. Egy értéket, amelyet akkor kapunk, ha a feltétel igaz.
3. Egy másik értéket, amelyet akkor kapunk, ha a feltétel hamis.

A ternáris operátor jele:

```javascript
?
:
```

## 2. A ternáris operátor szintaxisa

A ternáris operátor általános felépítése:

```javascript
feltetel ? ertekHaIgaz : ertekHaHamis;
```

A működése:

- Ha a feltétel igaz (`true`), akkor az első értéket adja vissza.
- Ha a feltétel hamis (`false`), akkor a második értéket adja vissza.

Példa:

```javascript
let eletkor = 20;

let eredmeny = eletkor >= 18 ? 'Felnőtt' : 'Kiskorú';

console.log(eredmeny);
```

Kimenet:

```
Felnőtt
```

A program megvizsgálja, hogy az `eletkor` változó értéke legalább 18-e.

Mivel a feltétel igaz, az `eredmeny` változó a `"Felnőtt"` szöveget kapja.

## 3. Ternáris operátor és az if...else összehasonlítása

A ternáris operátor ugyanazt a feltételes döntést képes megvalósítani, mint az `if...else` szerkezet.

Megoldás if...else segítségével:

```javascript
let pontszam = 75;
let eredmeny;

if (pontszam >= 50) {
    eredmeny = 'Sikeres';
} else {
    eredmeny = 'Sikertelen';
}

console.log(eredmeny);
```

Megoldás ternáris operátorral:

```javascript
let pontszam = 75;

let eredmeny = pontszam >= 50 ? 'Sikeres' : 'Sikertelen';

console.log(eredmeny);
```

Mindkét program ugyanazt az eredményt adja.

A ternáris operátor különösen akkor hasznos, ha egy egyszerű feltétel alapján szeretnénk egy változónak értéket adni.

| Szempont                        | `if...else`                          | Ternáris operátor          |
| ------------------------------- | ------------------------------------ | -------------------------- |
| Felépítés                       | Több soros szerkezet                 | Rövid kifejezés            |
| Feltétel vizsgálata             | Igen                                 | Igen                       |
| Két lehetőség közötti választás | Igen                                 | Igen                       |
| Érték visszaadása               | Külön értékadással vagy `return`-nel | Közvetlenül                |
| Összetett programlogika         | Jól áttekinthető                     | Nehezebben olvasható lehet |

## 4. Ternáris operátor használata változók értékadásakor

A ternáris operátor egyik leggyakoribb felhasználási területe a változók feltételes inicializálása vagy értékadása.

Példa:

```javascript
let homerseklet = 28;

let allapot = homerseklet > 25 ? 'Meleg' : 'Hűvös';

console.log(allapot);
```

Kimenet:

```
Meleg
```

A program a hőmérséklet alapján választja ki a megfelelő szöveget.

Másik példa:

```javascript
let keszlet = 0;

let uzenet = keszlet > 0 ? 'A termék elérhető' : 'A termék nem elérhető';

console.log(uzenet);
```

Kimenet:

```
A termék nem elérhető
```

## 5. Ternáris operátor használata kiíratáskor

A ternáris operátor közvetlenül a `console.log()` függvényben is használható.

```javascript
let eletkor = 17;

console.log(eletkor >= 18 ? 'Beléphet' : 'Nem léphet be');
```

Kimenet:

```
Nem léphet be
```

Ebben az esetben nem szükséges külön változót létrehozni az eredmény tárolására.

## 6. Ternáris operátor használata függvényekben

A ternáris operátor függvények visszatérési értékének meghatározására is alkalmas.

```javascript
function parosVagyParatlan(szam) {
    return szam % 2 === 0 ? 'Páros' : 'Páratlan';
}

console.log(parosVagyParatlan(8));
console.log(parosVagyParatlan(5));
```

Kimenet:

```
Páros
Páratlan
```

A függvény megvizsgálja, hogy a szám kettővel osztva nulla maradékot ad-e.

- Ha igen, akkor `"Páros"` értéket ad vissza.
- Ha nem, akkor `"Páratlan"` értéket ad vissza.

## 7. Egymásba ágyazott ternáris operátor

Lehetőségünk van arra is, hogy egy ternáris operátoron belül egy másik ternáris operátort használjunk.

Ezt egymásba ágyazott ternáris operátornak nevezzük.

Példa:

```javascript
let pontszam = 85;

let osztalyzat =
    pontszam >= 90
        ? 'Jeles'
        : pontszam >= 75
          ? 'Jó'
          : pontszam >= 60
            ? 'Közepes'
            : pontszam >= 50
              ? 'Elégséges'
              : 'Elégtelen';

console.log(osztalyzat);
```

Kimenet:

```
Jó
```

A program több feltételt vizsgál egymás után:

1. Ha a pontszám legalább 90, akkor az eredmény `"Jeles"`.
2. Ha nem, de legalább 75, akkor `"Jó"`.
3. Ha nem, de legalább 60, akkor `"Közepes"`.
4. Ha nem, de legalább 50, akkor `"Elégséges"`.
5. Ha egyik feltétel sem teljesül, akkor `"Elégtelen"`.

Fontos: az egymásba ágyazott ternáris operátorok túlzott használata nehezen olvasható kódot eredményezhet. Több összetett feltétel esetén célszerűbb az `if...else if...else` szerkezetet választani.

## 8. Ternáris operátor logikai feltételekkel

A ternáris operátor feltételeként logikai operátorokat is használhatunk.

Példa az `&&` operátorral:

```javascript
let eletkor = 25;
let vanJogositvany = true;

let vezetes = eletkor >= 18 && vanJogositvany ? 'Vezethet' : 'Nem vezethet';

console.log(vezetes);
```

Kimenet:

```
Vezethet
```

A feltétel csak akkor igaz, ha mindkét részfeltétel teljesül:

- Az életkor legalább 18 év.
- A személy rendelkezik jogosítvánnyal.

Példa az `||` operátorral:

```javascript
let hetvege = true;
let szabadsag = false;

let pihenes = hetvege || szabadsag ? 'Pihenőnap' : 'Munkanap';

console.log(pihenes);
```

Kimenet:

```
Pihenőnap
```

Ebben az esetben elegendő, ha a két feltétel közül legalább az egyik igaz.

## 9. Ternáris operátor és a nullish coalescing operátor összehasonlítása

A ternáris operátort nem szabad összekeverni a nullish coalescing (`??`) operátorral.

A ternáris operátor egy feltétel alapján választ két érték közül:

```javascript
let eletkor = 20;

let eredmeny = eletkor >= 18 ? 'Felnőtt' : 'Kiskorú';
```

A `??` operátor akkor adja vissza a jobb oldali értéket, ha a bal oldali érték `null` vagy `undefined`.

```javascript
let nev = null;

let megjelenitendoNev = nev ?? 'Ismeretlen';

console.log(megjelenitendoNev);
```

Kimenet:

```
Ismeretlen
```

A két operátor tehát eltérő célra szolgál.

| Operátor | Feladata                                                        |
| -------- | --------------------------------------------------------------- |
| `? :`    | Feltétel alapján választ két érték közül                        |
| `??`     | Alapértelmezett értéket biztosít `null` vagy `undefined` esetén |

## 10. Gyakori hibák és fontos tudnivalók

### 10.1. A kettőspont elhagyása

A ternáris operátorban a kérdőjel és a kettőspont is kötelező.

Hibás példa:

```javascript
let eredmeny = eletkor >= 18 ? "Felnőtt";
```

Helyes példa:

```javascript
let eredmeny = eletkor >= 18 ? 'Felnőtt' : 'Kiskorú';
```

### 10.2. A két lehetséges érték felcserélése

A kérdőjel utáni érték akkor kerül kiválasztásra, ha a feltétel igaz. A kettőspont utáni érték akkor, ha a feltétel hamis.

```javascript
let szam = 10;

let eredmeny = szam > 5 ? 'Nagyobb' : 'Kisebb vagy egyenlő';

console.log(eredmeny);
```

Kimenet:

```
Nagyobb
```

### 10.3. Túl bonyolult ternáris kifejezések

A túl sok egymásba ágyazott feltétel rontja a kód olvashatóságát.

Nehezen áttekinthető példa:

```javascript
let eredmeny = a > 10 ? (b > 5 ? 'A' : 'B') : c > 3 ? 'C' : 'D';
```

Ilyen esetekben érdemes inkább `if...else` szerkezetet használni.

### 10.4. Nem feltétlenül logikai értékek a feltételben

A ternáris operátor feltétele nem kizárólag `true` vagy `false` lehet. A JavaScript a feltételt logikai értékké alakítja.

```javascript
let nev = 'Anna';

let uzenet = nev ? 'Van megadott név' : 'Nincs megadott név';

console.log(uzenet);
```

Kimenet:

```
Van megadott név
```

A nem üres szöveg igaznak számít (`truthy`), ezért az első érték kerül kiválasztásra.

## 11. Összefoglalás

A ternáris operátor egy feltételes kifejezés, amely két lehetséges érték közül választ.

Általános szintaxisa:

```javascript
feltetel ? ertekHaIgaz : ertekHaHamis;
```

A legfontosabb tudnivalók:

- A `?` jel vezeti be az igaz feltételhez tartozó értéket.
- A `:` jel választja el az igaz és hamis esethez tartozó értékeket.
- A ternáris operátor egy kifejezés, ezért például változó értékadásakor is használható.
- Egyszerű feltételeknél rövidebb lehet, mint az `if...else`.
- Összetett feltételeknél az `if...else` gyakran áttekinthetőbb.

# 12. Ellenőrző kérdések

1. Mi a ternáris operátor, és milyen feladat megoldására használjuk?
2. Miért nevezzük ternárisnak ezt az operátort?
3. Milyen jelekből épül fel a ternáris operátor?
4. Mi történik, ha a ternáris operátor feltétele igaz?
5. Mi történik, ha a ternáris operátor feltétele hamis?
6. Mi a különbség az `if...else` szerkezet és a ternáris operátor között?
7. Hogyan használhatjuk a ternáris operátort egy változó értékének meghatározására?
8. Mit nevezünk egymásba ágyazott ternáris operátornak?
9. Miért lehet problémás a túl sok egymásba ágyazott ternáris kifejezés használata?
10. Mi a különbség a ternáris (`? :`) és a nullish coalescing (`??`) operátor között?

# 13. Gyakorlati feladatok

Az alábbi feladatokat JavaScriptben, megoldás nélkül készítsd el!

1. Életkor ellenőrzése: Hozz létre egy `eletkor` változót. Ternáris operátor segítségével döntsd el, hogy az illető nagykorú-e! Ha legalább 18 éves, az eredmény legyen `"Nagykorú"`, egyébként `"Kiskorú"`.
2. Páros vagy páratlan: Hozz létre egy `szam` változót. A maradékos osztás (`%`) segítségével és ternáris operátorral állapítsd meg, hogy a szám páros vagy páratlan!
3. Pozitív vagy negatív: Hozz létre egy `szam` változót. Ternáris operátor segítségével vizsgáld meg, hogy az értéke pozitív-e! Pozitív érték esetén `"Pozitív"`, egyébként `"Nem pozitív"` legyen az eredmény.
4. Sikeres vagy sikertelen vizsga: Hozz létre egy `pontszam` változót. Ha az értéke legalább 50, az eredmény legyen `"Sikeres vizsga"`, egyébként `"Sikertelen vizsga"`.
5. Hőmérséklet ellenőrzése: Hozz létre egy `homerseklet` változót. Ha az értéke nagyobb 25-nél, jelenítsd meg a `"Meleg idő"` szöveget, egyébként a `"Hűvös idő"` szöveget!
6. Készlet ellenőrzése: Hozz létre egy `keszlet` változót. Ha a készlet nagyobb nullánál, az eredmény legyen `"Elérhető"`, egyébként `"Elfogyott"`.
7. Három kategória meghatározása: Hozz létre egy `pontszam` változót. Egymásba ágyazott ternáris operátor segítségével határozd meg a következő kategóriákat:
    - 80 ponttól: `"Kiváló"`.
    - 50 és 79 pont között: `"Megfelelő"`.
    - 50 pont alatt: `"Nem megfelelő"`.
8. Belépés ellenőrzése: Hozz létre két változót: `eletkor` és `vanJegy`. A belépés csak akkor legyen engedélyezett, ha az életkor legalább 18 év, és a személy rendelkezik jeggyel. A feltétel vizsgálatához használd az `&&` operátort!
9. Kedvezmény meghatározása: Hozz létre egy `vasarlasOsszeg` változót. Ha az összeg legalább 20 000 Ft, az eredmény legyen `"10% kedvezmény"`, egyébként `"Nincs kedvezmény"`.
10. Függvény készítése: Készíts egy `nagyobbSzam` nevű függvényt, amely két számot kap paraméterként. Ternáris operátor segítségével adja vissza a nagyobb számot! Ha a két szám egyenlő, adja vissza valamelyik szám értékét.
