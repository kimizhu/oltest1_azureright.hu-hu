---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Az Azure Rights Management k&#246;vetelm&#233;nyei
A Microsoft Azure Rights Management (Azure RMS) telepítése a szervezetben, győződjön meg arról, hogy az alábbi előfeltételek. Ezután a [Azure Rights Management – üzembehelyezési menetrend](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) Rights Management telepítéséhez szükséges a szervezet.

|Követelmény|További információ|
|---------------|----------------------|
|Az RMS felhő előfizetés|A szervezet, amely támogatja az RMS felhő előfizetéssel kell rendelkeznie.<br /><br />Licencelési információ: a [Felhő előfizetések, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) című szakaszában talál.|
|Az Azure Active directory|A szervezet az Azure Active directory RMS felhasználói hitelesítés támogatásához kell rendelkeznie. Ezenkívül ha szeretné használni a felhasználói fiókokat a helyszíni címtárból (AD DS), is konfigurálnia kell címtár-integrációt.<br /><br />Ha rendelkezik a szükséges ügyfélszoftvert, és megfelelően konfigurált MFA támogató infrastruktúra többtényezős hitelesítést (MFA) Azure RMS használata támogatott.<br /><br />További információ: a [Az Azure Active directory](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant) című szakaszában talál.|
|Ügyféleszközök|Felhasználók rendelkeznie kell egy ügyfél (számítógép vagy mobileszköz) rendszerű eszközök RMS támogató operációs rendszert.<br /><br />További információ: a [Ügyfél eszközök, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) című szakaszában talál.|
|Alkalmazások|Felhasználók, amelyek támogatják az RMS alkalmazást kell futtatni.<br /><br />További információ: a [Alkalmazások, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) című szakaszában talál.|
|Kapcsolat az internetes és a függő felhőszolgáltatások támogató infrastruktúra|Ha tűzfal vagy hálózati eszközöket, amelyek be kell állítani bizonyos kapcsolatok engedélyezése című államadósság [Office 356 URL-címek és IP-címtartományok](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />A lista az URL-címek és IP-címek a **Office 356 portal- és identitáskezelési** szakasz az Office 365 portálra, Azure Active Directory-erőforrásokat és Azure Rights Management vonatkozik. Ez a cikk a következő témakör utasításait segítségével naprakész állapotban tartani, a változások ezt az információt a RSS-hírcsatorna való előfizetéssel.<br /><br />Mellett az adott Azure RMS Office cikkben szereplő információkat:<br /><br />-   Nem végződhetnek a TLS-ügyfélszolgáltatás kapcsolatot (például a csomag szintű ellenőrzés végrehajtásához). Ezzel a módszerrel működésképtelenné válik a rögzítéshez RMS ügyfelek használhatják a Microsoft által felügyelt hitelesítésszolgáltatók a biztonságossá a kommunikációt az Azure RMS tanúsítványt.<br />-   Ne használjon, amely egy felhasználó nevében hitelesíti a webproxy konfigurálása.|

Ha szeretné az Azure RMS használata a helyszíni kiszolgálók, a következő termékek támogatottak:

-   Exchange-kiszolgáló

-   SharePoint-kiszolgáló

-   Fájl besorolást infrastruktúra támogatja a Windows Server fájlkiszolgálókon

Ebben a forgatókönyvben további Azure RMS követelményeivel kapcsolatos további információkért lásd: a [A helyszíni kiszolgálókon, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers) című szakaszában talál.

> [!IMPORTANT]
> A következő környezet nem támogatott:
> 
> -   AD RMS és Azure RMS-párhuzamos adott szervezet kívül futtató az áttelepítés során a következő témakörben ismertetett módon [Áttelepítés Active Directory tartalomvédelmi szolgáltatások az Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).
> 
> A támogatott áttelepítési útvonal [az Active Directory tartalomvédelmi szolgáltatások az Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx), és a [Azure RMS AD RMS-nek](http://msdn.microsoft.com/library/azure/dn629429.aspx). Ha az Azure RMS telepítése, és ezután eldöntheti, hogy már nem használja a felhőalapú szolgáltatás, lásd: [Leállítására, és az Azure Rights Management inaktiválásáról](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

A következő részekben további tudnivalók az Azure RMS követelményeknek.

## <a name="BKMK_SupportedSubscriptions"></a>Felhő előfizetések, amelyek támogatják az Azure RMS
Azure RMS Alkalmazást használja, a szervezet kell legalább a következő előfizetések elegendő számú licenceit a felhasználók és a szolgáltatások védeni a fájlokat, és az e-mail üzeneteket. Ha olyan szolgáltatás, amely érvényes lesz a felhasználók (a fájlok vagy e-mailek tulajdonosainak) védelmét, ezeket a felhasználókat szükséges egyik ezeket a licenceket. Felhasználók, akik csak fogyaszt (például olvasása és szerkesztése) a védett adatok nem szükséges licenccel.

-   Office 365-höz

-   Az Azure Rights Management Premium (korábbi nevén Azure RMS önálló)

-   A nagyvállalati mobilitási csomaghoz

-   RMS egyéni felhasználók számára

További információ a következő részekben és iratkozzon fel a beállításokat.

Az Azure RMS-képességek a fizetett előfizetés licencelési összehasonlítása, lásd: [Rights Management Services (RMS) összehasonlítás ajánlatok](http://technet.microsoft.com/dn858608).

### Office 365-előfizetés
[30 napos ingyenes próbaverzió: Vállalati E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Ez az előfizetés úgy van kialakítva, a szervezet számára, akik az Office online szolgáltatások, valamint a tartalomvédelmi szolgáltatás, amely használja az Azure RMS használja. Azonban nem minden Office 365-előfizetések Azure RMS foglalják magukban.

|A beállítás licencelés|Office 365 üzleti Essentials|Az Office 365 üzleti Premium|Office 365 Enterprise E1<br /><br />Office 365 oktatási A1|Office 365 Enterprise E3<br /><br />Office 365 oktatási A3<br /><br />Office 365 kormányzati G3|Office 365 Enterprise E4<br /><br />Office 365 oktatási a4-es<br /><br />Office 365 kormányzati G4|Office 365 Enterprise K1|A SharePoint-terv 1<br />SharePoint terv 2|Az Exchange Online terv 1<br />Exchange Online terv 2|
|--------------------------|--------------------------------|--------------------------------|------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|----------------------------|------------------------------------------|-----------------------------------------------------|
|Adatvédelem jogok (IRM)|Nem|Nem|Nem|Igen|Igen|Nem|Nem|Nem|

### Az Azure Rights Management Premium előfizetés
[30 napos ingyenes próbaverzióval](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Ez az előfizetés korábbi nevén Azure RMS önálló és Azure RMS használni szeretne, de nem rendelkezik, amely tartalmazza az Azure RMS előfizetés szervezetek számára tervezték. Például, hogy rendelkezik előfizetéssel az Office 365 üzleti Essentials vagy az Office 365 Enterprise E1, ha ezeket az előfizetéseket kihagyása Azure RMS (lásd a táblázat az előző részben). Az Azure RMS Alkalmazást használja, akkor sikerült vásárolhat előfizetést az Azure Rights Management Premium (, vagy vásároljon egy másik előfizetést, például az Office 365 Enterprise E4, amely tartalmazza az Azure RMS).

További információ: [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Ezt az előfizetést a próbaidőszak 25 felhasználóhoz, ingyenes Azure RMS kipróbálni is kínál. Ha az előfizetés lejárta előtt csere előfizetés vásárlása lásd az alábbi szakasz "Mi történik, amikor a próba-előfizetést lejárnak?"

|A beállítás licencelés|Office 365 üzleti Essentials|Az Office 365 üzleti Premium|Office 365 Enterprise E1<br /><br />Office 365 oktatási A1|Office 365 Enterprise E3<br /><br />Office 365 oktatási A3<br /><br />Office 365 kormányzati G3|Office 365 Enterprise E4<br /><br />Office 365 oktatási a4-es<br /><br />Office 365 kormányzati G4|Office 365 Enterprise K1|A SharePoint-terv 1<br />SharePoint terv 2|Az Exchange Online terv 1<br />Exchange Online terv 2|
|--------------------------|--------------------------------|--------------------------------|------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|----------------------------|------------------------------------------|-----------------------------------------------------|
|Adatvédelem jogok (IRM)|Igen|Yes <sup>1</sup>|Igen|Igen|Igen|Igen|Igen|Igen|
<sup>1</sup> üzleti Premium, valamint az egyes ügyfél korlátozások vonatkoznak: Tartalom védelméhez, és az RMS védett tartalmakat is használjanak az Outlook Web Appjét és az RMS-megosztó alkalmazás használatával. Az Office 365 üzleti Premium minden más Office alkalmazást, amely tartalmazza az Office Online és az ügyfélalkalmazások segítségével védett tartalmakat is alkalmas.

#### <a name="BKMK_TrialExpiryBehavior"></a>Mi történik, amikor lejár a próba-előfizetést?
Ha a próba-előfizetés lejár, nem fogja tudni elérni a próba-előfizetés használatával az Azure RMS által védett tartalom. Azonban ha majd, amely támogatja az Azure RMS előfizetés vásárlása, hozzáférés automatikusan vissza.

Egy elvesztését access lejártakor kivétel Ha szervezete Azure RMS RMS egyének előfizetés előtt használt szerezte be a próba-előfizetést. Ezután a hozzáférést a korábban védett tartalom marad, a próba-előfizetés lejárta után is.

### Nagyvállalati mobilitási csomag előfizetés
[30 napos ingyenes próbaverzióval](http://go.microsoft.com/fwlink/?LinkId=615385)

Ez az előfizetés úgy van kialakítva, a szervezet számára, aki szeretné használni az Azure Active Directory Premium, a Windows Intune és az Azure Rights Management kombinációja. További információ: a [Microsoft nagyvállalati mobilitási áttekintése](http://go.microsoft.com/fwlink/?LinkId=615386).

|A beállítás licencelés|Office 365 üzleti Essentials|Az Office 365 üzleti Premium|Office 365 Enterprise E1<br /><br />Office 365 oktatási A1|Office 365 Enterprise E3<br /><br />Office 365 oktatási A3<br /><br />Office 365 kormányzati G3|Office 365 Enterprise E4<br /><br />Office 365 oktatási a4-es<br /><br />Office 365 kormányzati G4|Office 365 Enterprise K1|A SharePoint-terv 1<br />SharePoint terv 2|Az Exchange Online terv 1<br />Exchange Online terv 2|
|--------------------------|--------------------------------|--------------------------------|------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|----------------------------|------------------------------------------|-----------------------------------------------------|
|Adatvédelem jogok (IRM)|Igen|Yes <sup>1</sup>|Igen|Igen|Igen|Igen|Igen|Igen|
<sup>1</sup> üzleti Premium, valamint az egyes ügyfél korlátozások vonatkoznak: Tartalom védelméhez, és az RMS védett tartalmakat is használjanak az Outlook Web Appjét és az RMS-megosztó alkalmazás használatával. Az Office 365 üzleti Premium minden más Office alkalmazást, amely tartalmazza az Office Online és az ügyfélalkalmazások segítségével védett tartalmakat is alkalmas.

### RMS személyeknek az előfizetéshez
Ezt az előfizetést az Azure RMS vagy Active Directory tartalomvédelmi szolgáltatások még nem telepített szervezetén belül készült. Olvassa el a szervezet által használt Azure RMS által védett tartalom címzetteknél segítségével, és is tudja védeni a saját tartalmat.

További információ: [RMS egyének és az Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## <a name="BKMK_AzureADTenant"></a>Az Azure Active directory
Egy Azure AD-címtárba Azure RMS Alkalmazást használó kell rendelkeznie. A könyvtár a szervezet fiók használatával jelentkezzen be a Azure felügyeleti portálon, amelyen, például konfigurálása és a Rights Management sablonok kezelése.

Ha már nincs Azure-előfizetés a szervezet, beszerezheti egy próba-előfizetésre regisztrál.: Nyissa meg a [Azure beolvasása lépések](https://account.windowsazure.com/organization) lapon, és kövesse az utasításokat.

További információkért tekintse meg az Azure Active Directory dokumentációjának következő erőforrásai:

-   [Mi az Azure AD-címtárba?](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Ismerteti az Azure-előfizetéseket társított Azure AD](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Ha szeretné-e az Azure Active directory integrálása a helyszíni AD-erdővel, lásd: [címtár-integráció](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Ha a mobileszközök és Mac számítógépek hitelesíteni a helyszíni AD FS-t vagy egy egyenértékű hitelesítésszolgáltató használatával:
> 
> -   A minimális kiszolgálói verzióját kell használnia az AD FS **Windows Server 2012 R2**, vagy egy másik hitelesítési szolgáltató, amely támogatja az OAuth 2.0-s protokoll.

### <a name="BKMK_MFA"></a>Többtényezős hitelesítést (MFA) és Azure RMS
Használandó többtényezős hitelesítést (MFA) az Azure RMS van szükség, legalább egy, a következő:

-   Office 2013 (minimális verzió):

    -   Office 2013 akkor is telepítenie kell a [2015. június 9., frissítse az Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). További információ a frissítés, és hogyan modern hitelesítést az Active Directory hitelesítési könyvtár ADAL-alapú bejelentkezési kelti Office 2013, lásd: [Office 2013 modern hitelesítést nyilvános előzetes bejelentette](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)  az Office blog a.

-   A Rights Management megosztóalkalmazás Windows:

    -   A 1.0.1908.0, amely megerősíti használja a Vezérlőpult Programok és szolgáltatások minimális verziója van telepítve. A megosztóalkalmazás kapcsolatos további információkért lásd:  [Rights Management Megosztóalkalmazás Windows](../Topic/Rights_Management_Sharing_Application_for_Windows.md).

-   Rights Management megosztóalkalmazást a mobileszközök és Mac számítógépek:

    -   Győződjön meg arról, hogy rendelkezik-e telepítve a legújabb verzióra. A multi-factor Authentication támogatási került, az RMS-megosztó alkalmazás 2015. szeptember kiadásában.

Ezután konfigurálja a multi-factor Authentication megoldás:

-   A Microsoft által felügyelt bérlők számára (kell Azure Active Directoryban, vagy az Office 365):

    -   Konfigurálja az Azure MFA többtényezős hitelesítés kényszerítése a felhasználók számára. Útmutatásért lásd: [Ismerkedés az Azure multi-factor Authentication a felhőben](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) származó az Azure dokumentációjában.

        Az Azure multi-factor Authentication kapcsolatos további információkért lásd: [Mi az Azure multi-factor Authentication?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)

-   Az összevont bérlők (működési összevonási kiszolgálók helyszíni):

    -   Az összevonási kiszolgálók konfigurálása az Azure Active Directoryban, vagy az Office 365. Például ha az AD FS-t használ, tekintse át [további hitelesítési módszerek konfigurálása az AD FS](https://technet.microsoft.com/library/dn758113.aspx) a TechNet webhelyén.

        Ebben a forgatókönyvben kapcsolatos további információkért lásd:  [a működik, és az Office 365 – identitás program most kiforrott](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) az Office blog a.

## <a name="BKMK_SupportedDevices"></a>Ügyfél eszközök, amelyek támogatják az Azure RMS
Az alábbi szakaszok segítségével azonosíthatja, hogy mely eszközöket támogatja az Azure Rights Management (RMS), és mely RMS szolgáltatásait támogatja:

-   [Számítógépek](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [Mobileszközök](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [Ügyfél eszközképességek](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Számítógépek
A következő számítógép operációs rendszereket támogatja az Azure Rights Management:

-   **Windows 7** (x 86, x 64)

-   **Windows 8** (x 86, x 64)

-   **Windows 8.1** (x 86, x 64)

-   **Windows 10** (x 86, x 64)

-   **Mac OS X**: Mac OS X 10.8 (hegyi Lion) legalacsonyabb verziója

### <a name="BKMK_RMSSupportedMobileDevices"></a>Mobileszközök
A következő mobileszköz operációs rendszereket támogatja az Azure Rights Management:

-   **Windows Phone**: Windows Phone 8.1

-   **Android telefonok és táblagépek**: Minimális verzió az Android 4.0.3

-   **iPhone és iPad**: Az iOS 7.0 minimális verzió

-   **Windows RT táblagép**: A Windows 8 RT, Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>Ügyfél eszközképességek
Nem minden támogatott ügyfél-eszköz jelenleg minden RMS képességek támogatja. Az alábbi táblázat segítségével azonosíthatja, hogy mely alkalmazások támogatják az RMS képességek és a kivételeket.

Hiányában a támogatott képességek vonatkoznak, Azure RMS és AD RMS-e. Emellett az AD RMS-támogatást az iOS, Android, az operációs rendszer X és Windows Phone 8.1 szükséges [Active Directory Rights felügyeleti szolgáltatások mobil eszköz bővítmény](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341).

A táblázat oszlopainak kapcsolatos információk:

-   **Védett PDF**: Fájlok, amelyek rendelkeznek egy .ppdf kiterjesztésű, és automatikusan létrehozott Office-fájlok és a PDF-fájlok megosztása az RMS-megosztó alkalmazás használatakor e-mailben. Az RMS-megosztó alkalmazás egy védett PDF-fájlok olvasó tartalmazza. Korábban létrehozott Azure RMS vagy Active Directory tartalomvédelmi szolgáltatások használatával védett PDF-fájlokat, ha folytathatja olvasni ezeket a fájlokat, a Windows, iOS és Android-eszközök Foxit olvasó és Nitro Pro használatával.

-   **E-mail:** Az e-mail ügyfelek felsorolt védheti az e-mailt, amely az összes csatolt fájlt védi automatikusan. Ebben az esetben az ügyfél előzetes szolgáltatás megjelenítheti a védett tartalomhoz (üzenet és melléklet) hitelesített címzettek. Azonban ha e-mailben saját magát nem védett, de a melléklet védett, az ügyfél előzetes szolgáltatás nem tudja megjeleníteni a hitelesített címzettek védett mellékletet.

-   **Más fájltípusok**: Szöveg-és képfájlok például .txt, .xml, .jpg, és jpeg fájlnévkiterjesztéssel rendelkező fájlokat tartalmazza. Ezeket a fájlokat a fájlnévkiterjesztés módosítása után a natív módon RMS által védett, és csak olvashatóvá válik. Nem natív módon védett fájlok .pfile fájlnévkiterjesztés RMS általános védelemmel rendelkező. További információ: a [védelmi szintek – natív és általános](https://technet.microsoft.com/library/dn339003.aspx) és [támogatott fájltípusok és fájlnévkiterjesztések](https://technet.microsoft.com/library/dn339003.aspx) a szakasz a [Rights Management megosztóalkalmazás rendszergazdai útmutatója](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**Eszköz operációs rendszere**|A Word, Excel, PowerPoint|Védett PDF-fájl|E-mailek|Más fájltípusok|
|----------------------------------|-----------------------------|-------------------|------------|-------------------|
|**Windows**|Az Office 2010<br /><br />Office 2013<br /><br />Office mobilalkalmazások (csak az Azure RMS)<sup>1</sup><br /><br />Office Online<sup>2</sup>|Gaaiho Doc<br /><br />Az Adobe GigaTrust asztali PDF-ügyfél<br /><br />Foxit olvasó<br /><br />Nitro PDF-olvasó<br /><br />RMS-megosztó alkalmazás|Az Outlook 2010<br /><br />Az Outlook 2013<br /><br />Az Outlook Web App (OWA)<br /><br />A Windows Mail<sup>3</sup>|RMS-megosztó alkalmazás Windows: Szöveg, kép, fájl párbeszédpanele<br /><br />A Siemens JT2Go: JT fájlok (csak Windows 10)|
|**iOS**|IPhone és iPad Office<sup>4</sup><br /><br />Office Online<sup>2</sup><br /><br />TITUS dokumentumok|Foxit olvasó<br /><br />RMS-megosztó alkalmazás<sup>1</sup><br /><br />TITUS dokumentumok|NitroDesk<br /><br />IPhone és iPad Outlook<sup>3</sup><br /><br />Az iOS OWA<br /><br />Biztonságos szigetek IQProtector<sup>1</sup><br /><br />TITUS Mail|RMS-megosztó alkalmazás<sup>1</sup>: Szöveg, kép, fájl párbeszédpanele<br /><br />TITUS dokumentumok: Fájl párbeszédpanele|
|**Android**|Android alkalmazás GigaTrust<br /><br />Office Online<sup>2</sup>|Android alkalmazás GigaTrust<br /><br />Foxit olvasó<br /><br />RMS-megosztó alkalmazás<sup>1</sup>|9Folders<br /><br />Android alkalmazás GigaTrust<br /><br />NitroDesk<br /><br />Android OWA<sup>5</sup><br /><br />Samsung E-mail (S3 és újabb verziók)<br /><br />Biztonságos szigetek IQProtector<sup>1</sup><br /><br />A mobileszköz TITUS besorolása|RMS-megosztó alkalmazás<sup>1</sup>: Szöveg, kép, fájl párbeszédpanele|
|**AZ OPERÁCIÓS RENDSZER X**|Office 2011 (csak az AD RMS)<br /><br />A Mac Office 2016<br /><br />Office Online<sup>2</sup>|Foxit olvasó<br /><br />RMS-megosztó alkalmazás<sup>1</sup>|Az Outlook 2011 (csak az AD RMS)<br /><br />Az Outlook 2016 for Mac<br /><br />Az Outlook Mac|RMS-megosztó alkalmazás<sup>1</sup>: Szöveg, kép, fájl párbeszédpanele|
|**Windows RT**|Office 2013 RT<br /><br />Office Online<sup>2</sup>|Nem támogatott|Az Outlook 2013 RT<br /><br />A Windows Posta alkalmazásban<br /><br />A Windows Mail<sup>3</sup>|A Siemens JT2Go: JT fájlok|
|**Windows Phone 8.1**|Office Mobile (csak az AD RMS)|RMS-megosztó alkalmazás<sup>1</sup>|Az Outlook Mobile|RMS-megosztó alkalmazás<sup>1</sup>: Szöveg, kép, fájl párbeszédpanele|
|**BlackBerry 10**|Nem támogatott|Nem támogatott|BlackBerry e-mail<sup>3</sup>|Nem támogatott|
<sup>1</sup> támogatja a védett tartalom megtekintése.

<sup>2</sup> támogatja a SharePoint online-hoz, a OneDrive az üzleti és az Outlook Web Access védett tartalom megtekintése.

<sup>3</sup> használja az Exchange ActiveSync IRM, amelyet az Exchange-rendszergazda engedélyezni kell. Felhasználók megtekintése, válasz, és nem tudja biztosítani az összes védett e-mailek, de a felhasználók maguk új e-mailek válasz.

<sup>4</sup> támogatja megtekintésére és szerkesztésére védett dokumentumokat. További információkért lásd a következő hozzászólás meg az Office blog: [Az Azure Rights Management támogatási iPhone és iPad Office származik.](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>5</sup> további információ: a következő hozzászólás az Office blog meg: [OWA Android most már elérhető a jelölje ki az eszközöket](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> A különböző platformok irodában esedékes RMS támogatásával kapcsolatos további információkért lásd a következő hozzászólás a az Office blog: [Office mindenhol, titkosítási mindenhol](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Alkalmazások, amelyek támogatják az Azure RMS
A következő alkalmazások natív módon támogatja az Azure RMS, ami azt jelenti, hogy RMS szorosan integrálva van ezeket az alkalmazásokat támogató felhasználási korlátozás RMS API-k használatával. Ezek az alkalmazások is ismert az RMS-kompatibilis:

-   **A Microsoft Office alkalmazások** (Word, Excel, PowerPoint és az Outlook) a következő programcsomagok a tartalom segítségével megvédheti Azure RMS:

    -   Office 365 ProPlus

    -   Office 365 Enterprise E3

    -   Office 365 Enterprise E4

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Az Office (kivételével Office 2007) más kiadásai felhasználhat védett tartalmakat.

    > [!NOTE]
    > Az Azure RMS Office Professional Plus 2010 vagy az Office Professional 2010:
    > 
    > -   A Rights Management megosztóalkalmazás Windows igényel
    > -   Nem támogatott a Windows 10

-   **A Rights Management megosztóalkalmazás Windows rendszerhez**

    A Windows Rights Management megosztóalkalmazás kapcsolatos további információkért lásd a következőket:

    -   [A Rights Management megosztóalkalmazás rendszergazdai útmutatója](http://technet.microsoft.com/library/dn339003.aspx)

    -   [A Rights Management megosztóalkalmazás felhasználói útmutatója](http://technet.microsoft.com/library/dn339006.aspx)

-   **A Rights Management megosztóalkalmazás mobil platformokon**

    A Rights Management megosztóalkalmazás mobil platformok kapcsolatos további információkért lásd a következőket:

    -   Töltse le a megfelelő alkalmazás a hivatkozásokra a [Microsoft Rights Management lap](http://go.microsoft.com/fwlink/?LinkId=303970)

    -   Mobileszközök kezelése a Microsoft Intune esetén telepítheti és konfigurálhatja az alkalmazás a [iOS és Android rendszerű, a házirend által kezelt alkalmazás](https://technet.microsoft.com/library/dn878026.aspx).

    -   [Gyakran ismételt kérdések a Microsoft Rights Management Megosztóalkalmazás mobil platformok](http://technet.microsoft.com/dn451248)

-   **Más alkalmazásokat, amelyek támogatják az RMS API-k**:

    -   Az RMS SDK használatával házon belül írt az üzletági alkalmazások

    -   Az RMS SDK használatával írt szoftvergyártók alkalmazások

    Az SDK-val kapcsolatos további információkért tekintse meg a [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> A következő alkalmazások jelenleg nem támogatott Azure RMS által:
> 
> -   A Microsoft Office for Mac 2011
> -   Microsoft onedrive vállalati verzió a SharePoint Server 2013
> -   Az XPS-megjelenítő
> 
> Emellett az RMS-megosztó alkalmazás rendelkezik a következő korlátozásokkal:
> 
> -   Windows alapú számítógépek esetén: Windows 7 Service Pack 1 vagy újabb verziója szükséges.

Hogyan támogatja ezeket az alkalmazásokat az Azure RMS kapcsolatos további információkért lásd: [Hogyan alkalmazások támogatják a Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Őket konfigurálásával kapcsolatos további információkért lásd: [Azure Rights Management alkalmazások konfigurálása](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## <a name="BKMK_SupportedServers"></a>A helyszíni kiszolgálókon, amelyek támogatják az Azure RMS
Az Azure RMS-összekötő, mely úgy működik, mint a helyszíni kiszolgálók és az Azure RMS közötti kommunikációs felületet (továbbító) használatakor a következő helyszíni kiszolgálói termékek Azure RMS használata támogatott. Emellett ebben a konfigurációban meg kell adni a Active Directory-erdők között az Azure Active Directory címtár-szinkronizálás.

-   **Exchange Server**:

    -   Az Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Fájlkiszolgálókon, futtassa a Windows Server, és használhatja a fájl besorolást infrastruktúra (FCI)**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Windows Server 2008 R2 rendszerű fájlkiszolgálók nem rendelkezik egy beépített felügyeleti feladat fájlművelet RMS-védelmet alkalmazni, mert az RMS-összekötő nem használható ebben a forgatókönyvben. Azonban használhatja fájl besorolást infrastruktúra és az Azure RMS ezen operációs rendszerek Ha konfigurál egy egyéni felügyeleti feladatot futtatni egy végrehajtható fájl vagy parancsprogram, amely az Azure RMS segítségével védheti meg fájljait. Például Windows PowerShell-parancsfájl, amely használja a [RMS-védelmet parancsmagok](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Ezek a parancsmagok is használata az újabb verzióit futtató Windows Server, az az előnye, hogy ezek a parancsmagok védheti minden fájltípushoz kiszolgálók. Az RMS-összekötő csak az Office-fájlok védelmére. Útmutató útmutatásért lásd: [RMS-védelmi Windows Server fájl besorolás infrastruktúrával &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

Az RMS-összekötő a Windows Server 2012 R2, Windows Server 2012 és Windows Server 2008 R2 esetén támogatott.

Az RMS-összekötő a helyszíni kiszolgálók konfigurálásával kapcsolatos további információkért lásd: [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Lásd még
[Getting Started with Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

