# JavaScript – `for...in` ciklus

## 1. Mi az a `for...in` ciklus?

A `for...in` ciklus a JavaScript egyik bejáró ciklusa. Elsősorban objektumok tulajdonságainak (property) bejárására használjuk.

A ciklus minden ismétléskor az objektum egy-egy tulajdonságának kulcsát, vagyis nevét adja vissza.

Például egy objektum tartalmazhatja egy személy nevét, életkorát és városát:

```javascript
const szemely = {
    nev: 'Kovács Anna',
    kor: 25,
    varos: 'Szeged',
};
```

A `for...in` segítségével végigmehetünk az objektum tulajdonságain anélkül, hogy előre ismernünk kellene azok nevét.

## 2. A `for...in` ciklus felépítése

Általános szintaxisa:

```javascript
for (let kulcs in objektum) {
    // Ciklusmag
}
```

A részek jelentése:

| Elem        | Jelentés                                                |
| ----------- | ------------------------------------------------------- |
| `for`       | A ciklus kezdete.                                       |
| `let kulcs` | Az aktuális tulajdonság nevét tároló változó.           |
| `in`        | Jelzi, hogy az objektum tulajdonságain haladunk végig.  |
| `objektum`  | Az objektum, amelynek tulajdonságait bejárjuk.          |
| `{ }`       | A ciklusmag, amely minden tulajdonságnál végrehajtódik. |

Fontos, hogy a `kulcs` változó nem a tulajdonság értékét, hanem annak nevét tartalmazza.

## 3. Objektum tulajdonságainak bejárása

Nézzünk egy egyszerű példát!

```javascript
const auto = {
    marka: 'Toyota',
    tipus: 'Corolla',
    evjarat: 2022,
    szin: 'fehér',
};

for (let kulcs in auto) {
    console.log(kulcs);
}
```

Kimenet:

```
marka
tipus
evjarat
szin
```

A ciklus minden ismétléskor az objektum következő tulajdonságának nevét rendeli a `kulcs` változóhoz.

A folyamat:

1. Első ismétlés: `kulcs = "marka"`.
2. Második ismétlés: `kulcs = "tipus"`.
3. Harmadik ismétlés: `kulcs = "evjarat"`.
4. Negyedik ismétlés: `kulcs = "szin"`.

Miután az összes bejárható tulajdonságon végighaladt, a ciklus befejeződik.

## 4. A tulajdonságok értékének lekérdezése

A `for...in` a tulajdonságok nevét adja vissza. Ha az értékekre is szükségünk van, a kulcs segítségével érhetjük el őket.

Ehhez szögletes zárójelet használunk:

```javascript
const auto = {
    marka: 'Toyota',
    tipus: 'Corolla',
    evjarat: 2022,
    szin: 'fehér',
};

for (let kulcs in auto) {
    console.log(kulcs, auto[kulcs]);
}
```

Kimenet:

```
marka Toyota
tipus Corolla
evjarat 2022
szin fehér
```

A `auto[kulcs]` kifejezés az objektum aktuális tulajdonságának értékét adja vissza.

Miért nem használjuk az `auto.kulcs` alakot?

Mert ebben az esetben a JavaScript szó szerint a `kulcs` nevű tulajdonságot keresné.

A szögletes zárójelben viszont a `kulcs` változó aktuális értékét használjuk.

```javascript
const szemely = {
    nev: 'Anna',
    kor: 25,
};

for (let kulcs in szemely) {
    console.log(szemely[kulcs]);
}
```

Kimenet:

```
Anna
25
```

## 5. Objektum tulajdonságainak módosítása

A `for...in` segítségével az objektum tulajdonságainak értékét is módosíthatjuk.

```javascript
const arak = {
    kenyer: 600,
    tej: 450,
    sajt: 1200,
};

for (let kulcs in arak) {
    arak[kulcs] = arak[kulcs] * 2;
}

console.log(arak);
```

Kimenet:

```
{
    kenyer: 1200,
    tej: 900,
    sajt: 2400
}
```

A ciklus minden tulajdonság értékét megszorozza kettővel.

A módosítás azért működik, mert az `arak[kulcs]` kifejezéssel közvetlenül az objektum megfelelő tulajdonságát érjük el.

## 6. Feltételek használata a `for...in` ciklusban

A cikluson belül feltételeket is használhatunk.

Például csak a szám típusú értékeket szeretnénk megjeleníteni:

```javascript
const adatok = {
    nev: 'Kovács Anna',
    kor: 25,
    varos: 'Szeged',
    fizetes: 450000,
};

for (let kulcs in adatok) {
    if (typeof adatok[kulcs] === 'number') {
        console.log(kulcs, adatok[kulcs]);
    }
}
```

Kimenet:

```
kor 25
fizetes 450000
```

A `typeof` operátor segítségével megvizsgáljuk az aktuális tulajdonság értékének típusát.

A `typeof` eredménye ebben az esetben `"number"` vagy `"string"`.

## 7. `break` használata

A `break` utasítással megszakíthatjuk a ciklus végrehajtását.

```javascript
const szemely = {
    nev: 'Anna',
    kor: 25,
    varos: 'Szeged',
    foglalkozas: 'fejlesztő',
};

for (let kulcs in szemely) {
    if (kulcs === 'varos') {
        break;
    }

    console.log(kulcs, szemely[kulcs]);
}
```

Kimenet:

```
nev Anna
kor 25
```

Amikor a ciklus eléri a `varos` tulajdonságot, a `break` megszakítja a teljes ciklust.

## 8. `continue` használata

A `continue` utasítás kihagyja az aktuális ismétlés hátralévő részét, majd a következő tulajdonságra lép.

```javascript
const szemely = {
    nev: 'Anna',
    kor: 25,
    varos: 'Szeged',
    foglalkozas: 'fejlesztő',
};

for (let kulcs in szemely) {
    if (kulcs === 'kor') {
        continue;
    }

    console.log(kulcs, szemely[kulcs]);
}
```

Kimenet:

```
nev Anna
varos Szeged
foglalkozas fejlesztő
```

A `kor` tulajdonság kimarad a feldolgozásból, de a ciklus többi része tovább fut.

## 9. `for...in` használata tömbökkel

A `for...in` ciklus tömbökkel is használható, de fontos megérteni a működését.

Tömb esetén a ciklus az elemek indexeit adja vissza, nem közvetlenül az elemek értékét.

```javascript
const gyumolcsok = ['alma', 'körte', 'barack'];

for (let index in gyumolcsok) {
    console.log(index);
}
```

Kimenet:

```
0
1
2
```

Az aktuális értéket az index segítségével kérhetjük le:

```javascript
const gyumolcsok = ['alma', 'körte', 'barack'];

for (let index in gyumolcsok) {
    console.log(gyumolcsok[index]);
}
```

Kimenet:

```
alma
körte
barack
```

Bár a `for...in` tömbökkel is működik, általában nem ez a legjobb választás a tömbök elemeinek bejárására.

Tömbökhöz inkább a `for...of` ciklust használjuk, ha az elemek értékére van szükségünk.

## 10. Saját tulajdonságok és örökölt tulajdonságok

A JavaScript objektumai örökölhetnek tulajdonságokat más objektumoktól.

A `for...in` nemcsak az objektum saját, hanem az örökölt, felsorolható tulajdonságait is bejárhatja.

Ha csak az objektum saját tulajdonságait szeretnénk feldolgozni, használhatjuk az `Object.hasOwn()` metódust.

```javascript
const szulo = {
    orszag: 'Magyarország',
};

const szemely = Object.create(szulo);

szemely.nev = 'Anna';
szemely.kor = 25;

for (let kulcs in szemely) {
    if (Object.hasOwn(szemely, kulcs)) {
        console.log(kulcs, szemely[kulcs]);
    }
}
```

Kimenet:

```
nev Anna
kor 25
```

Az `orszag` tulajdonság örökölt tulajdonság, ezért az `Object.hasOwn()` ellenőrzés miatt nem jelenik meg.

## 11. `for...in` és `for...of` összehasonlítása

A két ciklus neve hasonló, de eltérő célra használjuk őket.

| Szempont                | `for...in`                           | `for...of`                                       |
| ----------------------- | ------------------------------------ | ------------------------------------------------ |
| Elsődleges felhasználás | Objektumok tulajdonságainak bejárása | Iterálható értékek bejárása                      |
| Objektumnál             | Tulajdonságneveket ad vissza         | Egyszerű objektumnál nem használható közvetlenül |
| Tömbnél                 | Indexeket ad vissza                  | Elemértékeket ad vissza                          |
| Szövegnél               | Indexeket ad vissza                  | Karaktereket ad vissza                           |
| `Set` esetén            | Nem erre való                        | Értékeket ad vissza                              |
| `Map` esetén            | Nem erre való                        | Kulcs-érték párokat ad vissza                    |

Példa a különbségre:

```javascript
const gyumolcsok = ['alma', 'körte', 'barack'];

for (let index in gyumolcsok) {
    console.log(index);
}

for (let gyumolcs of gyumolcsok) {
    console.log(gyumolcs);
}
```

Az első ciklus kimenete:

```
0
1
2
```

A második ciklus kimenete:

```
alma
körte
barack
```

A legfontosabb különbség:

- `for...in`: a tulajdonságok kulcsain halad végig.
- `for...of`: az iterálható adatszerkezet értékein halad végig.

## 12. Gyakori hibák

1\. Az érték helyett a kulcs kiírása

```javascript
const szemely = {
    nev: 'Anna',
    kor: 25,
};

for (let kulcs in szemely) {
    console.log(kulcs);
}
```

Ez a tulajdonságok neveit írja ki, nem az értékeket.

Ha az értékeket szeretnénk megjeleníteni:

```javascript
for (let kulcs in szemely) {
    console.log(szemely[kulcs]);
}
```

2\. A pontoperátor helytelen használata

```javascript
for (let kulcs in szemely) {
    console.log(szemely.kulcs);
}
```

Ez nem az aktuális kulcs értékét használja. A helyes forma:

```javascript
console.log(szemely[kulcs]);
```

3\. A `for...in` használata tömbök bejárására

Tömbök esetén a `for...in` indexeket ad vissza. Ha közvetlenül az elemekre van szükségünk, használjunk `for...of` ciklust.

4\. Örökölt tulajdonságok figyelmen kívül hagyása

A `for...in` örökölt, felsorolható tulajdonságokat is visszaadhat. Ha csak a saját tulajdonságokra van szükségünk, ellenőrizzük azokat az `Object.hasOwn()` metódussal.

# 13. Ellenőrző kérdések

1\. Mire használjuk elsősorban a `for...in` ciklust?

A) Tömbök elemeinek módosítására.\
B) Objektumok tulajdonságainak bejárására.\
C) Függvények meghívására.\
D) Számok összeadására.

2\. Melyik a `for...in` ciklus helyes szintaxisa?

A)

```javascript
for (let kulcs in objektum) {
    console.log(kulcs);
}
```

B)

```javascript
for (let kulcs of objektum) {
    console.log(kulcs);
}
```

C)

```javascript
foreach (kulcs in objektum) {
    console.log(kulcs);
}
```

D)

```javascript
for (in kulcs objektum) {
    console.log(kulcs);
}
```

3\. Mit tartalmaz a `kulcs` változó?

A) Az objektum teljes tartalmát.\
B) Az aktuális tulajdonság értékét.\
C) Az aktuális tulajdonság nevét.\
D) Az objektum tulajdonságainak számát.

4\. Hogyan kérdezhetjük le dinamikusan egy objektum tulajdonságának értékét?

A) `objektum(kulcs)`\
B) `objektum[kulcs]`\
C) `objektum->kulcs`\
D) `objektum.key`

5\. Mi lesz a kimenet?

```javascript
const auto = {
    marka: 'Toyota',
    evjarat: 2022,
};

for (let kulcs in auto) {
    console.log(kulcs);
}
```

A) `Toyota`, `2022`\
B) `marka`, `evjarat`\
C) `0`, `1`\
D) `auto`

6\. Mit ad vissza a `for...in` ciklus tömbök esetén?

A) Az elemek értékeit.\
B) Az elemek típusát.\
C) Az elemek indexeit.\
D) A tömb hosszát.

7\. Melyik utasítással szakíthatjuk meg teljesen a ciklust?

A) `continue`\
B) `stop`\
C) `exit`\
D) `break`

8\. Mire használható az `Object.hasOwn()` metódus?

A) Egy objektum törlésére.\
B) Annak ellenőrzésére, hogy egy tulajdonság az objektum saját tulajdonsága-e.\
C) Az objektum összes értékének összeadására.\
D) Új tulajdonság automatikus létrehozására.

9\. Melyik ciklus célszerűbb, ha egy tömb elemeinek értékeit szeretnénk közvetlenül feldolgozni?

A) `for...in`\
B) `for...of`\
C) Mindig `while`\
D) Egyik sem.

10\. Mi történik az alábbi kód végrehajtásakor?

```javascript
const szemely = {
    nev: 'Anna',
    kor: 25,
};

for (let kulcs in szemely) {
    console.log(szemely[kulcs]);
}
```

A) Kiírja a `nev` és `kor` kulcsokat.\
B) Kiírja az `Anna` és `25` értékeket.\
C) Hibát okoz.\
D) Csak az `Anna` értéket írja ki.

# 14. Gyakorló feladatok

1\. Objektum tulajdonságainak kiírása

Hozz létre egy `tanulo` nevű objektumot, amely legalább öt tulajdonságot tartalmaz:

- név;
- életkor;
- város;
- osztály;
- átlag.

A feladatod:

- Járd be az objektumot `for...in` ciklussal!
- Írd ki a tulajdonságok nevét!
- Minden tulajdonság külön sorban jelenjen meg!

2\. Kulcsok és értékek megjelenítése

Hozz létre egy `laptop` nevű objektumot, amely tartalmazza a márkát, a típust, a memóriát, a tárhelyet és az árat.

A feladatod:

- Járd be az objektumot `for...in` ciklussal!
- Írd ki minden tulajdonság nevét és értékét!
- A kimenet legyen könnyen olvasható, például: `marka: Lenovo`.

3\. Objektum számértékeinek összeadása

Hozz létre egy `kiadasok` nevű objektumot, amely legalább öt különböző kiadást tartalmaz.

A feladatod:

- Járd be az objektumot `for...in` ciklussal!
- A `typeof` segítségével ellenőrizd, hogy az érték szám-e!
- Add össze a szám típusú értékeket!
- Írd ki az összesített kiadást!

4\. Objektum értékeinek módosítása

Hozz létre egy `arak` nevű objektumot, amely legalább öt termék árát tartalmazza.

A feladatod:

- Járd be az objektumot `for...in` ciklussal!
- Minden termék árát növeld meg 10%-kal!
- Módosítsd az eredeti objektumot!
- A ciklus után írd ki az új árakat!

5\. Tulajdonság keresése

Hozz létre egy `szemely` nevű objektumot, amely több személyes adatot tartalmaz.

A feladatod:

- Kérj be a felhasználótól egy tulajdonságnevet a `prompt()` segítségével!
- A `for...in` ciklussal keresd meg, hogy létezik-e ilyen tulajdonság!
- Ha megtaláltad, írd ki a nevét és az értékét!
- Ha nem található meg, jeleníts meg egy megfelelő üzenetet!
- Használd a `break` utasítást a keresés megszakításához!

6\. Csak a szöveges értékek megjelenítése

Hozz létre egy `adatok` nevű objektumot, amely szöveges, szám- és logikai értékeket is tartalmaz.

A feladatod:

- Járd be az objektumot `for...in` ciklussal!
- A `typeof` segítségével vizsgáld meg az értékek típusát!
- Csak a szöveges értékeket írd ki!
- A többi értéket hagyd ki a feldolgozásból!

7\. Tömb indexeinek és értékeinek megjelenítése

Hozz létre egy `tantargyak` nevű tömböt legalább hat tantárggyal.

A feladatod:

- Járd be a tömböt `for...in` ciklussal!
- Írd ki minden elem indexét és értékét!
- A kimenet például ilyen legyen: `0 - Matematika`.

8\. Örökölt tulajdonságok kiszűrése

Hozz létre egy `alapAdatok` objektumot két tulajdonsággal.

Ezután hozz létre egy másik objektumot az `Object.create()` segítségével, amely örökli az `alapAdatok` tulajdonságait.

A feladatod:

- Adj hozzá az új objektumhoz legalább három saját tulajdonságot!
- Járd be az objektumot `for...in` ciklussal!
- Használd az `Object.hasOwn()` metódust!
- Csak az új objektum saját tulajdonságait írd ki!

9\. Objektum tulajdonságainak kihagyása

Hozz létre egy `dolgozo` nevű objektumot, amely legalább öt tulajdonságot tartalmaz.

A feladatod:

- Járd be az objektumot `for...in` ciklussal!
- A `continue` segítségével hagyd ki az egyik kiválasztott tulajdonságot!
- A többi tulajdonság nevét és értékét jelenítsd meg!

10\. Termékadatok feldolgozása

Hozz létre egy `termek` nevű objektumot, amely a következő adatokat tartalmazza:

- terméknév;
- kategória;
- ár;
- raktárkészlet;
- akciós állapot.

A feladatod:

- Járd be az objektumot `for...in` ciklussal!
- Jelenítsd meg az összes tulajdonság nevét és értékét!
- A szám típusú értékeket külön is számold össze!
- A logikai értékeket külön ellenőrizd!
- Ha az akciós állapot `true`, jelenítsd meg az „Akciós termék” üzenetet!

## 15. Összefoglalás

A `for...in` ciklus elsősorban objektumok tulajdonságainak bejárására szolgál.

A legfontosabb tudnivalók:

- A `for...in` az objektum tulajdonságainak kulcsait adja vissza.
- Az értékeket az `objektum[kulcs]` kifejezéssel érhetjük el.
- Az objektum tulajdonságai módosíthatók a cikluson belül.
- A `break` megszakítja a ciklust.
- A `continue` kihagyja az aktuális ismétlést.
- Tömböknél indexeket ad vissza, nem közvetlenül az elemek értékeit.
- Örökölt tulajdonságokat is bejárhat, ezért szükség esetén használjuk az `Object.hasOwn()` metódust.
- Tömbök értékeinek bejárására általában a `for...of` alkalmasabb.

A két ciklus közötti különbség röviden:

```javascript
// for...in: kulcsok
for (let kulcs in objektum) {
    console.log(kulcs);
}

// for...of: értékek
for (let ertek of tomb) {
    console.log(ertek);
}
```
