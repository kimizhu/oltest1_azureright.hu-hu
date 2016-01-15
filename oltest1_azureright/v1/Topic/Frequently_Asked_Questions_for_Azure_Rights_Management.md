---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Az Azure Rights Management gyakori k&#233;rd&#233;sek
Bizonyos gyakran ismételt kérdések a Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], más néven Azure RMS:

## Mit kell Azure RMS telepítése, és hogyan do I induláshoz?
Először [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md), melynek a felhő-előfizetési beállítások kapcsolatos információkat, hogyan használhatja a helyszíni kiszolgálók, az Azure RMS, mely telepítési forgatókönyvek jelenleg nem támogatott, mely eszközök és alkalmazások támogatási Azure RMS és hivatkozást Ha módosítania kell az IP-címek és a tűzfalak és proxykiszolgálók tartománynevének listáját. Ellenőrizze a többi témaköre is érdemes a [Getting Started with Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md) szakaszban, hogyan alapszintű ismerete kaphat [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] is a szervezet adatainak védelmében, az alkalmazások működése, és hogyan összehasonlítja a helyszíni Active Directory tartalomvédelmi verzióját, és tanulmányozza a feltételek és a jellemző rövidítések [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Amikor készen áll a saját Azure RMS-ellenőrzésre, vagy telepítenie kell azt a szervezet, kövesse a [Azure Rights Management – üzembehelyezési menetrend](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) lépéseket, és hivatkozásokat is tartalmaz további információkat és az útmutató utasításokat listáját.

Ha további információt, az erőforrások és a támogatási lehetőségekről, tekintse meg a [Információk és támogatás a Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Is Azure RMS is integrálhatja a helyszíni kiszolgálóval?
Igen. Az Azure RMS integrálható a helyszíni kiszolgálók, például az Exchange Server, a SharePoint és a Windows-fájlkiszolgálók. Ehhez használja a [Rights Management összekötő](https://technet.microsoft.com/library/dn375964.aspx). Vagy, ha az Önt érdeklő csak a Windows Server fájl besorolást infrastruktúra (FC) segítségével, használhatja a [RMS-védelmet parancsmagok](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Is szinkronizálni, és az Active Directory tartományi vezérlőket az Azure ad-val a zökkenőmentes hitelesítést élmény a felhasználók számára, például összevonásához használatával [az Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Azure RMS automatikusan állít elő, és kezeli XrML tanúsítványok szükséges, ezért nem használja a egy helyszíni PKI. Hogyan Azure RMS-tanúsítványokat használ, további információ: a [A forgatókönyv Azure RMS működése: Először használja, a tartalom védelmi tartalom fogyasztás](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough) szakasz a [Mi az Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) témakör.

## Az egyes felhasználók Exchange online-hoz és a többi Exchange-kiszolgálón van az Exchange központi hibrid telepítés – Ez az Azure RMS által támogatott?
Feltétlenül és a töltött dolog, a felhasználók tudják zökkenőmentesen védetté tehessék és használhassák a védett e-mailek és a mellékleteket a két Exchange központi telepítések egységességét. Ehhez a konfigurációhoz [Azure RMS aktiválása](https://technet.microsoft.com/library/jj658941.aspx) és [IRM engedélyezése Exchange online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), majd [telepítése és konfigurálása az RMS-összekötő](https://technet.microsoft.com/library/dn375964.aspx) Exchange-kiszolgáló.

## Üzemi környezetben Azure RMS telepíthető, ha a vállalatom majd zárolva van a megoldás vagy elvesztését access tartalmára, amely védi a Microsoft Azure RMS kockázat?
Nem, akkor mindig maradnak az adatok ellenőrzése a, és továbbra is elérhető, akkor is, ha úgy dönt, hogy már nem használja az Azure RMS. További információ: [Leállítására, és az Azure Rights Management inaktiválásáról](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Azonban az Azure RMS-telepítés leszerelése, mielőtt szeretnénk fogadtatásra talál, és miért végzett ezzel a lépéssel megértése. Ha az Azure RMS nem teljesíti az üzleti igényei, ellenőrizze nálunk abban az esetben, ha új funkciók mellett-jövőbeni tervezett, vagy ha vannak olyan alternatív megoldásokat. E-mail üzenet küldése [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) és a Microsoft megvitatni a technikai és üzleti követelmények Boldog lesz.

## Szabályozható, amely a felhasználók Azure RMS segítségével tartalom védelméhez?
Igen, az Azure RMS felhasználói bevezetési vezérlők ebben a forgatókönyvben rendelkezik. További információ: a [Bevezetési vezérlők fázisos központi telepítés konfigurálása](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) szakasz a [Az Azure Rights Management aktiválása](../Topic/Activating_Azure_Rights_Management.md) témakör.

## Felhasználók megakadályozása védett dokumentumok megosztása az adott szervezet?
A legnagyobb előnyeit Azure RMS egyik nélkül explicit megbízhatósági kapcsolatot az egyes fiókpartner-szervezet konfigurálása, mert az Azure AD meg a hitelesítési gondoskodik vállalatok együttműködés támogatja.

Nincs annak megakadályozásához, hogy a felhasználók biztonságosan dokumentumok megosztása az adott szervezetek felügyeleti lehetőség. Például szeretné blokkolja a szervezet, amely nem megbízható, vagy amely versengő üzleti rendelkezik. Védett dokumentumokat küldeni ezeket a felhasználók Azure RMS megakadályozza a szervezetek nem értelmezhető a felhasználók megoszthatják volna a dokumentumok nem védett, mert ez valószínűleg az ebben a forgatókönyvben történjen, utolsó lépésként! Például így nem tudja megállapítani, akik van vállalati bizalmas dokumentumok megosztása ezek a szervezetek teheti a dokumentum (vagy e-mail) Azure RMS által védett a felhasználóknak.

## A vállalatom kívül személlyel megosztása egy védett dokumentumot, ha nem, hogy a felhasználó beolvasása hitelesítésének módját?
Az Azure RMS Azure Active Directory-fiókkal és egy társított e-mail cím mindig felhasználói hitelesítést, amely a rendszergazdák számára teszi a vállalatok együttműködés zökkenőmentes használja. Ha a másik szervezet használja az Azure-szolgáltatásokhoz, felhasználók már rendelkezik fiókok az Azure Active Directoryban, még akkor is, ha ezeket a fiókokat jönnek létre és kezeli a helyszíni és Azure majd szinkronizálva.  Ha a szervezet Office 365 alatt a tartalmazza, ez a szolgáltatás is használja az Azure Active Directory a felhasználói fiókok.  Ha a felhasználó szervezeti nem kezelt fiókok az Azure-ban, felhasználók regisztrálhat [RMS egyéni felhasználók számára](https://technet.microsoft.com/library/dn592127.aspx), amely létrehoz egy nem felügyelt Azure-bérlőhöz és a könyvtár a szervezet a felhasználó egy olyan fiókkal, hogy a felhasználó majd hitelesíthető Azure RMS.

Ezeknek a fiókoknak a hitelesítési módszert a rendszergazda a szervezetében rendelkezik beállításoktól az Azure Active Directory-fiókok függően változhat. Például jelszavakat létrehozott sikerült használják ezeket fiókokhoz, a többtényezős hitelesítést (MFA), az összevonási vagy a jelszavakat az Active Directory tartományi szolgáltatásokban létrehozott, és ezután szinkronizálja az Azure Active Directory.

## Hozzáadható a felhasználók saját vállalati kívül egyéni sablonok?
Igen.  A végfelhasználók (és a rendszergazdák) alkalmazások közül választhat, egyéni sablonok létrehozásával teszi gyors és könnyen kell alkalmazni az adatvédelem, előre megadott házirendek használatával. A sablon beállításai közül, akik hozzáférhetnek a tartalom, és a szervezeten kívüli megadható felhasználók és csoportok a szervezeten belül, és a felhasználó számára.

A szervezeten kívüli felhasználók megadásához használja a [Azure Rights Management Windows PowerShell-modul](https://technet.microsoft.com/library/jj585012.aspx). Ezek a beállítások bármelyikét használhatja:

-   **Exportálási, szerkesztése és a frissített sablon importálása**:  Ez a legegyszerűbb mód, ha azt szeretné, hogy ezek a külső felhasználók hozzáadása egy meglévő sablont, amely tartalmazza az egyéb csoportok. Használja a [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) sablon exportálása parancsmag egy. Szerkesztheti a külső e-mail címek, ezek a felhasználók és a meglévő csoportok és a jogok jogainak hozzáadása CSV-fájl. Ezután a [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) Azure RMS térni parancsmaggal importálja ezt a módosítást.

-   **a jogok definiáló objektum hozhat létre és -sablonok frissítése**:    Adja meg a külső e-mail címek és a jogok a jogok definíció objektum, amely majd létrehozása vagy módosítása egy sablon használatával. A jogok definiáló objektum használatával adja meg a [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) parancsmag segítségével hozzon létre egy változót, és adja meg az - RightsDefinition paramétert a változót a [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) parancsmag (az új sablon) vagy [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) parancsmag (Ha a meglévő sablon még módosítása). Azonban ezek a felhasználók hozzáadása egy meglévő sablont, szüksége lesz a sablonok és nem csak a külső felhasználók jogok definíció objektumok a meglévő csoportok definiálása.

Egyéni sablonokkal kapcsolatos további információkért lásd: [Az Azure Rights Management egyéni sablonok konfigurálása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

## Milyen eszközt, és mely fájltípusokat Azure RMS által támogatott?
Támogatott eszközök listáját itt találja: a [Ügyfél eszközök, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) szakasz a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) témakör. Mivel jelenleg a minden támogatott eszközök támogatja az összes RMS képességeit, ügyeljen arra, hogy ellenőrizze a [Ügyfél eszközképességek](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) tábla ugyanazon a témakörben.

Az Azure RMS minden fájltípushoz is támogatja. A szöveg, kép, a Microsoft Office (Word, Excel, PowerPoint) fájlok, .pdf fájlok, és néhány más alkalmazás fájltípus Azure RMS biztosít, amely tartalmazza a titkosítás és a jogok (engedélyek) érvényesítése natív védelmet. A más alkalmazásokhoz és fájltípusok általános védelmet biztosít a fájl beágyazás és a hitelesítéshez ellenőrizze, hogy ha egy felhasználó jogosult-e a fájl megnyitásához.

Azure RMS által natív módon támogatott fájlnév-kiterjesztések listája, a [támogatott fájltípusok és fájlnévkiterjesztések](http://technet.microsoft.com/library/dn339003.aspx) szakasza a [Rights Management megosztóalkalmazás rendszergazdai útmutatója](http://technet.microsoft.com/library/dn339003.aspx). Nem szereplő fájlnévkiterjesztések támogatottak az RMS megosztóalkalmazás általános védelmet automatikusan alkalmazza ezeket a fájlokat.

## Ha támogatni áttelepítése Active Directory tartalomvédelmi szolgáltatások?
Kezdetben Azure RMS nem támogatja az áttelepítést a Rights Management, például az AD RMS egy helyi központi telepítéséből. De mostantól támogatott.

További információ: [Áttelepítés Active Directory tartalomvédelmi szolgáltatások az Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

## Azt valóban BYOK Azure RMS Alkalmazást használja, de ismert, hogy ez nem kompatibilis az Exchange Online – Újdonságok a tanácsokat?
A jelenlegi korlátozás késleltetés az Azure RMS-telepítés ne legyen. Ha az Exchange Online, és szeretné használata kerüljön saját kulcsot (BYOK), javasoljuk, hogy központi telepítését Azure RMS az alapértelmezett kulcskezelés módban, ahol a Microsoft hoz létre és kezeli a kulcsot. Ezzel a módszerrel, összes előnyét védelme fontos fájljait és e-mailek most áthelyezése BYOK később (Ha például az Exchange Online támogatásához BYOK) lehetőséget.

Azonban a vállalati házirendekkel használatát írják elő hardveres biztonsági modult (HSM), és ez megakadályozza az Azure RMS-telepítés ellenkező esetben, ha egy másik lehetőséget egy központi telepítéséhez, Azure RMS BYOK Exchange csökkentett RMS. További információ: a [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) szakasz a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) témakör.

## A keresett szolgáltatása úgy tűnik, nem védett függvénytárak SharePoint együttműködve – a rendszer támogatja a tervezett szolgáltatás?
Jelenleg a SharePoint támogatja RMS védett dokumentumokat a tartalomvédelmi szolgáltatás használatával védett könyvtárak, amelyek nem támogatják az egyéni sablonok, dokumentumkövetési és néhány egyéb szolgáltatásait.  További információ bontsa ki a   [SharePoint Online és az üzleti OneDrive: A tartalomvédelmi szolgáltatás konfigurációja](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) szakasz a [Hogyan alkalmazások támogatják a Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) témakör.

Ha egy adott funkció, amely még nem támogatott érdeklik, ügyeljen arra, hogy figyelje a közlemények a [RMS csapat blogja](http://blogs.technet.com/b/rms/).

## Hogyan konfigurálhatók a üzleti egy meghajtót a SharePoint Online rendszerben, hogy a felhasználók biztonságosan megoszthatják fájljaik belüli és kívüli a vállalat?
Alapértelmezés szerint az Office 365 rendszergazdájával, akkor ne állítson be felhasználók tegye.

SharePoint-hely rendszergazdájaként engedélyezi, és konfigurálja a tartalomvédelmi szolgáltatás a saját SharePoint-dokumentumtárban, mint a OneDrive úgy van kialakítva, a felhasználóknak, hogy engedélyezze és konfigurálja a tartalomvédelmi szolgáltatás a saját üzleti szalagtár OneDrive.  Azonban PowerShell használatával ehhez a számukra. Útmutatás, bontsa ki a [SharePoint Online és az üzleti OneDrive: A tartalomvédelmi szolgáltatás konfigurációja](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline)  szakasz a [Azure Rights Management alkalmazások konfigurálása](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) cikk.

## Van bármilyen tippek vagy a sikeres RMS telepítés köröket?
Miután partnerek felügyelete sok központi telepítések, és figyeli az ügyfelek számára, tanácsadók és a támogatási szakértők – a legnagyobb tippek azt is adhatók át az egyik tapasztalja: **Tervezési egyszerű jogok szabályzatok és**.

Azure RMS támogatja a biztonságos megosztása bárkivel, mert a is megadja a felhasználói adatok védelmi körét ambiciózus lehet. De konzervatív a jogok házirendeknek. Számos szervezet a legnagyobb az üzletmenetet származik az adatszivárgás megelőzése az alapértelmezett jogmegadási sablon, amely korlátozza a hozzáférést a felhasználók a szervezet alkalmazásával. Természetesen kaphat, ha szüksége – megtilthatja nyomtatás, mint sokkal részletes szerkesztési stb. De tartsa a részletesebb korlátozások feltétlenül szükséges a magas szintű biztonsági dokumentumokhoz kivételként, és nem implementálja a szigorúbb házirendek egy nap, de több szakaszolt tervezése.

## Milyen funkciókat is vagy nem használható az Azure RMS különböző előfizetéseket?
Az Azure RMS (Office 365 prémium szintű Microsoft Azure RMS és a nagyvállalati mobilitási csomagban) támogató kifizetett előfizetések vannak támogatott RMS szolgáltatások eltérések. Ezek listáját lásd: [Rights Management Services (RMS) összehasonlítás ajánlatok](http://technet.microsoft.com/dn858608).

Az ingyenes előfizetés, amely támogatja az Azure RMS (RMS egyéni felhasználók számára) lefoglaló Azure RMS által védett tartalom támogatja. További információ: [RMS egyének és az Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Honnan szerezhető be az ingyenes Azure RMS-előfizetés (RMS egyéni felhasználók számára) technikai információkat – például annak valóban működését, hogyan átveheti az irányítást a fiókokat és mely tartományok nem használható?
Látni fogja az alábbi kérdésekre adott válaszok a [RMS egyének és az Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md) témakör.

## Hogyan visszanyerheti az alkalmazottak, akik most már kilépett a szervezet által védett fájlok elérésére?
Az Azure RMS, amellyel a hitelesített felhasználóknak teljes tulajdonosi jogosultsággal rendelkeznek az összes használati licenceket, hogy megadta-e a szervezet RMS bérlői felügyelői funkciójának használatához. Ez a funkció lehetővé teszi, hogy jogosult szolgáltatások indexet, és vizsgálja meg a fájlokat, igény szerint.

További információ: [Fő felhasználók konfigurálása az Azure Rights Management és felderítési szolgáltatásokat vagy adatok helyreállítása](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

## Előfordulhat, hogy képernyőfelvételt Rights Management?
A Rights Management képernyőfelvételt véletlen vagy gondatlan közzétételét bizalmas adatokat is hozzájárul a gyakran használt képernyő rögzítési eszközök többsége az blokkolja. Vannak azonban számos módon, hogy a felhasználó is megoszthatják az adatokat, a képernyőn megjelenő, és egy képernyőfelvétel véve az egyetlen módszer. A felhasználó a megjelenített információk megosztása leképezési például kép kamera telefonjuk használatával, írja be újra az adatok vagy egyszerűen intézni továbbítói valakinek.

Az alábbi példák bemutatják, technológia önmagában nem mindig akadályozza nem kellene adatmegosztást. Rights Management segítséget nyújtanak a fontos adatok védelme engedélyezési és használati házirendekkel, amíg más szabályozza a vállalati jogok felügyeleti megoldást kell használni. Például végrehajtása a fizikai biztonságot, gondosan képernyőn, és figyelje a felhasználók számára engedélyezte a hozzáférést a szervezet adatait, és fektet be felhasználói oktatás, így a felhasználók megérteni, hogy milyen adatok nem osztható.

## Hol található információ támogató Azure RMS – például jogi, a megfelelőség és a szolgáltatásiszint-szerződések?
Az Azure RMS támogatja az egyéb szolgáltatások, és más szolgáltatások is támaszkodik. Az Azure RMS, de nem az Azure RMS szolgáltatás használatával kapcsolatos információkat keres, ha ellenőrizze a következőket:

**Jogi és adatvédelmi:**

-   Tudnivalók a Microsoft Azure szerződés: [A Microsoft Azure-szerződés](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   A Microsoft Azure adatvédelmével kapcsolatos információkat: [A Microsoft Azure adatvédelmi nyilatkozata](http://azure.microsoft.com/support/legal/privacy-statement/)

**Biztonsági, megfelelőségi és naplózási:**

Tekintse meg a [Biztonság, a megfelelőségi és szabályozási előírások](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance) szakasz a [Mi az Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) témakör. Továbbá:

-   Az Azure RMS külső tanúsítványok: [A Microsoft Azure Megbízhatósági központ](http://azure.microsoft.com/support/trust-center/)

-   Érvényes a FIPS 140-információkat: [Érvényes a FIPS 140 érvényesítése](https://technet.microsoft.com/library/security/cc750357.aspx)

**Szolgáltatási szintek:**

-   Szolgáltatásiszint-szerződés Azure RMS által kiválasztott ország: [Szolgáltatásiszint-szerződés](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Szolgáltatásiszint-szerződés az Azure Active Directory: [Szolgáltatásiszint-szerződések](http://azure.microsoft.com/support/legal/sla/)

**Dokumentáció:**

-   Az Azure Active Directory dokumentációjának helyhez: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Azure Active Directory-könyvtár: [Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Office 365-könyvtár: [Office 365-höz](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Mi a teendő, ha kérdésem itt nem?
A hivatkozások és erőforrások felsorolt [Információk és támogatás a Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

Emellett vannak a végfelhasználók számára tervezett gyakori kérdések:

-   [Gyakran ismételt kérdések a Rights Management Megosztóalkalmazás Windows rendszerhez](https://technet.microsoft.com/dn467883)

-   [Gyakran ismételt kérdések a Rights Management Megosztóalkalmazás mobil és Mac-platformok](https://technet.microsoft.com/dn451248)

-   [Gyakran ismételt kérdések a dokumentumok nyomon követése](http://go.microsoft.com/fwlink/?LinkId=523977)

Ez gyakran ismételt kérdések a lap Újdonságok a havi dokumentáció frissítés közlemények szerepel a rendszeresen frissül a [Microsoft Rights Management (RMS) csapat](http://blogs.technet.com/b/rms/) blog.

> [!TIP]
> Használhatja a [dokumentumok címke](http://blogs.technet.com/b/rms/archive/tags/docs/) meg a következő blogbejegyzésben több könnyedén megtalálhatja a ezek dokumentáció közleményeket.

## Lásd még
[Getting Started with Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

