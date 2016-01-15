---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# Hogyan alkalmaz&#225;sok t&#225;mogatj&#225;k a Azure Rights Management
Használja a következő információkat a megtudhatja, hogyan a végfelhasználói alkalmazások (például az Office alkalmazások, a Word, Excel, PowerPoint és az Outlook) és a szolgáltatás (például az Exchange és a SharePoint) használhatja a Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] védelme a szervezet adatait:

-   [RMS-megosztó alkalmazás a Windows rendszerhez és a mobil platformokon](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Office-alkalmazásokhoz: Az Excel, a PowerPoint, az Outlook, a Word](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Az Exchange Online és az Exchange-kiszolgáló](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online és a SharePoint-kiszolgáló](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [Fájlkiszolgálók, futtassa a Windows Server, és használja a fájl besorolás infrastruktúra (FCI)](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [Más alkalmazások, amely támogatja az RMS API-k](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> Az alkalmazások és -verziók ellenőrizni, hogy [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) támogatja, olvassa el [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md).

Bizonyos esetekben információk védelméről automatikusan alkalmazza, házirend, amelyeket konfigurál szerint. Például ez a helyzet SharePoint könyvtárak, az osztályozott fájlok és az Exchange átviteli szabályok. Egyéb esetben felhasználók telepítenie kell információk védelméről magukat a saját alkalmazásaikat, sablon kiválasztásával, vagy adott lehetőség választásával. Például ez a helyzet amikor a felhasználó e-mail osztani a fájlt, vagy védelem a fájl hozzáférés korlátozását vagy a kiválasztott felhasználó vagy felhasználók a vállalaton kívülre használatát.

Sablonok megkönnyíti a felhasználók (és a rendszergazdák számára a házirendek konfigurálása) a megfelelő szintű védelmet, és a szervezeten belülről személyek való hozzáférés korlátozása. Bár [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] érkezik két alapértelmezett sablonok, valószínűleg érdemes csökkentésére az időpontokat, amikor egyéni beállítások megadásához rendelkeznek egyéni sablonok létrehozása. További tudnivalókért tekintse meg a [Az Azure Rights Management egyéni sablonok konfigurálása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

A a esetekben, ahol felhasználók kell vonatkozik információk védelme magukat, lennie arra, hogy a szolgáltatásigénylési útmutatásért és útmutatásokat hogyan és mikor ehhez. Az utasításokat az alkalmazást, és az általuk használt verziók az adott kell lennie, és hogyan használják, és az útmutató a mikor és hogyan alkalmazási adatok védelmi kell lennie a saját üzleti megfelelő. További tudnivalókért tekintse meg a [A felhasználók fájlok Azure Rights Management használatával segíti.](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md).

Ezeket az alkalmazásokat, az Azure RMS konfigurálásával kapcsolatos további tudnivalókért tekintse meg [Azure Rights Management alkalmazások konfigurálása](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

> [!TIP]
> Példák és az Azure RMS használó alkalmazások képernyőképek, tekintse meg a [A művelet az Azure RMS: A rendszergazdák és felhasználók lásd](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) a szakasz az [Mi az Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) című témakört.

## <a name="BKMK_SharingAppIntro"></a>RMS-megosztó alkalmazás a Windows rendszerhez és a mobil platformokon
Az RMS-megosztási alkalmazás egy ingyenes, letölthető alkalmazás, amely támogatja az Office 2010 szükséges, de a Windows rendszerű számítógép, a Mac-számítógépek és a mobil eszközök is javasolt. Előnyeit egyik, hogy az alkalmazások és a natív módon nem támogató fájlok általános védelmi tud alkalmazni [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], ami azt jelenti, hogy minden fájl lehet védetté tenni. A különböző védelmi szintekkel kapcsolatos további információkért tekintse meg a [szintű védelmet – natív és általános](http://technet.microsoft.com/library/dn339003.aspx) a szakasz az [a Rights Management megosztási alkalmazás rendszergazdai útmutatójában](http://technet.microsoft.com/library/dn339003.aspx).

Amikor a felhasználók azok a fájlok védelme az RMS használatával megosztó alkalmazásban, is nyomon követhetik, amely azokat a védett dokumentumok, és szükség esetén visszavonni az őket a hozzáférést. Ez azért van így használatával a [hely követési dokumentum](http://go.microsoft.com/fwlink/?LinkId=529562).

A Windows-számítógépek esetében az RMS-megosztó unobtrusively az alkalmazás integrálódik az és növeli az alkalmazások, amelyek a felhasználók már:

-   Az Office bővítmény a Word, a Excel, a PowerPoint és az Outlook telepítve van. Így lehetővé teszi a felhasználók egy **védett megosztás** a menüszalagon, amely meghívja fájlokat kell küldve védelme leggyakrabban használt beállítások könnyen használható párbeszédpanel gombra. Ez a gomb is tartalmaz gyorsan a dokumentum nyomon követése a hely elérésére.

-   Egy új kattintson a jobb gombbal fájl Explorer lehetőséget. Így lehetővé teszi a felhasználók egy **védelem** lehetőséget, amely egy könnyen használható párbeszédpanel beállításokat, amelyek a leggyakrabban egy lemezen tárolt fájlok védelme érdekében meghívja.

-   A megjelenítő megnyitni, amely által védett fájlokat [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. A megjelenítő automatikusan hívják meg, amikor nincs semmilyen más telepített alkalmazás, amely a védett fájl megnyitása sikerült.

-   Az Office 2010, amely lehetővé teszi a Word, Excel, PowerPoint és az Outlook ez alkalmazáscsomagból használata integrációjával biztosítja a háttérkiszolgáló konfigurációs [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Bár az RMS-megosztó alkalmazás Windows le, és egyetlen számítógépre telepített használatával a [a Microsoft Rights Management lap](http://go.microsoft.com/fwlink/?LinkId=303970), egy vállalati központi csendes telepítés és az egyéni konfiguráció is támogatja. További tudnivalókért tekintse meg a következő erőforrások:

-   [A Rights Management megosztási alkalmazás rendszergazda guide](http://technet.microsoft.com/library/dn339003.aspx)

-   [A Rights Management megosztási alkalmazás felhasználói útmutató](http://technet.microsoft.com/library/dn339006.aspx)

Az RMS-megosztó alkalmazás mobileszközök támogatja a gyakran használt mobil eszközök, például iPad és iPhone, Android, Windows Phone és Windows Deréksz. Letölthető az alkalmazás a megfelelő tárolóból, és a ezeket a hivatkozásokat vannak a [a Microsoft Rights Management lap](http://go.microsoft.com/fwlink/?LinkId=303970).

## <a name="BKMK_OfficeAppsIntro"></a>Office-alkalmazásokhoz: Az Excel, a PowerPoint, az Outlook, a Word
Ezek az alkalmazások natív módon támogatja a Rights Management tartalomvédelmi (szolgáltatás IRM) használatával és megadása esetén a felhasználók egy mentett dokumentumot vagy e-mail üzenet küldhető a védelem alkalmazható. Felhasználók sablonokat, vagy válassza a hozzáférési, jogok és használati korlátozások nagyon testreszabott beállításait. Felhasználók beállíthatják például egy fájlt, így is elérhető csak a szervezet, vagy a vezérlő személyek által, hogy a fájl szerkeszthető, vagy csak olvasható korlátozott, vagy megakadályozza, hogy éppen nyomtatott. Időérzékeny fájlokat, a lejárati ideje beállítható, hogy (közvetlenül a felhasználók által vagy sablon alkalmazása) esetében, amikor a fájl többé nem érhetők el. Az Outlook, a felhasználók is választhatja a **nem továbbítandó** adatok szivárgás elkerülése érdekében a lehetőséget.

### <a name="BKMK_ExchangeIntro"></a>Az Exchange Online és az Exchange-kiszolgáló
Az Exchange Online vagy az Exchange Server, ha további információkat tartalmaz a védelmi megoldások információkat jogok tartalomvédelmi (szolgáltatás IRM) integrációs használható:

-   **Exchange ActiveSync Tartalomvédelmi** hogy a mobil eszközök védelmét, és helyet igényelne védett az e-mailek.

-   Az RMS-támogatás a **az Outlook Web App**, hasonlóan az Outlook ügyfélprogramot végrehajtott, a, hogy a felhasználók által sablonok vagy egyéni beállítások megadásával védhető e-mailek, és a felhasználók olvashatják és használja a védett őket küldött e-mailek.

-   **Adatvédelmi szabályok** Outlook ügyfelek számára a megadott címzetteknek, hogy a rendszergazda konfigurálja automatikus alkalmazásához az RMS-sablonok e-mail üzenetek. Például a jogi osztályának belső e-mailek küldése, ha azok a jogi részleg tagjai által csak olvasható és nem továbbítható. Felhasználók, tekintse meg az e-mail üzenet elküldése előtt alkalmazott védelmét, és alapértelmezés szerint azok eltávolíthatja, ha azok úgy dönt, hogy nem szükséges. E-maileket a rendszer elküldés előtt titkosítja. További tudnivalókért tekintse meg a [Outlook adatvédelmi szabályok](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) és [Outlook védelmi szabály létrehozása](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) az Exchange-könyvtárban.

-   **Átviteli szabályok** hogy a rendszergazda konfigurálja alkalmazandó automatikusan RMS-sablonok e-mail üzenetek alapján tulajdonságai, például a feladó, a címzett, az üzenet tárgya és a tartalom. Ezek a koncepció hasonló adatvédelmi szabályok, de nem megadása esetén a felhasználók a védelem megszüntetéséhez, az Outlook Web Access és a mobil eszközök által küldött e-maileket alkalmazható és nem titkosítására e-mailek, mielőtt az ügyféltől jelentkezéseket. További tudnivalókért tekintse meg a [Transport védelmi szabály létrehozása](http://technet.microsoft.com/library/dd302432.aspx) az Exchange-könyvtárban.

-   **Adatvesztés megelőzése (DLP) házirendeket** hogy e-mailek szűrése feltételek csoportja tartalmazza, és megteszi a szükséges bizalmas tartalom (például a személyes adatok vagy a hitelkártyaadatait) adatvesztés megelőzése érdekében. Házirend-tippek észlelésekor érzékeny adatokat, a riasztási számára, hogy alkalmazása az adatok védelme, az e-mailt az információk alapján lehetséges, hogy kell használható. További tudnivalókért tekintse meg a [adatvesztés megelőzése](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) az Exchange-könyvtárban.

-   **Office 365 üzenet titkosítási** hogy használja a szállítási titkosított e-maileket küldeni a vállalaton kívüli személyek szabályok, és az e-mailt az Outlook Web App hasonló illesztő a böngészőben olvasható. A Jótállás kizárása szöveg és a vállalat titkosított e-mailek fejlécében szöveg testreszabása, és még hozzáadása a vállalat emblémáját. További tudnivalókért tekintse meg a [Office 365 üzenet titkosítási](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx) az Office webhely.

Exchange Server használatakor is használhatja az adatok védelme szolgáltatások [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] az RMS-összekötő telepít, amely összekötőként egy továbbító a helyszíni-kiszolgálók és az RMS-felhőalapú szolgáltatás között. További tudnivalókért tekintse meg a [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_SharePointIntro"></a>SharePoint Online és a SharePoint-kiszolgáló
SharePoint Online vagy a SharePoint-kiszolgáló használatakor, információt, lehetővé teszi, hogy a rendszergazdák a listákat és könyvtárak védetté tenni, hogy ha a felhasználó ellenőrzések kimenő dokumentum, a fájl védelmét, hogy csak a hitelesített személyek rights management (szolgáltatás IRM) integrációs megtekinthetik és használhatják a fájl szerint a megadott adatok védelmi házirendek is használhatja. Például a fájl előfordulhat, hogy csak olvasható, tiltsa le az a szöveg másolása, megakadályozza a helyi mentésével és megakadályozza, hogy a fájl nyomtatási.

Egy rendszergazda, a végfelhasználó soha nem mindig alkalmazza a listák és könyvtárak, információk védelme. És az összes dokumentum, hogy a tárolóban levő, és nem egyedi fájlok a lista vagy a könyvtár szintjén alkalmazva.  SharePoint Online használata esetén a felhasználók is alkalmazhat Tartalomvédelmi azok OneDrive üzleti Library.

A Tartalomvédelmi szolgáltatás először engedélyeznie kell a SharePoint rendszerhez. Ezt követően a tartalomvédelmi szolgáltatás megadása egy könyvtár. SharePoint Online és az üzleti OneDrive felhasználók is megadhatja a tartalomvédelmi szolgáltatás a saját üzleti Library OneDrive. SharePoint nem használja a jogok sablonok, bár a SharePoint konfigurációs beállításokat választhatja ki, amely a legjobban felel meg a beállításokat, hogy a sablonok adható meg.

Ha a SharePoint-kiszolgálót használ, az adatok védelme szolgáltatások is használhatja [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] az RMS-összekötő telepít, amely összekötőként egy továbbító a helyszíni-kiszolgálók és az RMS-felhőalapú szolgáltatás között. További tudnivalókért tekintse meg a [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!NOTE]
> Jelenleg nincsenek néhány korlátozások SharePoint tartalomvédelmi szolgáltatás használatakor:
> 
> -   Az alapértelmezett vagy egyéni sablonok, amelyek az Azure portál kezelheti nem használható.
> -   Fájlok, amelyek egy. PPDF a fájlnévkiterjesztést védett PDF-fájlokat nem támogatottak. Az fájlokat, akik rendelkeznek. PDF-fájlnévkiterjesztést, és hogy rendelkezik a rendszer natív módon RMS által védett támogatottak, ha olyan PDF-olvasóra, amely támogatja az RMS natív módon használhatja.
> -   Mobil eszközök a Microsoft Office még nem támogatja a RMS, mert ezeket az eszközöket kell a böngésző segítségével megtekintheti az RMS védett fájlokat, és a fájlok csak olvasható.

Azure RMS felhasználási korlátozás vonatkozik, és dokumentumok adattitkosítás SharePoint letöltésekor, és nem akkor, amikor a dokumentum első SharePoint létrehozott vagy feltölteni a tárba. Hogyan védett dokumentumok letöltése előtt kapcsolatos információkért lásd: [adatok titkosítását a onedrive-on, üzleti és a SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) származó a SharePoint dokumentációja tartalmazza.

További információt az Azure RMS használata a SharePoint tekintse meg a következő hozzászólás a az Office blog: [Újdonságok a tartalomvédelmi szolgáltatás SharePoint és a SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>Fájlkiszolgálók, futtassa a Windows Server, és használja a fájl besorolás infrastruktúra (FCI)
Windows Server fájl besorolás infrastruktúra használatára konfigurálásakor a Fájlkiszolgálói erőforrás-kezelő szolgáltatás vizsgálata a helyi fájlokat, és határozza meg, hogy érzékeny adatokat tartalmaznak. Ez a feltételeknek megfelelő fájlok azok vannak címkével besorolási tulajdonságok, hogy a rendszergazda meghatározása. A fájl besorolás infrastruktúra is megfelelő lépések megtételére automatikus, a besorolás szerint. A következő műveletek közül tartalmazza az információk védelméről alkalmazása használatával [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] és a központi telepítési a Rights Management-összekötő (más néven az RMS-összekötő). Office fájlok majd automatikusan Azure RMS által védett.

Az összes fájltípus védelme érdekében meg szeretné nem használja az RMS-összekötő, de ehelyett a Windows PowerShell parancsfájl futtatása, a parancsmagok használatával a [RMS védelmi eszköz](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

A besorolás házirendek a úgy, hogy a potenciális adatok szivárgás jogosulatlan és engedélyezett felhasználók megakadályozhatja az teljes mértékben konfigurálható, és a magas kiterjeszthető. Akkor is segíthet csökkenteni a hálózati rendszergazdák által az adatszivárgás veszélye, mert, amelyek nem igényelnek a rendszergazdák számára a hozzáférést a fájlokhoz házirendeket konfigurálhat.

Telepítését és konfigurálását az RMS-összekötő Office-fájlokkal kapcsolatos információkért lásd: [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

További tájékoztatást a Windows PowerShell-parancsfájl használata az összes fájltípus [RMS-védelmi Windows Server fájl besorolás infrastruktúrával &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

## <a name="BKMK_APIAppsIntro"></a>Más alkalmazások, amely támogatja az RMS API-k
Az RMS SDK használatával a belső írhatnak sor üzleti alkalmazások natív módon támogatásához [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Hogyan információk védelméről integrálva van-e ezek az alkalmazások attól függ, hogy hogyan írt. Például az integrációs automatikusan alkalmazott előfordulhat, hogy szükséges minimális felhasználói beavatkozás, vagy több testreszabott felület, a felhasználók kérheti információk védelméről alkalmazandó fájlokat beállítások konfigurálása. Az SDK kapcsolatos további információkért tekintse meg a [a Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

Sok szoftver szállítói ehhez hasonlóan, adja meg az alkalmazások tájékoztatási védelmi megoldások, más néven enterprise rights management (ERM) termékek. A népszerű példa, amely támogatja a PDF-olvasó [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] adott platformokhoz. Használható a tábla a [Ügyfél eszközképességek](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) szakasza a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) témakör azonosítja az alkalmazást, amely támogatja az RMS (RMS enlightened alkalmazások), és a webes keresés megvásárlására, vagy töltse le az alkalmazást.

> [!TIP]
> Újonnan kiadott alkalmazások esetében, jelölje be az RMS közösségi csatornák, a felsorolt [Információk és támogatás a Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Lásd még
[Getting Started with Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

