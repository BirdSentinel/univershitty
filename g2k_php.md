# PHP

Na ha túlszenvedted magad a JavaScript doksin, igazából itt már nem fogsz megszakadni, mert ennek a doksinak egy része elég repetitív lesz. Konkrétan amit átvettünk az előző doksiba átemeljük php-ba, kezdjük is:

## Mi az a PHP?

A PHP egy internet által nagyrészt használt programozási nyelv, mely backend-en fut, és van annyira erős hogy komplex projektekre is alkalmas legyen. Például tudtad hogy a Facebook is PHP-val készült?! Oké a Facebook egy rák, de na, azért mégis csak nagy cucc és ezzel megy, szóval itt a lehetőséged hogy alkoss valamit jobbat! De hogyan is nézki egy PHP fájl? Először is, fusson a gépeden a XAMPP az Apache-al elindítja, és legyen egy `index.php` fájlod amibe most írd bele ezt:

```
<!DOCTYPE html>
<html>
    <head>
        <title>PHP gyakorló oldalam</title>
    </head>
    <body>

        <?php
            echo "Sup bro, PHP-ból lettem kiírva!";
        ?>

    </body>
</html>
```

Most azt fogod látni hogy PHP-ból sikeresen kiírtál egy szöveget HTML-be! Ezzel az alapkóddal igazából mehetsz is tovább a doksi további részében gyakorolni.

# Az alapok

## Változók

Ahogy azt már a JS doksiban is olvashattad, minden programozási nyelvben vannak változók. Változóknak nevezzük azt, amiben valamilyen értéket vagy adatok tárolunk, legyen az szöveg, vagy szám stb. Nézzünk példát:

```
<?php
$txt = "univershitty.hu";
echo "Legjobb egyetem a " . $txt . "!";
//Legjobb egyetem a univershitty.hu!
?>
```

Itt azt láthatjuk hogy létrehoztunk egy változót majd ki is irattuk az értékét echo-val! Nézzük még pár példát változókra:
```
<?php
$text = "Ez a sima string szöveg";
$number = 69; //nice
$array = ["Ez", "egy", "tömb!"];
$boolval = true;

$person = ["Name"=>"Jani", "Age"=>41, "Place"=>"Budapest"];
//Ez pedig egy asszociatív tömb
?>
```

Ezeket fogjuk használni majd, jó ha ezeket tudod. PHP változó-t mint láthatod $ jellel kezded, beírod a nevét, és utána az értéket amit meg akarsz adni neki.

**PHP változó nevek létrehozásának a szabályai:**

- A változó mindig $ jellel kezdődik, közvetlen utána a nevével
- A változó neve betűvel vagy _ -al kell kezdődjön
- A változó neve nem kezdődhet számmal
- A változó betűket, számokat és _ -t tartalmazhat (A-z, 0-9 és _)
- A változó nevek case-sensitive-ek, szóval a `$age` és `$AGE` két külön változónak számít!

## Hogyan iratjuk ki a változókat?

Vegyük példának az előző kódunk:

```
<?php
$text = "Ez a sima string szöveg";
$number = 69; //nice
echo $text;
echo $number;

$array = ["Ez", "egy", "tömb!"];
print_r($array);
//a print_r-el az egész tömböt kiiratjuk
echo $array[1];
//itt pedig kiirattuk a második elemét a tömbnek

$boolval = true;
echo $boolval;

$person = ["Name"=>"Jani", "Age"=>41, "Place"=>"Budapest"];
//Ez pedig egy asszociatív tömb
print_r($person);
//Ezzel kiirattuk az egész tömböt
echo $person["name"];
//Ezzel pedig kiiratuk a tömb "name" értékét
?>
```

## Asszociatív tömbök

JS-ben már megismerkedhettünk az alap változókkal, amik ugyan azok mint itt is, példát adtam rá, ugyan azt a megfogalmazást mégegyszer nem írom le. Viszont az asszociatív tömböket itt kiemelném, még pedig azért is mert jó ha ezt tudjuk hogy működik, mivel majd később amikor adatbázisból olvasunk ki adatot, azt is ugyan így fogjuk vissza kapni!

```
<?php
$person = ["Name"=>"Jani", "Age"=>41, "Place"=>"Budapest"];
?>
```

A fenti példában egy asszociatív tömböt láthatunk, ez annyiban különbözik a sima tömbtől, hogy még a sima tömbben számokkal azonosítjuk melyik tömb elemre vagyunk kíváni, itt minden tömb elemnek van egy neve, és később azokkal azonosítjuk/hívjuk meg őket, például itt most kiiratom a nevet és az életkort:

```
<?php
$person = ["Name"=>"Jani", "Age"=>41, "Place"=>"Budapest"];
echo $person["Name"];
echo $person["Age"];
?>
```

# Operátorok és változók kezelése

Az operátorok és a változók kezelése szintén hót ugyan az mint JavaScript-ben, csak ugye még ott a változók `var valami`-k voltak, itt `$valami` lesz. De azért nézzünk rá példát.

## Érték változtató operátorok

**= jel operátor**

Ezzel adunk meg értéket egy változónak.

```
$valami = "csirip";
```

**+ és . operátor**

Na itt már jön egy fricska, még JS-ben csak + jellel adtunk össze dolgokat, itt már a . (pont) is jön. De miben különböznek?

```
<?php
$text1 = "Kiscica";
$text2 = "Kiskutya";
$texts = $text1.$text2; //KiscicaKiskutya

$number1 = 5;
$number2 = 2;
$sum = $number1+$number2; //7
$sum2 = $number1.$number2; //52
?>
```

A fenti példában is látható, hogy még . -al egymás mellé raktam a változókat, a +-al szám változókat adtam össze. Erre láthatod a példában hogy mi történt amikor a két számot +-al és .-al adtam össze. Így tudsz változókat összerakni PHP-ban, de nézzünk még erre példát:

```
<?php
$text1 = "Kiscica";
$text2 = "Kiskutya";
$texts = "A ".$text1." nem mindig ".$text2."!";
echo $texts; //A Kiscica nem mindig Kiskutya!
?>
```

Itt arra láthatunk példát hogy sima szöveget és változókat rendeltünk össze, majd 1 szövegként kezeltük őket és kiirattuk őket! Viszont felmerülhet benned, hogy jó jó szöveget iratok ki, de mivan ha én "-t azaz macskakörmöt is megakarok jeleníteni a szövegben? Mert mondjuk HTML-t akarok generálni és ugye abba lehetnek macskakörmök az attribútumok miatt? Semmi gond!

```
<?php
$text = "Kiscica";
$texts = "<a href=\"https://www.google.com/keressmagadnak\">".$text."</a>";
echo $texts;
?>
```

Ennek az eredménye lett az hogy: `<a href="https://www.google.com/keressmagadnak">Kiscica</a>` ami egy HTML kompatibilis "szöveg" amit kiirattunk. Mint látodhatod, a macskakörmöt a szövegen belül úgy belenítettük meg hogy eléraktunk egy \ jelet, majd pontokkal összeraktuk a szöveget még változóval kiegészítve.

**További operátorok**

Ahogy már azt fentebb is említettem, a JavaScript-ben használható operátorok 1:1 megegyeznek a PHP-sokkal. De, nézzünk azért 1-2 példát:

```
<?php
//ez ugye a += operátorunk
$number1 = 2;
$number2 = 5;
$number1 += 5;
echo $number1; //7

//Itt ugye az else ág fog lefutni mert nem igaz a feltétel...
if ($number1 == $number2) {
    echo "Egyenlő volt a két szám";
} else {
    echo "Nem volt egyenlő a két szám";
}

//Itt pedig igaz lesz a feltétel
if ($number1 < $number2) {
    echo "Az első szám kissebb mint a második";
}
?>
```

**+= és .= operátorok**

JavaScript-ben már megismerkedhettünk a **+=** operátorral, amivel a meglévő változó adatához újabb számot vagy szöveget tudtunk hozzáadni. Na ugye JS-ben a szövegre IS += operátort használtunk, PHP-ban viszont szöveg hozzáadáshoz már a **.=** operátort kell használni. Példa:

```
<?php
$text = "Kiscica";
$text .= " és Kiskutya";
echo $text; //Kiscica és Kiskutya

$number = 5;
$number += 3;
echo $number; //8
?>
```

# if, for, while

A címben említett funkciók is ugyan azzal működéssel bírnak mint javascriptben, írok rájuk azért 1-1 példát:

```
$number1 = 2;
$number2 = 5;

//Itt ugye az else ág fog lefutni mert nem igaz a feltétel...
if ($number1 == $number2) {
    echo "Egyenlő volt a két szám";
} else {
    echo "Nem volt egyenlő a két szám";
}

for ($i = 0; $i < 100; $i++) {
    echo $i.". For ciklus eheeh\n";
}

$name = "Jani";

switch ($name) {
    case "Béla":
        echo "Ő Béla";
        break;
    case "Jani":
        echo "Ő Jani";
        break;
    case "Zoli":
        echo "Ő Zoli";
        break;
    case "Árpád":
        echo "Ő Árpád";
        break;
    case "Pisti":
        echo "Ő Pisti";
        break;
    default:
        echo "Egyik sem!";
}
```

Látjátok? Ugyan az mint amit JS-ben tanultatok, csak ugye a PHP-s változókat írjuk bele, na meg ugye ott console.log-al irattam ki a példákat, itt echo-val.

# PHP related things

Na most hogy túlszenvedted magad a repetitív részen, nézzük milyen újdonságok vannak a PHP-ba.

## Tartalom megjelenítése PHP-ból HTML-be

Kezdjük valami nagyon egyszerűvel. Először is látnod kell egy szemléletet magad előtt: A böngésződ egy kész HTML kódot kap, azt jeleníti meg, a PHP-t nem a böngésződ futtatja le, hanem a háttérbe a szerver, az ad vissza neked HTML kódot amit tud értelmezni a böngésződ. Szóval amikor megjeleníteni kívánt tartalmat kívánsz csinálni és generálni PHP-val, úgy gondolkodj, hogy te HTML kódot generálsz ki ezzel. Nézzünk meg egy primitív példát:

Hozzunk létre egy index.php fájlt és legyen ez a tartalma:

```
<?php
$website_name = "Szikrázó Elefánt";
?>

<!DOCTYPE html>
<html>
    <head>
        <title><?php echo $website_name; ?></title>
        <meta charset="UTF-8">
    </head>
<body>

<h2>Üdv a <i><?php echo $website_name; ?></i> oldalon!</h2>

</body>
</html>
```

Na itt most ügyesen az oldal tetején létrehoztunk egy változót, benne az oldal nevével, és mi ügyes kis lusta programozók vagyunk, ugyan azt a szöveget nem fogjuk kézzel sok helyre kiírni sokszor, ezt egy változóval helyettesítettük a helyét. A HTML részében a kódnak láthatjuk, hogy ahova kiakartam iratni a változót, oda mindig nyitottam és csuktam és PHP kód részletet, így tudtam ki "echo"-zni a változónkat amit felül hoztam létre, biztonság kedvéért hogy jobban megértsd, a fenti php-s kódot így kapja meg a böngésző most:

```
<!DOCTYPE html>
<html>
    <head>
        <title>Szikrázó Elefánt</title>
        <meta charset="UTF-8">
    </head>
<body>

<h2>Üdv a <i>Szikrázó Elefánt</i> oldalon!</h2>

</body>
</html>
```

Mint láthatjuk ezt simán kézzel is létrehozhattuk volna, de mi ügyesek vagyunk, és PHP-ból alkottuk!

Nézzünk meg még egy olyan példát, hogy az oldalunk címét én 100-szor kívánom kiiratni az oldalra egymás alá:

```
<?php
$website_name = "Szikrázó Elefánt";
?>

<!DOCTYPE html>
<html>
    <head>
        <title><?php echo $website_name; ?></title>
        <meta charset="UTF-8">
    </head>
<body>

<h2>Üdv a <i><?php echo $website_name; ?></i> oldalon!</h2>

<?php
for ($i = 0; $i < 100; $i++) {
    echo "<p>".$i.". ".$website_name."</p>";
}
?>

</body>
</html>
```

Na ha ezt most lefuttatod látod hogy 100-szor kiírtuk az oldal címét egymás alá, és akkor ez most HTML-be úgy nézki hogy.... Hallod, nem, isten bizony nem írom le ezt a kódot, nézd meg a böngésződ inspectorjában és hidd el:D A koncepció ugye az volt most, hogy egy HTML tag-et generáltam ki 100-szor, benne azzal hogy hanyadik sornál járok meg a weboldal címe változónk ugyebár.

Na most hogy megvagyunk azzal a koncepcióval hogy kell PHP-ból HTML-be kiírni dolgokat, vágjunk bele egy kicsit extrémebb dologba: Csatlakozzunk SQL adatbázishoz és irassunk ki onnan tartalmat!

# Néhány hasznos cucc PHP-ban

Ezeket jó ha tudod, hasznos kis cuccok, sok jóság létrehozásában segítenek.

## intval()

Az `intval()` függvényt arra szoktam használni hogy leellenőrizzem hogy egy adott változó tuti szám-e. Na most ez úgy működik hogy egy változót kér be, aztán mindenféleképpen valami számot fog visszaadni. Példák:

```
<?php
echo intval(42);                      // 42
echo intval(4.2);                     // 4
echo intval('42');                    // 42
echo intval('+42');                   // 42
echo intval('-42');                   // -42
echo intval('asd');                   // 0
echo intval('asd123');                // 0
?>
```

Ha mondjuk szöveg kerül bele akkor 0-át fog visszaadni. Ez tökjó kiszűrni user inputokat, ahol mondjuk a HTML-ből csak számot kérnénk vissza, de mókás gyerek ismeri az inspectort és szöveget írna be, akkor ezzel letudod szűrni hogy te mondjuk az adatbázis fele mindenféleképpen számot küldj tovább, legrosszabb esetben egy 0-át.

## mb_strlen()

Az `mb_strlen()` függvényt stringek hosszúságának számolására használjuk. Azaz ha adunk neki egy szöveget, visszaadja számba hogy hány karakter hosszú. Példák:

```
<?php
$mystring = "kiskutya";
echo mb_strlen($mystring);            // 8
?>
```

Ezt én például arra szoktam használni, hogy amikor adatbázisból kiiratok valami adatot, megnézem ezzel milyen hosszú szöveget kaptam vissza. Mondjuk például várok valami youtube linket egy embedded videóhoz, és mondjuk csak akkor akarom kirenderelni ha 3-nál több karakter van abba a stringbe, ha mond 1 karakter pl csak béna volt és csak egy space-t írt bele, akkor ne jelenítsem meg.

## header()

Ezzel HTTP header-öket lehet küldeni. Én ezt arra szoktam használni hogy elnavigáljam a user-t valamely másik oldalra. Kicsit bővebben lehet még [olvasni itt](https://www.w3schools.com/php/func_network_header.asp) a funkcióiról. Példa amire én használom:
```
<?php
header("Location: /articles");
//Ez az articles oldalra átnavigál minket, szóval ha pl www.vulkancapa.hu domainen vagyunk, akkor www.vulkancapa.hu/articles linkre visz át.
header("Refresh:0");
//Ezzel pedig teljesen újra töltjük a jelenlegi oldalt
?>
```

## isset()

Ezzel lehet megnézni hogy egy változó-t létrehoztak-e vagy nem-e NULL az értéke. Ezt én speciel arra szoktam használni hogy megnézzem bevan-e jelentkezve a paraszt az oldalra, és annak függvényében jelenítem meg mondjuk a gombokat a status baron.

```
<?php
if(isset($_SESSION['login_user'])) {
    //Ha a session-be létezik a bejelentkezett user akkor csinálok vmit
}

$valami = "asd";
if (isset($valami)) {
    //Ez lefog futni mert létezik a $valami változó
}

if (isset($nemvalami)) {
    //Ez pedig nem fog lefutni mert nincs $nemvalami változónk
}
?>
```

Egyébként az `isset()` függvény mindig true-t vagy false-t return-öl, így if-ekbe teljesen alkalmas beépíteni ahogy a példában is volt.

## htmlspecialchars()

A `htmlspecialchars()` függvénybe kapott stringet... hogy is mondjam. Nyers html kompatibilissá teszi?... This makes no sense. Szóval konyhanyelven, ha adsz neki egy html stringet és te mondjuk ezt html-be kiakarod printelni, szal hogy a tag-eket is lásd, ezen keresztül nyomasd bele. Ez amúgy tökéletes sanitize-olni is a szöveget, mondjuk egy kis szöveg posztoló cuccot írsz html-be és nem akarod hogy html tageket irogáljanak bele a userek, ezzel nyomasd végig, de nézzük a példát úgy jobban megérted:

```
<?php
$test = "<a href='test'>Test</a>";
$new = htmlspecialchars($test);
echo $new; // &lt;a href=&#039;test&#039;&gt;Test&lt;/a&gt;
echo $test; //próbáld ki!
?>
```

Ha ezt lefuttatod, látod hogy amit a példafüggvényünkön keresztül irattunk ki, azt ténylegesen látjuk a böngészőbe, amit pedig csak simán ki echo-ztunk, rendes HTML kódnak érzékelte!

## Funkciók

Ez egy igencsak fontos része hogy fain PHP kódokat írjunk, meg hogy ne ismételjük önmagunkat. Ha már felfogtad agyilag a JavaScript doksit, ez már nem lesz újdonság, csak megmutatom PHP-ba hogy tudsz ilyet írni.

```
function myfunction() {
    echo "Na ezt egy funkcióból echoztunk ki!";
}

myfunction();
//És ha ezt meghívjuk, láthatjuk a szöveget... Azért ez ismerős a JS doksiból nem?!
```

Nézzünk most meg return funkciót is!

```
function myfunction() {
    $myvar = "Szövegünk";
    return $myvar;
}

$something = myfunction();
echo $something;
//Ez pedig a "Szövegünk" szöveget fogja vissza returnölni.

function myboolfunction() {
    return true;
}

if (myboolfunction()) {
    //Ez az if-ünk lefog futni mert a felső function true-t adott vissza.
}
```

Most pedig nézzük meg azt, hogy változókat adunk át a funkciónak.

```
function sum(int $number1, int $number2) {
    $summed = $number1 + $number2;
    return $summed;
}

echo sum(1,2); //3
```

Ez a funkciók vár 2 változót, amivel kezd valamit, és returnöli az eredményt. Annyit láthatunk itt a JS-es funkciókkal szembe hogy itt LEHET megadni neki tipust, hogy mit várunk el! Itt van még egy példa:

```
function myfunction(bool $istrue, string $text) {
    $mytextadd = "nem volt igaz az istrue.";
    if ($istrue) {
        $mytextadd = "igaz volt az istrue.";
    }

    return $text." és ".$mytextadd;
}

echo myfunction(true,"Heheheh"); //Heheheh és igaz volt az istrue.
```

És ugye adhatunk meg neki bool-t, string-et, int-et, array-t, object-et stbstb...

Még egy utolsó példa, hogy mivan akkor ha mondjuk egy olyan funkciót akarsz létrehozni ahova néha 1 néha 2 értéket kéne átadni?! Na tudsz olyat, hogy a funkció létrehozásánál egyből megadsz egy kezdőértéket a várni kívánt változónak, és ha meghívásnál nem kapja meg, azt fogja használni és nem fog sírni hogy kevesebb argumentet kapott.

```
function myfunction(string $text, string $text2 = "Nem adtál meg szöveget") {
    $mytext = $text.$text2;
    return $mytext;
}

echo myfunction("valami"); //valamiNem adtál meg szöveget
echo myfunction("valami","adtam meg szöveget"); //valamiadtam meg szöveget
```

## Funkciók és egyéb kódok kiszervezése külön fájlokba

Na most azt tudni illik hogy a jól átlátható kód részben azon is múlik, hogy nem egy darab fájlba van 4500 sornyi kód telefosva mert ember legyen a talpán aki ezt átlátja. Erről bővebben a másik doksiban olvashatsz ahogy kicsit részletesebben elmagyarázom hogy miért fontos hogy értelmes mappákba legyen szétszedve az oldalad, hogyan és miért darabold szét a css fájlaid stb. Na de nézzük meg most a PHP-s részt.

Tegyük fel neked van egy kód részleted amit sok helyen akarsz használni (vagy akár már 2 helyen is), könyörgöm, nehogy elkezd le ctrl+c és ctrl+v-zni minden egyes helyre... Mert majd jön a felismerés hogy egyszer változtatni kéne rajta.

mypage.php
```
<?php
function sum(int $number1, int $number2) {
    $summed = $number1 + $number2;
    return $summed;
}

echo sum(1,2); //3
echo sum(2,2); //4
?>
```

anotherpage.php
```
<?php
function sum(int $number1, int $number2) {
    $summed = $number1 + $number2;
    return $summed;
}

echo sum(5,7); //12
echo sum(1,8); //9
?>
```

Na most nem érzed kicsit furán hogy 2 külön oldalon is ledefiniáltad ugyan azt a kódot? Nem lenne egyszerűbb egy helyről használni őt? Há' dehogynem. Nézzünk meg egy példát ahol a `sum()` funkciónkat külön fájlba szedtem, majd a másik két oldalamba implementáltam:

component_sum.php
```
<?php
function sum(int $number1, int $number2) {
    $summed = $number1 + $number2;
    return $summed;
}
?>
```

mypage.php
```
<?php
include("component_sum.php");

echo sum(1,2); //3
echo sum(2,2); //4
?>
```

anotherpage.php
```
<?php
include("component_sum.php");

echo sum(5,7); //12
echo sum(1,8); //9
?>
```

Na itt most azt láthatjuk hogy a funkciónkat külön szedtem egy fájlba, majd azokat beincludeoltam azokba a fájlokba, ahol használni szeretném. Hogy kell ezt elképzelni, hogy működik? Amikor behúzod include-al a fájlt, olyan mintha oda annak a helyére kerülne a kód a másik fájlból, és akkor azt már tudja olvasni a php kódunk. Ugye sorrend itt is számít, szóval ne először hívd meg a funkciók és utána include-old meg nyilván nem fog működni.

Érdemes tudni, hogy nem csak ez az egy módja van hogy behúzz egy másik php file-t a kódodba, mutatok 4 lehetőséget és felhasználási módját:

```
<?php
include("component_sum.php");
//Az include-al simán behúzhatjuk a másik php fájlt, akár többször is egymás után, ez mondjuk arra jó ha mondjuk a HTML-ünkből valami HTML kódot többször akarunk berakni egymás után.

include_once("component_sum.php");
//Az include_once pedig ugyan azt csinálja mint a sima include, viszont csak EGYSZER töltődik be, többször még véletlenül se tudjuk.

require("component_sum.php");
//A require-el szintén ugyan úgy betudjuk tölteni a fájlt mint az include-al, viszont a kettő abban tér el egymással, hogy még ha include-al töltünk be valamit, és nem található a fájl, a kód tovább fut és csak egy hibát ír, viszont ha a require-nél nem találja a fájlt, a kód futása is leáll mivel kritikusan fontos fájlt akarunk betölteni amire mindenféleképpen szükségünk van az oldal működéséhez.

require_once("component_sum.php");
//Ugyan az mint az include_once, szintén csak egyszer töltődik be a fájl, viszont mint a sima require, mindenféleképpen bekell töltenie, anélkül nem fut tovább a kód. Ezt általában adatbázis csatlakozós file betöltéséhez szoktuk használni.
?>
```

# TODO: Csatlakozás adatbázishoz

Na ha még ezt is felfogod, ezzel a tudással már képes leszel egy olyan weboldalt létrehozni mint a [vulkancapa.hu](https://www.vulkancapa.hu)! Ez már egy kicsit komplexebb lesz, illetve szükség lesz pár php fájl létrehozására, továbbá erősen ajánlott hogy mielőtt ennek neki vágnál olvasd végig az SQL doksit. Írnám is miket hozz létre milyen tartalommal, aztán neki állok magyarázni:

Ebben a fájlban definiáljuk le az adatbázis csatlakozást.

connection.php
```
<?php
$servername = "localhost:3306";
$username = "root";
$password = "";
$dbname = "mytestdb";
$conn = new mysqli($servername, $username, $password, $dbname);
$conn->set_charset("utf8");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

Miután ez megvan, `localhost/phpmyadmin`-ba hozzunk létre egy `mytestdb` nevű adatbázist, aztán futtassuk le rajta ezt a kódot:
```
CREATE TABLE my_articles (
    id int AUTO_INCREMENT PRIMARY KEY NOT NULL,
    title varchar(255) NOT NULL,
    summary varchar(255) NOT NULL,
    content text,
    published datetime
);

INSERT INTO my_articles (title, summary, content, published) VALUES ('Teszt cikk', 'Ez egy nagyon szép teszt cikknek a rövid összefoglalója!', 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam consectetur libero in nunc consectetur, eget bibendum metus eleifend. Curabitur ligula massa, bibendum id varius ut, malesuada vitae diam. Donec non magna sit amet magna eleifend cursus. Phasellus ac egestas ante, eget egestas mauris. Pellentesque pretium velit at erat dapibus, quis pretium eros pellentesque. Phasellus suscipit lectus elit, ac varius lorem fermentum eleifend. Quisque in tincidunt sem. Proin nec laoreet quam, quis porttitor est.', '2021-12-28 12:34:56');

INSERT INTO my_articles (title, summary, content, published) VALUES ('Még egy szép teszt cikk', 'Nyugi ennek a cikknek sincs értelmes mondani valója.', 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam consectetur libero in nunc consectetur, eget bibendum metus eleifend. Curabitur ligula massa, bibendum id varius ut, malesuada vitae diam. Donec non magna sit amet magna eleifend cursus. Phasellus ac egestas ante, eget egestas mauris. Pellentesque pretium velit at erat dapibus, quis pretium eros pellentesque. Phasellus suscipit lectus elit, ac varius lorem fermentum eleifend. Quisque in tincidunt sem. Proin nec laoreet quam, quis porttitor est.', '2021-12-28 13:51:31');
```

articleView.php
```
<?php
require("connection.php");

$sql = "SELECT title, summary, content, published FROM my_articles ORDER BY published DESC";
$sql_read = $conn->prepare($sql);
$sql_read->execute();
$data_from_sql = $sql_read->get_result();

if ($data_from_sql->num_rows > 0) {
    while($row = $data_from_sql->fetch_assoc()) {
        echo "<div style=\"width: 800px;\">
            <h2>".$row["title"]."</h2>
            <b>".$row["published"]."</b>
            <p>".$row["summary"]."</p>
            <p>".$row["content"]."</p>
            <hr>
        </div>";
    }
} else {
    echo "<h2>Nincs cikk!</h2>";
}
?>
```

Juhuuu! Ha ezeket ügyesen összeraktuk és megnyitjuk a `localhost/articleView.php` oldalt a böngészőnkben akkor látnunk kell a két cikkünket az oldalon! Tök jó hogy ezt most összeraktuk, de megkéne érteni mit csináltunk úgy hogy egyesével menjünk végig a fájlokon:

## connection.php

Célszerű ezt az egészet egy külön fájlba kiszervezni mert úgy is rengeteg oldalon fogjuk használni.

```
<?php
//Hozzunk létre itt négy változót, amiben az átláthatóság kedvéért eltároljuk az adatbázis csatlakozáshoz szükséges adatokat
//Ezek az adatok az alap XAMPP telepítéses címek, nyilván ez változhat, főleg amikor egy bérelt szerverre kitelepítjük az oldalunkat
$servername = "localhost:3306";
$username = "root";
$password = "";
//Eme felső 3 adat az alap XAMPP-os telepítésnél mindig ez lesz, egyedül az adatbázis nevünk változhat, itt most egy mytestdb nevű adatbázist hozunk létre
$dbname = "mytestdb";

//Itt egy változóba létrehozunk egy adatbázist csatlakozást a felső adatokkal megadva
$conn = new mysqli($servername, $username, $password, $dbname);

//Ez a sor itt életed megmentője, hogy ne kelljen az ékezetes karakterek hibáival szarakodni
$conn->set_charset("utf8");

//És csináljunk egy ilyet is, hogy ha valami nem lenne jó adatbázis csatlakozásnál, írja ki a hibát
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

## Az SQL kód

Hát itt most csak egy egyszerű SQL kódot írtam, ahol létrehoztunk egy egyszerű táblázatot és beletöltöttünk két adatot. Erről bővebben tájékozódhatsz az **SQL doksiban** ott úgy is levan írva minden.

## articleView.php

```
<?php
//behúzzuk ugye a csatlakozást
require("connection.php");

//Én úgy szoktam hogy az átláthatóság kedvéért egy külön $sql nevű változóba írom bele az SQL kódot
$sql = "SELECT title, summary, content, published FROM my_articles ORDER BY published DESC";

//Egy tetszőleges nevű változóba beletöltjük a mysqli-s adatbázis objektumunkat az SQL kóddal amit később kezelni fogunk
$sql_read = $conn->prepare($sql);

//itt lefuttatjuk az SQL commandot amit felül megadtunk
$sql_read->execute();

//get_result függvénnyel pedig az eredmény objektumot átadjuk szintén egy tetszőleges nevű változónak
$data_from_sql = $sql_read->get_result();


//leellenőrizzük hogy több sor tálatot kaptunk-e vissza a lekérdezésből mint 0, ha nem, akkor írjuk ki hogy nincs cikk
if ($data_from_sql->num_rows > 0) {
    //Ha több sort kaptunk vissza mint 0, akkor egy while ciklussal soronként egy tömbbe átadjuk a találatokat
    //Majd a ciklusban az asszociatív tömböt amit kaptunk bele, kiiratjuk az adatokat a megfelelő helyre
    //Itt én most generáltam egy egyszerű kis html-t a cikkünk megjelenítésére
    while($row = $data_from_sql->fetch_assoc()) {
        echo "<div style=\"width: 800px;\">
            <h2>".$row["title"]."</h2>
            <b>".$row["published"]."</b>
            <p>".$row["summary"]."</p>
            <p>".$row["content"]."</p>
            <hr>
        </div>";
    }
} else {
    echo "<h2>Nincs cikk!</h2>";
}
?>
```

# Login

Nézzünk meg egy hótegyszerű login-t. Először is csináljunk az adatbázisban egy táblát amiben parasztokat tárolunk:

```
CREATE TABLE my_users (
    id int AUTO_INCREMENT PRIMARY KEY NOT NULL,
    username varchar(255) NOT NULL,
    password varchar(255) NOT NULL,
    displayname varchar(255) NOT NULL
);

INSERT INTO my_users (username, password, displayname) VALUES ('janiahegyrol','123','Jani');
INSERT INTO my_users (username, password, displayname) VALUES ('bor','bicikli','Pepsi Béla');
```

## session.php

Ebben fogjuk eltárolni a bejelentkezett user adatait, illetve célszerű dolog a `connection.php`-t ebbe behúzni, és utánna minden fájlban a `session.php`-t includeolni mivel abban már benne lesz akkor a csatlakozás, és a bejelentkezett user adatai is.

```
<?php
require('connection.php');
session_start();

if(isset($_SESSION['login_user'])) {
    $user_check = $_SESSION['login_user'];

    $sql = "SELECT id, username, displayname FROM my_users WHERE username=?";
    $get_user = $conn->prepare($sql);
    $get_user->bind_param("s", $user_check);
    $get_user->execute();
    $get_user_result = $get_user->get_result();
    $row_get_user = $get_user_result->fetch_assoc();

    $login_session_id = $row_get_user["id"];
    $login_session_username = $row_get_user["username"];
    $login_session_displayname = $row_get_user["id"];
}
?>
```

## login.php

Csináljunk egy egyszerű bejelentkező oldalt is.

```
<?php
require('session.php');

// Ha bevagyunk jelentkezve, ne tudjuk megnyitni a login oldalt
if (isset($_SESSION['login_user'])){
    header("location: /");
}

if($_SERVER["REQUEST_METHOD"] == "POST") {
    // Lekérjük a változókat
    $form_username = $_POST["username"];
    $form_password = $_POST["password"];

    // Nézzük meg létezik-e a felhasználó
    // Ez vissza ad egy számot hány darab felhasználó van az adatbázisba
    $get_exist = $conn->prepare("SELECT count(id) AS countid FROM my_users WHERE username=?");
    $get_exist->bind_param("s", $form_username);
    $get_exist->execute();
    $result_exist = $get_exist->get_result();
    $row_exist = $result_exist->fetch_assoc();
    // Nyilvánvalóan 1-et kell kapnunk
    if ($row_exist["countid"] == 1) {
        // Kérjük le a user adatait
        $get_login = $conn->prepare("SELECT username, password FROM my_users WHERE username=?");
        $get_login->bind_param("s", $form_username);
        $get_login->execute();
        $result_login = $get_login->get_result();
        $row_login = $result_login->fetch_assoc();

        // Kerüljük el a hibát hogy nem ad meg jelszót a user
        if (mb_strlen($row_login["password"]) < 2) {
            $row_login["password"] = "";
        }
    
        // Ellenőrizzük le hogy egyezik-e a beírt jelszó az adatbázisban lévővel
        if ($form_password == $row_login["password"]) {
            // Ha igen, töltsük be a Session-be a usernevet és küldjük a főoldalra a usert
            $_SESSION["login_user"] = $form_username;
            header("Location: /");
        } else {
            $error = "Nem megfelelő belépési adatok!";
        }
    } else {
        // Ha 0 vagy valami érthetetlen okból több mint 1-et kapnánk vissza akkor dobjunk hibát
        $error = "Nem található ilyen felhasználó!";
    }  
}
?>

<form autocomplete="off" action="login.php" method="post" enctype="multipart/form-data">
    <?php
        if(isset($error)) {
            echo "<p class=\"error-title\">".$error."</p>";
        }
    ?>
    <p>Felhasználónév</p>
    <input type="text" name="username" maxlength="50" placeholder="Felhasználónév">
    <p>Jelszó</p>
    <input type="password" name="password" placeholder="Jelszó">
    <button type="submit">Belépés</button>
</form>
```

Létrehoztunk itt egy egyszerű bejelentkezést, a példából a HTML részen kihagytam most a body, html stb tageket a lényeg kedvéért, de amúgy ne hagyjuk ki. (Sőt, gyakorlásnak csináld meg rendesen!) Ezen példában csak a nyers jelszót hasonlítjuk össze, titkosítást most nem használunk, egyenlőre csak értsd meg önmagában hogy működik ez az egész, de ha érdekel, [ezen a linken](https://www.php.net/manual/en/function.password-verify.php) megtalálod a jelszó ellenőrző függvényt.

Ha ezzel megvagy és sikeres a login, legyen egy `index.php` fájlunk aminek ez a tartalma:

```
<?php
echo "Üdv ".$login_session_displayname."!";
?>
```

Amikor sikeres volt a bejelentkezés, ide kell hogy átvigyen az oldal, és ha minden rendben ment a bejelentkezett user nevét kell látnod a böngészőben.

# Logout

Ez egy nevetségesen egyszerű dolog lesz, csinálj egy `logout.php` fájlt:

```
<?php
 session_start();

 if(session_destroy()) {
    header("Location: /");
 }
?>
```
...és ennyi. Törölni kell a session-t, azaz kijelentkezik a user, és visszakerülünk a főoldalra.

# Regisztráció

# Email küldés