# Zack's Univershitty
Welcum bois and gals. Szóval kapni fogtok tőlem egy alapvető ~~picsánrúgást~~ tudást amivel elindulhattok a webfejlesztői szakmán.

## Amire szükséged lesz
- Kettes szintű "faszomkivan" feel a jelenlegi szakmáddal
- Egy Linux/MacOS/Winfos gép
- ~~Mardosó depresszió~~ Minimális életkedv
- [Github Desktop alkalmazás](https://desktop.github.com)
- [Visual Studio Code](https://code.visualstudio.com/download)
- [XAMPP](https://www.apachefriends.org/download.html)
- [Google Chrome](https://www.google.com/chrome/)
- Regisztráció Github-ra

## Szépen fogsz és felraksz mindent
Ezután a Github appal leklónozod ezt a repot a gépedre:
![git](docs/img/git.jpg "git")
Ajánlom a következő útvonalat: __C:/Files/Git/univershitty__

Miután megvagy, nyisd meg a XAMPP-ot, konfigolni fogunk egy kicsit.
![httpdconf](docs/img/httpdconf.png "httpdconf")
<br>Majd kikeresed a `DocumentRoot` részt és beírod ezen mappa elérését:
```
DocumentRoot "C:/Files/Git/univershitty"
<Directory "C:/Files/Git/univershitty">
```

Ha megvagy, az __Actions__ rész alatt Stop/Start gombbal indítsd újra az Apache modult.

Ezután nyisd meg a Chrome-ot, és a böngésző címsorába írj be ennyit: `localhost` csapj egy entert és ezt kell látnod:
![univershitty](docs/img/univershitty.png "univershitty")

## 0. Git
    - Alapvető git dolgok
    - Github
    - Repok
    - Commitolás
    - Branchelés
## 1. Fájlok és mappa szerkezet
    - Mappák
    - Szerkezet
    - Fájl elnevezések
## 2. HTML/CSS
    - Alapfelépítés
    - Tag-ek
    - Attribútumok
    - CSS
## 3. JavaScript
    - Változók
        (Egy változó neve csak angol abc-nek megfelelő betűket tartalmazhat, nem kezdődhet speciális karakterrel, szóval csak betűvel kezdjük, számot tartalmazhaz, de nem lehet az az első karakter, illetve ha szót akarunk benne elválasztani akkor _ használjunk. pl: segg_le1 )
    - Var/Let/Const
    - Operátorok
    - Kondíciók
    (= baloldaliba beletölti a jobb oldalit, == vizsgálat hogy ugyan az-e, === vizsgálat hogy ugyan az-e plusz megnézi hogy a TIPUSA is ugyan az-e)
    - DOM manipulálása
    - For/While ciklus
    - Switch
## 4. Alapvető programozás/PHP
    - *azok mint JS-nél*
## 5. SQL
    - This is where the fun begins:)
## 6. Egy alapvető blog összerakása

## 7. Tesztelési folyamat