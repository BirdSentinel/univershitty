# HTML
Na elemezzünk egy kis HTML-t.

## Dö béziksz

Hogy mi is az a HTML? Az Amerikaiak 11%-a azt hiszi hogy egy nemi betegség ([Erről tanulmány](https://time.com/12410/11-of-americans-think-html-is-an-std/)), te meg azt hiszed hogy egy _programozási nyelv_, heh, nope. Ez egy markup nyelv, mivel még egy if/else-t se tartalmaz, így nem mondható programnyelvnek, ezért ha csajozol és kérdezik miben programozol ne mondd azt hogy HTML mert még ők is kiröhögnek.

Na nézzünk meg egy példát, hogy nézki egy alap HTML oldal:

```
<!DOCTYPE html>
<html>
    <head>
        <title>Zack's Univershitty</title>
        <link rel="stylesheet" href="styles/main.css">
        <meta charset="UTF-8">
    </head>
    <body>
        <div class="center-box">
            <p>Ez lesz az oldalad alapja!</p>
        </div>
    </body>
</html>
```

Huha ide látom hogy beakadtál mint az orsó fék, hogy mi a bánat ez, na menjünk rajta végig szépen sorban.

`<!DOCTYPE html>`

Minden HTML fájlod legelső sora ez lesz, mivel ezzel mondod meg a böngészőnek hogy ez egy HTML5-ös fájl lesz. (Amúgy működik enélkül is, de na... formalitás.)

`<html></html>`

Ezen tag közé rakod az egész oldal tartalmát, mindent. Ezenkívül nem írunk semmi HTML related dolgot.

Majd a `<html>` tagen belül található 2 fő tag.

```
<head>
    <title>Zack's Univershitty</title>
    <link rel="stylesheet" href="styles/main.css">
    <meta charset="UTF-8">
</head>
```

A `<head>`-en belül adunk meg olyan dolgokat mint például az oldal címe (amit látsz a tabon felül), húzunk be az oldalra CSS és JavaScript fájlokat, példa a CSS fájl betöltésére:

`<link rel="stylesheet" href="styles/main.css">`

Ezzel betöltjük a "styles" mappán belüli main.css stílusfájlt.

Ezután található egy piszok fontos sor, amit minden (legalábbis magyar ékezetes) oldalra beírunk!

`<meta charset="UTF-8">`

Hogy mit csinál ez? Na csinálj egy HTML oldalt, írj bele magyar ékezetes szöveget, főleg hosszú ŰŐÍ betűkkel, és nézd meg mit fogsz látni a böngésződbe. Beírtad hogy "Árvíztűrő tükörfúrógép" erre azt látod a böngészőbe hogy: "ÃrvÃ­ztÅ±rÅ‘ tÃ¼kÃ¶rfÃºrÃ³gÃ©p"... (Van amikor amúgy enélkül is normálisan látod a szöveget, ez gép beállítástól/böngészőtől is függ, de erre ne alapozzunk, írd oda!!!) Na most azért látod ezt a kusza szöveget, mert nem jó a charset az oldaladon, ezért neked bekell állítani "UTF-8"-ra a megadott sorral, így nem lesznek problémáid az ékezetes szövegekkel.

...És végül jöjjön a lényeg, amit látni fogunk a weboldalon:

```
<body>
    <div class="center-box">
        <p>Ez lesz az oldalad alapja!</p>
    </div>
</body>
```

A `<body>` tag! Ami ezen belül van, azt fogja megjeleníteni nekünk a böngésző! A fenti példában azt látod hogy egy div dobozban van benne egy paragraph szöveg. Ha nyomsz a böngésződben egy F12-t, előjön a fejlesztői menü ahol láthatod hogy minden weboldalon a cuccok amiket látsz, az a `<body>` tag-en belül helyezkednek el.

Na ennyi lenne az alap, most menjünk bele kicsit részletesebben a dolgokba:

## Tag
`<div class="center-box"></div>`

Ez, ami fent van, egy _div_ **tag**. Általában HTML-ben a tag-eket `<valami>`-vel kezdjük (azaz kacsacsőrözünk) és `</valami>`-vel fejezzük be. Ezen kettő cucc közé kerülhet bármi. Sima szöveg, vagy további tag-ek. Vannak kivételek, ilyen például az `<img src="www.link.com/kep.jpg"/>` melyet egyből nyitunk és zárunk is. Ezekből mazsolázhatsz bőven a [www.w3schools.com](https://www.w3schools.com/html/ oldalon. (Ez lesz a Bibliád mostantól, ezzel kelsz, ezzel fekszel, budiba az iPad-en ez lesz a kezdőlapod.)

## Attribútum
`<a href="https://www.google.com">Link</a>`

Fentebb egy link látható. Ez is ugyan olyan tag mint a div. Ebben láthatunk egy _href_ cuccot, az ilyen cuccokat, amik az első kacsacsőrös nyitóbaszba vannak benne, **attribútumnak** nevezzük. Ezekkel adunk meg az adott tag-nek tulajdonságokat, mint például felül ez a href egy linket jelent. Az attribútumoknak általában az a formája hogy `valami="adat"`. A kettős macskaköröm közé írjuk be a cuccot az egyenlőség jel után.

## CSS classok
`<div class="center-box"></div>`

Ahogy már fent is láthattad ezt a kódot, ennek a div-nek megadtunk egy `center-box` nevű CSS class-t. Mi a bánat az a class kérded? Ezzel tudunk _.css_ fájlokból stílust megadni a megadott tag-nek. A _class_ (mivel ez is az) attribútumba igazából annyi nevet adhatunk meg amennyit nem szégyellünk, példa:

`<div class="header-text-container center-box colored-box"></div>`

Na most azt láthatjuk hogy 3db class nevet adtunk meg neki, ezekre CSS-ből tudunk majd hivatkozni.

## ID-k
`<h2 id="title">Párolgó Denevér</h2>`

Fentebb egy cím tag-et láthatunk, megadva egy id-vel. ID, nevéből adódóan egy azonosító. Most a példába megadtunk neki egy "title" nevet. Egy névből csak 1db lehet az oldalon (nem az id=-ből, hanem ugyan olyan nevűből lehet csak egy), írhatsz többet is ha hülye vagy, de mindig csak a legelsőt fogja megtalálni ha ráhivatkozol pl JavaScript-ből. Mire jó ez? Formailag nagyobb dolgok azonosítására szoktunk használni, mint pl egy sidebar, header stb. Illetve így JavaScript-ből nagyon egyszerű megtalálni az adott elemet, példa:

`document.getElementById("title").innerHTML`

Ez visszaadja nekünk a _title_ elem tartalmát.