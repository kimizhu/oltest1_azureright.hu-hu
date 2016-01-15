---
description: na
keywords: na
title: Configuring Custom Templates for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
---
# Az Azure Rights Management egy&#233;ni sablonok konfigur&#225;l&#225;sa
Azure Rights Management (Azure RMS) aktiválása után felhasználók képesek automatikusan könnyen házirendek alkalmazása, amelyek a hozzáférés korlátozása a szervezet jogosult felhasználók bizalmas fájlokat két alapértelmezett sablonok használatával. Ezek a sablonok két rendelkezik a következő jogosultságokkal házirendi korlátozásokkal:

-   A védett tartalomhoz csak olvasható megtekintése

    -   Megjelenítendő név: **&lt; név &gt; - csak bizalmas nézet**

    -   Adott engedély: Tartalom megtekintése

-   Olvassa el, vagy módosítsa az engedélyeket a védett tartalomhoz

    -   Megjelenítendő név: **&lt; név &gt; - bizalmas**

    -   Adott engedélyek: Tartalom megtekintését, mentse a fájlt, tartalom szerkesztése, hozzárendelt jogok megtekintése, válasz mindenkinek makrói, előre, válasz, engedélyezése

Emellett a [RMS-megosztó alkalmazás](http://technet.microsoft.com/library/dn339006.aspx) lehetővé teszi, hogy a felhasználók saját engedélyek beállításainak megadása. És az Outlook ügyfélprogram és az Outlook Web Access jelölhetők ki a **nem továbbítható** beállítást az e-mailek.

A számos szervezet az alapértelmezett sablonokat is elegendő lehet. Azonban ha azt szeretné, házirend-sablonok létrehozása a saját egyéni jogokat, azt megteheti. Egyéni sablonok okok a következők:

-   Azt szeretné, hogy a sablon egy részét az összes felhasználó helyett a szervezet felhasználói jogosultságokat.

-   Csak a felhasználók számára, és válasszon ki egy sablont (részlegek sablon) alkalmazások ahelyett, hogy a szervezet tekintse meg az összes felhasználó részhalmazát kívánja, és kiválaszthatja a sablont.

-   Szeretné jobbra egy sablont, megtekintése és módosítása, például az egyéni határozza meg, de nem másolja, és nyomtassa ki.

-   További beállítások konfigurálása a sablonban, többek között a lejárati dátumot, hogy a tartalom elérhető internetkapcsolat nélkül szeretné.

A felhasználók kijelölheti egyéni például ezeket a beállításokat tartalmazó sablon meg kell először hozzon létre egy egyéni sablont, konfigurálja és közzéteszi az.

Az alábbi szakaszok segítségével könnyebben konfigurálható és egyéni sablonokkal:

-   [Hogyan lehet létrehozni, konfigurálni és egyéni sablon közzététele](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToConfigureCustomTemplates)

-   [A sablon másolása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)

-   [(Archívum) sablonok eltávolítása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToArchiveTemplates)

-   [A felhasználók sablonok frissítése](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)

-   [A Windows PowerShell-hivatkozás](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_PowerShellTemplates)

## <a name="BKMK_HowToConfigureCustomTemplates"></a>Hogyan lehet létrehozni, konfigurálni és egyéni sablon közzététele
Hozzon létre, és az Azure felügyeleti portálon egyéni sablonok kezelése. Ehhez használhatja közvetlenül az Azure felügyeleti portálról, vagy jelentkezzen be az Office 365 felügyeleti központban, és adja meg a **speciális szolgáltatásai** Rights Management, mely majd irányítja az Azure felügyeleti portálon.

Az alábbi eljárások segítségével létrehozni, konfigurálni és egyéni sablonok közzététele a Rights Management.

#### Egyéni sablon létrehozása

1.  Attól függően, hogy bejelentkezik az Office 365 felügyeleti központban, vagy az Azure portálon tegye a következők valamelyikét:

    -   Az a [Office 365 felügyeleti központban](https://portal.office.com/):

        1.  Kattintson a bal oldali ablaktáblában **szolgáltatás beállításai**.

        2.  Az a **szolgáltatás beállításai** lap **a rights management**.

        3.  Az a **adatai védelme** részen kattintson **kezelése**.

        4.  Az a **a rights management** részen kattintson **speciális szolgáltatásai**.

            > [!NOTE]
            > Ha még nem aktiválta a Rights Management, előbb kattintson **aktiválása** és erősítse meg a műveletet. További információ: [Az Azure Rights Management aktiválása](../Topic/Activating_Azure_Rights_Management.md).
            > 
            > Kattintott még nem **speciális szolgáltatásai** előtt, a Rights Management aktiválása után kövesse a képernyőn megjelenő utasításokat lekérni egy ingyenes Azure-előfizetést, amely az Azure portál eléréséhez szükséges.

            Lehetőségre kattintva **speciális szolgáltatásai** betölti az Azure-portálon, ahol kezelheti **RIGHTS MANAGEMENT** a szervezet Azure Active Directory.

    -   Az a [Azure-portálon](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  A bal oldali ablaktáblában kattintson a **az ACTIVE DIRECTORY**.

        2.  Az a **az active directory** lapra, kattintson a **a RIGHTS MANAGEMENT**.

        3.  Válassza ki a directory Rights Management kezeléséhez.

        4.  Ha még nem aktiválta a Rights Management, kattintson a **AKTIVÁLÁSA** és erősítse meg a műveletet.

            > [!NOTE]
            > További információ: [Az Azure Rights Management aktiválása](../Topic/Activating_Azure_Rights_Management.md).

2.  Hozzon létre egy új sablont:

    -   Az Azure-portálon a a **Ismerkedés a Rights Management** gyors start lap, kattintson a **Hozzon létre egy új jogmegadási sablon**.

        Ha nem azonnal láthatók a lapon az Office 365 utasítások végrehajtása után járjon navigációs, fent, az Azure portálon.

3.  Az a **hozzáadása egy új jogmegadási sablon** lapon, válassza ki, amelyben meg fog írja be a sablon neve és leírása, amelyet a felhasználók nyelv (később is hozzáadhatja több nyelvet). Adjon egyedi nevet és egy leírást, majd a Kész gombra.

Az a **Ismerkedés a Rights Management** gyors start lap, kattintson a gombra **a jogmegadási sablonok kezelése**. Látni fogja az újonnan létrehozott sablon sablonok állapotú listájára felvett **Archivált**. Ebben a szakaszban a sablont létrehozni, de nincs beállítva, és nem látható a felhasználók számára.

#### Konfigurálása és egyéni sablon közzététele

1.  Válassza ki az újonnan létrehozott sablont a **SABLONOK** lap az Azure felügyeleti portálon.

2.  A a **hozzá lett adva a sablon** gyors start lap, kattintson a **első lépések** 1,. lépésben **engedélyeit a felhasználók és csoportok konfigurálása** kattintson **az INDULÁSHOZ** vagy **hozzáadása**, majd válassza ki a felhasználókat és csoportokat, akihez a jogok a tartalmat az új sablon által védett.

    > [!NOTE]
    > A felhasználók vagy csoportok, akkor jelölje be az e-mail címet kell rendelkeznie. Éles környezetben ez az eset szinte mindig lesz, de egy egyszerű tesztelési környezetben szükség lehet e-mail címeket hozzá felhasználói fiókokat vagy csoportokat.

    A bevált gyakorlat használata helyett felhasználók egyszerűbbé teszi a sablonok felügyeleti csoportok. Ha rendelkezik helyszíni Active Directory és az Azure AD szinkronizál, a levelezési csoportok, amelyek a biztonsági csoportokat vagy a terjesztési csoportok is használhatja. Azonban ha azt szeretné, a szervezet minden felhasználója engedélyek, lesz hatékonyabb másolja az alapértelmezett sablonok valamelyikét adja meg a több csoport helyett. További információ: a [A sablon másolása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates) című szakaszában talál.

    > [!TIP]
    > Később felhasználókat adhat át a sablon a szervezeten kívüli használatával a [Azure Rights Management Windows PowerShell-modul](https://technet.microsoft.com/library/jj585012.aspx) és a következő módszerek egyikével:
    > 
    > -   **Exportálási, szerkesztése és a frissített sablon importálása**:  Ez a legegyszerűbb módszer a külső felhasználók hozzáadása egy meglévő sablont, amely tartalmazza az egyéb csoportok. Használja a [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) sablon exportálása parancsmag egy. Szerkesztheti a külső e-mail címek, ezek a felhasználók és a meglévő csoportok és a jogok jogainak hozzáadása CSV-fájl. Ezután a [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) Azure RMS térni parancsmaggal importálja ezt a módosítást.
    > -   **Használja a jogok definiáló objektum-sablonok frissítése**:    Adja meg a külső e-mail címek és a jogok a jogok definíció objektum, amely ezután használhatja a sablont frissítése. A jogok definiáló objektum használatával adja meg a [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) parancsmag segítségével hozzon létre egy változót, és adja meg az - RightsDefinition paramétert a változót a [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) parancsmaggal módosíthat egy meglévő sablont. Azonban ezek a felhasználók hozzáadása egy meglévő sablont, akkor is meg kell jogok definíció objektumok a meglévő csoportok definiálása a sablonok és nem csak az új, a külső felhasználók.

3.  Kattintson a Tovább gombra, majd rendelje hozzá a felsorolt engedélyekkel a kijelölt felhasználók és csoportok egyikét.

    További információ az egyes jogok (és egyéni engedélyek), használja a megjelenített leírása. Részletesebb információkat is érhető el a [Használati jogok konfigurálása az Azure Rights Management](../Topic/Configuring_Usage_Rights_for_Azure_Rights_Management.md). RMS támogató alkalmazások esetében azonban változó lehet, hogy hogyan végrehajtsa ezeket a jogokat. Tekintse át a dokumentációt, és hajtsa végre a saját a felhasználók ellenőrzése viselkedését, mielőtt telepítené a felhasználók számára a sablont használó alkalmazások tesztelése. Ez a sablon csak a rendszergazdák számára látható a teszteléshez bizonyosodjon sablon részlegek sablon (6. lépés).

4.  Ha a kiválasztott **egyéni**, kattintson a Tovább gombra, majd válassza ki egyéni ezeket a jogokat.

    Bár az egyéni jogosultságokat, az egyes alkalmazások bármilyen kombinációját képes használni, a vonatkozó bizonyos jogokkal előfordulhat, hogy más egyéni jogosultságai függőségekkel rendelkeznek. Ez a helyzet, amikor a függő jogok is automatikusan kijelöli.

    > [!TIP]
    > Fontolja meg a **másolása és a tartalom kibontása** jobbra, és ez jogot a kijelölt rendszergazdák vagy más szerepkörök, amelyek információt helyreállítási feladatkörök személyzet. Ezt a jogosultságot megadása lehetővé teszi, hogy védelmet, ha szükséges, a fájlok és az e-mailek, amely védi a sablon használatával távolítsa el őket. Ez a sablon szintű védelem eltávolítása biztosít további részletes vezérlési mint felügyelői funkcióval.

5.  A Kész gombra.

6.  Ha azt szeretné, hogy látható legyen a felhasználók csak egy részhalmazát sablonok alkalmazások listájának megjelenésekor a sablont: Kattintson a **hatókör** részlegek sablonként konfigurálásához, majd kattintson a **az INDULÁSHOZ**. Ellenkező esetben folytassa a 9.

    Részlegek sablonokkal kapcsolatos további információk: Alapértelmezés szerint minden felhasználó az Azure könyvtárban, tekintse meg a közzétett sablonokat, és azok is jelölje ki azokat az alkalmazásokat tartalom védelmére szeretne. Ha azt szeretné, hogy csak néhány a közzétett sablonok a meghatározott felhasználókra, ezek a felhasználók a sablonok kell hatókörét. Ezek a felhasználók csak ezt követően kijelölheti ezeket a sablonokat lesz. Amely nem ad meg más felhasználók nem látják a sablonok, és ezért nem választhatja ki azokat. Ezzel a módszerrel teheti a felhasználók, könnyebben megfelelő sablon kiválasztása, különösen akkor, ha azokat a csoportokat vagy osztályok által használandó tervezett sablonokat hoz létre. Majd a felhasználók látni csak a sablonok, amelyek a számukra.

    Például egy sablont a HR-osztály, alkalmazza a csak olvasási engedéllyel a pénzügyi részleg létrehozott. Így csak a HR-részleg tagjai alkalmazhatja a sablon használata a Rights Management megosztóalkalmazás, a sablon az e-mailek Engedélyezve csoporthoz hatókör nevű emberi. Ez a csoport Lásd és is csak tagjai alkalmazza ezt a sablont.

7.  Az a **sablon látható** lapon, jelölje be a felhasználókat és csoportokat, akik fogja tudni érni, és válassza ki a sablont az RMS-kompatibilis alkalmazások. Az előtt, ajánlott eljárásként csoportok használata helyett felhasználók és csoportok vagy felhasználók választja rendelkeznie kell egy e-mail címet.

8.  Kattintson a Tovább gombra, és döntse el, hogy kell-e a részlegek sablon kompatibilitási konfigurálása. Ha rákattint, **KOMPATIBILITÁSI**, jelölje be a jelölőnégyzetet, majd kattintson **teljes**.

    Miért előfordulhat, hogy konfigurálnia kell kompatibilitási? Nem minden alkalmazás részlegek sablonok is támogatja. Ehhez az szükséges, az alkalmazás első hitelesítenie kell az RMS szolgáltatással a sablonok letöltése előtt. Ha a hitelesítési folyamat nem kerül sor, alapértelmezés szerint nincs a részlegek sablonok letöltődnek. Ez a viselkedés felülbírálhatja megadásával, hogy a részlegek sablonok kell letöltenie, az alkalmazás kompatibilitását, és válassza a **Ez a sablon megjelenítése az összes felhasználó számára, ha az alkalmazások nem támogatják a felhasználói identitás** jelölőnégyzetet.

    Például ha nem konfigurálja a részlegek sablon kompatibilitási ebben a példában az emberi erőforrások, csak a felhasználók a HR-részleg megjelenik a részlegek sablon használata az RMS-megosztó alkalmazás, de a felhasználók nem részlegek sablon látható, ha az Outlook Web Access (OWA) az Exchange Server 2013, mivel az OWA Exchange és az Exchange ActiveSync jelenleg nem támogatja részlegek sablonok. Ez az alapértelmezett viselkedés úgy konfigurálja az alkalmazás kompatibilitását bírálja felül, ha csak a felhasználók a HR-részleg részlegek sablon látható, az RMS-megosztó alkalmazás használnak, de minden felhasználó részlegek sablon látható, amikor az Outlook Web Access (OWA) használnak. Felhasználók OWA vagy az Exchange ActiveSync, az Exchange Online használja, ha az összes a felhasználók látni fogják a részlegek sablonok vagy felhasználók nem látják a részleg sablonokat, a sablon állapota (archiváláshoz vagy közzétett) az Exchange Online alapján.

    > [!NOTE]
    > Nincs még natív módon támogató részlegek sablonok alkalmazások akkor is használhatja a [egyéni RMS sablon letöltési parancsfájl](http://go.microsoft.com/fwlink/?LinkId=524506) vagy más eszközök ezeket a sablonokat az RMS-ügyfél helyi mappa telepítéséhez. Ezt követően ezek az alkalmazások megfelelően megjeleníti a részlegek sablonok csak a felhasználók és csoportok, a sablon hatókör kiválasztott:
    > 
    > -   Az Office 2010, az ügyfél-mappa van **%localappdata%\Microsoft\DRM\Templates**.
    > -   Az ügyfélszámítógépről, amely az összes sablon töltött le másolja, és illessze be a sablonfájlokat más számítógépekre.
    > 
    > Office 2016 natív módon támogatja részlegek sablonok, és ezért nem a legújabb frissítések Office 2013 ([KB 3054853](https://support.microsoft.com/kb/3054853)).

9. Kattintson a **KONFIGURÁLÁSA** és adja hozzá a felhasználók a nevét és leírását, a sablon a nyelven együtt használja, további nyelveket. Ha a felhasználók több nyelvet, fontos a minden nyelv használják, és adjon meg egy nevet és leírást a nyelven. Felhasználók megjelenik a nevét és leírását, a sablon nyelvével azonos nyelven, az ügyfél operációs rendszer, amely biztosítja, hogy a dokumentum vagy e-mail üzenet alkalmazott házirend megértik. Ha az ügyfél operációs rendszerrel nem egyezik, neve és leírása látható visszaáll a nyelvet és a leírást, amely a sablon létrehozásakor megadott.

    Ellenőrizze, hogy kívánja-e a következő beállításokat módosíthatja:

    |Beállítás|További információ|
    |-------------|----------------------|
    |**a tartalom elévülési**|Határozza meg a dátum vagy a sablon napok száma, amikor ne nyissa meg a sablon által védett fájlok. Adja meg azt a dátumot, vagy adja meg az időt, amely a fájl érvényben van a védelmi kezdve napok számát.<br /><br />Dátum megadása esetén az időzóna hatékony éjfél.|
    |**kapcsolat nélküli hozzáférés**|Ez a beállítás használatával egyenleg e biztonsági követelmények, hogy rendelkezik szembeni követelmény, hogy a felhasználók kell tudni megnyitni védett fájlokat, ha nincs internetkapcsolat.<br /><br />Ha megadja, hogy a tartalom nem érhető el internetkapcsolat nélkül, vagy tartalom érhető el csak a megadott számú nap, a küszöbérték elérésekor az lehet, hogy újra hitelesített felhasználók és a hozzáférésüket naplózza. Ha ez történik, ha a hitelesítő adatok nem kerülnek a gyorsítótárba, a bejelentkezés előtt tudják nyitni a fájlt a rendszer kéri a felhasználókat.<br /><br />Ismételt hitelesítés mellett a házirendet, és a felhasználói csoport tagsága újra értékelt. Ez azt jelenti, hogy felhasználók működése eltérő hozzáférési eredmények ugyanaz a fájl, ha a házirend és csoporttagsága, amikor azok utolsó érhetők el a fájlt a változtatások vannak.|

10. Ha meggyőződött arról, hogy a sablon megfelelően vannak konfigurálva a felhasználók számára, kattintson a **Közzététel** láthatóvá a sablon a felhasználók számára, és kattintson a **MENTÉS**.

11. Kattintson a Vissza gombra, ha vissza szeretne lépni a kezelési portálon a **SABLONOK** oldal, ahol a sablon most már frissített állapotát **közzétett**.

Ne módosítsa a sablon, és jelölje ki, majd ismét hajtsa végre az első lépések lépéseket. Vagy válassza ki az alábbi lehetőségek egyikét:

-   További felhasználók és csoportok hozzáadása, és adja meg a jogok csoportok és felhasználók számára: Kattintson a **jogok**, majd kattintson az **hozzáadása**.

-   Felhasználók vagy csoportok, a korábban kiválasztott eltávolítása: Kattintson a **jogok**, válassza ki a felhasználót vagy csoportot a listából, és kattintson a **törlése**.

-   Módosításához jelölje ki azokat az alkalmazásokat a sablonok mely felhasználók láthatják: Kattintson a **hatókör**, majd kattintson **hozzáadása** vagy **törlése**, vagy **KOMPATIBILITÁSI**.

-   Láthatóvá a sablon már nem az összes felhasználó számára: Kattintson a **KONFIGURÁLÁSA**, kattintson a **ARCHÍVUM**, és kattintson a **mentése**.

-   Az egyéb konfigurációs módosításokat: Kattintson a **KONFIGURÁLÁSA**, végezze el a változtatásokat, és kattintson a **MENTÉS**.

> [!WARNING]
> Ha módosítja egy korábban mentett sablont, az ügyfelek nem látják ezeket a módosításokat a sablon sablonok a vállalat számítógépein frissítéséig. További információ: a [A felhasználók sablonok frissítése](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates) című szakaszában talál.

## <a name="BKMK_HowToCopyTemplates"></a>A sablon másolása
Ha szeretne létrehozni egy új sablont, amely rendelkezik egy meglévő sablont nagyon hasonlít a beállításokat, jelölje be az eredeti sablonnak a a **SABLONOK** lapján kattintson **MÁSOLÁSI**, adjon meg egy egyedi nevet és a szükséges módosításokat.

> [!IMPORTANT]
> Ha egy sablont másol a **közzétett** vagy **Archivált** állapot bekerül is. Így ha egy közzétett sablon másolása, azonnali állapota lesz közzétéve, amíg nem változtatja meg.

Egyéni és az alapértelmezett sablonok másolhatja. Ajánlott eljárásként másolása helyett egy új egyéni sablont létrehozása, ha azt szeretné, hogy a szervezet minden felhasználója számára jogosultságot adni a sablon az alapértelmezett sablonok valamelyikét. Ez a módszer azt jelenti, hogy nem kell létrehozni, vagy adja meg az összes felhasználó több csoportnak válassza. Ebben a helyzetben azonban nem biztos benne, hogy új nevét és a további nyelveket a másolt sablon leírását adja meg.

## <a name="BKMK_HowToArchiveTemplates"></a>(Archívum) sablonok eltávolítása
Az alapértelmezett sablonok nem lehet törölni, de archiválva, hogy a felhasználók nem látják azokat.

Hasonlóan közzétett rendelkeznek egy egyéni sablont, és már nem szeretné látni, hogy a felhasználók, ha szerkesztheti a sablont, és válassza a **ARCHÍVUM** és **mentése** a a **KONFIGURÁLÁSA** oldalon. Vagy választhatja azt a **SABLONOK** lapon, és válassza **ARCHÍVUM**.

Mivel az alapértelmezett sablonokat archiválására ezeket a sablonokat nem lehet szerkeszteni kell használnia a **ARCHÍVUM** a beállítást a **SABLONOK** lap. Az Outlook nem archiválja **nem továbbítható** beállítást.

#### Alapértelmezett sablon eltávolítása

-   Az a **SABLONOK** lapon válassza ki az alapértelmezett sablont, és kattintson a **ARCHÍVUM**.

A állapota változik **közzétett** a **Archivált**. Ha meggondolja magát, válassza ki a sablont, és kattintson a **Közzététel**.

## <a name="BKMK_RefreshingTemplates"></a>A felhasználók sablonok frissítése
Azure RMS használatakor sablonok automatikusan letöltődnek ügyfélszámítógépekre, hogy a felhasználók közül lehet választani azokat az alkalmazásokat. Azonban szükség lehet további lépéseket, ha módosítja a sablonokat:

|Alkalmazás vagy szolgáltatás|Sablonok módosítása után frissítésének módját|
|--------------------------------|-------------------------------------------------|
|Exchange online-hoz|Manuális konfiguráció sablonok frissítéséhez szükséges.<br /><br />Bontsa ki az alábbi szakasz a konfigurációs lépéseket [Exchange Online csak: Töltse le az Exchange konfigurálása megváltozott egyéni sablonokkal](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_ExchangeOnlineTemplatesUpdate).|
|Office 365-höz|Automatikusan frissülnek – nem szükséges további lépéseket.|
|Office 2016 és Office 2013<br /><br />RMS-megosztó alkalmazás Windows rendszerhez|Automatikusan frissülnek – ütemezés szerint:<br /><br />-   Ezek az Office újabb verziója: Az alapértelmezett frissítési időköze 7 naponta fut.<br />-   Az RMS-megosztó alkalmazás Windows: Az alapértelmezett frissítési időköze 1.0.1784.0 verziójától kezdve, minden nap. Korábbi verziók van egy alapértelmezett frissítési időköze 7 naponta.<br /><br />Az ütemezés hamarabb kikényszeríti, bontsa ki az alábbi szakasz [Office 2016, Office 2013 és az RMS-megosztó alkalmazás Windows: A módosított egyéni sablon frissítése kényszerítése](#BKMK_Office2013ForceUpdate).|
|Az Office 2010|A felhasználók bejelentkezéskor frissíteni.<br /><br />Kikényszeríti, kérje meg, vagy jelentkezzen ki, és jelentkezzen be újra a felhasználókat. Vagy a következő részben [Csak az Office 2010: A módosított egyéni sablon frissítése kényszerítése](#BKMK_Office2010ForceUpdate).|
Az RMS-megosztó alkalmazás használó mobil eszközök sablonok automatikusan letöltődnek (és frissítése, ha szükséges) szükséges további konfiguráció nélkül.

### <a name="BKMK_ExchangeOnlineTemplatesUpdate"></a>Exchange Online csak: Töltse le az Exchange konfigurálása megváltozott egyéni sablonokkal
Felügyeleti szolgáltatás (IRM) már konfigurálta az Exchange online-hoz, ha egyéni sablonok nem letölti a felhasználók mindaddig, amíg módosítja a következő Windows PowerShell használatával az Exchange Online.

> [!NOTE]
> További információ a Windows PowerShell használatáról az Exchange Online: [PowerShell használatával az Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Ez az eljárás minden alkalommal, amikor módosítja egy sablont kell megtennie.

##### Az Exchange Online-sablonok frissítése

1.  A Windows PowerShell használatával az Exchange Online, kapcsolódni a szolgáltatáshoz:

    1.  Adja meg az Office 365 felhasználónevet és jelszót:

        ```
        $Cred = Get-Credential
        ```

    2.  Kapcsolódás az Exchange Online szolgáltatás a következő két parancsok futtatásával:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Használja a [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) parancsmaggal importálja újra a megbízható közzétételi tartomány (TPD) Azure RMS:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Ha például a TPD neve **RMS Online – 1** (jellemző nevét számos szervezet), adja meg: **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > A TPD neve ellenőrzéséhez használja a [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) parancsmagot.

3.  Győződjön meg arról, hogy a sablonok sikeresen importálta, várjon néhány percet, majd futtassa a [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) parancsmag és az összes típust kell beállítania. Példa:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Akkor célszerű megtartani egy másolatot, a kimenet, így egyszerűen másolhatja a sablon nevét, vagy a GUID egy sablont később archiválja.

4.  Minden egyes importált sablont, amelyet az Outlook Web Appjét elérhetőnek kell lenniük, a kell használnia a [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) parancsmag és az elosztott típust kell beállítania:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Mivel az Outlook Web Access gyorsítótárazza a felhasználói felület, 24 órán belül, a felhasználók nem láthatják az új sablon a naponta legfeljebb.

Emellett ha egy sablon archiválja (egyéni vagy alapértelmezett), és használja az Exchange Online és az Office 365, felhasználók továbbra is az archivált sablonok megtekintéséhez, ha az Outlook Web Appjét vagy mobil eszközöket, amelyek az Exchange ActiveSync protokoll használnak.

Úgy, hogy a felhasználók többé nem látja a sablonok, az Exchange Online Windows PowerShell használatával kapcsolódni a szolgáltatáshoz, és ezután a [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) parancsmag a következő parancs futtatásával:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### <a name="BKMK_Office2013ForceUpdate"></a>Office 2016, Office 2013 és az RMS-megosztó alkalmazás Windows: A módosított egyéni sablon frissítése kényszerítése
Office 2016, Office 2013 vagy a Rights Management (RMS) megosztóalkalmazás Windows rendszerű számítógépeken a beállításjegyzék szerkesztésével módosíthatja az automatikus ütemezést, hogy megváltozott-sablonok frissítése számítógépeken gyakrabban az alapértelmezett érték. Az azonnali frissítéshez kényszeríthet a meglévő adatok törlése a beállításazonosítót.

> [!WARNING]
> A Beállításszerkesztő helytelen használata, ha akkor súlyos problémákat okozhat, amelyek az operációs rendszer újratelepítését tehetik szükségessé. A Microsoft nem garantálja, hogy a Beállításszerkesztő nem megfelelő használatából fakadó problémák megoldhatók. A Beállításszerkesztőt saját kockázatára használhatja.

##### Az automatikus ütemezésének módosítása

1.  A beállításjegyzék-szerkesztőben, hozzon létre és egyet a következő beállításazonosítókat:

    -   A frissítés gyakoriságát beállítása a nap (legalább 1 nap):  Hozzon létre egy új beállításazonosító **TemplateUpdateFrequency** és adatok, és módosításokat letöltéséhez letöltött sablon napokban gyakoriságát határozza meg egy egész számot határozza meg. Az alábbi táblázat segítségével megkeresheti a beállításjegyzékbeli elérési utat a új beállításazonosító létrehozásához.

        |A beállításjegyzék elérési útja|Típusa|Érték|
        |-----------------------------------|----------|---------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|A REG_DWORD|TemplateUpdateFrequency|

    -   A frissítés gyakoriságát megadása másodpercben (legalább 1 másodperc):  Hozzon létre egy új beállításazonosító **TemplateUpdateFrequencyInSeconds** és adatok, és minden olyan változás letöltéséhez letöltött sablon másodpercben gyakoriságát határozza meg egy egész számot határozza meg. Az alábbi táblázat segítségével megkeresheti a beállításjegyzékbeli elérési utat a új beállításazonosító létrehozásához.

        |A beállításjegyzék elérési útja|Típusa|Érték|
        |-----------------------------------|----------|---------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|A REG_DWORD|TemplateUpdateFrequencyInSeconds|

    Győződjön meg arról, hozzon létre, és egyet beállításértékek, kettő egyszerre nem. Ha telepítve van, mindkettő **TemplateUpdateFrequency** figyelmen kívül hagyja.

2.  Ha a sablonok az azonnali frissítéshez kényszeríteni kívánja, folytassa a a következő eljárást. Ellenkező esetben indítsa újra az Office alkalmazások és a Fájlkezelőben példányai most.

##### Az azonnali frissítéshez kényszerítése

1.  A Beállításszerkesztő segítségével törli az adatokat a **LastUpdatedTime** értéket. Például előfordulhat, hogy az adatokat jeleníti meg **2015-04-20T15:52**; törlése 2015-04-20T15:52, hogy az adatokat nem jelenik meg. Az alábbi táblázat segítségével megkeresheti a beállításjegyzékbeli elérési utat a beállításérték törlése.

    |A beállításjegyzék elérési útja|Típusa|Érték|
    |-----------------------------------|----------|---------|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; MicrosoftRMS_FQDN &gt; \Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > A beállításjegyzékbeli elérési utat a *&lt; MicrosoftRMS_FQDN &gt;* hivatkozik a Microsoft RMS szolgáltatás teljes Tartománynevét. Ha azt szeretné, ez az érték ellenőrzése:
    > 
    > 1.  Futtassa a [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) Azure RMS parancsmagot. Ha még nem már telepítette a Windows PowerShell modul Azure RMS, tekintse meg a [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 2.  A kimenetben azonosítja a **LicensingIntranetDistributionPointUrl** értéket.
    > 
    >     Példa: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Távolítsa el a értékből **https://** és **/_wmcs/licencelés** a karakterláncból. A többi érték a Microsoft RMS szolgáltatás teljes Tartománynevét. A fenti példában a Microsoft RMS szolgáltatás FQDN lenne a következő értéket:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  A következő mappát, és a benne található összes fájl törlése: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Indítsa újra az Office alkalmazások és a Fájlkezelőben példányai.

### <a name="BKMK_Office2010ForceUpdate"></a>Csak az Office 2010: A módosított egyéni sablon frissítése kényszerítése
Az Office 2010-et futtató számítógépekre a beállításjegyzék szerkesztésével beállíthatja, hogy megváltozott sablonokat számítógépek frissítése nélkül a felhasználók számára, jelentkezzen ki, és a biztonsági értéket. Az azonnali frissítéshez kényszeríthet a meglévő adatok törlése a beállításazonosítót.

> [!WARNING]
> A Beállításszerkesztő helytelen használata, ha akkor súlyos problémákat okozhat, amelyek az operációs rendszer újratelepítését tehetik szükségessé. A Microsoft nem garantálja, hogy a Beállításszerkesztő nem megfelelő használatából fakadó problémák megoldhatók. A Beállításszerkesztőt saját kockázatára használhatja.

##### A frissítési gyakoriság módosítása

1.  A Beállításszerkesztő segítségével hozzon létre egy új beállításazonosító **UpdateFrequency** és adatok, és módosításokat letöltéséhez letöltött sablon napokban gyakoriságát határozza meg egy egész számot határozza meg. Az alábbi táblázat segítségével megkeresheti a beállításjegyzékbeli elérési utat a új beállításazonosító létrehozásához.

    |A beállításjegyzék elérési útja|Típusa|Érték|
    |-----------------------------------|----------|---------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|A REG_DWORD|UpdateFrequency|

2.  Ha a sablonok az azonnali frissítéshez kényszeríteni kívánja, folytassa a a következő eljárást. Ellenkező esetben újraindítja most az Office-alkalmazásait.

##### Az azonnali frissítéshez kényszerítése

1.  A Beállításszerkesztő segítségével törli az adatokat a **LastUpdatedTime** értéket. Például előfordulhat, hogy az adatokat jeleníti meg **2015-04-20T15:52**; törlése 2015-04-20T15:52, hogy az adatokat nem jelenik meg. Az alábbi táblázat segítségével megkeresheti a beállításjegyzékbeli elérési utat a beállításérték törlése.

    |A beállításjegyzék elérési útja|Típusa|Érték|
    |-----------------------------------|----------|---------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  A következő mappát, és a benne található összes fájl törlése: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Indítsa újra az Office-alkalmazásait.

## <a name="BKMK_PowerShellTemplates"></a>A Windows PowerShell-hivatkozás
Minden, ami teheti Azure felügyeleti portálon hozhat létre és kezelhet sablonok végrehajthat a parancssorból, a Windows PowerShell használatával. Emellett is exportálhatja és sablonok, importálja, hogy másolja a bérlők között, vagy végezze el a komplex tulajdonságokat tömeges Szerkesztés sablonok, például a többnyelvű nevét és leírását.

Exportálás is használható, és biztonsági mentése és visszaállítása az egyéni sablonok bevált gyakorlat az importált, rendszeresen biztonsági másolatot készíteni az egyéni sablonokat úgy, hogy nem készült módosítást, ha egyszerűen visszatérhet egy korábbi verziót.

> [!IMPORTANT]
> Windows PowerShell használatával létrehozása és kezelése az Azure RMS jogmegadási sablonok, rendelkeznie kell legalább 2.0.0.0 verzióját a [Azure RMS Windows PowerShell-modul](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Ha korábban telepítette a Windows PowerShell-modul, a következő parancsot egy PowerShell-ablak verziószámának ellenőrzése: `(Get-Module aadrm -ListAvailable).Version`

Telepítési tudnivalókat lásd: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

A parancsmagok létrehozása és kezelése sablonok támogató:

-   [Hozzáadás AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Exportálás-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Importálás-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [Új AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Eltávolítás-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## További lépések
Miután konfigurálta az egyéni sablonok Azure Rights Management, használja a [Azure Rights Management – üzembehelyezési menetrend](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) történő ellenőrzése, hogy további konfigurációs lépéseket forgassa előtt célszerű [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] felhasználók és rendszergazdák. Ha nincs más konfigurációs lépésre meg szeretné tekinteni, [Azure Rights Management használata](../Topic/Using_Azure_Rights_Management.md) a sikeres telepítését támogatja a szervezet működési útmutatást.

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

