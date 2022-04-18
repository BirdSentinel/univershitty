# Az első lépések
Ebben a doksiban összeszedtem az első lépéseket, hogy miket kell felraknod a gépedre hogy elkezd magadba tömni ezeket a doksikat.

## Programok

Ezeket igazából csak én javaslom, mindegyikre van egy tonna alternatíva, kinek mi jön be, mindet ki kell próbálni. Személyszerint én is kezdtem Notepad++-al, majd Atom majd végül évek óta megragadtam a Visual Studio Code-nál. Ebben a webfejlesztősdiben az a szép hogy millió féle tool-al és hozzáállással lehet csinálni. Na meg hát az oprendszerek, ott is ugye vannak eltérések ki milyen programot használ. Én Mac user vagyok egy ideje, de tudom hogy nagyrészetek Windows-t használ, ezért ezt a tutorial-t is úgy igazítom most.

### Git

Én a [Github](https://github.com/)-ot részesítem Git-ezéshez előnyben. Mire jó ez nekünk? Tegyük fel hetek óta dolgozol a fancy weblapodon a kis lapostopodon, jön Cirmi macskád és telibehugyálja szónélkül a géped, rip SSD, rip adat, rip munkád. Még egy jó példa. Dolgozol valamin, megcsináltad. 1 hét múlva észreveszed hogy nem működik ott a kódod, de nem vágod mi tette tönkre. Semmi nyomod nincs visszakövetni a változást. Verziókezelés? Nem, az hogy megszámozott vagy dátumozott mappákba rakod időnként az egész projekted az borzalom, hidd el, agyvérzést fogsz kapni tőle.

Giten akár lépésenként nyomom tudod követni a kód változásaid (ha commitolod őket), vissza is tudod állítani előző állapotra stb stb. Magáról a Gitezésről [ezen a linken](https://docs.github.com/en/get-started/quickstart/hello-world) olvashatsz bővebben.

Az első lépésed itt legyen az, hogy beregisztrálsz [Github](https://github.com/)-ra, és letöltöd a gépedre a [Github Desktop](https://desktop.github.com/) appot.

### Szerver

Hogy ezt a tutorial sorozatot végig tudd csinálni rendesen, érdemes valami lokális szervert feltelepíteni, én a [XAMPP](https://www.apachefriends.org/download.html)-ot ajánlom. Itt a rendszerednek megfelelőt szedd le, például a 7.4.28-as verziót, vagy éppen ami a legfrissebb.

### Editor program

Hát nyilván azért ne notepad-be szerkesszük a kódunkat, rakjunk fel valami értelmest, én a [Visual Studio Code](https://code.visualstudio.com/download)-ot ajánlom. Illetve miután felraktad, bal oldalt az Extensions részben (4db kocka ikon) rakd fel a `vscode-icons` kiegészítőt, rak ikonokat minden féle fájlok meg mappák mellé, nagyon átláthatóvá teszi a projekted, must have cucc!


## A konfigolás

Miután felraktunk mindent, [Github](https://github.com/)-on hozzunk létre egy új [Repository](https://github.com/new)-t, ide fogunk egyenlőre dolgozni. A neve lehet "gyakorlas" vagy bármi ilyesmi.

Amikor ezt létrehoztuk, a Github app-ban `clone`-ozzuk le az előbb létrehozott reponkat, lehetőleg valami egyszerű helyre, én pl a `C:\Files\Git\repodneve` helyre raknám.

Miután ezzel is megvagyunk, nyissuk meg a `XAMPP Control Panel`-t. Az `Apache` sorában lévő `Config` gombra kattintva előjön egy menü, ahol válasszuk az `Apache (httpd.conf)` opciót. Ilyenkor megnyílik egy notepadbe egy konfig fájl, ahol megkéne keresned azokat a sorokat ahol ezt látod:

```
# DocumentRoot: The directory out of which you will serve your
# documents. By default, all requests are taken from this directory, but
# symbolic links and aliases may be used to point to other locations.
#
DocumentRoot "D:/Files/Git/vulkancapahu"
<Directory "D:/Files/Git/vulkancapahu">
```

A `DocumentRoot` és `Directory` részbe írd bele a leklónozodd repod mappájának elérhetőségét, ahogy példának írtam fentebb is, ha ez megvan, mentsd el a fájlt és zárd be.

Ezután a `XAMPP Control Panel`-ban az `Apache` sorában lévő `Start` gombra kattintva elindul a webszerverünk, melyet ki is tudunk próbálni, még pedig úgy, hogy a böngészőnkben a címsorban megnyitjuk a `localhost` címet. Ennyi, semmi www satöbbi, csak `localhost`.

Természetesen ilyenkor még semmit se fogunk látni, mivel egy teljesen üres mappára mutat a böngészőnk. Nyissuk meg a `Visual Studio Code`-ot és hozzunk létre egy `index.html` fájlt a leklónozodd repo-nk mappájában, és valamit írjunk bele a fájlba. Mentsük el, és frissítsük a böngészőnkben a lapot. Ha látjuk a beleírt szöveget, mindent jól csináltunk!

## A továbbiak

Innentől kezdve neki állhatunk a többi doksit is tanulmányozni szépen sorjában. Fejlesztős böngészőnek egyébként a `Chrome`-ot ajánlom, mivel elég jó a fejlesztői konzolja (ezt az F12 gombbal tudod előhozni).

## A doksik sorjában

0. [Az első lépések](https://univershitty.hu/webdev)
1. [HTML](https://univershitty.hu/webdev/html)
2. [CSS](https://univershitty.hu/webdev/css)
3. [JS](https://univershitty.hu/webdev/js)
4. [PHP](https://univershitty.hu/webdev/php)