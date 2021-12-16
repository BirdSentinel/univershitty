# PHP

Na ha túlszenvedted magad a JavaScript doksin, igazából itt már nem fogsz megszakadni, mert ennek a doksinak egy része elég repetitív lesz. Konkrétan amit átvettünk az előző doksiba átemeljük php-ba, kezdjük is:

## Mi az a PHP?



## todo: átírni a js doksit php-ra

## PHP related things

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

## Csatlakozás adatbázishoz