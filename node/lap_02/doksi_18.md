# Spread és rest operátor (`...`) JavaScriptben

## 1. Mi a spread és a rest operátor?

A JavaScriptben a három pontból álló (`...`) szintaxist két különböző célra használhatjuk:

- Spread operátor: egy tömb vagy más iterálható érték elemeit különálló értékekként bontja ki.
- Rest operátor: több különálló értéket gyűjt össze egyetlen tömbbe vagy objektumba.

Mindkét esetben ugyanazt a három pontból álló jelölést használjuk, de a működésük és a felhasználási területük eltérő.

A két operátor megértése különösen fontos a tömbök, objektumok, függvényparaméterek és az adatok másolása során.

## 2. Spread operátor (`...`)

A spread operátor jelentése: szétterítés vagy kibontás.

Segítségével egy tömb elemeit különálló értékekként használhatjuk fel egy másik tömbben, függvényhívásban vagy objektumban.

### 2.1. Tömb elemeinek kibontása

Nézzünk egy egyszerű példát!

```javascript
const szamok = [10, 20, 30];

console.log(...szamok);
```

Kimenet:

```
10 20 30
```

A `...szamok` kifejezés a tömb elemeit különálló értékekként adja át.

A spread operátor nélkül a tömb egyetlen értékként jelenne meg:

```javascript
const szamok = [10, 20, 30];

console.log(szamok);
```

Kimenet:

```
[10, 20, 30]
```

### 2.2. Tömbök összefűzése

A spread operátor segítségével több tömb elemeit egy új tömbbe helyezhetjük.

```javascript
const elso = [1, 2, 3];
const masodik = [4, 5, 6];

const eredmeny = [...elso, ...masodik];

console.log(eredmeny);
```

Kimenet:

```
[1, 2, 3, 4, 5, 6]
```

A `...elso` és a `...masodik` kifejezés kibontja a tömbök elemeit, amelyek az új tömbbe kerülnek.

További elemeket is hozzáadhatunk az összefűzés során:

```javascript
const elso = [10, 20];
const masodik = [40, 50];

const eredmeny = [5, ...elso, 30, ...masodik, 60];

console.log(eredmeny);
```

Kimenet:

```
[5, 10, 20, 30, 40, 50, 60]
```

### 2.3. Tömb másolása

A spread operátor egyik gyakori felhasználási területe a tömbök másolása.

```javascript
const eredeti = [10, 20, 30];

const masolat = [...eredeti];

console.log(eredeti);
console.log(masolat);
```

Kimenet:

```
[10, 20, 30]
[10, 20, 30]
```

A két tömb tartalma azonos, de különálló tömbök jönnek létre.

Ez azt jelenti, hogy ha a másolatot módosítjuk, az eredeti tömb elemei nem változnak meg.

```javascript
const eredeti = [10, 20, 30];

const masolat = [...eredeti];

masolat.push(40);

console.log(eredeti); // [10, 20, 30]
console.log(masolat); // [10, 20, 30, 40]
```

Fontos: a spread operátorral készített másolat csak sekély másolat (shallow copy). Ha a tömb másik tömböt vagy objektumot tartalmaz, akkor a belső objektumok referenciái közösek maradnak.

Példa:

```javascript
const eredeti = [{ nev: 'Anna' }, { nev: 'Péter' }];

const masolat = [...eredeti];

masolat[0].nev = 'János';

console.log(eredeti[0].nev); // János
```

A külső tömb új, de a benne található objektumok nem másolódtak le külön.

### 2.4. Legnagyobb és legkisebb érték meghatározása

A spread operátort a `Math.max()` és a `Math.min()` függvényekkel is használhatjuk.

Ezek a függvények különálló számokat várnak paraméterként, a spread operátor pedig kibontja a tömb elemeit.

```javascript
const szamok = [15, 8, 42, 23, 11];

const legnagyobb = Math.max(...szamok);
const legkisebb = Math.min(...szamok);

console.log(legnagyobb);
console.log(legkisebb);
```

Kimenet:

```
42
8
```

A `Math.max(...szamok)` működése olyan, mintha ezt írnánk:

```javascript
Math.max(15, 8, 42, 23, 11);
```

### 2.5. Objektumok másolása és összefűzése

A spread operátor objektumok esetében is használható.

Segítségével egy objektum tulajdonságait átmásolhatjuk egy új objektumba.

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    eletkor: 25,
};

const masolat = { ...felhasznalo };

console.log(masolat);
```

Kimenet:

```
{
    nev: "Kovács Anna",
    eletkor: 25
}
```

Új tulajdonságokat is hozzáadhatunk:

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    eletkor: 25,
};

const ujFelhasznalo = {
    ...felhasznalo,
    varos: 'Szeged',
    aktiv: true,
};

console.log(ujFelhasznalo);
```

Kimenet:

```
{
    nev: "Kovács Anna",
    eletkor: 25,
    varos: "Szeged",
    aktiv: true
}
```

Két objektumot is összefűzhetünk:

```javascript
const alapadatok = {
    nev: 'Anna',
    eletkor: 25,
};

const egyebAdatok = {
    varos: 'Szeged',
    aktiv: true,
};

const felhasznalo = {
    ...alapadatok,
    ...egyebAdatok,
};

console.log(felhasznalo);
```

Kimenet:

```
{
    nev: "Anna",
    eletkor: 25,
    varos: "Szeged",
    aktiv: true
}
```

Fontos: ha két objektumban azonos nevű tulajdonság szerepel, akkor a később kibontott objektum értéke felülírja a korábbit.

```javascript
const alapadatok = {
    nev: 'Anna',
    eletkor: 25,
};

const modositas = {
    eletkor: 30,
};

const felhasznalo = {
    ...alapadatok,
    ...modositas,
};

console.log(felhasznalo.eletkor); // 30
```

## 3. Rest operátor (`...`)

A rest operátor jelentése: a fennmaradó elemek összegyűjtése.

Segítségével több különálló értéket egyetlen tömbbe vagy objektumba gyűjthetünk össze.

A rest operátort leggyakrabban függvényparamétereknél és objektumok, illetve tömbök szétbontásánál használjuk.

### 3.1. Rest operátor függvényparamétereknél

Egy függvénynek általában meghatározott számú paramétert adunk át.

A rest operátor segítségével azonban tetszőleges számú argumentumot fogadhatunk.

```javascript
function osszead(...szamok) {
    let osszeg = 0;

    for (let szam of szamok) {
        osszeg += szam;
    }

    return osszeg;
}

console.log(osszead(10, 20));
console.log(osszead(10, 20, 30));
console.log(osszead(5, 10, 15, 20, 25));
```

Kimenet:

```
30
60
75
```

A `...szamok` összegyűjti a függvénynek átadott összes argumentumot egy tömbbe.

A függvényen belül a `szamok` egy hagyományos tömbként használható.

### 3.2. Rest operátor hagyományos paraméterekkel

A rest operátort más paraméterekkel együtt is alkalmazhatjuk.

```javascript
function felhasznaloAdatok(nev, eletkor, ...egyebAdatok) {
    console.log('Név:', nev);
    console.log('Életkor:', eletkor);
    console.log('Egyéb adatok:', egyebAdatok);
}

felhasznaloAdatok('Anna', 25, 'Szeged', 'anna@example.com', true);
```

Kimenet:

```
Név: Anna
Életkor: 25
Egyéb adatok: ["Szeged", "anna@example.com", true]
```

A működés:

1. Az első argumentum a `nev` paraméterbe kerül.
2. A második argumentum az `eletkor` paraméterbe kerül.
3. Az összes további argumentum az `egyebAdatok` tömbbe kerül.

Fontos: a rest paraméternek mindig az utolsó paraméternek kell lennie a függvény paraméterlistájában.

Hibás példa:

```javascript
function pelda(...adatok, nev) {
    // Hibás paraméterlista
}
```

Helyes példa:

```javascript
function pelda(nev, ...adatok) {
    console.log(nev);
    console.log(adatok);
}
```

### 3.3. Rest operátor tömbök szétbontásakor

A rest operátort tömbök destrukturálásakor is használhatjuk.

A destrukturálás lehetővé teszi, hogy egy tömb elemeit külön változókba helyezzük.

```javascript
const szamok = [10, 20, 30, 40, 50];

const [elso, masodik, ...tobbi] = szamok;

console.log(elso);
console.log(masodik);
console.log(tobbi);
```

Kimenet:

```
10
20
[30, 40, 50]
```

A működés:

- Az `elso` változó megkapja az első elemet.
- A `masodik` változó megkapja a második elemet.
- A `tobbi` változó egy tömbbe gyűjti az összes fennmaradó elemet.

Másik példa:

```javascript
const gyumolcsok = ['alma', 'körte', 'barack', 'szilva'];

const [elso, ...maradek] = gyumolcsok;

console.log(elso);
console.log(maradek);
```

Kimenet:

```
alma
["körte", "barack", "szilva"]
```

### 3.4. Rest operátor objektumok destrukturálásakor

Objektumok esetében is használhatjuk a rest operátort.

Segítségével néhány tulajdonságot külön változóba helyezhetünk, a többit pedig egy új objektumba gyűjthetjük.

```javascript
const felhasznalo = {
    nev: 'Kovács Anna',
    eletkor: 25,
    varos: 'Szeged',
    email: 'anna@example.com',
};

const { nev, ...egyebAdatok } = felhasznalo;

console.log(nev);
console.log(egyebAdatok);
```

Kimenet:

```
Kovács Anna

{
    eletkor: 25,
    varos: "Szeged",
    email: "anna@example.com"
}
```

A működés:

- A `nev` tulajdonság értéke a `nev` változóba kerül.
- Az összes többi tulajdonság az `egyebAdatok` objektumba kerül.

## 4. A spread és a rest operátor összehasonlítása

Bár mindkét esetben a `...` jelölést használjuk, a két operátor ellentétes irányú műveletet végez.

| Szempont            | Spread operátor                            | Rest operátor                                 |
| ------------------- | ------------------------------------------ | --------------------------------------------- |
| Jelölése            | `...`                                      | `...`                                         |
| Jelentése           | Kibontás                                   | Összegyűjtés                                  |
| Működése            | Egy tömb vagy objektum elemeit szétteríti  | Több értéket egy tömbbe vagy objektumba gyűjt |
| Jellemző használata | Tömbök és objektumok másolása, összefűzése | Függvényparaméterek, destrukturálás           |
| Eredménye           | Különálló elemek vagy tulajdonságok        | Tömb vagy objektum                            |

### Egyszerű összehasonlító példa

Spread:

```javascript
const szamok = [10, 20, 30];

const masolat = [...szamok];
```

A tömb elemei kibontásra kerülnek egy új tömb létrehozásakor.

Rest:

```javascript
function osszead(...szamok) {
    console.log(szamok);
}

osszead(10, 20, 30);
```

A különálló argumentumok egyetlen tömbbe kerülnek.

## 5. Gyakori hibák és fontos tudnivalók

### 5.1. Spread és rest összekeverése

A három pont jelentése a használati helyétől függ.

```javascript
const szamok = [10, 20, 30];

const masolat = [...szamok];
```

Itt spread operátorról beszélünk, mert kibontjuk a tömb elemeit.

```javascript
function pelda(...adatok) {
    console.log(adatok);
}
```

Itt rest operátorról beszélünk, mert összegyűjtjük az argumentumokat.

### 5.2. A rest paraméter nem lehet az utolsó előtti helyen

Hibás:

```javascript
function osszead(...szamok, utolso) {
    // Hibás
}
```

Helyes:

```javascript
function osszead(kezdoErtek, ...szamok) {
    console.log(kezdoErtek);
    console.log(szamok);
}
```

### 5.3. A spread operátor nem minden értéknél használható ugyanúgy

A tömbök elemeinek kibontása természetes művelet, de a spread operátor csak megfelelő, iterálható értékeknél használható függvényargumentumok és tömbök esetében.

Például szöveg esetén:

```javascript
const nev = 'Anna';

console.log(...nev);
```

Kimenet:

```
A n n a
```

A szöveg karakterei különálló értékekként kerülnek kibontásra.

Egy egyszerű szám viszont nem iterálható:

```javascript
const szam = 10;

// Hibát eredményez:
console.log(...szam);
```

### 5.4. A spread operátor sekély másolatot készít

A tömbök és objektumok spread operátorral történő másolásakor csak a külső szerkezet jön létre újra. A belső objektumok referenciái közösek maradhatnak.

```javascript
const eredeti = {
    nev: 'Anna',
    cim: {
        varos: 'Szeged',
    },
};

const masolat = { ...eredeti };

masolat.cim.varos = 'Budapest';

console.log(eredeti.cim.varos); // Budapest
```

Ezért összetett adatszerkezetek másolásakor figyelni kell a sekély másolat tulajdonságaira.

### 5.5. Azonos objektumtulajdonságok felülírása

Ha több objektumot bontunk ki egy új objektumba, az azonos nevű tulajdonságoknál a később megadott érték lesz érvényes.

```javascript
const alap = {
    nev: 'Anna',
    kor: 25,
};

const modositas = {
    kor: 30,
};

const eredmeny = {
    ...alap,
    ...modositas,
};

console.log(eredmeny.kor); // 30
```

## 6. Összefoglalás

A spread és a rest operátor ugyanazt a `...` jelölést használja, de eltérő célra.

Spread operátor:

- Kibontja egy tömb vagy más iterálható érték elemeit.
- Tömbök összefűzésére és másolására használható.
- Objektumok másolására és összefűzésére is alkalmas.
- Függvényeknek különálló argumentumokat adhatunk át vele.

Rest operátor:

- Több értéket egyetlen tömbbe vagy objektumba gyűjt.
- Függvényeknél tetszőleges számú argumentum kezelésére alkalmas.
- Tömbök destrukturálásakor összegyűjti a fennmaradó elemeket.
- Objektumok destrukturálásakor összegyűjti a fennmaradó tulajdonságokat.

A legfontosabb különbség:

- Spread: kibontás.
- Rest: összegyűjtés.

# 7. Ellenőrző kérdések

1. Mit jelent a spread operátor, és milyen jelölést használunk hozzá?
2. Mit jelent a rest operátor, és mi a feladata?
3. Mi a legfontosabb különbség a spread és a rest operátor működése között?
4. Hogyan használhatjuk a spread operátort két tömb összefűzésére?
5. Hogyan készíthetünk egy tömbről másolatot a spread operátor segítségével?
6. Miért nevezzük a spread operátorral készített tömb- vagy objektummásolatot sekély másolatnak?
7. Hogyan használhatjuk a rest operátort függvényparamétereknél?
8. Miért kell a rest paraméternek az utolsó helyen szerepelnie a függvény paraméterlistájában?
9. Hogyan használhatjuk a rest operátort tömbök és objektumok destrukturálásakor?
10. Mi történik akkor, ha két objektum kibontásakor azonos nevű tulajdonságok szerepelnek bennük?

# 8. Gyakorlati feladatok

Az alábbi feladatokat JavaScriptben, megoldás nélkül készítsd el!

1. Tömb elemeinek kibontása: Hozz létre egy `szamok` nevű tömböt, amely tartalmazza az `10`, `20`, `30`, `40` és `50` értékeket. A spread operátor segítségével jelenítsd meg az elemeket különálló értékekként a konzolon!
2. Tömbök összefűzése: Hozz létre két tömböt. Az első tartalmazzon öt egész számot, a második további öt egész számot. A spread operátor segítségével készíts egy harmadik tömböt, amely mindkét tömb elemeit tartalmazza!
3. Tömb másolása: Hozz létre egy legalább öt elemből álló tömböt. A spread operátor segítségével készíts róla másolatot! Adj hozzá egy új elemet a másolathoz, majd jelenítsd meg mindkét tömböt!
4. Legnagyobb és legkisebb szám: Hozz létre egy legalább nyolc számot tartalmazó tömböt. A spread operátor és a `Math.max()`, illetve `Math.min()` függvények segítségével határozd meg a legnagyobb és a legkisebb értéket!
5. Objektumok összefűzése: Hozz létre két objektumot! Az első tartalmazza a felhasználó nevét és életkorát, a második a városát és e-mail-címét. A spread operátor segítségével egyesítsd a két objektumot egy új objektumba!
6. Tetszőleges számú argumentum: Készíts egy `osszead` nevű függvényt, amely a rest operátor segítségével tetszőleges számú számot képes fogadni! A függvény számolja ki és adja vissza az argumentumok összegét!
7. Rest operátor hagyományos paraméterekkel: Készíts egy `felhasznaloAdatok` nevű függvényt, amely első paraméterként egy nevet, második paraméterként egy életkort fogad. Az összes további argumentumot a rest operátor segítségével gyűjtse össze egy tömbbe! Jelenítsd meg az összes adatot!
8. Tömb destrukturálása: Hozz létre egy legalább hat elemből álló tömböt! Destrukturálás segítségével tárold el az első két elemet külön változókban, a többi elemet pedig a rest operátorral gyűjtsd össze egy új tömbbe!
9. Objektum destrukturálása: Hozz létre egy `felhasznalo` objektumot, amely tartalmazza a `nev`, `eletkor`, `varos`, `email` és `telefon` tulajdonságokat! Destrukturálással emeld ki a `nev` és `eletkor` értékét, a többi tulajdonságot pedig a rest operátor segítségével gyűjtsd össze egy új objektumba!
10. Spread és rest együttes használata: Készíts egy `feldolgoz` nevű függvényt, amely első paraméterként egy tömböt, további paraméterekként pedig tetszőleges számú értéket fogad! A függvény a spread operátor segítségével hozzon létre egy új tömböt, amely tartalmazza az eredeti tömb elemeit és az összes további argumentumot! A függvény jelenítse meg az új tömböt!
