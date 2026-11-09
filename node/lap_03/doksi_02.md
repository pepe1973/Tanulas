# Többágú elágazás JavaScriptben (`switch`)

## 1. Mi az a `switch`?

A JavaScriptben a `switch` utasítást akkor használjuk, amikor egy változó vagy kifejezés értéke alapján több lehetséges végrehajtási útvonal közül szeretnénk választani.

A `switch` hasonló célt szolgál, mint az `if`, `else if` és `else` utasítások, azonban bizonyos esetekben áttekinthetőbbé teszi a programkódot.

Például képzeljük el, hogy egy programban a hét napjainak sorszáma alapján szeretnénk megjeleníteni a nap nevét:

- 1 – hétfő
- 2 – kedd
- 3 – szerda
- 4 – csütörtök
- 5 – péntek
- 6 – szombat
- 7 – vasárnap

Ezt több `if` utasítással is megoldhatnánk, de a `switch` segítségével egyszerűbben is megírhatjuk.

## 2. A `switch` alapvető szintaxisa

A `switch` szerkezete:

```javascript
switch (kifejezes) {
    case ertek1:
        // Utasítások, ha a kifejezés értéke ertek1
        break;

    case ertek2:
        // Utasítások, ha a kifejezés értéke ertek2
        break;

    case ertek3:
        // Utasítások, ha a kifejezés értéke ertek3
        break;

    default:
    // Utasítások, ha egyik case sem teljesül
}
```

A szerkezet részei:

- `switch`: elindítja a többágú elágazást.
- `kifejezes`: az az érték, amelyet a program megvizsgál.
- `case`: egy lehetséges értéket határoz meg.
- `break`: kilép a `switch` szerkezetből.
- `default`: az alapértelmezett ág, amely akkor fut le, ha egyik `case` sem illeszkedik.

A `case` ágak és a `default` ág sorrendje tetszőleges lehet, de a `default` ágat általában a szerkezet végére helyezzük.

## 3. Egyszerű `switch` példa

Vizsgáljuk meg a hét napjainak sorszámát!

```javascript
const nap = 3;

switch (nap) {
    case 1:
        console.log('Hétfő');
        break;

    case 2:
        console.log('Kedd');
        break;

    case 3:
        console.log('Szerda');
        break;

    case 4:
        console.log('Csütörtök');
        break;

    case 5:
        console.log('Péntek');
        break;

    case 6:
        console.log('Szombat');
        break;

    case 7:
        console.log('Vasárnap');
        break;

    default:
        console.log('Érvénytelen nap!');
}
```

A program működése:

1. A `nap` változó értéke 3.
2. A `switch` megvizsgálja a megadott értéket.
3. Sorban összehasonlítja a `case` ágak értékeivel.
4. Megtalálja a `case 3` ágat.
5. Végrehajtja az adott ág utasítását.
6. A `break` hatására kilép a `switch` szerkezetből.

A konzolon megjelenő eredmény:

```
Szerda
```

## 4. A `break` utasítás szerepe

A `break` utasítás különösen fontos a `switch` használatakor.

Feladata, hogy megszakítsa a `switch` végrehajtását, és kilépjen annak szerkezetéből.

Nézzük meg, mi történik, ha elhagyjuk!

```javascript
const szam = 2;

switch (szam) {
    case 1:
        console.log('Egy');

    case 2:
        console.log('Kettő');

    case 3:
        console.log('Három');

    default:
        console.log('Alapértelmezett ág');
}
```

A konzolon a következő jelenik meg:

```
Kettő
Három
Alapértelmezett ág
```

Ennek oka, hogy a JavaScript a megfelelő `case` megtalálása után a további utasításokat is végrehajtja, egészen addig, amíg el nem éri a `switch` végét vagy egy `break` utasítást.

Ezt a működést fall-through-nak nevezzük.

Fontos: Ha nem szeretnénk több ág utasításait egymás után végrehajtani, minden megfelelő `case` ág végére tegyünk `break` utasítást.

## 5. A `default` ág használata

A `default` ág akkor hajtódik végre, ha a `switch` egyik `case` értékével sem egyezik meg a vizsgált kifejezés.

Példa:

```javascript
const jegy = 8;

switch (jegy) {
    case 1:
        console.log('Elégtelen');
        break;

    case 2:
        console.log('Elégséges');
        break;

    case 3:
        console.log('Közepes');
        break;

    case 4:
        console.log('Jó');
        break;

    case 5:
        console.log('Jeles');
        break;

    default:
        console.log('Érvénytelen jegy!');
}
```

Mivel a `jegy` változó értéke 8, egyik `case` sem illeszkedik.

A konzol eredménye:

```
Érvénytelen jegy!
```

A `default` ág használata nem kötelező, de gyakran hasznos az olyan értékek kezelésére, amelyekre nem számítottunk.

## 6. Több `case` ág közös végrehajtása

Előfordulhat, hogy több különböző érték esetén ugyanazt az utasítást szeretnénk végrehajtani.

Ilyenkor több `case` ágat is egymás után írhatunk.

Például egy nap esetében szeretnénk eldönteni, hogy hétköznapról vagy hétvégéről van-e szó.

```javascript
const nap = 6;

switch (nap) {
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
        console.log('Hétköznap');
        break;

    case 6:
    case 7:
        console.log('Hétvége');
        break;

    default:
        console.log('Érvénytelen nap!');
}
```

A program működése:

- Ha a `nap` értéke 1 és 5 közé esik, a program a „Hétköznap” szöveget jeleníti meg.
- Ha a `nap` értéke 6 vagy 7, a program a „Hétvége” szöveget jeleníti meg.
- Más érték esetén a `default` ág fut le.

A közös végrehajtás azért működik, mert a `case` ágak között nincs `break`, így a végrehajtás eljut a közös utasításig.

Ez a `switch` egyik hasznos lehetősége.

## 7. A `switch` szigorú összehasonlítást használ

A JavaScript `switch` utasítása a `case` értékek összehasonlításakor szigorú egyenlőséget (`===`) használ.

Ez azt jelenti, hogy az értéknek és az adattípusnak is egyeznie kell.

Példa:

```javascript
const ertek = '5';

switch (ertek) {
    case 5:
        console.log('Szám típusú öt');

        break;

    case '5':
        console.log('Szöveg típusú öt');

        break;

    default:
        console.log('Más érték');
}
```

A konzolon megjelenő eredmény:

```
Szöveg típusú öt
```

Ennek oka:

```javascript
5 === '5'; // false
5 == '5'; // true
```

A `switch` nem alakítja automatikusan számmá a szöveget, vagy szöveggé a számot az összehasonlítás során.

Ezért fontos figyelni az adattípusokra.

## 8. A `switch` és az `if` összehasonlítása

Mindkét szerkezet alkalmas feltételes elágazások megvalósítására, de más helyzetekben célszerű használni őket.

`if` használata:

```javascript
const eletkor = 20;

if (eletkor < 13) {
    console.log('Gyermek');
} else if (eletkor < 18) {
    console.log('Kiskorú');
} else {
    console.log('Felnőtt');
}
```

Itt különböző logikai feltételeket vizsgálunk.

`switch` használata:

```javascript
const szerep = 'admin';

switch (szerep) {
    case 'admin':
        console.log('Adminisztrátor');
        break;

    case 'user':
        console.log('Felhasználó');
        break;

    case 'guest':
        console.log('Vendég');
        break;

    default:
        console.log('Ismeretlen szerepkör');
}
```

Itt egy változó konkrét értékei alapján választunk.

| Szempont                    | `if`                          | `switch`                 |
| --------------------------- | ----------------------------- | ------------------------ |
| Működés                     | Logikai feltételeket vizsgál  | Értékeket hasonlít össze |
| Összehasonlítás             | Többféle feltétel használható | Szigorú egyenlőség       |
| Tartományvizsgálat          | Igen                          | Közvetlenül nem          |
| Több konkrét érték kezelése | Lehetséges                    | Általában áttekinthetőbb |
| Alapértelmezett ág          | `else`                        | `default`                |

Mikor melyiket használjuk?

- `if`: ha összetett feltételeket, tartományokat vagy logikai kifejezéseket vizsgálunk.
- `switch`: ha egy változó több konkrét értékétől függően szeretnénk különböző műveleteket végrehajtani.

## 9. A `switch` használata szöveges értékekkel

A `switch` nemcsak számokkal, hanem szöveges értékekkel is használható.

Például egy egyszerű menürendszerben:

```javascript
const menu = 'termekek';

switch (menu) {
    case 'kezdolap':
        console.log('Kezdőlap megnyitása');
        break;

    case 'termekek':
        console.log('Termékek listázása');
        break;

    case 'kapcsolat':
        console.log('Kapcsolat oldal megnyitása');
        break;

    default:
        console.log('Az oldal nem található');
}
```

A `switch` pontosan összehasonlítja a szöveges értékeket. Ezért például a `"Termekek"` és a `"termekek"` két különböző érték.

A kis- és nagybetűk eltérése tehát számít.

## 10. Összetettebb példa: egyszerű számológép

Készítsünk egy egyszerű számológépet, amely a műveleti jel alapján választja ki az elvégzendő műveletet.

```javascript
const a = 20;
const b = 5;
const muvelet = '*';

switch (muvelet) {
    case '+':
        console.log(a + b);
        break;

    case '-':
        console.log(a - b);
        break;

    case '*':
        console.log(a * b);
        break;

    case '/':
        if (b !== 0) {
            console.log(a / b);
        } else {
            console.log('Nullával nem lehet osztani!');
        }
        break;

    default:
        console.log('Ismeretlen művelet!');
}
```

A program működése:

1. Létrehozza az `a` és `b` változókat.
2. A `muvelet` változóban eltárolja a kívánt művelet jelét.
3. A `switch` megvizsgálja a műveleti jelet.
4. A megfelelő `case` ágban elvégzi a műveletet.
5. Osztás esetén ellenőrzi, hogy a második szám nem nulla-e.
6. Ismeretlen műveleti jel esetén a `default` ág hajtódik végre.

A konzolon megjelenő eredmény:

```
100
```

Ez a példa azt is megmutatja, hogy a `switch` ágakon belül további feltételes elágazásokat, például `if` utasításokat is használhatunk.

# 11. Ellenőrző kérdések

1\. Mire használjuk a `switch` utasítást JavaScriptben?

A) Ciklusok létrehozására.

B) Több lehetséges érték alapján történő elágazásra.

C) Változók törlésére.

D) Függvények létrehozására.

2\. Melyik kulcsszóval kezdődik a többágú elágazás?

A) `case`

B) `default`

C) `switch`

D) `break`

3\. Mi a `case` szerepe?

A) Meghatároz egy lehetséges értéket.

B) Kilép a ciklusból.

C) Létrehoz egy változót.

D) Leállítja a programot.

4\. Mi a `break` utasítás feladata?

A) Új `case` ágat hoz létre.

B) Visszatér egy függvényből.

C) Megszakítja a teljes JavaScript-futtatókörnyezetet.

D) Kilép a `switch` szerkezetből.

5\. Mikor hajtódik végre a `default` ág?

A) Minden esetben.

B) Csak az első `case` előtt.

C) Ha egyik `case` sem illeszkedik.

D) Ha a `break` lefutott.

6\. Mi történik, ha egy `case` ág végéről elhagyjuk a `break` utasítást?

A) A program hibát jelez.

B) A következő ág utasításai is végrehajtódhatnak.

C) A `default` ág automatikusan kimarad.

D) A `switch` azonnal újraindul.

7\. Milyen összehasonlítást használ a `switch`?

A) `==`

B) `!=`

C) `===`

D) `=`

8\. Melyik esetben célszerűbb általában a `switch` használata?

A) Ha egy szám értékét több tartomány alapján vizsgáljuk.

B) Ha egy változó több konkrét értéke alapján választunk műveletet.

C) Ha ciklust szeretnénk létrehozni.

D) Ha egy tömb elemeit szeretnénk rendezni.

9\. Mi lesz az eredmény az alábbi kódban?

```javascript
const szam = 2;

switch (szam) {
    case 1:
        console.log('A');
        break;

    case 2:
        console.log('B');
        break;

    case 3:
        console.log('C');
        break;

    default:
        console.log('D');
}
```

A) A

B) B

C) C

D) D

10\. Melyik állítás igaz a `switch` utasításra?

A) Csak számokkal használható.

B) Nem használható szöveges értékekkel.

C) A `default` ág kötelező.

D) A `case` ágakban többféle adattípus is vizsgálható.

# 12. Gyakorlati feladatok

A következő feladatokat JavaScriptben oldd meg! A megoldásokhoz használd a `switch`, `case`, `break` és `default` utasításokat.

1\. Hét napjai

Hozz létre egy `nap` nevű változót, amely 1 és 7 közötti számot tartalmaz.

A `switch` segítségével jelenítsd meg a megfelelő nap nevét!

Ha a szám nem 1 és 7 közé esik, jelenjen meg az „Érvénytelen nap!” üzenet.

2\. Osztályzatok

Hozz létre egy `jegy` nevű változót.

A lehetséges értékek alapján jelenítsd meg:

- 1 – Elégtelen
- 2 – Elégséges
- 3 – Közepes
- 4 – Jó
- 5 – Jeles

Más érték esetén jelenjen meg egy hibaüzenet.

3\. Hétköznap vagy hétvége

Hozz létre egy `nap` változót.

A `switch` segítségével döntsd el, hogy az adott nap hétköznap vagy hétvége!

A hétfő–péntek értékekhez ugyanazt az utasítást használd, a szombat és vasárnap értékekhez pedig egy másikat.

4\. Egyszerű számológép

Hozz létre két számot tároló változót és egy műveleti jelet tartalmazó változót.

A `switch` segítségével végezd el a következő műveleteket:

- összeadás (`+`)
- kivonás (`-`)
- szorzás (`*`)
- osztás (`/`)

Osztás esetén ellenőrizd, hogy a második szám nem nulla-e!

5\. Évszakok

Hozz létre egy `honap` nevű változót, amely 1 és 12 közötti számot tartalmaz.

A `switch` segítségével jelenítsd meg az évszakot:

- 12, 1, 2 – Tél
- 3, 4, 5 – Tavasz
- 6, 7, 8 – Nyár
- 9, 10, 11 – Ősz

Más érték esetén jelenjen meg egy hibaüzenet!

6\. Szerepkörök

Hozz létre egy `szerep` nevű szöveges változót.

A lehetséges értékek:

- `"admin"` – Adminisztrátor
- `"user"` – Felhasználó
- `"guest"` – Vendég

A `switch` segítségével jelenítsd meg a szerepkörhöz tartozó jogosultsági szintet!

Ismeretlen szerepkör esetén jelenjen meg egy hibaüzenet.

7\. Közlekedési lámpa

Hozz létre egy `szin` nevű változót.

A lehetséges értékek:

- `"piros"` – Állj!
- `"sarga"` – Figyelem!
- `"zold"` – Szabad az áthaladás!

A `switch` segítségével jelenítsd meg a megfelelő üzenetet!

8\. Egyszerű éttermi rendelés

Hozz létre egy `rendeles` nevű változót.

A lehetséges értékek:

- `"pizza"` – Pizza rendelés
- `"hamburger"` – Hamburger rendelés
- `"salata"` – Saláta rendelés
- `"leves"` – Leves rendelés

A `switch` segítségével jelenítsd meg a kiválasztott étel nevét és egy hozzá tartozó árat!

Ismeretlen rendelés esetén jelenjen meg egy hibaüzenet.

9\. Hónapok napjainak száma

Hozz létre egy `honap` változót, amely 1 és 12 közötti számot tartalmaz.

A `switch` segítségével jelenítsd meg az adott hónap napjainak számát!

- 31 napos hónapok: 1, 3, 5, 7, 8, 10, 12.
- 30 napos hónapok: 4, 6, 9, 11.
- Február: 28 nap.

Az egyszerűség kedvéért ne foglalkozz a szökőévekkel!

10\. Menüvezérelt program

Készíts egy egyszerű menürendszert!

Hozz létre egy `valasztas` változót, amely a felhasználó választását tárolja.

A lehetséges menüpontok:

- 1 – Felhasználók listázása
- 2 – Új felhasználó hozzáadása
- 3 – Felhasználó törlése
- 4 – Kilépés

A `switch` segítségével jelenítsd meg a kiválasztott menüpontnak megfelelő üzenetet!

Más érték esetén jelenjen meg az „Érvénytelen menüpont!” üzenet.

# 13. Összefoglalás

A `switch` egy többágú elágazási szerkezet, amely segítségével egy kifejezés értéke alapján különböző utasításokat hajthatunk végre.

A legfontosabb elemei:

| Elem      | Feladat                           |
| --------- | --------------------------------- |
| `switch`  | Elindítja az elágazást            |
| `case`    | Meghatároz egy lehetséges értéket |
| `break`   | Kilép a `switch` szerkezetből     |
| `default` | Kezeli a nem illeszkedő értékeket |

A legfontosabb tudnivalók:

- A `switch` szigorú egyenlőséget (`===`) használ.
- A `break` megakadályozza a további ágak nem kívánt végrehajtását.
- Több `case` ág közös utasításokat is használhat.
- A `default` ág nem kötelező, de hasznos.
- A `switch` számokkal és szöveges értékekkel is használható.
- Összetett logikai feltételekhez általában az `if` szerkezet megfelelőbb.
