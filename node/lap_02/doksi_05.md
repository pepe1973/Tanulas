# Összetett adattípusok JavaScriptben

## 1. Mik azok az összetett adattípusok?

A JavaScriptben az adatokat két nagy csoportba sorolhatjuk:

1. Primitív adattípusok
2. Összetett adattípusok

A primitív adattípusok egyszerű, önálló értékeket tárolnak, például szöveget, számot vagy logikai értéket.

Az összetett adattípusok ezzel szemben több érték vagy tulajdonság együttes tárolására és kezelésére alkalmasak.

Például egy felhasználó adatait nem feltétlenül szeretnénk különálló változókban tárolni:

```javascript
let nev = 'Kovács Anna';
let kor = 25;
let varos = 'Szeged';
let aktiv = true;
```

Ehelyett az összetartozó adatokat egyetlen objektumba rendezhetjük:

```javascript
let felhasznalo = {
    nev: 'Kovács Anna',
    kor: 25,
    varos: 'Szeged',
    aktiv: true,
};
```

Az összetett adattípusok segítségével áttekinthetőbbé, rendezettebbé és könnyebben kezelhetővé tehetjük a program adatstruktúráit.

A JavaScript legfontosabb összetett adattípusai és adatszerkezetei:

- Objektum (`Object`)
- Tömb (`Array`)
- Függvény (`Function`)
- Dátum (`Date`)
- Térkép (`Map`)
- Halmaz (`Set`)
- Gyengén hivatkozó térkép (`WeakMap`)
- Gyengén hivatkozó halmaz (`WeakSet`)

Ezek közül az objektumok és a tömbök a leggyakrabban használt adatszerkezetek.

## 2. Objektum – Object

Az objektum olyan összetett adattípus, amely adatokat tulajdonságok formájában tárol.

Egy objektum tulajdonságai általában kulcs-érték párokból állnak.

A kulcs a tulajdonság neve, az érték pedig az eltárolt adat.

### 2.1. Objektum létrehozása

Az objektumokat leggyakrabban kapcsos zárójelek (`{}`) segítségével hozzuk létre.

```javascript
let felhasznalo = {
    nev: 'Kovács Anna',
    kor: 25,
    varos: 'Szeged',
    aktiv: true,
};
```

Az objektum négy tulajdonságot tartalmaz:

| Tulajdonság | Érték           | Adattípus |
| ----------- | --------------- | --------- |
| `nev`       | `"Kovács Anna"` | string    |
| `kor`       | `25`            | number    |
| `varos`     | `"Szeged"`      | string    |
| `aktiv`     | `true`          | boolean   |

Egy objektum tulajdonságainak értéke különböző adattípusú lehet. Akár másik objektumot, tömböt vagy függvényt is tárolhatunk benne.

### 2.2. Objektumtulajdonságok elérése

Az objektum tulajdonságait kétféleképpen érhetjük el.

Pontozott jelöléssel:

```javascript
let felhasznalo = {
    nev: 'Anna',
    kor: 25,
};

console.log(felhasznalo.nev);
console.log(felhasznalo.kor);
```

Szögletes zárójeles jelöléssel:

```javascript
console.log(felhasznalo['nev']);
console.log(felhasznalo['kor']);
```

Mindkét megoldás ugyanazt az eredményt adja.

A szögletes zárójeles megoldás különösen akkor hasznos, ha a tulajdonság neve változóban található.

```javascript
let tulajdonsag = 'nev';

console.log(felhasznalo[tulajdonsag]);
```

### 2.3. Objektumtulajdonságok módosítása

Egy objektum meglévő tulajdonságainak értékét egyszerű értékadással módosíthatjuk.

```javascript
let felhasznalo = {
    nev: 'Anna',
    kor: 25,
};

felhasznalo.kor = 26;

console.log(felhasznalo.kor);
```

Eredmény:

```
26
```

### 2.4. Új tulajdonság hozzáadása

Egy objektumhoz új tulajdonságot is hozzáadhatunk.

```javascript
let felhasznalo = {
    nev: 'Anna',
    kor: 25,
};

felhasznalo.varos = 'Szeged';

console.log(felhasznalo);
```

Az objektum az új tulajdonsággal egészül ki.

### 2.5. Tulajdonság törlése

A `delete` operátor segítségével eltávolíthatunk egy tulajdonságot.

```javascript
let felhasznalo = {
    nev: 'Anna',
    kor: 25,
    varos: 'Szeged',
};

delete felhasznalo.kor;

console.log(felhasznalo);
```

A `kor` tulajdonság törlődik az objektumból.

### 2.6. Beágyazott objektumok

Egy objektum másik objektumot is tartalmazhat.

```javascript
let felhasznalo = {
    nev: 'Anna',
    kor: 25,
    cim: {
        varos: 'Szeged',
        utca: 'Kossuth Lajos utca',
        hazszam: 10,
    },
};
```

A beágyazott objektum tulajdonságait egymás után fűzött pontozott jelöléssel érhetjük el.

```javascript
console.log(felhasznalo.cim.varos);
console.log(felhasznalo.cim.utca);
```

Eredmény:

```
Szeged
Kossuth Lajos utca
```

A beágyazott objektumok segítségével összetettebb adatstruktúrákat alakíthatunk ki.

## 3. Tömb – Array

A tömb olyan adatszerkezet, amely több érték tárolására alkalmas, meghatározott sorrendben.

A tömb elemeit indexek segítségével érhetjük el. A JavaScriptben az indexelés nullától kezdődik.

Például:

```javascript
let gyumolcsok = ['alma', 'körte', 'szilva', 'barack'];
```

A tömb elemei:

| Index | Érték  |
| ----- | ------ |
| 0     | alma   |
| 1     | körte  |
| 2     | szilva |
| 3     | barack |

### 3.1. Tömb létrehozása

A tömböket leggyakrabban szögletes zárójelek (`[]`) segítségével hozzuk létre.

```javascript
let szamok = [10, 20, 30, 40, 50];

let nevek = ['Anna', 'Péter', 'Katalin'];

let adatok = [10, 'JavaScript', true];
```

A tömbök különböző adattípusú értékeket is tartalmazhatnak.

### 3.2. Tömb elemeinek elérése

Az elemeket az indexük alapján érhetjük el.

```javascript
let gyumolcsok = ['alma', 'körte', 'szilva'];

console.log(gyumolcsok[0]);
console.log(gyumolcsok[1]);
console.log(gyumolcsok[2]);
```

Eredmény:

```
alma
körte
szilva
```

Ha olyan indexet használunk, amelyhez nem tartozik elem, akkor az eredmény `undefined` lesz.

```javascript
console.log(gyumolcsok[5]);
```

### 3.3. Tömb elemeinek módosítása

A tömb egy adott elemét az index segítségével módosíthatjuk.

```javascript
let gyumolcsok = ['alma', 'körte', 'szilva'];

gyumolcsok[1] = 'barack';

console.log(gyumolcsok);
```

Eredmény:

```
["alma", "barack", "szilva"]
```

### 3.4. A tömb hossza

A `length` tulajdonság megadja, hogy hány elemet tartalmaz a tömb.

```javascript
let szamok = [10, 20, 30, 40];

console.log(szamok.length);
```

Eredmény:

```
4
```

### 3.5. Elemek hozzáadása

A `push()` metódus a tömb végére helyez egy vagy több elemet.

```javascript
let gyumolcsok = ['alma', 'körte'];

gyumolcsok.push('szilva');

console.log(gyumolcsok);
```

A `unshift()` metódus a tömb elejére helyez új elemet.

```javascript
gyumolcsok.unshift('barack');

console.log(gyumolcsok);
```

### 3.6. Elemek eltávolítása

A `pop()` eltávolítja a tömb utolsó elemét.

```javascript
let szamok = [10, 20, 30];

szamok.pop();

console.log(szamok);
```

Eredmény:

```
[10, 20]
```

A `shift()` eltávolítja a tömb első elemét.

```javascript
let szamok = [10, 20, 30];

szamok.shift();

console.log(szamok);
```

Eredmény:

```
[20, 30]
```

### 3.7. Tömb bejárása

A tömb elemeit ciklusok segítségével dolgozhatjuk fel.

For ciklussal:

```javascript
let gyumolcsok = ['alma', 'körte', 'szilva'];

for (let i = 0; i < gyumolcsok.length; i++) {
    console.log(gyumolcsok[i]);
}
```

For...of ciklussal:

```javascript
for (let gyumolcs of gyumolcsok) {
    console.log(gyumolcs);
}
```

forEach() metódussal:

```javascript
gyumolcsok.forEach(function (gyumolcs) {
    console.log(gyumolcs);
});
```

Mindhárom megoldás alkalmas a tömb elemeinek feldolgozására.

### 3.8. Tömbök beágyazása

Egy tömb másik tömböt is tartalmazhat. Ezt többdimenziós tömbnek vagy tömbökből álló tömbnek nevezzük.

```javascript
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
];
```

Egy adott elem eléréséhez több indexet használunk.

```javascript
console.log(matrix[0][0]);
console.log(matrix[1][2]);
console.log(matrix[2][1]);
```

Eredmény:

```
1
6
8
```

## 4. Tömbök és objektumok kombinálása

A JavaScriptben gyakran előfordul, hogy egy tömb objektumokat tartalmaz.

Ez különösen hasznos például felhasználók, termékek vagy megrendelések adatainak tárolásakor.

```javascript
let felhasznalok = [
    {
        id: 1,
        nev: 'Anna',
        kor: 25,
    },
    {
        id: 2,
        nev: 'Péter',
        kor: 30,
    },
    {
        id: 3,
        nev: 'Katalin',
        kor: 28,
    },
];
```

A tömb egyes objektumait index segítségével érhetjük el.

```javascript
console.log(felhasznalok[0].nev);
console.log(felhasznalok[1].kor);
```

Eredmény:

```
Anna
30
```

Az objektumokból álló tömböket gyakran használjuk webalkalmazásokban, például adatbázisból érkező adatok feldolgozásakor.

## 5. Function – függvény mint összetett adattípus

A JavaScriptben a függvények is értékek. Ez azt jelenti, hogy változóhoz rendelhetők, paraméterként átadhatók más függvényeknek, és visszatérési értékként is szerepelhetnek.

A függvényeket ezért gyakran első osztályú függvényekként (first-class functions) említjük.

### 5.1. Függvény létrehozása

```javascript
function koszones() {
    console.log('Szia!');
}

koszones();
```

A `function` kulcsszóval létrehozott függvény egy meghatározott feladat végrehajtására alkalmas kódrészlet.

### 5.2. Függvény tárolása változóban

A függvényt változóhoz is rendelhetjük.

```javascript
let koszones = function () {
    console.log('Szia!');
};

koszones();
```

Ez egy függvénykifejezés (function expression).

### 5.3. Nyílfüggvény

A függvények rövidebb formában, nyílfüggvényként is létrehozhatók.

```javascript
let osszead = (a, b) => {
    return a + b;
};

console.log(osszead(10, 20));
```

Eredmény:

```
30
```

### 5.4. Függvény mint objektumtulajdonság

Egy objektum tulajdonsága függvény is lehet. Az objektum ilyen függvénytulajdonságát metódusnak nevezzük.

```javascript
let felhasznalo = {
    nev: 'Anna',

    koszones: function () {
        console.log('Szia, ' + this.nev + '!');
    },
};

felhasznalo.koszones();
```

Eredmény:

```
Szia, Anna!
```

## 6. Date – dátum és idő kezelése

A `Date` objektum dátumok és időpontok kezelésére szolgál.

Segítségével lekérdezhetjük az aktuális dátumot, létrehozhatunk egy adott időpontot, valamint dátumműveleteket is végezhetünk.

### 6.1. Aktuális dátum lekérdezése

```javascript
let most = new Date();

console.log(most);
```

A `new Date()` az aktuális dátumot és időpontot tartalmazó Date objektumot hoz létre.

### 6.2. Meghatározott dátum létrehozása

```javascript
let datum = new Date('2026-10-31');

console.log(datum);
```

### 6.3. Dátum részeinek lekérdezése

```javascript
let most = new Date();

console.log(most.getFullYear());
console.log(most.getMonth());
console.log(most.getDate());
console.log(most.getHours());
console.log(most.getMinutes());
```

Fontos, hogy a `getMonth()` metódus a hónapokat nullától indexeli:

- 0 – január;
- 1 – február;
- 2 – március;
- ...
- 11 – december.

### 6.4. Dátum módosítása

A Date objektum dátum- és időértékei különböző metódusokkal módosíthatók.

```javascript
let datum = new Date('2026-10-31');

datum.setFullYear(2027);

console.log(datum);
```

## 7. Map – kulcs-érték alapú adatszerkezet

A `Map` olyan adatszerkezet, amely kulcs-érték párokat tárol.

Hasonlít az objektumhoz, de több szempontból rugalmasabb:

- a kulcs bármilyen adattípus lehet;
- megőrzi a beszúrás sorrendjét;
- közvetlenül lekérdezhető az elemek száma;
- könnyen bejárható.

### 7.1. Map létrehozása

```javascript
let felhasznalo = new Map();

felhasznalo.set('nev', 'Anna');
felhasznalo.set('kor', 25);
felhasznalo.set('varos', 'Szeged');
```

A `set()` metódus új kulcs-érték párt hoz létre, vagy módosítja a már meglévő kulcshoz tartozó értéket.

### 7.2. Értékek lekérdezése

A `get()` metódussal kérdezhetjük le az adott kulcshoz tartozó értéket.

```javascript
console.log(felhasznalo.get('nev'));
console.log(felhasznalo.get('kor'));
```

### 7.3. Kulcs létezésének ellenőrzése

A `has()` metódus megvizsgálja, hogy létezik-e egy adott kulcs.

```javascript
console.log(felhasznalo.has('nev'));
console.log(felhasznalo.has('email'));
```

Eredmény:

```
true
false
```

### 7.4. Elem törlése és Map ürítése

```javascript
felhasznalo.delete('kor');
```

Az összes elem eltávolításához:

```javascript
felhasznalo.clear();
```

### 7.5. Map bejárása

```javascript
let adatok = new Map();

adatok.set('nev', 'Anna');
adatok.set('kor', 25);

for (let [kulcs, ertek] of adatok) {
    console.log(kulcs, ertek);
}
```

## 8. Set – egyedi értékek halmaza

A `Set` olyan adatszerkezet, amely csak egyedi értékeket tárol.

Ha ugyanazt az értéket többször próbáljuk hozzáadni, a Set csak egy példányt tart meg belőle.

### 8.1. Set létrehozása

```javascript
let szamok = new Set();

szamok.add(10);
szamok.add(20);
szamok.add(30);
szamok.add(20);

console.log(szamok);
```

A `20` érték csak egyszer szerepel a halmazban.

### 8.2. Set létrehozása tömbből

```javascript
let szamok = new Set([10, 20, 20, 30, 30, 40]);

console.log(szamok);
```

A Set automatikusan eltávolítja az ismétlődő értékeket.

### 8.3. Elem létezésének ellenőrzése

A `has()` metódussal ellenőrizhetjük, hogy egy érték szerepel-e a halmazban.

```javascript
let nevek = new Set(['Anna', 'Péter', 'Katalin']);

console.log(nevek.has('Anna'));
console.log(nevek.has('Béla'));
```

### 8.4. Elem törlése és halmaz ürítése

```javascript
nevek.delete('Péter');
```

A teljes halmaz ürítése:

```javascript
nevek.clear();
```

### 8.5. Set bejárása

```javascript
let szamok = new Set([10, 20, 30]);

for (let szam of szamok) {
    console.log(szam);
}
```

A Set különösen hasznos ismétlődő adatok eltávolítására és egyedi értékek nyilvántartására.

## 9. WeakMap és WeakSet

A `WeakMap` és a `WeakSet` speciális adatszerkezetek, amelyek objektumokra vonatkozó gyenge hivatkozásokat kezelnek.

Ezeket elsősorban speciális programozási helyzetekben használjuk, amikor az objektumokhoz kapcsolódó kiegészítő adatokat vagy tagságot szeretnénk nyilvántartani anélkül, hogy az adatszerkezet önmagában megakadályozná az objektum memóriából való felszabadítását.

### 9.1. WeakMap

A WeakMap kulcsai csak objektumok vagy nem regisztrált Symbol értékek lehetnek. A kulcsok gyengén hivatkozottak.

```javascript
let gyengeTarolo = new WeakMap();

let felhasznalo = {
    nev: 'Anna',
};

gyengeTarolo.set(felhasznalo, 'Adminisztrátor');

console.log(gyengeTarolo.get(felhasznalo));
```

A WeakMap nem járható be `for...of` ciklussal, és nincs `size` tulajdonsága.

### 9.2. WeakSet

A WeakSet objektumokat és nem regisztrált Symbol értékeket képes tárolni gyenge hivatkozással.

```javascript
let aktivFelhasznalok = new WeakSet();

let felhasznalo = {
    nev: 'Anna',
};

aktivFelhasznalok.add(felhasznalo);

console.log(aktivFelhasznalok.has(felhasznalo));
```

A WeakSet nem alkalmas egyszerű számok vagy szövegek tárolására, és nem járható be hagyományos ciklussal.

## 10. A primitív és összetett adattípusok közötti különbség

A két adattípus-csoport közötti különbség különösen fontos a változók értékadásának és másolásának megértéséhez.

### 10.1. Primitív értékek másolása

Primitív értékek esetén az érték másolódik.

```javascript
let a = 10;
let b = a;

b = 20;

console.log(a);
console.log(b);
```

Eredmény:

```
10
20
```

A `b` változó módosítása nem változtatja meg az `a` értékét.

### 10.2. Objektumok másolása

Objektumok esetén az értékadáskor a hivatkozás másolódik.

```javascript
let elso = {
    nev: 'Anna',
};

let masodik = elso;

masodik.nev = 'Péter';

console.log(elso.nev);
console.log(masodik.nev);
```

Eredmény:

```
Péter
Péter
```

Mindkét változó ugyanarra az objektumra hivatkozik, ezért az egyik változón keresztül végrehajtott módosítás a másikon keresztül is látható.

### 10.3. Objektum másolása spread operátorral

Ha különálló objektumot szeretnénk létrehozni, használhatjuk a spread operátort.

```javascript
let elso = {
    nev: 'Anna',
    kor: 25,
};

let masodik = { ...elso };

masodik.nev = 'Péter';

console.log(elso.nev);
console.log(masodik.nev);
```

Eredmény:

```
Anna
Péter
```

Fontos, hogy a spread operátor csak sekély másolatot (shallow copy) készít. A beágyazott objektumok továbbra is közös hivatkozások lehetnek.

### 10.4. Tömb másolása

Tömbök esetén is használhatjuk a spread operátort.

```javascript
let eredeti = [10, 20, 30];

let masolat = [...eredeti];

masolat.push(40);

console.log(eredeti);
console.log(masolat);
```

Eredmény:

```
[10, 20, 30]
[10, 20, 30, 40]
```

A két tömb különálló tömb, ezért az egyik módosítása nem változtatja meg a másikat.

## 11. Az összetett adattípusok ellenőrzése

A `typeof` operátorral az összetett értékek típusát is megvizsgálhatjuk.

```javascript
let objektum = {};
let tomb = [];
let datum = new Date();
let fuggveny = function () {};

console.log(typeof objektum);
console.log(typeof tomb);
console.log(typeof datum);
console.log(typeof fuggveny);
```

Eredmény:

```
object
object
object
function
```

Fontos megjegyzések:

- A tömbök esetében a `typeof` eredménye `"object"`.
- A Date objektum esetében szintén `"object"` az eredmény.
- A függvények esetében a `typeof` eredménye `"function"`.

### 11.1. Tömb ellenőrzése

Mivel a tömbökre a `typeof` `"object"` értéket ad vissza, a tömbök ellenőrzésére az `Array.isArray()` metódust használjuk.

```javascript
let tomb = [10, 20, 30];
let objektum = {
    nev: 'Anna',
};

console.log(Array.isArray(tomb));
console.log(Array.isArray(objektum));
```

Eredmény:

```
true
false
```

# 12. Összefoglalás

| Adattípus  | Felhasználás                         | Példa             |
| ---------- | ------------------------------------ | ----------------- |
| `Object`   | Kulcs-érték párok tárolása           | `{ nev: "Anna" }` |
| `Array`    | Rendezett elemek tárolása            | `[10, 20, 30]`    |
| `Function` | Újrafelhasználható műveletek         | `function() {}`   |
| `Date`     | Dátum és idő kezelése                | `new Date()`      |
| `Map`      | Rugalmas kulcs-érték tárolás         | `new Map()`       |
| `Set`      | Egyedi értékek tárolása              | `new Set()`       |
| `WeakMap`  | Objektumkulcsokhoz kötött adatok     | `new WeakMap()`   |
| `WeakSet`  | Objektumok tagságának nyilvántartása | `new WeakSet()`   |

A legfontosabb tudnivalók:

- Az objektumok kulcs-érték párokban tárolják az adatokat.
- A tömbök rendezett, indexelhető adatszerkezetek.
- A függvények JavaScriptben szintén értékek.
- A Date objektum dátumok és időpontok kezelésére alkalmas.
- A Map különböző típusú kulcsokat is képes kezelni.
- A Set csak egyedi értékeket tárol.
- A WeakMap és WeakSet objektumokhoz kapcsolódó gyenge hivatkozásokat kezel.
- Az összetett értékek másolásakor a hivatkozások viselkedésére is figyelni kell.
- A `typeof` önmagában nem elegendő a tömbök felismerésére; erre az `Array.isArray()` használható.

# 13. Ellenőrző kérdések

1. Mit nevezünk összetett adattípusnak JavaScriptben?
2. Mi a különbség az objektum és a tömb között?
3. Hogyan érhetjük el egy objektum tulajdonságait?
4. Miért nullától kezdődik a tömbök indexelése?
5. Mire használjuk a `push()` és a `pop()` metódusokat?
6. Mit jelent az, hogy a függvények első osztályú értékek JavaScriptben?
7. Milyen célra használjuk a Date objektumot?
8. Mi a különbség a Map és a Set között?
9. Miért nem elegendő a `typeof` operátor a tömbök felismerésére?
10. Mi a különbség a primitív értékek és az objektumok másolása között?

# 14. Gyakorlati feladatok

A feladatokat JavaScriptben oldd meg! A megoldások során használj objektumokat, tömböket, függvényeket és a megfelelő beépített adatszerkezeteket. A feladatokhoz nem tartozik megoldás.

1\. feladat – Egyszerű objektum létrehozása

Hozz létre egy `diak` nevű objektumot a következő tulajdonságokkal:

- `nev`
- `kor`
- `osztaly`
- `varos`
- `aktiv`

Rendelj hozzájuk tetszőleges értékeket!

Ezután:

- Jelenítsd meg az objektum összes tulajdonságát!
- Módosítsd a diák életkorát!
- Adj hozzá egy új `email` tulajdonságot!
- Töröld az `aktiv` tulajdonságot!

2\. feladat – Beágyazott objektum

Hozz létre egy `termek` nevű objektumot, amely a következő adatokat tartalmazza:

- termék neve;
- ár;
- kategória;
- készleten lévő darabszám;
- gyártó adatai.

A gyártó adatait külön beágyazott objektumban tárold:

- cégnév;
- ország;
- weboldal.

Jelenítsd meg külön a termék nevét és a gyártó országát!

3\. feladat – Tömbök kezelése

Hozz létre egy `szamok` nevű tömböt legalább 10 egész számmal!

Ezután:

- Jelenítsd meg a tömb első elemét!
- Jelenítsd meg az utolsó elemét!
- Jelenítsd meg a tömb hosszát!
- Módosítsd a harmadik elemet!
- Adj hozzá két új elemet!
- Távolítsd el az utolsó elemet!

4\. feladat – Tömb bejárása és számítások

Hozz létre egy legalább 10 elemből álló számtömböt!

Ciklus segítségével:

- Jelenítsd meg az összes elemet!
- Számold ki az elemek összegét!
- Határozd meg a legnagyobb értéket!
- Határozd meg a legkisebb értéket!
- Számold ki az elemek átlagát!

5\. feladat – Objektumokból álló tömb

Hozz létre egy `termekek` nevű tömböt, amely legalább öt termékobjektumot tartalmaz!

Minden termék rendelkezzen az alábbi tulajdonságokkal:

- `id`
- `nev`
- `ar`
- `keszlet`

Ezután:

- Jelenítsd meg az összes termék nevét!
- Jelenítsd meg az összes termék árát!
- Számold ki a termékek átlagárát!
- Jelenítsd meg azokat a termékeket, amelyek ára meghalad egy általad megadott összeget!

6\. feladat – Függvények használata

Hozz létre egy `szamitasok` nevű objektumot!

Az objektum tartalmazzon négy metódust:

- `osszead(a, b)`
- `kivon(a, b)`
- `szoroz(a, b)`
- `oszt(a, b)`

A metódusok végezzék el a nevüknek megfelelő műveleteket, és adják vissza az eredményt!

Ezután hívd meg mindegyik metódust, és jelenítsd meg az eredményeket!

7\. feladat – Dátum és idő

Hozz létre egy `Date` objektumot az aktuális dátummal!

Jelenítsd meg külön:

- az évet;
- a hónapot;
- a napot;
- az órát;
- a percet;
- a másodpercet.

Ezután hozz létre egy másik Date objektumot egy általad megadott dátummal, és jelenítsd meg annak adatait is!

8\. feladat – Map adatszerkezet

Hozz létre egy `felhasznalo` nevű Map adatszerkezetet!

Tárold el benne a következő adatokat:

- név;
- életkor;
- e-mail-cím;
- város.

Ezután:

- Jelenítsd meg az összes értéket!
- Módosítsd a felhasználó életkorát!
- Ellenőrizd, hogy létezik-e az `email` kulcs!
- Töröld a város adatát!
- Járd be a Map összes elemét egy ciklussal!

9\. feladat – Set adatszerkezet

Hozz létre egy tömböt legalább 15 számmal úgy, hogy több érték ismétlődjön benne!

Alakítsd át a tömböt Set adatszerkezetté!

Ezután:

- Jelenítsd meg az eredeti tömböt!
- Jelenítsd meg a Set elemeit!
- Hasonlítsd össze az eredeti tömb és a Set elemszámát!
- Ellenőrizd egy általad választott szám létezését!
- Adj hozzá egy új értéket!
- Távolíts el egy meglévő értéket!

10\. feladat – Összetett adatkezelési feladat

Készíts egy egyszerű könyvnyilvántartó programot!

Hozz létre egy `konyvek` nevű tömböt, amely legalább öt könyvobjektumot tartalmaz.

Minden könyv rendelkezzen az alábbi tulajdonságokkal:

- `id`
- `cim`
- `szerzo`
- `kiadasEve`
- `ar`
- `elerheto`

Ezután készíts külön függvényeket az alábbi műveletekre:

1. Az összes könyv adatainak megjelenítése.
2. Egy könyv keresése cím alapján.
3. A legdrágább könyv meghatározása.
4. Az elérhető könyvek listázása.
5. Egy könyv árának módosítása.
6. Egy könyv eltávolítása az adatbázisból.

A program végén hívd meg az összes függvényt, és ellenőrizd a működésüket.
