# Hibakezelés

A ´65 nyomtatvány betöltése után egy emailt kapunk, ami egyrészt a legenerált ´65 Nyomtatvány XML file-t tartalmazza és egy szöveges dokumentumot a feldolgozás menetéről és a hibákról.

## Kezelhetetlen hibákról

A hibák egy része olyan jellegű, amire a program nem ad megoldást, csak felhívja rá a figyelmet.

### Nincs adószám

Ha egy SAP sorban nincs adószám, akkor nem lehet szállítót meghatározni. Mivel az M lapok kitöltését szállítónként kell elvégezni ezért az adószám meghatározása nélkül a sorral nem lehet dolgozni.

Az ilyen sorok esetén figyelmeztetést kapunk, hogy a sor nem dolgozható fel. A sort figyelmen kívül hagyja a rendszer.

### Adószám hossza nem megfelelő

Ha egy SAP sorban az adószámot elgépeltük, akkor nem lehet szállítót meghatározni. Mivel az M lapok kitöltését szállítónként kell elvégezni ezért az adószám meghatározása nélkül a sorral nem lehet dolgozni.

Az ilyen sorok esetén figyelmeztetést kapunk, hogy a sor nem dolgozható fel. A sort figyelmen kívül hagyja a rendszer.

### Az Adószám hibás, NAV rendszeréből nem lehet valid adatokat lekérni

Ha egy SAP sorban hibás adószámot adunk, akkor nem lehet szállítót meghatározni. Mivel az M lapok kitöltését szállítónként kell elvégezni ezért az adószám meghatározása nélkül a sorral nem lehet dolgozni.

Az ilyen sorok esetén figyelmeztetést kapunk, hogy a sor nem dolgozható fel. A sort figyelmen kívül hagyja a rendszer.

## Felvett számlák hibákkal

Amikor sikerült az SAP lista alapján az adószámmal a szállítót azonosítani, akkor a számla megtalálható a listában és rákerül az M lapokra.
Az így megtalált számláknál 3 lehetséges eset van:

1. NAV Online rendszerből rögzített számlát találtunk a sorhoz. Itt a számla adatok pontosak.
	- Amennyiben az SAP listán szereplő számlaszám pontosan egyezik a rögzített számla számával, nem lesz a sorhoz megjegyzés fűzve.
	- Amennyiben a számlaszámok nem pontosan egyeznek meg, a sorhoz a **Ellenőrizze le, hogy a számlaszám megfelelő e** megjegyzés lesz fűzve.
	
2. SAP sor alapján a program generálta a számlát. Ekkor a **Automatikusan generált számla** és a **Ellenőrizze le, hogy a számlaszám megfelelő e.** üzenetek kerülnek a szmlára. 

3. Manuálisan rögzített számla esetén van találat. Ez akkor szokott előfordulni, ha NAV-ból nem jön a számla és valamilyen okból már korábbaan rögzítettük kézzel.
    - Amennyiben a számlaszámok nem pontosan egyeznek meg, a sorhoz a **Ellenőrizze le, hogy a számlaszám megfelelő e** megjegyzés lesz fűzve.

### "Ellenőrizze le, hogy a számlaszám megfelelő e" üzenet 

Néhány esetben az SAP-ból kapott sor alapján találunk NAV-os számlát, de a számlaszám nem pontosan egyezik meg. A program egy logika alapján a nem teljesen egyező számlákhoz is keres megfelelő NAV számlát.

Ilyen esetekben csak valószínű a találat, de a program biztos nem lehet benne, ezért a NAV-os számlához Saját referenciának berakja az SAP-ban rögzített számlaszámot, de a számlához megjelgyzést fűz, hogy nem pontos egyezés, le kell ellenőrizni.

Amennyiben a párosítás jó volt, csak zárjuk le a megjegyzést.

Amennyiben hibás találat volt a következőket kell tenni:

- Elővesszük a számlát, hogy megnézzük nincs e a számlaszám elgépelve.
- A párosítást megszüntetjük úgy, hogy a **Saját referencia** mezőt kitöröljük.

Ezután 2 lehetőség van

1.  Rákeresünk a szállító adószáma alapjn az összes számlára és megnézzük, szerepel e ott a számla. Ha igen, a **Saját referencia** mezőjébe beírjuk az SAP-ba lévő számlaszámot.
2.	Ha nem találunk illeszkedő számlát, kézzel felrögzítjük a rendszerbe.

> Kézi rögzítéskor az eredeti számla alapján vigyük fel a számla adatait pontosan! Amennyiben az SAP számlaszám eltér a valóditól, mentés után módosítsuk és a **Saját referencia** mezőbe írjuk be az SAP-ban lévő számlaszámot.

> Ha lehet másoljuk ne gépeljük. Fontos, hogy pontosan írjuk be a referenciát, a szünetekkel, jelekkel együtt.

### "Automatikusan generált számla" üzenet

Feldolgozás során az SAP számlaszám alapján nincs találat, akkor a rendszer rögzít egy számlát. Ez a számla részleges, dátumokat és összegeket mindenképpen ellenőrizni kell.

Első teendő itt is, hogy elővesszük az eredeti számlát és rákeresünk a rendszerben a számlaszámra.

> Keresésénél ne felejtsük el kivenni a **Csak nyitott üzenetekkel** pipát.

- Ha találtunk számlát, akkor az SAP számlaszámmal rögzített számlát töröljük, és a talált NAV számla **Saját azonosító** mazőjébe írjuk be az SAP-ba rögzített számlaszámot.
- Ha nem találtunk számlát, akkor az előrögzített számlát javítsuk az eredeti számla alapján (számlaszám, dátumok, összegek). A számlaszám mezőbe az eredeti számlán lévő **pontos** számlaszámot írjuk, a **Saját referencia** mezőbe pedig az SAP -ban lévő számlaszámot.

> Célszerű javítást azzal kezdeni, hogy az előrögzített számlaszámot a vágólapra másoljuk, mert javításnál vagy csak referencia beírásnál csak be kell illeszteni, elkerülve a gépelési hibákat.

### "Negatív előjelü számla hivatkozott eredeti számla nélkül" üzenet

Ha van negatív előjelü számlánk és nem lehet NAV számlával párosítani, akkor két lehetőség van:

1. Valóban egy negatív előjelü számla. Ezt hagyjuk így, lezárhatjuk az üzeneteket. Hibalistára mindíg kidobja a program, de ne foglalkozzunk vele. Negatív számla nem kerül az M lapokra.
2. A számla egy módosító számla. Ekkor javítani kell a **Művelet** mező értékét CREATE értékről MODIFY vagy STORNO értékre. Ebben az esetben ki kell tölteni az **Eredeti számlaszám** mezőt. Amennyiben az eredeti számla neincs rögzítve a rendszerbe, rögzítsük. Szintén ki kell keresni az esetlegesen kiállított további módosító számlákat is és ha nincsenek a rendszerben, akkor rögzíteni kell. Figyeljünk oda, hogy az összesnél az **Eredeti számlaszám** mező azonos!

> A nav rendszere megengedi, hogy módosító számla legyen berögzítve, eredeti számla nélkül. Ekkor a **Módosító számla eredeti számla nélkül ** mező be van pipálva. Ez nekünk nem jó, mindenképpen fel kell rögzíteni az eredeti számlát is, mert a bevalláshoz ez kell.

> Egyre kevesebb "nem nav" számla lesz a rendszerben, mert elvileg minden számlát már be kell küldeni. 

