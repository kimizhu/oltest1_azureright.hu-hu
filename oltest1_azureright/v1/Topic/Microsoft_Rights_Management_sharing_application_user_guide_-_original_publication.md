---
description: na
keywords: na
title: Microsoft Rights Management sharing application user guide - original publication
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: 350b6869-084d-4e8a-a4d3-df44a40fa13b
robots: noindex,nofollow
---
# A Microsoft Rights Management megoszt&#243;alkalmaz&#225;s felhaszn&#225;l&#243;i &#250;tmutat&#243;ja – eredeti kiadv&#225;ny
A Windows Microsoft Rights Management megosztóalkalmazás felhasználói útmutatója a következő részekből áll:

-   [Evaluating and Installing Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Eval)

-   [Using Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_UsingMSRMSApp)

-   [Using User-Authored Permissions and Sharing Protected Content](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Custom)

-   [Using the Office Toolbar Add-in](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_OfficeToolbar)

-   [Administrator’s guidance for Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AdminGuide)

A gyakori kérdéseket és a hibaelhárítási tudnivalókat itt találja: [A Windows Microsoft Rights Management megosztóalkalmazással kapcsolatos gyakori kérdések](http://go.microsoft.com/fwlink/?LinkId=303971).

## <a name="BKMK_Eval"></a>A Microsoft Rights Management megosztóalkalmazás kiértékelése és telepítése
Ez a szakasz ismerteti a Microsoft Rights Management megosztóalkalmazás funkcióját és telepítésének módját:

-   [What is the Microsoft Rights Management sharing application?](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_WhatIs)

-   [Requirements for Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Reqs)

-   [Installing the Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Install)

### <a name="BKMK_WhatIs"></a>Mi a Microsoft Rights Management megosztóalkalmazás?
A Microsoft Rights Management megosztóalkalmazás a Microsoft Windowshoz opcionálisan letölthető alkalmazás, amely a következő funkciókkal rendelkezik:

-   A Windows 7 és annak korábbi verzióiban Windows Explorerként is ismert Fájlkezelőben lehetővé teszi egy fájl különálló,vagy több fájl együttes védelmét, valamint egy kiválasztott mappa fájljainak védelmét is.

-   Támogatást nyújt bármely fájltípus védelméhez, valamint beépített nézőkét biztosít a leggyakrabban használt szöveg- és képfájltípusokhoz.

-   Új gombokkal bővíti ki a Word, PowerPoint és Excel programban megtalálható Microsoft Office-eszköztárat.

### <a name="BKMK_Reqs"></a>A Microsoft Rights Management megosztóalkalmazás követelményei
A Microsoft Rights Management megosztóalkalmazást csak Windows 8.1-et, Windows 8-at, vagy Windows 7-et futtató számítógépen használhatja.

A Microsoft Rights Management megosztóalkalmazás csak a telepítőcsomag részeként telepített AD RMS-ügyfél 2.1-es verziójával működik. A Microsoft Rights Management megosztóalkalmazás csak az AD RMS-ügyfél ezen verziójával működik.

### <a name="BKMK_Install"></a>A Microsoft Rights Management megosztóalkalmazás telepítése
A Microsoft Rights Management megosztóalkalmazást a következőképpen telepítheti:

1.  Nyissa meg a [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) lapot a Microsoft webhelyén.

2.  A **Számítógépek** szakaszban kattintson az **RMS alkalmazás Windows rendszerhez** ikonra, és mentse le a Microsoft Rights Management megosztóalkalmazás telepítőcsomagját a számítógépére.

3.  Kattintson duplán a letöltött tömörített fájlra, majd kattintson duplán a **setup.exe** fájlra. Ha a telepítő az engedélyét kéri a folytatáshoz, kattintson az **Igen** gombra.

4.  A **Microsoft RMS telepítése** lapon kattintson a **Tovább** lehetőségre, és várja meg, amíg a telepítés befejeződik.

5.  A telepítés befejeztével kattintson az **Újraindítás** gombra a számítógép újraindításához és a telepítés befejezéséhez. Vagy kattintson a **Bezárás** gombra, és a telepítés befejezéséhez később indítsa újra számítógépét.

## <a name="BKMK_UsingMSRMSApp"></a>A Microsoft Rights Management megosztóalkalmazás használata
Ebben a szakaszban a Microsoft Rights Management megosztóalkalmazás különböző felhasználási módjait ismerheti meg:

-   [Creating a protected text (.ptxt) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_CreatePTXT)

-   [Viewing a protected text (.ptxt) or a protected image file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ViewPTXT)

-   [Creating a generic protected (.pfile) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_CreatePFILE)

-   [Viewing a generic protected (.pfile) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ViewPFILE)

-   [Removing protection from a file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Unprotect)

### <a name="BKMK_CreatePTXT"></a>Védett szövegfájl (.ptxt) létrehozása
A Microsoft Rights Management megosztóalkalmazással egy hagyományos szövegfájlt (.txt) átalakíthat védett szövegfájllá (.ptxt).

##### Védett szövegfájl (.ptxt) létrehozása

1.  A Fájlkezelőben kattintson a jobb gombbal egy mappában, kattintson az **Új** pontra, majd kattintson a **Szöveges dokumentum** parancsra.

2.  Nevezze át a fájlt (például Minta.txt-re).

3.  Kattintson duplán a fájlra, és nyissa meg a Jegyzettömbben.

4.  A Jegyzettömbben az alábbi módon írjon pár sor szöveget a fájlba, majd mentse el:

    ```
    This is a sample text file.
    This is a sample text file.
    This is a sample text file.
    This is a sample text file. 
    This is a sample text file.
    This is a sample text file.
    ```

5.  Kattintson a jobb gombbal a fájlra, majd a **Helyi védelem** lehetőségre, és válasszon egy sablont a listából. (Ne feledje, hogy ha első alkalommal használja az eszközt, akkor **A vállalat által megadott engedélyek** lehetőségre kattintva indíthatja el szervezete saját sablonjainak letöltését.)

6.  A **Microsoft Rights Management megosztóalkalmazás** képernyőn erősítse meg az alkalmazni kívánt házirendet, kattintson az **Alkalmaz** gombra, majd miután a fájl védetté vált, kattintson a **Bezárás** gombra.

### <a name="BKMK_ViewPTXT"></a>Védett szövegfájl (.ptxt) vagy védett képfájl megtekintése
Egy védett szövegfájl (.ptxt) megtekintéséhez a Fájlkezelőben kattintson duplán a fájlra (például a Minta.txt-re). Előfordulhat, hogy a jogok megszerzéséhez hitelesítenie kell az alkalmazást. A védelmi házirend a fájl elején jelenik meg.

A védett képeket hasonló módon nyithatja és tekintheti meg.

### <a name="BKMK_CreatePFILE"></a>Általános védelemmel ellátott fájl (.pfile) létrehozása
Az általános védelemmel ellátott (.pfile) fájlformátummal a Microsoft Rights Management megosztóalkalmazás vagy más, RMS-típusú beépített védelmet kínáló alkalmazások által nem támogatott fájltípusokat is általános védelemmel láthatjuk el.

Az általános védelemmel ellátott fájlformátummal például a beépített védelmet jelenleg még nem támogató Microsoft Visióval létrehozott .vsd fájlokat is megvédhetjük.

> [!NOTE]
> Az általános védelemmel ellátott fájlok csak hitelesítéshez biztonságosak. A program hitelesíti a védett fájl (.pfile) használatára jogosult felhasználót, megjeleníti a felhasználó jogait és engedélyeit, azonban ezek érvényüket vesztik, ha a fájlt megnyitják az eredeti formátumában (például ha a .vsd fájlt megnyitják a Visióban). A jogosultsággal nem rendelkező, nem hitelesíthető felhasználók nem nyithatják meg a védett fájlt.

##### Általános védelemmel ellátott fájl (.pfile) létrehozása Visio rajzfájlból (.vsd)

1.  A Fájlkezelőben kattintson a jobb gombbal egy mappában, kattintson az **Új** pontra, majd kattintson az **Új Visio dokumentum** parancsra.

2.  Nevezze át a fájlt (például Minta.txt-re).

3.  A fájlra duplán kattintva nyissa meg a Visióban.

4.  A Visióban adjon elemeket a rajzhoz, majd mentse és zárja be a fájlt.

5.  Kattintson a jobb gombbal a fájlra, majd a **Helyi védelem** lehetőségre, és válasszon egy házirendsablont a listából. (Ne feledje, hogy ha első alkalommal használja az eszközt, akkor **A vállalat által megadott engedélyek** lehetőségre kattintva indíthatja el szervezete saját sablonjainak letöltését.)

6.  A **Microsoft Rights Management megosztóalkalmazás** képernyőn válassza ki az alkalmazni kívánt házirendet, majd kattintson az **Alkalmaz** gombra.

7.  Egy üzenet jelzi, hogy a védett fájl Minta.vsd.pfile néven lett mentve (az eredeti fájl törlődik).

### <a name="BKMK_ViewPFILE"></a>Általános védelemmel ellátott fájl (.pfile) megtekintése
Általános védelemmel ellátott fájlok (.pfile) megtekintéséhez a Fájlkezelőben kattintson duplán az általános védelemmel ellátott (.pfile) fájlra (például a Minta.vsd.pfile fájlra), majd kattintson a **Megnyitás** lehetőségre.

### <a name="BKMK_Unprotect"></a>Fájl védelmének eltávolítása
A Microsoft Rights Management megosztóalkalmazással eltávolíthatja az előzőleg védelem alá helyezett fájlok védelmét.

Egy előzőleg védelem alá helyezett fájl védelmének eltávolításához (azaz a védelem megszüntetéséhez) az alábbiak szerint alkalmazza a **Védelem eltávolítása** lehetőséget:

1.  Kattintson a jobb gombbal a **Minta.ptxt** fájlra, mutasson a **Helyi védelem** pontra, és válassza a **Védelem eltávolítása** parancsot. Előfordulhat, hogy a jogok megszerzéséhez hitelesítenie kell az alkalmazást.

2.  A Minta.ptxt törlődik, helyére a Minta.txt fájl kerül.

## <a name="BKMK_Custom"></a>A felhasználó által létrehozott engedélyek felhasználása és védett tartalmak megosztása
Ebből a szakaszból megtudhatja, hogyan tehet védetté és használhat egy fájlt a felhasználó által létrehozott engedélyekkel, hogyan oszthat meg védett tartalmakat, és hogyan tehet védetté egyszerre több fájlt:

-   [Protecting a file with user-authored permissions](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ProtectCustom)

-   [Consuming files that have user-authored protection](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_UserDefined)

-   [Sharing protected content](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ShareProtected)

-   [Using keyboard shortcuts](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AccessKeys)

-   [Applying protection to multiple files and folders](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Multiple)

### <a name="BKMK_ProtectCustom"></a>Fájl védelme a felhasználó által létrehozott engedélyekkel
A felhasználó által létrehozott védelem a következő célokra használható:

-   Fájlhozzáférés korlátozása, hogy csak az e-mail címmel azonosított egyéni felhasználók adott csoportja férhessen hozzá a fájlhoz.

-   Fájlhasználat korlátozása, hogy csak adott jogok érvényesüljenek (például egy dokumentum csak olvasható legyen).

Ha egy fájl védelmét felhasználó által létrehozott engedélyekkel szeretné biztosítani, kattintson a jobb gombbal a fájlra, mutasson a **Helyi védelem** pontra, és kattintson az **Egyéni engedélyek** parancsra. A következő képernyő fog megjelenni:

![](../Image/ADRMS_MSRMSApp_ProtectCustom.gif)

Adja meg a kiválasztott felhasználók e-mail címét, a csúszka segítségével válassza ki a kívánt engedélyeket, majd kattintson az **Alkalmaz** gombra.

### <a name="BKMK_UserDefined"></a>A felhasználó által létrehozott védelemmel ellátott fájlok felhasználása
A Microsoft Rights Management megosztóalkalmazás által kezelt védett fájlok többségénél sablonalapú védelmi szintek alkalmazása biztosítja majd a védelmet. Azonban lehetséges, hogy a Microsoft Rights Management megosztóalkalmazás a felhasználó által létrehozott védelemmel rendelkező fájlokat is támogatja.

A felhasználó által létrehozott védelemmel a következő módokon védhető meg egy fájl:

-   Fájlhozzáférés korlátozása, hogy csak az e-mail címmel azonosított egyéni felhasználók erősen korlátozott csoportja férhessen hozzá a fájlhoz.

-   Fájlhasználat korlátozása, hogy csak egyetlen engedély érvényesüljön (például egy dokumentum csak nyomtatható legyen).

A szöveg- és képfájlok esetében az ilyen szintű védelemhez szükséges, hogy a szöveg- és képfájlok szerkesztéséhez, mentéséhez vagy korlátozásához használt alkalmazások támogassák az RMS-védelmet, valamint képesek legyenek az AD RMS szoftverfejlesztői készletben található védelmi API-k végrehajtására.

A felhasználó által létrehozott védelemmel ellátott fájlok megtekintésénél az engedélyek némileg eltérőek lesznek; az alábbi mintában látható módon jelennek meg a fájlnál.

Az általános védelemmel ellátott, .pfile formátumú fájlok esetében a felhasználó által létrehozott jogok és engedélyek a fájl védelméhez felhasznált sablon neve helyett a megerősítő képernyőn jelennek meg (a következő ábrán látható módon).

![](../Image/ADRMS_MSRMSApp_SP_ConsumePfile.gif)

### <a name="BKMK_ShareProtected"></a>Védett tartalom megosztása
Tartalom védelméhez és megosztásához kattintson a jobb gombbal a fájlra, majd a **Védett megosztás** parancsra. A következő képernyő fog megjelenni:

![](../Image/ADRMS_MSRMSAPP_SP_ShareProtected.gif)

Adja meg a kiválasztott felhasználók e-mail címét, a csúszka segítségével válassza ki a kívánt engedélyeket, majd kattintson a **Küldés** gombra. Az alkalmazás elindítja az Outlookot, amelyben egy előzetes levélhez csatolva megjelenik a védett fájl. Az eredeti fájl nem lesz védett.

A védett fájlok nem Windowst futtató eszközökön való megtekintését a **Felhasználás engedélyezése minden eszközön** választógombbal engedélyezheti. A felhasználóknak [le kell tölteniük a Microsoft Rights Management megosztóalkalmazást](http://go.microsoft.com/fwlink/?LinkId=303970) az eszközükre.

### <a name="BKMK_AccessKeys"></a>Billentyűparancsok használata
Az **Alt** billentyűt megnyomva megtekintheti az elérhető hívóbetűket. Az **Alt** + hívóbetű kombináció megnyomásával kiválaszthat egy opciót. Például a **Védett megosztás** párbeszédpanelen a hívóbetűk megjelenítéséhez nyomja meg az **Alt** billentyűt, majd nyomja meg az **Alt + E** kombinációt az **E-mailt kérek a dokumentum megnyitási kísérleteiről** lehetőség kiválasztásához.

![](../Image/ADRMS_MSRMSApp_AccessKeys.png)

### <a name="BKMK_Multiple"></a>Több fájl és mappa együttes védelme
A Microsoft Rights Management megosztóalkalmazással egyszerre több fájl is védelem alá helyezhető, például több fájl vagy egy nem védett fájlokat tartalmazó mappa kiválasztásával a Fájlkezelőben.

##### Több fájl vagy egy kiválasztott mappában található összes fájl védelme

1.  A Fájlkezelőben válasszon ki több fájlt, vagy egy védeni kívánt fájlokat tartalmazó mappát.

2.  Kattintson a jobb gombbal a kijelölt mappára vagy fájlokra, mutasson a **Helyi védelem** pontra, és válasszon egy sablont a listából. (Ne feledje, hogy ha első alkalommal használja az eszközt, akkor **A vállalat által megadott engedélyek** lehetőségre kattintva indíthatja el szervezete saját sablonjainak letöltését.)

3.  A **Microsoft Rights Management megosztóalkalmazás** képernyőn ellenőrizze, hogy a fájlok védetté váltak-e.

Ha hibákat észlel, tekintse át [A Windows Microsoft Rights Management megosztóalkalmazással kapcsolatos gyakori kérdések](http://go.microsoft.com/fwlink/?LinkId=303971) című cikket.

## <a name="BKMK_OfficeToolbar"></a>Az Office-eszköztárbővítmény használata
A Microsoft Rights Management megosztóalkalmazás Office-menüszalagba beépülő moduljával közvetlenül a Microsoft Office-ból is védelem alá helyezhet és oszthat meg Word-, PowerPoint- és Excel-fájlokat. A Microsoft Rights Management megosztóalkalmazás indításához kattintson a menüszalagon a **Védett megosztás** lehetőségre.

![](../Image/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

## <a name="BKMK_AdminGuide"></a>Rendszergazdai útmutató a Microsoft Rights Management megosztóalkalmazáshoz
A Microsoft Rights Management megosztóalkalmazás rendszergazdai útmutatója a következő részekből áll:

-   [Microsoft Rights Management sharing application Technical Overview](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AdminOverview)

-   [Supported File Types](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_SupportFileTypes)

-   [Automatic deployment for the Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ScriptedInstall)

### <a name="BKMK_AdminOverview"></a>Technikai tudnivalók a Microsoft Rights Management megosztóalkalmazásról
A Microsoft Rights Management megosztóalkalmazás a Microsoft Windows rendszerre és más platformokra opcionálisan letölthető alkalmazás, amely a következő funkciókkal rendelkezik:

-   Egyetlen fájl vagy több fájl csoportos védelme, valamint egy kiválasztott mappában található összes fájl védelme.

-   Teljes támogatást nyújt bármely fájltípus védelméhez, valamint beépített nézőkét biztosít a leggyakrabban használt szöveg- és képfájltípusokhoz.

-   Az RMS-védelmet nem támogató fájlok általános védelme.

-   Teljes együttműködés az Office Tartalomvédelmi szolgáltatásával (IRM-mel) védett fájlokkal.

-   Teljes együttműködés a SharePoint, az FCI és a támogatott PDF-szerkesztői eszközök segítségével védett PDF-fájlokkal.

A Microsoft Rights Management megosztóalkalmazás az új [AD RMS-ügyfél 2.1 futtatókörnyezetben](http://www.microsoft.com/download/details.aspx?id=38396) fut. Segítségével a felhasználók védelem alá helyezhetik a tartalmakat előre meghatározott, vagy a felhasználó által készített sablonokkal. A vállalati szinten üzembe helyezhető sablonok a vállalat igényei szerint személyre szabhatók. Az AD RMS 2.1 adottságait kihasználó Microsoft Rights Management megosztóalkalmazás egyszerű védelmet és fogyasztói élményt biztosít a végfelhasználóknak.

A Windows Azure AD RMS 2013. októberi kiadása óta az Office 2010-ben alapértelmezett módon védheti és oszthatja meg dokumentumait egy másik vállalat alkalmazottaival, akik a Windows Azure AD RMS segítségével tudják felhasználni azokat. Továbbá, ha a jelen kiadással 2. kriptográfiai módban használja az AD RMS-t, akkor az RMS segítségével elérheti egy másik, Windows Azure AD RMS-t használó vállalat alkalmazotti tartalmait is. További információ a 2. kriptográfiai módról: [Az AD RMS kriptográfiai módjai](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

A Microsoft Rights Management megosztóalkalmazást a következőképpen töltheti le:

1.  Microsoft-fiókjával (korábban Live ID) jelentkezzen be a [Microsoft Connect](http://connect.microsoft.com/) webhelyre.

2.  A **Kezdőlap** lapon keressen rá a **Rights Management Services** kifejezésre, és csatlakozzon a csoporthoz.

3.  Válassza a **Letöltések** lehetőséget, és kattintson a **Microsoft Rights Management megosztóalkalmazás** lehetőségre.

4.  A **Letöltés részletei** lapon válassza a **Microsoft Rights Management sharing application.zip** elemet, és kattintson a **Letöltés** gombra.

5.  Ha szükséges, telepítse a Microsoft File Transfer Manager alkalmazást, és a lépéseket követve töltse le a Microsoft Rights Management megosztóalkalmazást.

#### A Microsoft Rights Management megosztóalkalmazás által támogatott védelmi szintek
A Microsoft Rights Management megosztóalkalmazás két különböző szintű védelmet támogat, amelyek részleteit az alábbi táblázat tartalmazza.

||||
|-|-|-|
|Védelem típusa|Natív|Általános|
|Leírás|A szöveg- és képfájlok, a Microsoft Office- (Word, Excel, PowerPoint) fájlok, a .pdf fájlok és az egyéb, AD RMS-t támogató fájltípusok esetében a natív védelem erős szintű védelmet biztosít, amelybe beletartozik a titkosítás és a jogok (engedélyek) érvényesítése is.|Minden más alkalmazás és fájltípus esetében általános szintű védelem biztosított, ami magában foglalja a .pfile típusú fájlbeágyazást, valamint a hitelesítést, amellyel ellenőrizhető, hogy egy felhasználó jogosult-e a fájl megnyitására.|
|Védelem|A fájlok teljesen titkosítottak, a védelem pedig a következő módokon érvényesül:<br /><br />-   A fájlt e-mailben megkapó, vagy a fájlhoz fájl- vagy megosztóengedélyekkel hozzáférő felhasználóknak sikeresen hitelesíteniük kell magukat a védett fájl megtekintése előtt.<br />-   Ezenkívül ha a tartalom egy IP megtekintőben (a védett szöveg- és képfájlok esetében) vagy egy társított alkalmazásban (minden más támogatott fájltípus esetében) kerül megjelenítésre, a fájl védelem alá helyezésekor a tartalom tulajdonosa által beállított használati engedélyek és házirend is érvényesítésre kerül.|A fájlvédelem a következő módokon érvényesül:<br /><br />-   A fájl megnyitásához szükséges engedéllyel és hozzáféréssel rendelkező ügyfeleknek sikeresen hitelesíteniük kell magukat a védett fájl megtekintése előtt. Ha a hitelesítés sikertelen, a fájl nem nyitható meg.<br />-   Megjelennek a fájl védelem alá helyezésekor a tartalom tulajdonosa által beállított használati engedélyek és a házirend, amelyekből a hitelesített felhasználók megismerhetik az alkalmazni kívánt használati házirendet.<br />-   Naplózásra kerül minden alkalom, amikor a hitelesített felhasználók megnyitnak vagy elérnek egy fájlt, azonban a támogatást nem biztosító alkalmazások nem érvényesítenek használati jogokat.|
|Fájltípusonkénti alapértelmezés|A következő fájltípusokhoz tartozó alapértelmezett szintű védelem:<br /><br />-   Szöveg- és képfájlok<br />-   Microsoft Office-fájlok (Word, Excel, PowerPoint)<br />-   Portable document format (.pdf)<br /><br />További információt a Támogatott fájltípusok szakaszban talál.|Ez az alapértelmezett védelem minden egyéb, a teljes védelem által nem támogatott fájltípus esetén (mint például .vsdx, .rtf stb.).|

### <a name="BKMK_SupportFileTypes"></a>Támogatott fájltípusok
A következő táblázat a Microsoft Rights Management megosztóalkalmazás által támogatott fájltípusokat tartalmazza.

|Fájlkiterjesztés|Leírás|Eredeti fájlkiterjesztés|
|--------------------|----------|----------------------------|
|.ptxt|Védett szövegfájl|.txt|
|.pxml|Védett XML-fájl|.xml|
|.pjpg|Védett JPG képfájl|.jpg|
|.pjpeg|Védett JPEG képfájl|.jpeg|
|.ppng|Védett PNG képfájl|.png|
|.ptiff|Védett TIFF képfájl|.tiff|
|.pbmp|Védett Windows bitkép fájl|.bmp|
|.pgif|Védett GIF képfájl|.gif|
|.pgiff|Védett GIFF képfájl|.giff|
|.pjpe|Védett JPE képfájl|.jpe|
|.pjfif|Védett JFIF képfájl|.jfif|
|.pjif|Védett JIF képfájl|.jif|
A következő táblázat a Microsoft Office 2013, Office 2010 és Office 2007 által támogatott fájltípusokat tartalmazza. Két védőelemtípus létezik: az MsoIrmProtector és az OpcIrmProtector. További információ a védőelemtípusokról: [A Microsoft Office fájlformátumvédő elemei](http://archive.msdn.microsoft.com/OfficeProtectors).

|||
|-|-|
|Az MsoIrmProtector védőelem a következő fájltípusokat támogatja:<br /><br />-   doc<br />-   dot<br />-   xla<br />-   xls<br />-   xlt<br />-   pps<br />-   ppt|Az OpcIrmProtector védőelem a következő fájltípusokat támogatja:<br /><br />-   docm<br />-   docx<br />-   dotm<br />-   dotx<br />-   xlam<br />-   xlsb<br />-   xlsm<br />-   xlsx<br />-   xltm<br />-   xltx<br />-   xps<br />-   potm<br />-   potx<br />-   ppsx<br />-   ppsm<br />-   pptm<br />-   pptx<br />-   thmx|

### <a name="BKMK_ScriptedInstall"></a>A Microsoft Rights Management megosztóalkalmazás automatikus központi telepítése
Az RMS-megosztó alkalmazás Windows-verziója támogatja a parancsfájlból történő telepítést, épp ezért kiválóan alkalmas a vállalati központi telepítéshez.

##### Az RMS-megosztó alkalmazás letöltése automatikus központi telepítéshez

1.  Nyissa meg a Microsoft letöltőközpontjában a [Microsoft Windows Rights Management megosztóalkalmazás lapját](http://www.microsoft.com/en-us/download/details.aspx?id=40857), és kattintson a **Letöltés** gombra.

2.  Válassza ki és töltse le a szükséges fájlokat. Két ügyféltelepítő csomag létezik: egy a 64 bites Windowshoz (Microsoft Rights Management sharing application x64.zip), és egy másik a 32 bites Windowshoz (Microsoft Rights Management sharing application x86.zip).

3.  Bontsa ki a fájlokat a tömörített telepítőcsomagokból (ezt például a fájlokra duplán kattintva teheti meg). Ezután a kibontott fájlokat másolja fel egy olyan hálózati helyre, amely az ügyfélszámítógépek számára is hozzáférhető.

Az RMS-megosztó alkalmazás telepítőcsomagja különböző központi telepítési forgatókönyveket támogat, és a következőket tartalmazza:

|Leírás|Központi telepítési forgatókönyv|
|----------|------------------------------------|
|Microsoft Online bejelentkezési segéd|A következőkhöz szükséges:<br /><br />-   Office 2010 és Windows Azure RMS|
|Az Office gyorsjavítása (KB 2596501)|A következőkhöz szükséges:<br /><br />-   Office 2010 és Windows Azure RMS|
|A 2. kriptográfiai mód gyorsjavítása (KB 2627273)|A következőkhöz szükséges:<br /><br />-   Office 2010 és Windows Azure RMS|
|Az AD RMS-ügyfél és az RMS-megosztó alkalmazás|A következőkhöz szükséges:<br /><br />-   Office 2013 és Windows Azure RMS<br />-   Office 2010 és Windows Azure RMS<br />-   Office 2013 és Active Directory RMS<br />-   Office 2010 és Active Directory RMS<br />-   Az RMS-megosztó alkalmazás frissítése|
|Office-menüszalagbővítmény|A következőkhöz szükséges:<br /><br />-   Office 2013 és Windows Azure RMS<br />-   Office 2013 és Active Directory RMS<br />-   Office 2010 és Active Directory RMS<br />-   Az RMS-megosztó alkalmazás frissítése|
|Windows Azure Active Directory tartalomvédelmi előkészítő eszköz|A következőkhöz szükséges:<br /><br />-   Office 2010 és Windows Azure RMS|
> [!NOTE]
> Az **Office 2010 és Windows Azure RMS** forgatókönyvnél lehetséges, hogy a Windows Azure RMS-t vagy az Active Directory RMS-t használja, de szeretne biztonságosan dokumentumokat küldeni egy Windows Azure RMS-t használó vállalatnak.
> 
> Ha az Office 2010 támogatásához telepíti a Windows Azure Active Directory tartalomvédelmi előkészítő eszközt, ez két dolgot eredményez:
> 
> -   A beállításjegyzéket úgy módosítja, hogy az támogassa az RMS-megosztó alkalmazást.
> -   Csatlakoztatja a felhasználót, ami azt jelenti, hogy a számítógép kapcsolatba lép az AD RMS kiszolgálóval vagy a Windows Azure RMS-sel, és beszerzi a számítógép és a felhasználó számára az RMS használatához szükséges tanúsítványokat.

Az alábbi eljárásokkal a következő központi telepítési forgatókönyvek esetén beazonosíthatja az RMS-megosztó alkalmazás központi telepítéséhez szükséges parancsokat:

-   Office 2013 és Windows Azure RMS

-   Office 2010 és Windows Azure RMS

-   Office 2013 vagy Office 2010 és Active Directory RMS

-   Az RMS-megosztó alkalmazás frissítése

A parancsokban szereplő példák feltételezik, hogy a letöltött és kibontott fájlokat felmásolta egy hálózati megosztóhelyre, amelyhez az ügyfélszámítógépek a **\\server5\apps\rms** elérési úton férhetnek hozzá, valamint hogy az ügyfélszámítógépeken már létezik egy **C:\Log files** nevű mappa, ahol az alkalmazástelepítési naplófájlokat tárolja. Minden telepítésnél kiválaszthatja a telepítési naplófájl nevét, de a fájl .log kiterjesztésű kell legyen.

> [!IMPORTANT]
> Az RMS-megosztó alkalmazás központi telepítése előtt az eljárások során elő kell készítenie a szükséges parancsokat, hogy azok a számítógép környezetében minden felhasználó számára helyi rendszergazdai jogosultságokkal települjenek. A csomagot ezután bármely megszokott alkalmazástelepítési mechanizmussal (Csoportházirenddel vagy a System Center Configuration Managerrel) telepítheti a számítógépekre.
> 
> Ez alól kivétel a Windows Azure Active Directory tartalomvédelmi előkészítő eszköz, ugyanis ezt a számítógép minden felhasználójánál le kell futtatni egyszer, és a beállításjegyzék sikeres módosításához a futtatást magasabb szintű rendszerjogosultságokkal kell végrehajtani. Ez többféleképpen is megvalósítható, többek között a felhasználókat meg lehet kérni a parancs futtatására (például egy e-mailben elküldött vagy az ügyfélszolgálat portálján elhelyezett hivatkozással), vagy a parancsot egyszerűen hozzáadhatja a bejelentkezési parancsfájlhoz. Ha a felhasználók nem rendelkeznek helyi rendszergazdai fiókkal, és ezért nem tudja használni a runas parancsot, léteznek olyan telepítési eszközök, amelyek az Ön által megadott szabályok szerint automatikusan jogosultságszintre emelnek egy parancsot.

##### Az RMS-megosztó alkalmazás telepítése Office 2013 és Windows Azure RMS alá

1.  A következő parancsokkal telepítheti az AD RMS-ügyfelet és az RMS-megosztó alkalmazást:

    -   64 bites Windows esetén: x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "&lt;a naplófájl elérési útja és neve&gt;"

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   32 bites Windows esetén:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Például: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  A következő parancsokkal telepítheti az Office-beépülőmodult:

    -   Az Office 64 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > A telepítés befejezéséhez indítsa újra a számítógépet. A shutdown /i paranccsal például automatikus újraindítást kezdeményezhet.

    Például: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsoffice.log"`

##### Az RMS-megosztó alkalmazás telepítése Office 2010 és Windows Azure RMS alá

1.  A következő parancsokkal telepítheti a Microsoft Online bejelentkezési segédet:

    -   64 bites Windows esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "<log file path and name >"
        ```

    -   32 bites Windows esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "<log file path and name>"
        ```

    Például: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "C:\Log files\assistant.log"`

2.  A következő parancsokkal telepítheti az Office-gyorsjavítást:

    -   Az Office 64 bites verziója esetén:

        ```
        x64\office2010-kb2596501-fullfile-x64-glb.exe /norestart /quiet /log:"<log file path and name >"
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        x86\office2010-kb2596501-fullfile-x86-glb.exe /norestart /quiet /log:"<log file path and name>"
        ```

    Például: `\\server5\apps\rms\x64\office2010-kb2596501-fullfile-x64-glb.exe /norestart /quiet /log:"C:\Log files\kb2596501install.log"`

3.  A következő parancsokkal telepítheti az 2. kriptográfiai mód gyorsjavítását:

    -   64 bites Windows esetén:

        ```
        wusa.exe /norestart /quiet "x64\Windows6.1-KB2627273-v4-x64.msu" /log:"<log file path and name >"
        ```

    -   32 bites Windows esetén:

        ```
        wusa.exe /norestart /quiet "x86\Windows6.1-KB2627273-v4-x86.msu" /log:"<log file path and name>"
        ```

    Például: `\\server5\apps\rms\wusa.exe /norestart /quiet "x64\Windows6.1-KB2627273-v4-x64.msu" /log:"C:\Log files\kb267273.log"`

4.  A következő paranccsal telepítheti az AD RMS-ügyfelet és az RMS-megosztó alkalmazást:

    -   64 bites Windows esetén:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name >"
        ```

    -   32 bites Windows esetén:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Például: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

5.  A következő parancsokkal telepítheti az Office-beépülőmodult:

    -   Az Office 64 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > A telepítés befejezéséhez indítsa újra a számítógépet. A shutdown /i paranccsal például automatikus újraindítást kezdeményezhet.

    Például: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsoffice.log"`

6.  A Windows Azure Active Directory tartalomvédelmi előkészítő eszköz telepítése a következő parancs bejelentkezési parancsfájlokhoz való hozzáadásával:

    > [!IMPORTANT]
    > A parancs sikeres futtatásához a felhasználónak helyi rendszergazdai jogosultságokkal kell rendelkeznie.

    -   64 bites Windows 8 esetén:

        ```
        x64\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   32 bites Windows 8 esetén:

        ```
        X86\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   64 bites Windows 7 esetén:

        ```
        x64\win7\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   32 bites Windows 7 esetén:

        ```
        X86\win7\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    > [!NOTE]
    > Lehetséges, hogy a parancs a Windows Azure hitelesítő adatai megadására kéri a felhasználót. Ha a számítógép egyetlen tartománynak sem tagja, mindenképpen meg kell adni az adatokat. Ha a számítógép egy tartomány tagja, akkor lehetséges, hogy az eszköz fel tudja használni a gyorsítótárazott hitelesítő adatokat.

    Például: `\\server5\apps\rms\x64\aadrmprep.exe /initiateMe /logfile "C:\Log files\aadrmprepinstall.log"`

##### Az RMS-megosztó alkalmazás telepítése Office 2013 vagy Office 2010 és Windows Azure RMS alá

1.  A következő parancsokkal telepítheti az AD RMS-ügyfelet és az RMS-megosztó alkalmazást:

    -   64 bites Windows esetén:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   32 bites Windows esetén:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Például: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  A következő parancsokkal telepítheti az Office-beépülőmodult:

    -   Az Office 64 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > A telepítés befejezéséhez indítsa újra a számítógépet. A shutdown /i paranccsal például automatikus újraindítást kezdeményezhet.

    Például: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

##### Az RMS-megosztó alkalmazás frissítése

1.  A következő paranccsal telepítheti az AD RMS-ügyfelet és az RMS-megosztó alkalmazást:

    -   64 bites Windows esetén:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   32 bites Windows esetén:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Például: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  A következő parancsokkal telepítheti az Office-beépülőmodult:

    -   Az Office 64 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > A telepítés befejezéséhez indítsa újra a számítógépet. A shutdown /i paranccsal például automatikus újraindítást kezdeményezhet.

    Például: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

#### <a name="BKMK_verifyscripted"></a>A telepítés sikerességének ellenőrzése
A telepítési naplófájlokban ellenőrizheti egy telepítés sikerességét.

###### A Microsoft Online bejelentkezési segéd sikeres telepítésének ellenőrzése

-   A telepítés sikerességének ellenőrzéséhez keresse meg a következő szöveget a telepítési naplófájlban: **Installation success or error status: 0**

    Egy sikeres telepítésből származó példasorok:

    **MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins -- Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. Product Name: Microsoft RMS Office Addins. Product Version: 1.0.7. Product Language: 1033. Manufacturer: Microsoft. Installation success or error status: 0.**

###### Az Office-gyorsjavítás sikeres telepítésének ellenőrzése

-   A telepítés sikerességének ellenőrzéséhez keresse meg a következő szöveges karakterláncok bármelyikét a telepítési naplófájlban:

    -   Az Office 64 bites verziója esetén:

        -   **office2010-kb2596501-fullfile-x64-glb.exe exited with status SUCCESS**

        -   **office2010-kb2596501-fullfile-x64-glb.exe exited with status NOTAPPLICABLE**

    -   Az Office 32 bites verziója esetén:

        -   **office2010-kb2596501-fullfile-x86-glb.exe exited with status SUCCESS**

        -   **office2010-kb2596501-fullfile-x86-glb.exe exited with status NOTAPPLICABLE**

###### A 2. kriptográfiai módhoz tartozó gyorsjavítás sikeres telepítésének ellenőrzése

-   A telepítés sikerességének ellenőrzéséhez keresse meg a következő szöveges karakterláncok bármelyikét a telepítési naplófájlban:

    -   64 bites Windows esetén:

        -   **Windows6.1-KB2627273-v4-x64.msu exited with status SUCCESS**

        -   **Windows6.1-KB2627273-v4-x64.msu exited with status NOTAPPLICABLE**

    -   32 bites Windows esetén:

        -   **Windows6.1-KB2627273-v4-x86.msu exited with status SUCCESS**

        -   **Windows6.1-KB2627273-v4-x86.msu exited with status NOTAPPLICABLE**

###### Az AD RMS-ügyfél és az RMS-megosztó alkalmazás sikeres telepítésének ellenőrzése

-   A telepítés sikerességének ellenőrzéséhez keresse meg a következő szöveget a telepítési naplófájlban: **Installation success or error status: 0**

    Egy sikeres telepítésből származó példasorok:

    **MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1 -- Installation completed successfully.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer installed the product. Product Name: Active Directory Rights Management Services Client 2.1. Product Version: 1.0.1179.1. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.**

###### Az Office beépülő modul sikeres telepítésének ellenőrzése

-   A telepítés sikerességének ellenőrzéséhez keresse meg a következő szöveget a telepítési naplófájlban: **Installation success or error status: 0**

    Egy sikeres telepítésből származó példasorok:

    **MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins -- Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. Product Name: Microsoft RMS Office Addins. Product Version: 1.0.7. Product Language: 1033. Manufacturer: Microsoft. Installation success or error status: 0.**

###### A Windows Azure Active Directory tartalomvédelmi előkészítő eszköz sikeres telepítésének ellenőrzése

-   A telepítés sikerességének ellenőrzéséhez keresse meg a következő szöveget a telepítési naplófájlban: **aadrmprep.exe exited with status SUCCESS**

    > [!NOTE]
    > Egyes esetekben a telepítés kétszer is lefuthat, ekkor az első alkalommal sikertelen, a második alkalommal pedig sikeres lesz.

A következő parancsokkal ellenőrizheti manuálisan az eszköz által végrehajtott beállításjegyzék-módosításokat:

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

    "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

    "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

    @="&lt;tanúsítási URL-cím&gt;"

-   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

    DefaultUser="&lt;alapértelmezett_felhasználó&gt;"

#### <a name="BKMK_uninstallscripted"></a>Eltávolítási parancsok
Az üzembe helyezéshez szükséges telepítési parancsok közül nem mindegyik támogatja az eltávolítási parancsokat. Az alábbi parancsokkal a következő elemeket távolíthatja el: az AD RMS-ügyfelet és a megosztóalkalmazást, valamint az Office beépülő modult.

###### Az AD RMS-ügyfél és az RMS-megosztó alkalmazás eltávolítása

-   Az alábbi parancsokat használja:

    -   64 bites Windows esetén:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   32 bites Windows esetén:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

###### Az Office beépülő modul eltávolítása

-   Az alábbi parancsokat használja:

    -   Az Office 64 bites verziója esetén:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## Lásd még
[Microsoft Rights Management megosztóalkalmazás letöltése (http://go.microsoft.com/fwlink/?LinkId=303970)](http://go.microsoft.com/fwlink/?LinkId=303970)
 [A Windows Microsoft Rights Management megosztóalkalmazással kapcsolatos gyakori kérdések](http://go.microsoft.com/fwlink/?LinkId=303971)

