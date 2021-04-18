# Adószám ellenőrzés

Adószám ellenőrzés funkcióval egy magyar vagy EU-s adószám ellenőrizhető.

## Magyar adószám ellenőrzése

Meg kell adni az adószám első 8 számjegyét. Az adószám végén az egy jegyű áfa kódot és a 2 jegyű területi besorolás kódját nem kell megadni, de ha megadjuk sem okoz problémát. A tagoló "-" is benne lehet.

> A 8 számjegy után 3 további adattal igazából a rendszer nem dolgozik, ha ott hibás számot adunk meg, az sem okoz gondot. 

> Figyeljünk, hogy amennyiben nem 8 jegyű adószámot adunk meg, akkor a 3 utolsó szám egyezzen meg a kapott eredménnyel, mert a rendszer csak a 8 számjegyű adószámra keres és találat esetén eltérhet az adószám vége. 


### HU előtag az adószámban

Meg lehet adni az EU komform magyar adószámot is ami HU előtag után az adószám 8 számjegye. Ez abban könnyebség, ha valahonnan másoljuk az adószámot, nem kell bajlódni a HU előtag kihagyásával bajlódni.

## EU adószámok

Az EU adószámokat az Európai Únió által üzemeltetett [VIES](https://ec.europa.eu/taxation_customs/vies/?locale=hu) rendszerből végzi a program.

### Uniós adószámok felépítése


|Tagállam|Felépítés|Formátum|
|--------|:--------:|--------|
|AT-Ausztria|ATU99999999|Egyetlen karaktersor, amely 9 karakterből áll|
|BE-Belgium|BE0999999999 , BE1999999999|Egyetlen számsor, amely 10 számjegyből áll|
|BG-Bulgária|BG999999999 , BG9999999999|Egyetlen számsor, amely 9 vagy 10 számjegyből áll|
|CY-Ciprus|CY99999999L|Egyetlen karaktersor, amely 9 karakterből áll|
|CZ-Cseh Köztársaság|CZ99999999 , CZ999999999 , CZ9999999999|Egyetlen számsor, amely 8, 9 vagy 10 számjegyből áll|
|DE-Németország|DE999999999|Egyetlen számsor, amely 9 számjegyből áll|
|DK-Dánia|DK99 99 99 99	4|egyenként 2 számjegyből álló számsor|
|EE-Észtország|EE999999999|Egyetlen számsor, amely 9 számjegyből áll|
|EL-Görögország|EL999999999|Egyetlen számsor, amely 9 számjegyből áll|
|ES-Spanyolország|ESX9999999X4|Egyetlen karaktersor, amely 9 karakterből áll|
|FI-Finnország|FI99999999|Egyetlen számsor, amely 8 számjegyből áll|
|FR-Franciaország|FRXX 999999999|Egy karaktersor, amely 2 karakterből áll és egy számsor, amely 9 számjegyből áll|
|HR-Horvátország|HR99999999999|Egyetlen számsor, amely 11 számjegyből áll|
|HU-Magyarország|HU99999999|Egyetlen számsor, amely 8 számjegyből áll|
|IE-Írország|IE9S99999L, IE9999999WI|Egyetlen karaktersor, amely 8 vagy 9 karakterből áll|
|IT-Olaszország|IT99999999999|Egyetlen számsor, amely 11 számjegyből áll|
|LT-Litvánia|LT999999999,LT999999999999|Egyetlen számsor, amely 9 vagy 12 számjegyből áll|
|LU-Luxemburg|U99999999|Egyetlen számsor, amely 8 számjegyből áll|
|LV-Lettország|LV99999999999|Egyetlen számsor, amely 11 számjegyből áll|
|MT-Málta|T99999999|Egyetlen számsor, amely 8 számjegyből áll|
|NL-Hollandia|NLSSSSSSSSSSSS|Egyetlen karaktersor, amely 12 karakterből áll|
|PL-Lengyelország|L9999999999|Egyetlen számsor, amely 10 számjegyből áll|
|PT-Portugália|PT999999999|Egyetlen számsor, amely 9 számjegyből áll|
|RO-Románia|RO999999999|Egyetlen számsor, amely legalább 2, legfeljebb 10 számjegyből áll|
|SE-Svédország|SE999999999999|Egyetlen számsor, amely 12 számjegyből áll|
|SI-Szlovénia|SI99999999|Egyetlen számsor, amely 8 számjegyből áll|
|SK-Szlovákia|SK9999999999|Egyetlen számsor, amely 10 számjegyből áll|
|XI-Észak-Írországról|XI999 9999 99, XI999 9999 99 9995, XIGD9996, XIHA9997|1 block of 3 digits, 1 block of 4 digits and 1 block of 2 digits; or the above followed by a block of 3 digits; or 1 block of 5 characters|



**Jelmagyarázat:**
    
    - *: A formátum nem tartalmazza a két betűből álló országkódot
    - 9: számjegy
    - X: betű vagy számjegy
    - S: betű; számjegy; vagy a következő jelek egyike: +, *
    - L: betű
    
 **Megjegyzések:**
    
    1. Az országkódot követő első karakter mindig „U”.
    2. Az országkódot követő első számjegy mindig „0”.
    3. Az (új) 10 számjegyű formátum úgy jön létre, hogy a (korábbi) 9 számjegyű számsor az elején kiegészül egy nullával.
    4. Az első és az utolsó karakter lehet betű vagy szám, de nem lehet mindkettő szám.
    5. Fióktelepet jelöl.
    6. Kormányhivatalokat jelöl.
    7. Egészségügyi hatóságokat jelöl.
    8. Számít a kis- és a nagybetűk közötti különbség. Kérjük, hogy pontosan az itt bemutatott felépítésnek megfelelően írja be a keresőmezőbe az adószámot.    
    

### Mit tegyek, ha a vevőm adószámát a rendszer érvénytelennek minősíti?

A Bizottság webhelye valós idejű információkkal szolgáló rendszer, amely a tagállamok által működtetett adatbázisok segítségével ellenőrzi az adószámok érvényességét. Amikor tehát Ön a rendszerben ellenőriz egy adószámot, azt tulajdonképpen a tagállami adatbázison keresztül ellenőrzi.

Ha a rendszer azt jelzi ki, hogy az Ön vevőjének uniós adószáma érvénytelen, a probléma rendezése érdekében forduljon annak az országnak az adóhatóságához, ahol vevőjének székhelye található.

### Mit tegyek, ha a rendszer nem működik?

A Bizottság webhelye valós idejű információkkal szolgáló rendszer, amely a tagállamok által működtetett adatbázisok segítségével ellenőrzi az adószámok érvényességét. Amikor tehát Ön a rendszerben ellenőriz egy adószámot, azt tulajdonképpen a tagállamiadatbázison keresztül ellenőrzi.

Előfordulhat, hogy a rendszer bizonyos időszakokban, a tagállami adatbázisok karbantartása miatt egyes lekérdezéseket nem tud végrehajtani.

A Bizottság tud erről a problémáról, és azon munkálkodik a tagállamokkal együtt, hogy az adatbázisok a lehető legkevesebb ideig legyenek hozzáférhetetlenek karbantartás és frissítés miatt.

### Lekérdezhető-e az adószámhoz tartozó név és cím?

Egyes tagállamok lehetővé teszik, hogy a rendszer megjelenítse az adóalany nevét és címét, ha az uniós adószám érvényes. Ha a név és cím nem jelenik meg, az azt jelenti, hogy az adószámot kibocsátó tagállam nem engedélyezi ezeknek az adatoknak a megjelenítését.

A vevőknek joguk van tájékoztatást kapni az adóhatóságuktól arról, hogy az uniós adószámhoz tartozik-e név és/vagy cím.

### Osztrák adószámok

Ausztriánál a helyes előtag az „AT”. Minden osztrák adószám „U” betűvel kezdődik. Amennyiben tehát egy osztrák adószám érvényességét kívánja ellenőrizni, az „AT” után egy „U” betűt kell begépelnie első karakternek.

### Egy spanyol adószám érvényességét ellenőriztem. A szám érvényes, az adóalany nevét és címét azonban nem jelzi ki a rendszer.

Spanyolország esetán az adószám alapján a név és cím információ nem kérdezhető le.