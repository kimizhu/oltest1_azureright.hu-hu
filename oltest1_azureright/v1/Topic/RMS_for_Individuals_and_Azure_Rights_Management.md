---
description: na
keywords: na
title: RMS for Individuals and Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
---
# RMS egy&#233;nek &#233;s az Azure Rights Management
RMS számára a szervezet számára, akik a bizalmas fájlok, amelyek a Microsoft Azure Rights Management (Azure RMS) által védett elküldött szabad önkiszolgáló előfizetés, de azokat nem hitelesíthető, mert azok IT-részleg nem egy fiók kezelése azokat az Azure-ban. Például az IT-részleg nem rendelkezik az Office 365, vagy használja az Azure-szolgáltatások.

Ezek a felhasználók egy szabad munkahelyi vagy iskolai fiók használata az Azure RMS, és töltse le és telepítse a Rights Management megosztóalkalmazás feliratkozhat. Ennek eredményeként ezek a felhasználók most hitelesítheti igazolni, hogy-e a személy, hogy a védett fájlokat az elküldött, és olvassa el a számítógépeken, illetve a mobil eszközök a védett fájlokat.

A Rights Management megosztóalkalmazás a Windows-számítógépen használja, ezek a felhasználók is helyen fájlok védelme vagy védett fájlokat személyek belül vagy azon kívül, a szervezet által e-mailt küldeni. Ha az e-mailt, amelyeket küldenek részesülők egy szervezet is nem kezelt felhasználói fiókok az Azure-ban, azok túl feliratkozhat az RMS egyének fiók olvasni a védett e-mail melléklet.

> [!IMPORTANT]
> Az ingyenes előfizetés biztosítja, hogy a hitelesített felhasználók bármikor olvashatja, amely rendelkezik védett fájlokat. Jelenleg is használhatja az ingyenes előfizetés dokumentumok védelmét, és hozzon létre új védett e-mailek, de csak a próbaverzió használatra szolgál, és előfordulhat, hogy el kell távolítani a jövőben új védett tartalom szerzői képesség. További információkért és semmilyen módosítást egyének az RMS használatával lehet védetté tenni a tartalom, tekintse meg a [a Microsoft Rights Management szolgáltatás feltételek](https://portal.aadrm.com/Legal/Service).

Hogyan védelme a fájlokat a szabad Rights Management megosztóalkalmazás használatával kapcsolatos további információkért tekintse meg a [a Rights Management megosztási alkalmazás útmutató a felhasználók](http://technet.microsoft.com/library/dn339006.aspx).

Az egyes személyek RMS példa az önkiszolgáló előfizetési, Azure Active Directory által támogatott. Ez működésével kapcsolatos további tudnivalókért tekintse meg a [Mi az önkiszolgáló előfizetési Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/) a Microsoft Azure dokumentációjában. Használja a következő szakaszok egyének az RMS adott további információk:

-   [Hogyan felhasználók feliratkozni az RMS szolgáltatást a egyének](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_SignUp)

    -   [Technikai áttekintése](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TechnicalOverview)

-   [A rendszergazdák hogyan szabályozhatja, a létrehozott az RMS szolgáltatást egyének fiókok](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts)

-   [Annak megállapítása, hogy a felhasználók hogyan regisztrálta az RMS szolgáltatást az egyének](#BKMK_Detect)

## <a name="BKMK_SignUp"></a>Hogyan felhasználók feliratkozni az RMS szolgáltatást a egyének
A szabad fiók feliratkozás kérésre szintjéről a [a Microsoft Rights Management lap](https://portal.aadrm.com/), és adja meg a munkát, vagy iskolai e-mail címet. A legtöbb jellemző módon, hogy Ön fogjuk átirányítja az előfizetési oldal, ha egy védett melléklettel, hogyan utasításokat tartalmazó e-mail üzenetet kapott-e fizessen. E-mailt fog kapni a Microsoft válaszként, és beírja a részleteket a fiók létrehozásához elvégezheti a regisztrációt. Ha egy e-mailek megerősítő beolvasása a Microsoft, végső e-mailt küld Önnek egy olyan lapra le a megosztóalkalmazás a különböző eszközök és a hivatkozást a felhasználói útmutatóját.

#### Az RMS szolgáltatást egyének regisztráció

1.  Ugrás a Windows vagy Mac számítógépen, a [a Microsoft Rights Management lap](https://portal.aadrm.com).

2.  Írja be az e-mail cím, használnia a szervezetben, például a **janetm@contoso.com** vagy **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > Személyes e-mail fiókok nem támogatott, tehát ne adjon meg egy Microsoft-fiók (korábbi nevén egy Microsoft-Live ID-fiók) vagy egy másik személyes, előfordulhat, hogy az Internet szolgáltatótól otthon használt fiók.

3.  Kattintson a **kezdéshez**.

    A Microsoft az e-mail címet segítségével ellenőrizze, hogy a szervezet már rendelkezik-e a [amely tartalmazza az Azure RMS előfizetéssel](https://technet.microsoft.com/library/dn655136.aspx). Ha ez a helyzet, nincs szükség RMS az egyének, akkor fogja aláírt azonnal, és a önkiszolgáló feliratkozási az RMS szolgáltatást az egyének meg lett szakítva. Ha az Azure RMS előfizetéses nem található, fogjuk folytatja a műveletet a következő lépéssel.

4.  Várjon, amíg a megadott címre küldi az e-mailek megerősítő üzenetet. A Microsoft (DoNotReply@microsoft.com) lesz, és a a területe van **Microsoft RMS**.

5.  Amikor megjelenik az e-mailt, az utasításokat a feliratkozási eljárás befejezéséhez hivatkozásra kattint.

6.  A hivatkozás egy új **Microsoft Rights Management** lapon adja meg a fiók részleteit. Írja be az utónevét, vezetéknevét adja meg, és a erősítse meg a jelszót, az Ön által választott, válassza ki az országot (vagy az Öné, ha az Ön országában nem szerepel a legközelebbi ország) a legördülő, és kattintson **létrehozása**.

7.  Várjon, amíg egy másik e-mail üzenetet a Microsoft, amely most erősíti meg, hogy a fiók használatra kész.

8.  Amikor megkapja az e-mailt, kattintson a hivatkozásra kattintva jelentkezzen be, és olvassa el a varázsló utasításait töltse le és telepítse a megosztóalkalmazás, vagy kattintson a Súgó hivatkozásra, az alkalmazás megosztási útmutatója olvasni.

Most fiókja készül, készen indítsa el a fájl védett, és olvassa el a fájlokat, amelyek a másokkal védelme. Amikor a rendszer kéri jelentkezzen be a védelem, vagy olvassa el a védett fájlokat, adja meg a meg e-mail címét és a jelszót a létrehozásához használt fiók az RMS szolgáltatást az egyes személyek.

### <a name="BKMK_TechnicalOverview"></a>Technikai áttekintése
Az egyének RMS használ egy önkiszolgáló feliratkozási eljárás, hogy a felhasználók hitelesítésére Microsoft felhőalapú technológiát használó más szolgáltatásokba is használják.

Ez az, hogy a háttérben mi történik, ha a felhasználó bejelentkezik az RMS szolgáltatást az egyének és a szervezet nem található az Office 365 előfizetés vagy Azure-előfizetés, és ezért nem könyvtár hitelesíteni a felhasználók Azure:

1.  Ha az első felhasználóhoz a szervezet az RMS szolgáltatást előfizetés kérések számára, a tartománynévvel, e-mail címüket megadott meg, hogy azt már társítva egy Azure bérlői be van jelölve. Ha a nem létező bérlői, egy új bérlői és az Azure directory automatikusan létrejön a szervezet, ez a felhasználó első egy fiókot tartalmazó. Eltérően az előfizetéses Azure, ez a fiók első nem egy globális rendszergazda, de a normál felhasználó. Az új fiókot használ, az e-mail címhez és jelszóhoz, amelyet a felhasználó által megadott.

    > [!NOTE]
    > Néhány tartománynevek nem használható a következő könyvtár létrehozásakor, és ezért nem használható az RMS szolgáltatást egyének. Letiltott tartománynevek listája megtekinthetők a JavaScript-objektum jelöléssel fájlból: [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json)

    Ha egy meglévő bérlői megtalálható, akkor be van jelölve meg, hogy már rendelkezik egy előfizetést az Azure RMS. Amikor nincs előfizetés található, a szabad RMS egyének előfizetés is hozzá lehet adni.

2.  A szervezet az RMS egyének előfizetés kapnak. Most ez a felhasználó által Azure hitelesíthető és fájlok védelme, majd olvassa el a fájlokat, amelyek a másokkal Azure Rights Management használatával védelme. Védelmét, és a védett fájlokat olvasni, a felhasználónak rendelkeznie kell az RMS-enlightened alkalmazások, például a szabad [Rights Management megosztóalkalmazás](https://technet.microsoft.com/library/dn919648.aspx).

3.  Amikor a második felhasználó ugyanazt a szervezet olyan egyének előfizetés RMS kér, új felhasználói fiók hozzáadódik a korábban létrehozott Azure directory egyének előfizetés a szervezete RMS használatával. Ez a felhasználó második is mindent, amely az első felhasználó (fájlok védelmét, és olvassa el a védett fájlokat), de ezenkívül, ezek a két felhasználók mostantól több könnyen biztonságosan dolgozhat, mert azok alapértelmezett sablonok gyorsan alkalmazása fájlok, korlátozott hozzáférésű fiókokhoz a szervezet Azure könyvtárban.

4.  Szervezethez későbbi felhasználóit hajtsa végre az ugyanazon minta hozzáadása a szervezet Azure Directory felhasználói fiókok (ha az új felhasználók feliratkozás). A további fiókok hozzáadott a könyvtárban, a több felhasználó is biztonságosan együttműködhet munkatársakkal és partnerekkel, és több egyszerűen megakadályozza, hogy jogosulatlan személyek ezek a fájlok olvasását, ha azok nem férhet hozzá őket.

Ez a folyamat során nem a szervezet számára ingyenes, és nem szükséges az IT-részleg a munkát. Azonban az IT-részleg sikerült dönt, hogy az alábbi lehetőségek közül választhat:

-   **a fiókok és a regisztrációs folyamat**: A rendszergazdák tulajdonba a automatikusan létrehozott könyvtár és a fiókok az Azure-ban. A fiókok, majd kezelése, ha directory integrációs megoldást, például a jelszó-szinkronizálás és egyszeri bejelentkezés végrehajtási. Vagy azok a felhasználók fiókokat hozhat létre, vagy az RMS szolgáltatást egyének regisztrál megakadályozhatja.

    További tudnivalókért tekintse meg a következő szakaszban [A rendszergazdák hogyan szabályozhatja, a létrehozott az RMS szolgáltatást egyének fiókok](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts).

-   **Kezelése a Rights Management**: A rendszergazdák az RMS egyének előfizetés a szervezet, amely tartalmazza az Azure Rights Management előfizetéses alakíthatók. Ha ezt, a meglévő Azure könyvtárat és a fiókok egy folytonos átmenet meglévő számára, akik a egyének az RMS használt megőrzése érdekében. Minden fájlt, amelyet a felhasználók védett korábban továbbra is védi ugyanazt a házirendek, és az, hogy azok engedéllyel ahhoz, hogy a fájlokat személyek továbbra is fogja tudni használni a fájlokat azonos módon.

    Ha tanfolyamot a művelet, a szervezet előnyeit számára, hogy képes-e a Rights Management integrálhatók a munkafolyamatok, szolgáltatások és adatok tárolja. Ezenkívül kezelheti a Rights Management mert felügyeletet biztosít a szervezet bérlői kulcs Azure Rights Management rendelkezik. Most a következőket teheti:

    -   Állítsa be a Exchange és a SharePoint Azure Rights Management, támogatásához, még akkor is, ha ezek a helyszíni futnak. Exchange és a SharePoint natív módon támogatottak az online szolgáltatások, és a helyszíni kiszolgálók összekötő kezeli azokat. További tudnivalókért tekintse meg a következőket:

        -   Az Exchange Online, és a SharePoint Online szakaszokat a [Az Office 365: Az ügyfelek és az online szolgáltatások konfigurációja](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365) a a [Azure Rights Management alkalmazások konfigurálása](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) témakör

        -   [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)

    -   Hajtsa végre e-felderítési adatokat vállalati által birtokolt, hogy, ha szükséges, visszafejtéséhez fájlok, amelyek segítségével a Rights Management védettek. További tudnivalókért tekintse meg a [Fő felhasználók konfigurálása az Azure Rights Management és felderítési szolgáltatásokat vagy adatok helyreállítása](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

    -   Az összes naplózása a Rights Management, mint amit a szervezet. Ez akkor nagyon hatékony, mert nem csak Ön figyelheti mely fájlok védett, és aki sikeresen éri el ezeket a védett fájlokat, de a vélhetően gyanús viselkedés jogosulatlan személyektől, akik próbál hozzáférni a védett fájlokat is azonosíthatja. További tudnivalókért tekintse meg a [Naplózás, és az Azure Rights Management használati elemzése](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

    -   A felhasználók nyomon követésére és visszavonni a védett dokumentumok számára lehetővé, ha ezek a szolgáltatások által támogatott a [Azure RMS-előfizetés](https://technet.microsoft.com/dn858608). További tudnivalókért tekintse meg a  [nyomon követése, és a fájlok visszavonni](https://technet.microsoft.com/library/dn986611.aspx) származó a [RMS megosztási alkalmazás felhasználói útmutató](https://technet.microsoft.com/library/dn339006.aspx).

    -   Valósítja meg a hozás saját kulcs megoldás (BYOK), hogy a bérlői kulcsot az Azure Rights Management létrehozott helyszíni a IT házirendeket megfelelően-e, és biztonságosan át a Microsoft, ha egy biztonsági modul (HSM) használatával. További tudnivalókért tekintse meg a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

## <a name="BKMK_TakeControlofAccounts"></a>A rendszergazdák hogyan szabályozhatja, a létrehozott az RMS szolgáltatást egyének fiókok
Ha nem szeretné a szervezete RMS egyének előfizetés átalakítása előfizetéses, továbbra is szabályozható a felhasználói fiókok létrehozásának Azure könyvtárban a szervezet számára a következő módon:

-   Az Azure Active Directory és az Active Directory tartományi szolgáltatások infrastruktúra valósítja meg a címtár-integrációs megoldást. Szinkronizálhatja, valamint a jelszavakat, hogy a felhasználók nem lesz a Rights Management használata új fiók létrehozása, és a helyszíni jelszóházirendek az új Azure felhasználói fiókok alkalmazható. Úgy is szinkronizálhatja jelszavait, hogy a felhasználó nem rendelkezik a Rights Management használata egy másik jelszót.

-   Sikerült akadályozni a felhasználóknak az Azure Rights Management használata az RMS egyének előfizetés regisztrál. A legtöbb esetben nincs kevés előny ennek során, mert a felhasználók vagy fog megosztani a fájlokat (amelyek a vállalati kockázata) védelem nélkül, vagy fogja használni a fájl védelmét egy másik mechanizmus, amely nem biztosít az IT-osztálynak a kapcsolóval az adatok eléréséhez. Azonban ha azt szeretné, hogy megakadályozza, hogy a felhasználók az RMS használata egyének regisztrál, tegye a következők egyike után az Ön által végrehajtott a szervezet címtárának tulajdonjogát Azure:

    -   Akadályozza meg az összes regisztrál önkiszolgáló előfizetések, ez kiterjed az RMS számára.  Jelenleg nem állítható be a szolgáltatás; a beállítás csak az összes Azure előfizetések, amely az önkiszolgáló folyamat használja. Ehhez a beállítása a **AllowAdHocSubscriptions** paraméter, a false értékre a [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) parancsmag az Azure Active Directory a Windows PowerShell modulból. Példa: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Akadályozza meg az Azure-ban, ami azt jelenti, hogy, hogy csak olyan felhasználók, akik már rendelkezik fiókkal az Azure-ban feliratkozhat önkiszolgáló előfizetések, ez kiterjed az RMS egyének az új fiók létrehozása.  Ehhez a beállítása a **AllowEmailVerifiedUsers** paraméter, a false értékre a [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) parancsmag az Azure Active Directory a Windows PowerShell modulból. Példa: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Az Active Directory tartományi szolgáltatások infrastruktúra szinkronizálása az Azure Active Directoryban. Ez a művelet megakadályozza, hogy az új fiók létrehozását, amikor a felhasználók feliratkozni az önkiszolgáló előfizetések például az RMS egyének, és törlése, vagy tiltsa le az Azure könyvtárban korábban létrehozott fiókokhoz.

Vezérlő a felhasználói fiókok az Azure-címtárban, vagy megakadályozzák, hogy a felhasználók számára az RMS szolgáltatást regisztrál, nincs Azure-előfizetése, és saját a könyvtárban. Ha még nincs Azure-előfizetése, szerezheti be egy díjmentesen. Ha egy könyvtár automatikusan létrehozott meg az önkiszolgáló folyamat során, a tartomány létrehozásához használt tulajdonba. Ha már saját Azure könyvtár, de a felhasználó megadott egy új tartomány, a szervezet használó, egyesítése a meglévő könyvtár, hogy a tartomány. További tudnivalókért tekintse meg a utasításait [Mi az önkiszolgáló előfizetési Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)

## <a name="BKMK_Detect"></a>Annak megállapítása, hogy a felhasználók hogyan regisztrálta az RMS szolgáltatást az egyének
Rendszergazdaként hogyan tudja, ha a felhasználók regisztrálta az RMS szolgáltatást az egyének? Bármely, vagy az alábbi módszerek kombinációját használhatja:

-   Kérje meg a felhasználók hogyan azok szigorúan bizalmas fájlok védelme, különösen akkor, ha a vállalaton kívülre ütközhetnek.

-   Ha a szervezet Azure-előfizetése van, használja a [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) annak ellenőrzéséhez, hogy a parancsmag **RIGHTSMANAGEMENT_ADHOC** egyik az előfizetések okat. Ha igen, ez az egyének előfizetés biztosítani a szervezetben, az aktív egységek érhető el, a felhasználóknak, hogy az önkiszolgáló-előfizetési folyamat használja egy készlet, amely az RMS.

-   Használja a rendszer felügyeleti megoldás, például a System Center Configuration Manager, készlet a telepített szoftvereket, és a szoftver használja. A Rights Management megosztóalkalmazás használatával futtatja a **ipviewer.exe** program, és Ön is [Töltse le és telepítse az alkalmazást](http://go.microsoft.com/fwlink/?LinkId=303970) szabad, majd használata szoftverleltár névjegy vonatkozó egyéb jellemzőket azonosításához.

-   A kiterjesztések a Rights Management megosztóalkalmazás által létrehozott figyelni lennie. A .pfile és .ppdf kiterjesztésű példák egyértelmű, de más módosítani a fájlnévkiterjesztés, ha a natív módon Rights Management által védett fájlokat. További tudnivalókért tekintse meg a [támogatott fájltípusok és kiterjesztések](http://technet.microsoft.com/library/dn339003.aspx) szakasz a [a Rights Management megosztási alkalmazás rendszergazdai útmutatójában](http://technet.microsoft.com/library/dn339003.aspx).

## Lásd még
[Getting Started with Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

