# JavaScript változók elnevezési szabályai

## 1. Miért fontosak a változók elnevezési szabályai?

A változók a programozás alapvető elemei. Segítségükkel adatokat tárolhatunk, módosíthatunk és használhatunk fel a program végrehajtása során.

A változók elnevezése nemcsak technikai kérdés, hanem a program olvashatóságát és karbantarthatóságát is jelentősen befolyásolja.

Egy jól megválasztott változónév alapján a programozó könnyen megértheti, hogy az adott változó milyen adatot tárol, és milyen szerepet tölt be a programban.

Például:

```javascript
let x = 25;
let eletkor = 25;
```

Mindkét változó ugyanazt az értéket tárolja, de a második elnevezés sokkal beszédesebb.

A változók elnevezésénél két szempontot kell figyelembe venni:

- Technikai szabályok: meghatározzák, hogy milyen neveket fogad el a JavaScript.
- Elnevezési konvenciók: olyan ajánlások, amelyek segítik az egységes és jól olvasható kód írását.

## 2. A változónevek technikai szabályai

A JavaScript szigorú szabályokat határoz meg arra vonatkozóan, hogy milyen azonosítókat használhatunk változónévként.

Az azonosító (identifier) olyan név, amellyel a program különböző elemeire hivatkozhatunk.

Változók, függvények, osztályok és más programozási elemek elnevezésére is használhatunk azonosítókat.

### 2.1. A változónév betűvel kezdődjön

A változónév kezdődhet:

- Angol kisbetűvel (`a-z`).
- Angol nagybetűvel (`A-Z`).
- Aláhúzásjellel (`_`).
- Dollárjellel (`$`).

Példák:

```javascript
let nev = 'Anna';
let eletkor = 25;
let _eredmeny = 100;
let $ar = 2500;
let Felhasznalo = 'Péter';
```

A fenti változónevek technikailag érvényesek.

### 2.2. A változónév nem kezdődhet számmal

A változónév első karaktere nem lehet számjegy.

Hibás példák:

```javascript
let 1nev = "Anna";
let 2026ev = 2026;
let 5darab = 5;
```

Helyes megoldások:

```javascript
let nev1 = 'Anna';
let ev2026 = 2026;
let darab5 = 5;
```

A számjegyek tehát szerepelhetnek a változónévben, de nem állhatnak az első helyen.

### 2.3. A változónév nem tartalmazhat szóközt

A változónevekben nem használhatunk szóközt.

Hibás:

```javascript
let felhasznalo neve = "Anna";
let termek ara = 5000;
```

Helyes:

```javascript
let felhasznaloNeve = 'Anna';
let termekAra = 5000;
```

Több szóból álló változóneveknél különböző elnevezési konvenciókat alkalmazhatunk. Ezek közül a JavaScriptben a camelCase a legelterjedtebb.

### 2.4. Speciális karakterek használata

A változónevekben általában nem használhatunk tetszőleges speciális karaktereket.

Például a következők hibásak:

```javascript
let felhasznalo-neve = "Anna";
let termek.ara = 5000;
let osszeg% = 100;
```

Az aláhúzásjel (`_`) és a dollárjel (`$`) viszont megengedett.

Helyes példák:

```javascript
let felhasznalo_neve = 'Anna';
let termek_ara = 5000;
let $osszeg = 100;
```

### 2.5. A változónevek kis- és nagybetűérzékenyek

A JavaScript megkülönbözteti a kis- és nagybetűket. Ezt case sensitivity fogalommal jelöljük.

Ez azt jelenti, hogy a következő változónevek különböző azonosítóknak számítanak:

```javascript
let nev = 'Anna';
let Nev = 'Péter';
let NEV = 'Katalin';
```

A három változó egymástól függetlenül létezik.

Ezért fontos, hogy egy programon belül következetesen használjuk a változóneveket.

Például:

```javascript
let felhasznaloNev = 'Anna';

console.log(felhasznaloNev);
console.log(FelhasznaloNev);
```

A második `console.log()` hivatkozása hibát eredményez, mert a `FelhasznaloNev` nevű változó nincs deklarálva.

## 3. Fenntartott kulcsszavak és változónevek

A JavaScript számos olyan kulcsszót tartalmaz, amelyek a nyelv működéséhez szükségesek.

Ezeket fenntartott szavaknak (reserved words) nevezzük.

Ilyenek például:

- `let`
- `const`
- `var`
- `function`
- `return`
- `if`
- `else`
- `for`
- `while`
- `class`
- `new`
- `this`
- `switch`
- `try`
- `catch`

Ezeket nem használhatjuk közvetlenül változónévként.

Hibás példák:

```javascript
let let = 10;
let class = "JavaScript";
let return = 100;
```

Helyes megoldások:

```javascript
let letErtek = 10;
let osztalyNeve = 'JavaScript';
let visszateresiErtek = 100;
```

A fenntartott kulcsszavak használata azért tiltott, mert ezeknek már meghatározott jelentésük van a JavaScript nyelvben.

## 4. CamelCase elnevezési konvenció

A JavaScriptben a leggyakrabban alkalmazott változóelnevezési forma a camelCase.

A camelCase esetében:

- Az első szó kisbetűvel kezdődik.
- A további szavak első betűje nagybetű.
- A szavakat nem választjuk el szóközzel vagy aláhúzásjellel.

Példák:

```javascript
let felhasznaloNeve = 'Anna';
let termekAra = 5000;
let rendelesDatuma = '2026-10-31';
let osszesTermekDarab = 25;
let aktivFelhasznalo = true;
```

A camelCase előnye, hogy a változónevek könnyen olvashatók, miközben nem tartalmaznak tiltott szóközöket.

További példák:

| Változónév          | Jelentés                        |
| ------------------- | ------------------------------- |
| `nev`               | Egy személy neve                |
| `felhasznaloNev`    | Felhasználónév                  |
| `termekAra`         | Termék ára                      |
| `rendelesAzonosito` | Rendelés azonosítója            |
| `osszesitettAr`     | Összesített ár                  |
| `adatokBetoltve`    | Az adatok betöltésének állapota |

## 5. Snake_case elnevezési forma

A snake_case elnevezés esetében a szavakat aláhúzásjel választja el egymástól.

Például:

```javascript
let felhasznalo_neve = 'Anna';
let termek_ara = 5000;
let rendeles_datuma = '2026-10-31';
let osszes_termek_darab = 25;
```

A snake_case technikailag érvényes JavaScript-elnevezési forma.

Ugyanakkor a JavaScriptben a változók elnevezésére általában a camelCase használata ajánlott.

A snake_case gyakrabban fordul elő például Python-programokban vagy adatbázisok mezőneveiben.

Fontos, hogy egy projekten belül lehetőleg egységes elnevezési formát alkalmazzunk.

## 6. PascalCase elnevezési forma

A PascalCase esetében minden szó nagybetűvel kezdődik, beleértve az első szót is.

Például:

```javascript
let FelhasznaloNeve = 'Anna';
let TermekAra = 5000;
let RendelesDatuma = '2026-10-31';
```

A PascalCase technikailag érvényes változónév, de JavaScriptben elsősorban osztályok és konstruktorfüggvények elnevezésére használjuk.

Például:

```javascript
class Felhasznalo {
    constructor(nev, eletkor) {
        this.nev = nev;
        this.eletkor = eletkor;
    }
}

const felhasznalo = new Felhasznalo('Anna', 25);
```

Ebben a példában:

- `Felhasznalo` – osztálynév, PascalCase formában.
- `felhasznalo` – változónév, camelCase formában.
- `nev` és `eletkor` – tulajdonságnevek, camelCase formában.

## 7. Beszédes és egyértelmű változónevek

A változónévnek lehetőség szerint utalnia kell arra, hogy milyen adatot tárol.

Kerüljük az olyan általános elnevezéseket, amelyekből nem derül ki a változó szerepe.

Kevésbé megfelelő:

```javascript
let a = 2500;
let b = 3;
let c = a * b;
```

Jobb megoldás:

```javascript
let termekAra = 2500;
let darabszam = 3;
let teljesAr = termekAra * darabszam;
```

A második változatból könnyebben megérthető, hogy mit számol a program.

### 7.1. Kerüljük a túl rövid neveket

Az egybetűs változónevek bizonyos helyzetekben elfogadhatók, de általános esetben érdemes beszédesebb neveket választani.

Kevésbé megfelelő:

```javascript
let u = 'Anna';
let e = 25;
let v = true;
```

Jobb megoldás:

```javascript
let felhasznaloNev = 'Anna';
let eletkor = 25;
let aktiv = true;
```

Kivételt jelenthetnek például a rövid életű ciklusváltozók:

```javascript
for (let i = 0; i < 10; i++) {
    console.log(i);
}
```

A ciklusokban az `i` változó széles körben elfogadott konvenció.

### 7.2. Kerüljük a túl hosszú neveket

A beszédes változónevek hasznosak, de nem szükséges minden információt a változó nevébe sűríteni.

Kevésbé megfelelő:

```javascript
let felhasznaloTeljesNeveAkiJelenlegBeVanJelentkezve = 'Anna';
```

Egyszerűbb megoldás:

```javascript
let bejelentkezettFelhasznaloNeve = 'Anna';
```

A cél az, hogy a változónév rövid, egyértelmű és informatív legyen.

## 8. Változónevek az adattípus és a tartalom alapján

A változó elnevezése utalhat az általa tárolt adat jellegére is.

### 8.1. Szöveges adatok

Szöveges adatok tárolására használhatunk például:

```javascript
let vezetekNev = 'Kovács';
let keresztNev = 'Anna';
let emailCim = 'anna@example.com';
```

### 8.2. Számadatok

Számok esetében érdemes a mennyiségre vagy a jelentésre utaló neveket választani:

```javascript
let eletkor = 25;
let termekAra = 5000;
let darabszam = 10;
let pontszam = 95;
```

### 8.3. Logikai értékek

A logikai (`boolean`) változók `true` vagy `false` értéket tárolnak.

Ezeknél gyakran használunk olyan előtagokat, amelyek kérdésként vagy állapotként értelmezhetők.

Például:

```javascript
let aktiv = true;
let beVanJelentkezve = false;
let ervenyes = true;
let engedelyezve = false;
```

Gyakori angol elnevezések:

```javascript
let isActive = true;
let isLoggedIn = false;
let hasPermission = true;
let canEdit = false;
```

Az `is`, `has` és `can` előtagok segítenek felismerni, hogy a változó logikai értéket tárol.

### 8.4. Tömbök

Tömbök elnevezésénél célszerű többes számot vagy az adatok csoportjára utaló nevet használni.

Például:

```javascript
const felhasznalok = ['Anna', 'Péter', 'Katalin'];
const termekek = ['Laptop', 'Telefon', 'Monitor'];
const pontszamok = [80, 95, 70];
```

A névből így egyértelmű, hogy több adatot tartalmazó gyűjteményről van szó.

### 8.5. Függvények és változók elnevezése

A függvénynevek általában valamilyen műveletet vagy tevékenységet fejeznek ki.

A változónevek ezzel szemben inkább adatokat vagy állapotokat jelölnek.

Példa:

```javascript
const felhasznaloNev = 'Anna';

function felhasznaloBetoltese() {
    console.log('Felhasználó betöltése...');
}

function arKiszamitasa() {
    return 5000;
}
```

A függvénynevek gyakran igével kezdődnek, mert valamilyen műveletet írnak le.

## 9. Konstansok elnevezése

A `const` segítségével deklarált változók neveire is ugyanazok a technikai szabályok vonatkoznak.

A legtöbb esetben a `const` változókat is camelCase formában nevezzük el.

Példa:

```javascript
const felhasznaloNev = 'Anna';
const termekAra = 5000;
const maximalisDarabszam = 100;
```

Bizonyos programozási konvenciók szerint a valódi, állandó konfigurációs értékeket nagybetűs, aláhúzásjeles formában is elnevezhetjük.

Például:

```javascript
const MAXIMALIS_DARABSZAM = 100;
const API_URL = 'https://example.com/api';
const ALAPERTELMEZETT_NYELV = 'hu';
```

Ezt a formát általában olyan értékeknél használjuk, amelyek a program működése során nem változnak.

Fontos: a `const` önmagában nem jelenti azt, hogy az objektum vagy tömb tartalma sem módosítható.

Például:

```javascript
const felhasznalo = {
    nev: 'Anna',
};

felhasznalo.nev = 'Péter';

console.log(felhasznalo.nev);
```

A kód helyesen működik, mert a `const` az objektumra mutató hivatkozás újbóli értékadását tiltja, nem az objektum tulajdonságainak módosítását.

## 10. Magyar vagy angol változónevek?

A JavaScript lehetővé teszi, hogy magyar vagy angol változóneveket használjunk.

Magyar változónevek:

```javascript
let felhasznaloNev = 'Anna';
let eletkor = 25;
let rendelesOsszege = 15000;
```

Angol változónevek:

```javascript
let userName = 'Anna';
let age = 25;
let orderTotal = 15000;
```

Mindkét megoldás helyes.

A választásnál a legfontosabb szempont az egységesség.

Általános fejlesztési ajánlás:

- Nemzetközi projektekben általában angol változóneveket használjunk.
- Oktatási vagy helyi célú projektekben magyar elnevezések is alkalmazhatók.
- Egy projekten belül ne keverjük indokolatlanul a két nyelvet.
- A változónevek legyenek könnyen értelmezhetők.

A magyar ékezetes karakterek bizonyos esetekben használhatók JavaScript-azonosítókban, de a széles körű kompatibilitás és az egységes kódolási szokások miatt általában ékezet nélküli neveket célszerű választani.

Például:

```javascript
let felhasznaloNeve = 'Anna';
let osszesitettAr = 15000;
```

## 11. Gyakori elnevezési hibák

Az alábbi táblázat összefoglal néhány gyakori hibát és azok helyes megoldását.

| Hibás vagy kevésbé megfelelő név | Javasolt név              | Magyarázat                             |
| -------------------------------- | ------------------------- | -------------------------------------- |
| `1nev`                           | `nev1`                    | Nem kezdődhet számmal                  |
| `felhasznalo neve`               | `felhasznaloNeve`         | Nem tartalmazhat szóközt               |
| `termek-ara`                     | `termekAra`               | A kötőjel nem használható azonosítóban |
| `class`                          | `osztalyNeve`             | Fenntartott kulcsszó                   |
| `x`                              | `termekAra`               | Beszédesebb elnevezés                  |
| `Felhasznalo_neve`               | `felhasznaloNeve`         | Egységes camelCase forma               |
| `nev`, `Nev`                     | Egy következetes névforma | A kis- és nagybetű különbséget jelent  |

## 12. Összefoglalás

A JavaScript változónevek megadásakor egyszerre kell figyelembe venni a nyelv technikai szabályait és az olvasható kód kialakításának szempontjait.

A legfontosabb szabályok:

- A változónév betűvel, aláhúzásjellel vagy dollárjellel kezdődhet.
- Nem kezdődhet számmal.
- Nem tartalmazhat szóközt.
- Nem használhatunk benne tetszőleges speciális karaktereket.
- A fenntartott kulcsszavak nem használhatók változónévként.
- A JavaScript megkülönbözteti a kis- és nagybetűket.
- A változók elnevezésére általában a camelCase forma ajánlott.
- A változónevek legyenek beszédesek és egyértelműek.
- Egy projekten belül törekedjünk az egységes elnevezési konvenciókra.

# Ellenőrző kérdések

1. Miért fontos, hogy a JavaScript-változók beszédes és egyértelmű neveket kapjanak?
2. Milyen karakterekkel kezdődhet egy érvényes JavaScript-változónév?
3. Miért hibás a `let 2026ev = 2026;` változódeklaráció?
4. Miért nem használhatunk szóközt egy változónévben?
5. Mit jelent az, hogy a JavaScript kis- és nagybetűérzékeny?
6. Mit nevezünk fenntartott kulcsszónak? Mondj három példát!
7. Mi a különbség a camelCase, a snake_case és a PascalCase elnevezési formák között?
8. Miért előnyösebb a `termekAra` változónév az `x` változónévhez képest?
9. Milyen elnevezési konvenciót alkalmazhatunk logikai értéket tároló változóknál?
10. Mikor lehet indokolt a konstansok nagybetűs, aláhúzásjeles elnevezése?

# Gyakorlati feladatok

A következő feladatok célja, hogy gyakorold a JavaScript-változók helyes elnevezését. A feladatokat JavaScript-kódban oldd meg!

## 1. feladat – Hibás változónevek javítása

Az alábbi változódeklarációk hibásak. Javítsd ki őket úgy, hogy érvényes JavaScript-változóneveket kapjunk!

```javascript
let 1nev = "Anna";
let felhasznalo neve = "Péter";
let termek-ara = 5000;
let class = "JavaScript";
let 2026ev = 2026;
let osszeg% = 1000;
```

## 2. feladat – CamelCase átalakítás

Alakítsd át az alábbi neveket camelCase formára!

1. `felhasznalo_neve`
2. `termek_ara`
3. `rendeles_azonosito`
4. `osszes_termek_darab`
5. `bejelentkezett_felhasznalo`
6. `vasarlo_teljes_neve`
7. `adatbazis_kapcsolat`
8. `maximalis_pontszam`

## 3. feladat – Beszédes változónevek

Az alábbi kódban a változónevek nem megfelelőek.

Nevezd át őket úgy, hogy a program könnyebben olvasható legyen!

```javascript
let a = 'Laptop';
let b = 250000;
let c = 2;
let d = b * c;

console.log(a);
console.log(d);
```

A program működését ne változtasd meg, csak a változóneveket módosítsd!

## 4. feladat – Adatok tárolása

Hozz létre változókat egy felhasználó adatainak tárolására!

A következő adatokat tárold:

- Vezetéknév.
- Keresztnév.
- Életkor.
- E-mail-cím.
- Telefonszám.
- Aktív felhasználó állapota.

A változónevek legyenek camelCase formátumúak, és utaljanak a tárolt adatok jelentésére!

## 5. feladat – Változónevek kiválasztása

Az alábbi adatokhoz válassz megfelelő JavaScript-változóneveket!

1. Egy termék neve.
2. Egy termék ára.
3. A vásárolt termékek darabszáma.
4. A rendelés végösszege.
5. A felhasználó be van-e jelentkezve.
6. A rendelés teljesült-e.
7. A termékek listája.
8. A felhasználók listája.
9. Az adatbázis-kapcsolat állapota.
10. A maximálisan engedélyezett próbálkozások száma.

## 6. feladat – Logikai változók elnevezése

Hozz létre öt logikai változót (`boolean`) az alábbi állapotok tárolására!

- A felhasználó aktív.
- A felhasználó be van jelentkezve.
- A termék elérhető.
- A rendelés teljesült.
- A módosítás engedélyezett.

Használj beszédes változóneveket, és mindegyikhez rendelj `true` vagy `false` értéket!

## 7. feladat – Tömbök elnevezése

Hozz létre három tömböt az alábbi adatok tárolására!

- Öt felhasználó neve.
- Hat termék neve.
- Nyolc dolgozó életkora.

A tömbök neve legyen egyértelmű, és utaljon arra, hogy több adatot tartalmaznak!

## 8. feladat – Konstansok elnevezése

Hozz létre öt konstans változót az alábbi értékek tárolására!

- Maximális felhasználószám: 100.
- Alapértelmezett nyelv: `hu`.
- Alapértelmezett pénznem: `HUF`.
- Maximális próbálkozások száma: 5.
- Alkalmazás neve: `WebApp`.

Használj következetes, nagybetűs és aláhúzásjeles elnevezést!

## 9. feladat – Változónevek ellenőrzése

Vizsgáld meg az alábbi változóneveket!

Döntsd el mindegyikről, hogy technikailag érvényes vagy érvénytelen JavaScript-azonosító!

| Változónév         | Érvényes vagy érvénytelen? |
| ------------------ | -------------------------- |
| `nev`              | ?                          |
| `felhasznaloNev`   | ?                          |
| `1adat`            | ?                          |
| `_eredmeny`        | ?                          |
| `$ar`              | ?                          |
| `termek ara`       | ?                          |
| `class`            | ?                          |
| `osszeg2`          | ?                          |
| `felhasznalo-neve` | ?                          |
| `NEV`              | ?                          |
| `adat_2026`        | ?                          |
| `return`           | ?                          |

A döntésedet minden esetben indokold meg!

## 10. feladat – Egy egyszerű terméknyilvántartás változóinak elnevezése

Készíts egy egyszerű JavaScript-programot, amely egy termék adatait tárolja!

A programban szerepeljen:

- A termék neve.
- A termék azonosítója.
- A termék ára.
- A raktáron lévő darabszám.
- A termék elérhetősége.
- A termék kategóriája.
- A termékek listája.

A változóneveket következetesen camelCase formában add meg!

A program végén jelenítsd meg az összes adatot a `console.log()` segítségével!
