---
description: na
keywords: na
title: Deploying the Azure Rights Management Connector
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
---
# Az Azure Rights Management &#246;sszek&#246;tő telep&#237;t&#233;se
Ezen információ segítségével további információkhoz juthat a Microsoft Rights Management (RMS) összekötő és a használatát, a meglévő helyszíni központi telepítések, amely a Microsoft Exchange Server, Microsoft SharePoint Server vagy Windows Server rendszerű, és használja a fájl besorolást infrastruktúra (FCI) szolgáltatását a Fájlkiszolgálói erőforrás-kezelő fájlkiszolgálók adatok védelmének biztosítására.

> [!TIP]
> Magas szintű példa a pillanatképek: a [Automatikusan a Windows Server és a fájl besorolást infrastruktúra futtató fájlkiszolgálók fájljainak védelme](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_FCI) szakasz a [Mi az Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) témakör.

## <a name="OverviewConnector"></a>A Microsoft Rights Management összekötő áttekintése
A Microsoft Rights Management (RMS) összekötő teszi, hogy gyorsan meglévő helyszíni kiszolgálók engedélyezik a felhőalapú Microsoft Rights Management (Azure RMS) szolgáltatás használatához a tartalomvédelmi szolgáltatással (IRM) funkciókat. Ez a funkció a informatikai és a felhasználók könnyen védheti dokumentumokat és képeket mindkét a szervezeten belüli és a külső további infrastruktúra telepítéséhez, vagy létre megbízhatósági kapcsolatok más vállalatokkal nélkül. Ez az összekötő is használhatja, még akkor is, ha a felhasználók némelyike online szolgáltatások, abban az esetben a hibrid csatlakozni. Egyes felhasználók postaládáihoz Exchange Online használatára és a egyes felhasználók postaládáihoz Exchange-kiszolgáló használatára. Az RMS-összekötő telepítése után minden felhasználó is védetté tehessék és használhassák az e-mailek és a mellékletek Azure RMS segítségével, és adatvédelem a két központi telepítési konfigurációk közötti problémamentesen működik.

Az RMS-összekötő, hogy telepítse a Windows Server 2012 R2, Windows Server 2012 vagy Windows Server 2008 R2 rendszerű kiszolgálókon a helyszínen, kis-védelem erőforrásigényét szolgáltatás. Az összekötő a fizikai számítógépeken futó, mellett is futtatható virtuális gépeken, beleértve az Azure IaaS virtuális gépek. Miután telepít, és konfigurálja az összekötőt, a helyszíni kiszolgálók és a felhőszolgáltatás közötti kommunikáció felületi (továbbító) működik.

Ha saját bérlői kulcsot az Azure RMS (a kulcs, vagy BYOK forgatókönyv saját kerüljön), az RMS-összekötő és az azt használó helyszíni kiszolgálók nem érhető el a hardveres biztonsági modult (HSM), a bérlői kulcsot tartalmazó kezelheti. Ennek oka az Azure RMS a bérlő kulcsot használó összes titkosítási műveleteket kell elvégezni, és nem helyszíni.

![](../Image/RMS_connector.png)

Az RMS-összekötő a következő helyszíni kiszolgálók támogatja: Az Exchange Server, SharePoint-kiszolgáló és fájlkiszolgálókat, futtassa a Windows Server és a fájl besorolást infrastruktúra használatára és házirendeket alkalmazhat Office-dokumentumok mappába. Összes fájltípusokat fájl besorolást használatával védeni kívánt, ha nem használja az RMS-összekötő, de Ehelyett használja a [RMS-védelmet parancsmagok](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Támogatott verzió a helyi kiszolgáló, tekintse meg a "helyszíni támogató kiszolgálók Azure RMS" részben a [Alkalmazások, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) szakasza a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) témakör.

A következő részekben tervezése, telepítése és az RMS-összekötő konfigurálásához nyújtanak segítséget. Így a kiszolgálók használhatja az összekötő, majd tegye kell néhány közzétételi telepítési konfiguráció.

-   [Prerequisites for the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_Prereqs)

-   **1. lépés:**  [Installing the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_InstallingConnector)

-   **2. lépés:**  [Entering credentials](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#EnteringCredentials)

-   **3. lépés:**  [Authorizing servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#AuthorizingServers)

-   **4. lépés:**  [Configuring load balancing and high availability](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#ConfiguringConnector)

-   Nem kötelező: [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS)

-   Nem kötelező: [Configuring the RMS connector for a web proxy server](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringWebProxy)

-   Nem kötelező: [Installing the RMS connector administration tool on administrative computers](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_InstallingStandaloneTool)

-   **5. lépés:**  [Configuring servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#ConfiguringServers)

    -   [Configuring an Exchange server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ExchangeServer)

    -   [Configuring a SharePoint server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringSharePoint)

    -   [Configuring a file server for File Classification Infrastructure to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_FileServer)

-   [Next steps](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_NextSteps)

## <a name="BKMK_Prereqs"></a>Az RMS-összekötő előfeltételei
Az RMS-összekötő telepítése előtt győződjön meg arról, hogy az alábbi követelmények teljesülnek.

|Követelmény|További információ|
|---------------|----------------------|
|A Rights Management (RMS) szolgáltatás aktiválva van|[Az Azure Rights Management aktiválása](../Topic/Activating_Azure_Rights_Management.md)|
|Az Active Directory-erdők és az Azure Active Directory közötti címtár-szinkronizálás|RMS aktiválása után Azure Active Directoryban való együttműködésre a felhasználókat és csoportokat az Active Directory adatbázisban kell állítani. **Important:** Ez a címtár szinkronizálási lépés az RMS-összekötőhöz a működik, még akkor is tesztelési célú hálózatban kell megtennie. Bár az Office 365 és az Azure Active Directory használatával hoz létre manuálisan az Azure Active Directory-fiókot használ, ez az összekötő megköveteli, hogy a fiókok az Azure Active Directory szinkronizálásának az Active Directory tartományi szolgáltatások; Nincs elegendő manuális jelszó-szinkronizálás.<br />További információkért lásd a következőket:<br /><br />-   [Az Azure AD-bérlő konfigurálásával kapcsolatos](http://technet.microsoft.com/library/hh967611.aspx)<br />-   [Útmutatás a címtár-szinkronizálás engedélyezése a DirSync használatával, AAD-ben](http://technet.microsoft.com/library/hh967642.aspx)|
|Nem kötelező, de ajánlott:<br /><br />-   A helyszíni Active Directory között az Azure Active Directory összevonási engedélyezése|A helyszíni directory és az Azure Active Directory közötti identitás-összevonás engedélyezheti. Ez a konfiguráció lehetővé teszi, hogy a zökkenőmentes felhasználói élmény egyszeri bejelentkezéshez az RMS szolgáltatás használatával. Egyszeri bejelentkezés nélkül rendszer kéri a felhasználókat a hitelesítő adatait csak akkor védett tartalom.<br /><br />Összevonási konfigurálása az Active Directory összevonási szolgáltatások (AD FS) közötti Active Directory tartományi szolgáltatások és az Azure Active Directory használatával kapcsolatos információkért lásd: a [Ellenőrzőlista: Az AD FS megvalósítása és kezelése egyszeri bejelentkezés](http://technet.microsoft.com/library/jj205462.aspx) a Windows Server könyvtárában.|
|Legalább két tag számítógépeket, amelyeken az RMS-összekötő telepítése:<br /><br /><ul><li>Egy 64 bites fizikai vagy virtuális gép fut, a következő operációs rendszerek egyikét:<br /><br /><ul><li>Windows Server 2012 R2</li><li>Windows Server 2012</li><li>Windows Server 2008 R2</li></ul></li><li>Legalább 1 GB RAM</li><li>Legalább 64 GB szabad lemezterület</li><li>Legalább egy hálózati csatoló</li><li>Hozzáférés az interneten keresztül tűzfal (vagy webes proxy), amely nem igényel hitelesítést</li><li>Az erdő vagy tartományt, amely megbízik a szervezet más erdőkben telepített Exchange vagy a SharePoint-kiszolgálót, amely az RMS-összekötővel használni kívánt tartalmazó kell lennie</li></ul>|A hibatűrés és a magas rendelkezésre állású telepítenie kell az RMS-összekötő legalább két számítógép. **Tip:** Outlook Web Access vagy az Exchange ActiveSync IRM használó mobil eszközöket használ, és rendkívül fontos, hogy akkor karbantartása e-mailek és Azure RMS által védett mellékleteket a hozzáférést, ha azt javasoljuk, hogy a magas rendelkezésre állásának biztosításához átjárókiszolgálók terhelésű csoport központi telepítését.<br />Nem kell az összekötőt futtató dedikált kiszolgálókra, de a kiszolgálókról, hogy az összekötő fog használni egy külön számítógépre kell telepíteni. **Important:** Az Exchange Server, SharePoint-kiszolgáló vagy egy fájlkiszolgálón, amely a fájl besorolást infrastruktúra van konfigurálva, ha azt szeretné, hogy a szolgáltatások által funkciójának használatához az Azure RMS-t futtató számítógép nem telepíti az összekötőt. Emellett ne telepítse az összekötő tartományvezérlőre.|

## <a name="BKMK_InstallingConnector"></a>Az RMS-összekötő telepítése
Miután meggyőződött a Előfeltételek az előző szakaszban, az RMS-összekötő telepítéséhez használja a következő útmutatás szerint:

1.  Azonosítsa az RMS-összekötőt futtató számítógépeket (legalább két). Meg kell felelniük a az előző szakaszban felsorolt minimális megadását.

    > [!NOTE]
    > Bérlőnként (Office 365 bérlői vagy az Azure AD-bérlő) (több kiszolgáló magas rendelkezésre álló) egyetlen RMS összekötőt telepíteni fogja. Eltérően az Active Directory RMS használata nem szükséges telepíteni az RMS-összekötő minden erdőben.

2.  Töltse le a forrásfájlokat az RMS-összekötőhöz a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

    Az RMS-összekötő telepítése Töltse le a RMSConnectorSetup.exe.

    Továbbá:

    -   Ha később szeretné konfigurálni az összekötő egy 32 bites számítógépről, töltse le is RMSConnectorAdminToolSetup_x86.exe.

    -   Ha azt szeretné, a kiszolgálókonfigurációs eszköz használata az RMS-összekötőhöz, beállításjegyzék-beállításokat, akkor a helyszíni kiszolgálókon, automatizálása is töltse le a GenConnectorConfig.ps1.

3.  Futtatás a számítógépen, amelyen szeretné az RMS-összekötő telepítése **RMSConnectorSetup.exe** rendszergazdai jogosultságokkal.

4.  Válassza ki a Microsoft Rights Management összekötő telepítése lap kezdőlapján **a számítógépen telepíti a Microsoft Rights Management-összekötő**, és kattintson a **Tovább**.

5.  Olvassa el és fogadja el az RMS-összekötő licencfeltételeket, és kattintson **Tovább**.

A folytatáshoz adjon meg egy olyan fiókot és jelszót az RMS-összekötő konfigurálásához.

## <a name="EnteringCredentials"></a>Hitelesítő adatok megadása
Az RMS-összekötő konfigurálása előtt meg kell adnia az RMS-összekötő konfigurálásához megfelelő jogosultságokkal rendelkező fiók hitelesítő adatait.

Emellett ha megvalósította [bevezetési vezérlők](https://technet.microsoft.com/library/jj658941.aspx), győződjön meg arról, hogy a megadott fióknak tartalom védelmére képes. Például ha korlátozott a "IT-részleg" csoport tartalom védelme lehetővé teszi, az itt megadott fióknak az adott csoport tagjának kell lennie. Ha nem, akkor a hibaüzenet fog látni: **Nem sikerült a felügyeleti szolgáltatás és a szervezet helyét deríti fel. Ellenőrizze, hogy a szervezete a Microsoft Rights Management szolgáltatás engedélyezve van.**

A következő jogosultságokkal rendelkező fiókkal használhatja:

-   **Office 365 bérlői rendszergazdájával**: Az Office 365 bérlő globális rendszergazda fiók.

-   **Globális rendszergazda azure Rights Management**: Az Azure RMS bérlői rendszergazdai jogokkal rendelkező fiók.

-   **Microsoft RMS összekötő rendszergazda**: Az Azure Active Directoryban, amely rendelkezik jogosultságokkal telepítésére és felügyeletére a szervezet az RMS-összekötő fiók.

    > [!NOTE]
    > Ha szeretné használni a Microsoft RMS összekötőt rendszergazdai fiók, az RMS-összekötő rendszergazdai szerepkör hozzárendelése a következő először kell tennie:
    > 
    > 1.  Ugyanarra a számítógépre töltse le és telepítse a Windows PowerShell Rights Management. További információ: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 
    >     Indítsa el a Windows PowerShell a **Futtatás rendszergazdaként** parancsot, és az Azure RMS szolgáltatás használatával kapcsolódnak a [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) parancsot:
    > 
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  Futtassa a [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) parancs csak a következő paraméterek egyikét használva:
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     Például írja be: **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role " ConnectorAdministrator "**
    > 
    >     Bár ezek a parancsok a ConnectorAdministrator szerepkör használatához is használhatja a GlobalAdministrator szerepkör itt is.

RMS összekötő telepítési folyamat során az összes előfeltételként szükséges szoftverek érvényesítve, és telepítve, az Internet Information Services (IIS) telepítve van, ha nem már szerepel, és az összekötő szoftver telepítve és konfigurálva van. Emellett Azure RMS felkészül a konfiguráció a következő létrehozásával:

-   Egy üres táblázatot, amely jogosult-e az összekötő segítségével kommunikálni az Azure RMS-kiszolgálók. Kiszolgálók később fogja hozzáadni ehhez a táblához.

-   Biztonsági jogkivonatot az összekötő, amelyek engedélyezik az Azure RMS operations halmaza. Ezek a tokenek Azure RMS letöltődnek és a beállításjegyzékben a helyi számítógépen telepítve. A védett a data protection alkalmazásprogramozási felület (DPAPI) és a helyi rendszer fiók hitelesítő adatainak használatával.

A varázsló utolsó lapján tegye a következőket, majd kattintson **Befejezés**:

-   Ha ez az első összekötő, amely telepítette, nem jelöli be **indítási összekötő felügyeleti konzol kiszolgálók engedélyezésének** most. Ezt a beállítást választja a második (vagy utolsó) RMS összekötő telepítése után fog. Ehelyett futtassa újra a varázslót legalább egy másik számítógépen. Telepítenie kell egy legalább két összekötőt.

-   Ha már telepítette a második (vagy utolsó) összekötő, válassza ki a **indítási összekötő felügyeleti konzol kiszolgálók engedélyezésének**.

> [!TIP]
> Ezen a ponton van egy ellenőrzése, és ellenőrizze, hogy az RMS-összekötőhöz a webes szolgáltatások működési végezheti el:
> 
> -   Csatlakozás egy webböngészőből **http://&lt;connectoraddress&gt;/_wmcs/certification/servercertification.asmx**, tagjára *&lt; connectoraddress &gt;* a kiszolgáló címe vagy neve, amelynek a RMS connector telepítve van. Sikeres kapcsolódás megjelenítése a **ServerCertificationWebService** oldalon.

Ha módosítania kell az RMS összekötő eltávolítása, futtassa újra a varázslót, és válassza ki az Eltávolítás lehetőség.

## <a name="AuthorizingServers"></a>Kiszolgálók az RMS-összekötő engedélyezése
Az RMS-összekötő legalább két számítógépre telepítette, amikor készen áll a kiszolgálók és az RMS-összekötő használni kívánt szolgáltatások engedélyezése. Például az Exchange Server 2013 vagy a futtató kiszolgálókon SharePoint Server 2013.

Ezek a kiszolgálók definiálásához, futtassa az RMS-összekötő felügyeleti eszközt, és bejegyzéseket adjon hozzá a megengedett kiszolgálók listáját. Ez az eszköz kiválasztásakor futtatható **indítási összekötő felügyeleti konzol kiszolgálók engedélyezésének** a Microsoft Rights Management connector beállítása végén varázsló, vagy futtatható külön-külön a varázslóból.

Amikor Ön felhatalmaz ezekre a kiszolgálókra, figyelembe a következőket kell figyelembe venni:

-   Kiszolgálók hozzáadása különleges jogosultságot kapnak. Minden olyan fiókot, hogy adja meg az Exchange Server kiszolgálói szerepkört az összekötő-konfiguráció megkapja a [felügyelői szerepkör](https://technet.microsoft.com/library/mt147272.aspx) Azure RMS, amely hozzáférést biztosít a őket minden tartalom RMS ennél a bérlőnél. A felügyelői szolgáltatás automatikusan engedélyezve van ezen a ponton, ha szükséges. A biztonsági kockázatát a jogok kiterjesztésének elkerülése érdekében ügyeljen arra, hogy a szervezet Exchange-kiszolgálók által használt fiókokat ad meg. SharePoint-kiszolgáló vagy a fájlkiszolgálók, az FCI használó konfigurált összes kiszolgáló normál felhasználói jogosultságot kapnak.

-   Több kiszolgáló egy-egy bejegyzésnek megadhatja, ha az Active Directory biztonsági vagy terjesztési csoport vagy egynél több kiszolgáló által használt szolgáltatásfiók megadása. Ezt a konfigurációt használja, ha kiszolgálók csoportja osztoznak ugyanazon RMS tanúsítványokat és összes figyelembe kell venni tulajdonosok valamelyiket védett tartalom. Adminisztratív kiadások minimalizálása érdekében azt javasoljuk, hogy ez a konfiguráció egyetlen csoport, hanem az egyes kiszolgálók segítségével a szervezet Exchange-kiszolgálók vagy egy SharePoint-kiszolgálófarm engedélyezése.

Az a **kiszolgálók engedélyezett felhasználását az összekötő** lapján kattintson **Hozzáadás**.

### <a name="BKMK_AddServer"></a>-Kiszolgáló felvétele a megengedett kiszolgálók listája
Az a **a kiszolgáló használja az összekötő engedélyezése** lapon adja meg az objektum nevét, vagy tallózással keresse meg az objektum megbízott azonosítására.

Fontos, hogy engedélyezi-e a megfelelő objektum. Egy kiszolgáló, az összekötő használatára a helyszíni szolgáltatás (például Exchange vagy SharePoint) futtató fiókot a hitelesítéshez meg kell adni. Ha a szolgáltatás egy konfigurált szolgáltatási fiókként fut, adja hozzá például a szolgáltatás fiók nevét a listához. Ha a szolgáltatás helyi rendszerként fut, adja hozzá a számítógép-objektumot (például SERVERNAME$) nevét. Ajánlott eljárásként hozzon létre egy csoportot, amely tartalmazza ezeket a fiókokat, és adja meg az egyes kiszolgáló neve helyett a csoport.

További információ a különböző kiszolgálói szerepköröket:

-   Futtassa az Exchange-kiszolgálók: Meg kell adnia egy biztonsági csoportot, és használhatja az alapértelmezett csoport (**Exchange-kiszolgálók**), amely Exchange automatikusan létrehozott és karbantartott az összes Exchange-kiszolgáló az erdőben.

-   Futtassa a SharePoint-kiszolgálók:

    -   A SharePoint 2010 kiszolgáló (akkor nem használ szolgáltatásfiók) helyi rendszer fiókként való futtatásra van beállítva, ha manuálisan hozzon létre egy biztonsági csoportot az Active Directory tartományi szolgáltatásokban, és adja hozzá a kiszolgálón a számítógép neve objektumot ebben a konfigurációban ehhez a csoporthoz.

    -   Ha egy SharePoint-kiszolgálón a SharePoint 2013 rendszerhez (a SharePoint 2010 ajánlott eljárás), és az egyetlen lehetséges szolgáltatás fiók használatára van konfigurálva, tegye a következőket:

        1.  Vegye fel a szolgáltatásfiókot, amelyen a SharePoint központi felügyeleti szolgáltatása ahhoz, hogy a felügyeleti konzolról konfigurálható a SharePoint.

        2.  Adja hozzá a fiókot, amelyet a SharePoint-alkalmazáskészlet van konfigurálva.

        > [!TIP]
        > Ha két fiókot különböző, célszerű egyetlen csoportot hoz létre minimálisra csökkentheti az adminisztratív kiadások mindkét fiókot tartalmaz.

-   A fájl besorolást infrastruktúrát használó fájlkiszolgáló-a kapcsolódó szolgáltatási futtassa a helyi rendszer fiókként, engedélyeznie kell a számítógépfiók a fájlkiszolgálók (például SERVERNAME$) vagy a számítógép fiókokhoz tartalmazó csoport.

Amikor befejezte a kiszolgálók hozzáadása a listához, kattintson az **Bezárás**.

Ha még nem tette meg ezt, kell most terheléselosztási konfigurálása a a kiszolgálók, amelyeken az RMS-összekötő telepítve, és vegye figyelembe, hogy ezek a kiszolgálók és az imént felhatalmazott kiszolgálók közötti kapcsolatok a HTTPS PROTOKOLLT használja-e.

## <a name="ConfiguringConnector"></a>Betöltés terheléselosztási és magas rendelkezésre állású konfigurálása
A második vagy végleges példány az RMS-összekötő telepítése után egy összekötő URL-cím kiszolgáló nevét adja meg, és a rendszer terheléselosztási konfigurálására.

Az összekötő URL-cím kiszolgáló bármely név lehet szabályozhatja, hogy névtér alatt. Például létrehozhat egy bejegyzést a DNS rendszerben a **rmsconnector.contoso.com** és konfigurálja ezt a bejegyzést, a rendszer terheléselosztási IP-cím használatára. Nincs ilyen nevű vonatkozó speciális követelmények, és azt nem kell magukat összekötő kiszolgálókon kell konfigurálni. Kivéve, ha az interneten keresztül lehet kommunikálni az összekötő az Exchange és a SharePoint-kiszolgáló fogja, ez a név nem kell feloldani az interneten.

> [!IMPORTANT]
> Javasoljuk, hogy ne módosítsa ezt a nevet, mert kell majd törölje a tartalomvédelmi szolgáltatás konfigurációk ezek a kiszolgálók, és újra kell konfigurálnia a őket Exchange vagy a SharePoint-kiszolgálók használjanak az összekötő konfigurálása után.

Után neve jön létre a DNS-ben, és az IP-cím van beállítva, a terheléselosztási erre a címre irányítja a forgalmat a összekötő-kiszolgálók konfigurálása. Erre a célra, amely tartalmazza a hálózati terheléselosztás (NLB) szolgáltatást a Windows Server IP-alapú terheléselosztó bármely is használhatja. További információ: [terheléselosztás telepítési útmutatóját](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx).

A következő beállítások segítségével konfigurálhatja a hálózati Terheléselosztási fürt:

-   Portok: 80-as (HTTP) vagy a 443-as (HTTPS)

    A HTTP vagy HTTPS PROTOKOLLT használ-e kapcsolatos további információkért lásd a következő szakaszban.

-   Kapcsolat: Nincs

-   Elosztási módszer: Egyenlő

Ez a név a terheléselosztást alkalmazó rendszert (a kiszolgálók, az összekötő szolgáltatást az RMS) meghatározó később fogja használni, amikor konfigurálja a helyszíni kiszolgálók Azure RMS Alkalmazást szervezete RMS összekötő neve.

## <a name="BKMK_ConfiguringHTTPS"></a>A HTTPS PROTOKOLLT használja az RMS-összekötő konfigurálása
> [!NOTE]
> Ez a konfigurációs lépés kötelező, de ajánlott a biztonság további erősítése.

Bár a TLS vagy az SSL használata nem kötelező, az RMS-összekötőhöz, ajánlott a HTTP-alapú biztonsági szempontból kényes szolgáltatáshoz. Ez a konfiguráció hitelesíti a kiszolgálókon az összekötő az Exchange és a SharePoint-kiszolgáló számára az összekötőt használja. Emellett az összekötő ezen kiszolgálók által küldött összes adatok titkosítása.

Ahhoz, hogy az RMS-összekötőt használhatja a TLS Protokollt, az RMS-összekötőt futtató minden egyes kiszolgálón telepítse a kiszolgálói hitelesítési tanúsítványt, amely a nevét tartalmazza, amely az összekötőt használja. Például, ha meghatározott az RMS-összekötő nevére a DNS-van **rmsconnector.contoso.com**, kiszolgálói hitelesítési tanúsítványt tartalmazó telepítése **rmsconnector.contoso.com** a tanúsítvány tárgyában csupa kisbetűvel köznapi neveként. Megadhat **rmsconnector.contoso.com** a DNS-értéket, a tanúsítvány alternatív neveként. A tanúsítvány nem rendelkezik a kiszolgáló nevét tartalmazza. Ezután az IIS-ben, a tanúsítvány kötése az az alapértelmezett webhely.

Használja a HTTPS-beállítást, ha győződjön meg arról, hogy az összekötő futtató összes kiszolgáló rendelkezik-e egy érvényes kiszolgálói hitelesítési tanúsítványt, az Exchange és a SharePoint-kiszolgáló megbízható főtanúsítványhoz kapcsolódik. Emellett ha az összekötő-kiszolgálókon a tanúsítványait kiállító hitelesítésszolgáltató (CA) közzéteszi a visszavont tanúsítványok listájának (CRL), az Exchange és a SharePoint-kiszolgálókat fel kell tudni töltse le a CRL-t.

> [!TIP]
> Használhatja a következő információk és erőforrások segítséget, és telepítse a kiszolgálói hitelesítési tanúsítványt, és ez a tanúsítvány kötése a az alapértelmezett webhely az IIS-ben:
> 
> -   Active Directory tanúsítványszolgáltatások (AD CS) és egy vállalati hitelesítésszolgáltató (CA) segítségével a kiszolgáló hitelesítési tanúsítványok központi telepítésére, ha ismétlődő, és a webkiszolgáló-tanúsítvány sablonja majd használni. Ez a tanúsítványsablon használja **a kérelemben megadott** a tanúsítvány tulajdonos neve, ami azt jelenti, hogy a tanúsítvány igénylésekor adhat meg a tanúsítvány tulajdonos neve vagy a tulajdonos alternatív neve az RMS-összekötő neve teljesen minősített Tartománynevét.
> -   Ha a tanúsítvány megvásárlása egy másik vállalat vagy az önálló hitelesítésszolgáltató használata esetén olvassa el [Internet kiszolgálói tanúsítványok beállítása (IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) a a [webkiszolgáló (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) TechNet dokumentációs könyvtárában.
> -   A tanúsítványt használja az IIS konfigurálása, lásd: [egy kötés hozzáadása a webhelyhez (IIS 7)](http://technet.microsoft.com/library/cc731692.aspx) a a a a [webkiszolgáló (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) TechNet dokumentációs könyvtárában.

## <a name="BKMK_ConfiguringWebProxy"></a>Az RMS-összekötő proxy-webkiszolgáló konfigurálása
Ha az összekötő kiszolgálók olyan hálózathoz, amely nem rendelkezik közvetlen internetkapcsolattal, és a proxy-webkiszolgáló manuális konfigurálást igényel, az Internet-hozzáférés kimenő van telepítve, konfigurálnia kell a beállításjegyzék ezeken a kiszolgálókon az RMS-összekötőhöz.

#### Proxy-webkiszolgálót használ az RMS-összekötő konfigurálása

1.  Az RMS-összekötő szolgáltatást futtató kiszolgálókon nyissa meg a Beállításszerkesztőt a Regedit például.

2.  Navigáljon a **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  A karakterlánc típusú értékként hozzáadása **ProxyAddress** és adja meg az adatok ehhez az értékhez **http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;**

    Példa: **http://proxyserver.contoso.com:8080**

4.  Zárja be a Beállításszerkesztőt, és indítsa újra a kiszolgálót, vagy az IIS újraindítására IISReset parancs végrehajtását.

## <a name="BKMK_InstallingStandaloneTool"></a>Az RMS-összekötő felügyeleti eszköz telepítése rendszergazdai számítógépeken
Az RMS-összekötő felügyeleti eszköz futtatva olyan számítógépre, amely nem rendelkezik az RMS-összekötő telepítve, ha a számítógép megfelel-e a következő követelményeknek:

-   Windows Server 2012 vagy Windows Server 2012 R2 (az összes verzió), Windows Server 2008 R2 vagy Windows Server 2008 R2 Service Pack 1 (összes verzió), Windows 8.1, Windows 8, vagy Windows 7 rendszerű fizikai vagy virtuális gép.

-   Legalább 1 GB RAM.

-   Legalább 64 GB lemezterület szükséges.

-   Legalább egy hálózati adaptert.

-   Az interneten keresztül tűzfal (vagy webes proxy) való hozzáférést.

Az RMS-összekötő felügyeleti eszköz telepítéséhez futtassa a következő fájlokat:

-   32 bites számítógép esetén: RMSConnectorAdminToolSetup_x86.exe

-   64 bites számítógép esetén: RMSConnectorSetup.exe

Ha még nem töltve ezeket a fájlokat, azt megteheti az a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

## <a name="ConfiguringServers"></a>Az RMS-összekötő használatához kiszolgálók konfigurálása
Után telepítette, valamint elvégezte az RMS-összekötő konfigurálását, készen áll a használja a Rights Management és Azure RMS az összekötő használatával kapcsolódnak a helyszíni kiszolgálók konfigurálása. Ez azt jelenti, hogy a következő kiszolgálók konfigurálása:

-   Az Exchange 2013: Ügyfélelérési kiszolgálók és a postaláda-kiszolgálókon

-   Az Exchange 2010: Ügyfélelérési kiszolgálók és a központ átviteli kiszolgálók

-   A SharePoint: A SharePoint előtér-Webkiszolgalok, beleértve a központi felügyeleti kiszolgálót futtató

-   A fájl besorolást infrastruktúra: Windows Server rendszerű számítógépek, amelyek telepítették a fájl erőforrás-kezelő

Ez a konfiguráció van szükség a beállításjegyzék-beállításokat. Ehhez két lehetősége van:

|Konfigurációs beállítás|Előnyei|Hátrányok|
|---------------------------|-----------|-------------|
|Automatikus Microsoft RMS összekötő a kiszolgálókonfigurációs eszköz használatával|Nincs közvetlen szerkesztése a beállításjegyzékben. Ez az automatikus parancsfájl használatával.<br /><br />Nem szükséges a Microsoft RMS URL-cím beszerzése a Windows PowerShell-parancsmagok futtatásához.<br /><br />Az Előfeltételek automatikus ellenőrzésre (de nem automatikusan kijavítja) Ha helyileg futtatja.|Az eszköz futtatásakor meg kell nyitnia egy olyan kiszolgálóra, amely már fut az RMS-összekötő kapcsolat.|
|A beállításjegyzék szerkesztésével manuálisan|Nincs kapcsolata az RMS-összekötőt futtató kiszolgálóra szükség.|További felügyeleti pluszköltséggel jár, amelyek hibalehetőséget.<br /><br />Be kell szereznie a Microsoft RMS URL-CÍMÉT, amelyhez szükség van a Windows PowerShell-parancsok futtatásához.<br /><br />Mindig ellenőriznie kell az előfeltétel-ellenőrzések saját magát.|
> [!IMPORTANT]
> Mindkét esetben manuálisan kell bármely előfeltétel telepítse és konfigurálja a Exchange, SharePoint és fájl besorolást infrastruktúra használja a Rights Management.

A legtöbb szervezet számára a kiszolgálókonfigurációs eszköz használatával a Microsoft RMS összekötő automatikus konfigurációja lesz jobb megoldás, mivel így nagyobb hatékonyság és megbízhatóság mint manuális konfiguráció.

Ezeken a kiszolgálókon a konfigurációs módosítások elvégzése után újra kell indítania őket ha futnak az Exchange-hez vagy a SharePoint és a korábban beállított Active Directory tartalomvédelmi szolgáltatások használatára. Ezek a kiszolgálók újraindítását beállításakor őket a Rights Management először nincs szükség van. Mindig újra kell indítania a fájlkiszolgálóra, amelynek fájl besorolást infrastruktúra használata a konfigurációs módosítások elvégzése után van konfigurálva.

#### A kiszolgálókonfigurációs eszköz használata a Microsoft RMS-összekötő

1.  Ha még nem töltve a parancsfájl a kiszolgálókonfigurációs eszköz Microsoft RMS-összekötőhöz (GenConnectorConfig.ps1), letöltheti a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

2.  Mentse a GenConnectorConfig.ps1 fájlt azon a számítógépen ahol az eszköz fog futni. Ha helyileg futtatja az eszközt, ez a kiszolgáló konfigurálása az RMS-összekötő folytatott kommunikációhoz használni kívánt kell lennie. Ellenkező esetben mentheti minden olyan számítógépen.

3.  Döntse el, hogyan futtassa az eszközt:

    -   **Helyileg**: Futtathatja az eszközt interaktív módon, be kell állítani az RMS-összekötő kommunikálni a kiszolgálóról. Ez akkor hasznos, egyszeri konfigurálásához, például a tesztelési környezetben.

    -   **Szoftvertelepítést**: A beállításjegyzék fájljairól, majd központilag telepített egy vagy több megfelelő kiszolgálók egy rendszerek felügyeleti alkalmazás, amely támogatja a szoftver központi telepítése, mint a System Center Configuration Manager használatával előállításához eszköz futtatása

    -   **Csoportházirend-**: Az eszköz olyan parancsfájl, amely a kiszolgálók konfigurálását csoportházirend-objektumok hozhat létre a rendszergazda adhat előállításához futtathatja. Ez a parancsfájl az egyes kiszolgáló konfigurálva, hogy a rendszergazda ezután hozzárendelheti a megfelelő kiszolgálókat, amelyek egy csoportházirend-objektumot hoz létre.

    > [!NOTE]
    > Ez az eszköz a kiszolgálókat, amelyek az RMS-összekötő kommunikálnak, és ez a szakasz elején felsorolt konfigurálja. Ne futtassa az eszközt az RMS-összekötőt futtató kiszolgálókon.

4.  Indítsa el a Windows PowerShell a **futtassa rendszergazdaként** lehetőséget, és a Get-help paranccsal útmutatást az eszköz a kiválasztott konfigurációs módszer használatával hogyan lehet:

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

Futtassa a parancsfájlt, a szervezet az RMS-összekötő URL-CÍMÉT kell megadnia. Adja meg a protokoll-előtag (HTTP:// vagy HTTPS://) és az Ön által megadott DNS-ben az elosztott terhelésű cím, az összekötő összekötő nevét. Például https://connector.contoso.com. Az eszköz majd forduljon az RMS-összekötőt futtató kiszolgáló URL-címet használ, és más paramétereket, amelyeket a szükséges konfigurációk létrehozásához használt beszerzése.

> [!IMPORTANT]
> Ez az eszköz futtatásakor győződjön meg arról, hogy a szervezet és a nem a egyetlen az RMS összekötő-szolgáltatást futtató kiszolgáló nevét adja meg az RMS terhelésű összekötő nevét.

A következő részekben részletes információkat az egyes szolgáltatás:

-   [Configuring an Exchange server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ExchangeServer)

-   [Configuring a SharePoint server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringSharePoint)

-   [Configuring a file server for File Classification Infrastructure to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_FileServer)

> [!NOTE]
> Ezek a kiszolgálók konfigurálása után az összekötő használatára, ügyfél ezeken a kiszolgálókon helyileg telepített alkalmazások nem működik együtt az RMS. Ez akkor fordul elő, ha van, mert az alkalmazás próbálja a connector használata az RMS közvetlenül, ami nem támogatott használata helyett.
> 
> Emellett ha egy Exchange server Office 2010 helyben van telepítve, az ügyfélalkalmazás Tartalomvédelmi szolgáltatások működni erről a számítógépről után a kiszolgáló az összekötő használatára van konfigurálva, de ez nem támogatott.
> 
> Mindkét esetben telepítenie kell az ügyfélalkalmazások külön számítógépeken, amelyek nincsenek beállítva az összekötő használatához. Akkor lesz majd megfelelően RMS közvetlenül használható.

### <a name="BKMK_ExchangeServer"></a>Használja az összekötő egy Exchange-kiszolgáló konfigurálása
A következő Exchange-szerepkörök kommunikálnak az RMS-összekötő:

-   Az Exchange 2013: Ügyfél-hozzáférési kiszolgáló és a postaláda-kiszolgáló

-   Az Exchange 2010: Ügyfélelérési kiszolgáló és a Továbbítókiszolgáló központ

Az RMS-összekötő használata esetén ezek a Exchange-et futtató kiszolgálók a következő szoftververziók egyikét kell futtatnia:

-   Exchange Server 2013, az Exchange 2013 3. összesítő frissítést

-   Exchange Server 2010, Exchange 2010 Service Pack 3. kumulatív frissítés 6 a

Is ezeken a kiszolgálókon, az RMS-ügyfél, amely támogatja az RMS titkosítási mód 2-es telepíteni kell. A minimális verziója, amely támogatja a Windows Server 2008 része, amely letölthető gyorsjavítás [RSA kulcshossz 2048 bit növelni az AD RMS a Windows Server 2008 R2 és a Windows Server 2008](http://support.microsoft.com/kb/2627272). A minimális verziója a Windows Server 2008 R2 tölthető le: [RSA kulcshossz 2048 bit megnöveli az AD RMS Windows 7 vagy Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Windows Server 2012 és a Windows Server 2012 R2 natív módon támogatja a 2. kriptográfiai mód.

> [!IMPORTANT]
> Ezeket és az Exchange és az RMS-ügyfél újabb verzióit nincs telepítve, ha nem tudják használni az összekötő az Exchange konfigurálása. Ellenőrizze, hogy ezek a fájlok telepítve vannak a folytatás előtt.

##### Az összekötő használatához az Exchange-kiszolgálók konfigurálása

1.  Az Exchange kiszolgálói szerepkörök, amelyek az RMS-összekötő kommunikálnak tegye a következők valamelyikét:

    -   A kiszolgáló konfigurációs eszközt a Microsoft RMS összekötő futtatni. További információ: [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) Ebben a témakörben.

        Ha például az Exchange 2013-t futtató kiszolgálókon helyileg megadását az eszköz futtatásához:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
        ```

    -   Manuális beállításjegyzéket ügyeljen az alábbi szakaszok a táblázatok segítségével manuálisan adja hozzá a beállításjegyzék-beállításokat a kiszolgálókon.

2.  Engedélyezze az Exchange Tartalomvédelmi szolgáltatás. További információ: [információk Rights Management eljárások](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx) az Exchange-könyvtárban.

Használja az alábbi szakaszok a táblázatok, csak akkor, ha szeretné manuálisan adja hozzá, vagy ellenőrizze a beállításjegyzék-beállítások ezeken a kiszolgálókon és a kiszolgálók az RMS-összekötő konfigurálása. Útmutatás a következő táblák használata esetén:

-   *MicrosoftRMSURL* a szervezet a Microsoft RMS szolgáltatás URL-cím. Ez az érték keresése:

    1.  Futtassa a [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) Azure RMS parancsmagot. Ha még nem telepítette a Windows PowerShell-modul az Azure RMS, lásd: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

    2.  Az kimenetében azonosíthatja a **LicensingIntranetDistributionPointUrl** értéket.

        Példa: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Távolítsa el a értékből **/_wmcs/licencelés** a karakterláncból. A fennmaradó karakterlánca a Microsoft RMS URL-CÍMÉT. A fenti példában a Microsoft RMS URL-címe a következő érték néz ki:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.RMS.nA.aadrm.com**

-   *ConnectorFQDN* az összekötő a DNS-ben definiált terheléselosztó neve. Például **rmsconnector.contoso.com**.

-   Használja a HTTPS előtaggal összekötő URL-címe, ha beállította a HTTPS protokoll használatát a helyszíni kiszolgálók kommunikálni az összekötő. További információ: a [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) című szakaszában talál. A Microsoft RMS URL-címek mindig HTTPS PROTOKOLLT használják.

#### A beállításjegyzék-beállítások az Exchange 2013 tábla

|Beállításjegyzékbeli elérési utat|Típusa|Érték|Adatok|
|-------------------------------------|----------|---------|----------|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation|REG_SZ|Alapértelmezett|https://*MicrosoftRMSURL/_wmcs/certification*|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|REG_SZ|Alapértelmezett|https://MicrosoftRMSURL/_wmcs/Licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|

#### A beállításjegyzék-beállítások az Exchange 2010 tábla

|Beállításjegyzékbeli elérési utat|Típusa|Érték|Adatok|
|-------------------------------------|----------|---------|----------|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation|REG_SZ|Alapértelmezett|https://*MicrosoftRMSURL*/_wmcs/certification|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|REG_SZ|Alapértelmezett|https://*MicrosoftRMSURL*/_wmcs/licencelés|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|

### <a name="BKMK_ConfiguringSharePoint"></a>Az összekötő használatához SharePoint-kiszolgáló konfigurálása
A következő SharePoint-szerepkörök kommunikálnak az RMS-összekötő:

-   A SharePoint előtér-Webkiszolgalok, beleértve a központi felügyeleti kiszolgálót futtató

Az RMS-összekötő használata esetén ezek SharePoint futtató kiszolgálók a következő szoftververziók egyikét kell futtatnia:

-   A SharePoint Server 2013

-   A SharePoint Server 2010

A SharePoint 2013-kiszolgálón is futnia kell egy from1.0.622.34 keresztül 1.0.10907.0 van MSIPC ügyfél 2.1-es verziója.

> [!WARNING]
> Az MSIPC 2.1 ügyfelet több verzióját, ezért győződjön meg arról, a cikkben hivatkozott verziója.
> 
> Ellenőrizheti az ügyfél verzióját MSIPC.dll található verziószámát ellenőrzésével **\Program Files\Active Directory Rights Management Services Client 2.1**. A Tulajdonságok párbeszédpanelen jeleníti meg az MSIPC 2.1 ügyfelet verziószámát.

Ezek a SharePoint 2010 rendszert futtató kiszolgálók az MSDRM ügyfél, amely támogatja az RMS titkosítási mód 2-es telepítve kell lennie. A minimális verziója, amely támogatja a Windows Server 2008 része, amely letölthető gyorsjavítás [RSA kulcshossz 2048 bit növelni az AD RMS a Windows Server 2008 R2 és a Windows Server 2008](http://support.microsoft.com/kb/2627272), és a minimális verziója a Windows Server 2008 R2 tölthető le: [RSA kulcshossz 2048 bit megnöveli az AD RMS Windows 7 vagy Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Windows Server 2012 és a Windows Server 2012 R2 natív módon támogatja a 2. kriptográfiai mód.

##### Az összekötő használatához SharePoint-kiszolgálók konfigurálása

1.  A SharePoint-kiszolgálóra, amely az RMS-összekötő kommunikálni tegye a következők valamelyikét:

    -   A kiszolgáló konfigurációs eszközt a Microsoft RMS összekötő futtatni. További információ: [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) Ebben a témakörben.

        Ha például a SharePoint 2013-t futtató kiszolgálókon helyileg konfigurálandó eszköz futtatásához:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   Ha a SharePoint 2013 rendszer használata esetén győződjön manuális beállításjegyzéket az alábbi szakasz a táblázat segítségével manuálisan adja hozzá a beállításjegyzék-beállításokat a kiszolgálókon.

2.  Engedélyezze a SharePoint IRM. További információ: [konfigurálása tartalomvédelmi szolgáltatással (SharePoint Server 2010)](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx) a SharePoint-könyvtárban.

    Ha ezek a lépések konfigurálnia kell a SharePoint használata az összekötő megadásával **használata az RMS-kiszolgáló**, és írja be a terheléselosztó összekötő URL-cím beállított. Adja meg a protokoll-előtag (HTTP:// vagy HTTPS://) és az Ön által megadott DNS-ben az elosztott terhelésű cím, az összekötő összekötő nevét. Például ha az összekötő neve https://connector.contoso.com, a konfiguráció következőhöz hasonló az alábbi képen látható:

    ![](../Image/AzRMS_SharePointConnector.png)

    Miután tartalomvédelmi szolgáltatás engedélyezve van a SharePoint-farm, az egyes tárak a tartalomvédelmi szolgáltatás használatával engedélyezheti a **tartalomvédelmi** beállítást a **Könyvtárbeállítások** lapon az egyes könyvtárak.

    > [!IMPORTANT]
    > A SharePoint RMS elérni az összekötőt engedélyeznie kell a megfelelő fiókokat az RMS-összekötő felügyeleti eszköz. Ha még nem tette meg ezt, lásd: [Authorizing servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#AuthorizingServers) Ebben a témakörben.

A táblázat használható a következő szakaszban csak akkor, ha szeretné manuálisan adja hozzá, vagy ellenőrizze a beállításjegyzék beállításait a SharePoint 2013 futtató kiszolgáló.

#### A SharePoint 2013 beállításjegyzék beállításaival kapcsolatban tábla
Ez a tábla használatával utasításokat:

-   *MicrosoftRMSURL* a szervezet a Microsoft RMS szolgáltatás URL-cím. Ez az érték keresése:

    1.  Futtassa a [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) Azure RMS parancsmagot. Ha még nem telepítette a Windows PowerShell-modul az Azure RMS, lásd: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

    2.  Az kimenetében azonosíthatja a **LicensingIntranetDistributionPointUrl** értéket.

        Példa: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Távolítsa el a értékből **/_wmcs/licencelés** a karakterláncból. A fennmaradó karakterlánca a Microsoft RMS URL-CÍMÉT. A fenti példában a Microsoft RMS URL-címe a következő érték néz ki:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.RMS.nA.aadrm.com**

-   *ConnectorFQDN* az összekötő a DNS-ben definiált terheléselosztó neve. Például **rmsconnector.contoso.com**.

-   Használja a HTTPS előtaggal összekötő URL-címe, ha beállította a HTTPS protokoll használatát a helyszíni kiszolgálók kommunikálni az összekötő. További információ: a [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) című szakaszában talál. A Microsoft RMS URL-címek mindig HTTPS PROTOKOLLT használják.

|Beállításjegyzékbeli elérési utat|Típusa|Érték|Adatok|
|-------------------------------------|----------|---------|----------|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection|REG_SZ|https://*MicrosoftRMSURL*/_wmcs/licencelés|Attól függően, hogy a HTTP vagy HTTPS a SharePoint-kiszolgáló az RMS-összekötővel, a következők egyike:<br /><br />-   http://*ConnectorFQDN*/_wmcs/licencelés<br />-   https://*ConnectorFQDN*/_wmcs/licencelés|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification|REG_SZ|Alapértelmezett|Attól függően, hogy a HTTP vagy HTTPS a SharePoint-kiszolgáló az RMS-összekötővel, a következők egyike:<br /><br />-   http://*ConnectorFQDN*/_wmcs/certification<br />-   https://*ConnectorFQDN*/_wmcs/certification|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing|REG_SZ|Alapértelmezett|Attól függően, hogy a HTTP vagy HTTPS a SharePoint-kiszolgáló az RMS-összekötővel, a következők egyike:<br /><br />-   http://*ConnectorFQDN*/_wmcs/licencelés<br />-   https://*ConnectorFQDN*/_wmcs/licencelés|

### <a name="BKMK_FileServer"></a>Fájlkiszolgáló fájl besorolást infrastruktúra használata az összekötő konfigurálása
Office-dokumentumok védelme használja az RMS-összekötő és a fájl besorolást infrastruktúra, a fájlkiszolgáló a következő operációs rendszerek egyikét kell futtatnia:

-   Windows Server 2012 R2

-   Windows Server 2012

##### Az összekötő használatához fájlkiszolgálók konfigurálása

1.  A fájl besorolást infrastruktúra, és hogy konfigurált kiszolgálók kommunikálnak, az RMS-összekötő fájlt tegye a következők valamelyikét:

    -   A kiszolgáló konfigurációs eszközt a Microsoft RMS összekötő futtatni. További információ: [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) Ebben a témakörben.

        Ha például a helyben történő FCI fájlkiszolgálót konfigurálása eszköz futtatásához:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    -   Manuális beállításjegyzéket ügyeljen az alábbi szakasz a táblázat segítségével manuálisan adja hozzá a beállításjegyzék-beállításokat a kiszolgálókon.

2.  Besorolási szabályok és fájlkezelési feladatok az RMS titkosítási dokumentumok védelméhez létrehozását, és adja meg az RMS-RMS házirendek automatikusan alkalmazandó sablont. További információ: [Fájlkiszolgálói erőforrás-kezelő – áttekintés](http://technet.microsoft.com/library/hh831701.aspx) a Windows Server dokumentációs könyvtárában.

A táblázat használható a következő szakaszban csak akkor, ha szeretné manuálisan adja hozzá, vagy ellenőrizze a beállításjegyzék-beállításokat használja a fájl besorolást infrastruktúra védelmére dokumentum fájlkiszolgálón.

#### A fájlkiszolgáló és a fájl besorolást infrastruktúra a beállításjegyzék beállításai
Ez a tábla használatával utasításokat:

-   *ConnectorFQDN* az összekötő a DNS-ben definiált terheléselosztó neve. Például **rmsconnector.contoso.com**.

-   Használja a HTTPS előtaggal összekötő URL-címe, ha beállította a HTTPS protokoll használatát a helyszíni kiszolgálók kommunikálni az összekötő. További információ: a [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) című szakaszában talál. A Microsoft RMS URL-címek mindig HTTPS PROTOKOLLT használják.

|Beállításjegyzékbeli elérési utat|Típusa|Érték|Adatok|
|-------------------------------------|----------|---------|----------|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|REG_SZ|Alapértelmezett|http://*ConnectorFQDN*/_wmcs/licencelés|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation|REG_SZ|Alapértelmezett|http://*ConnectorFQDN*/_wmcs/certification|

## <a name="BKMK_NextSteps"></a>Az alábbi lépéseket
Most, hogy az RMS-összekötő telepítve és konfigurálva van, és a kiszolgálók, használatára vannak konfigurálva, a rendszergazdák és felhasználók is védeni és e-mailben és dokumentumok lefoglalhatja Azure RMS segítségével. Ahhoz, hogy ez könnyen a felhasználók számára, telepítse az RMS-megosztó alkalmazás, amely egy bővítmény telepíti az Office, és kattintson a jobb gombbal új lehetőségeket hozzáadja a Fájlkezelőben. További információ: a [Rights Management megosztóalkalmazás rendszergazdai útmutatója](http://technet.microsoft.com/library/%20dn339003%28v=ws.10%29.aspx).

Emellett érdemes figyelembe venni az RMS-összekötő és Azure RMS Alkalmazást szervezete használatának figyeléséhez nyújt segítséget a következő:

-   A beépített **Microsoft Rights Management összekötő** teljesítményszámlálókat.

-   A [RMS Analyzer eszköz](https://www.microsoft.com/en-us/download/details.aspx?id=46437), segítséget nyújtanak az RMS összekötő beállítást használja az összekötő állapotának figyelésére és esetleges konfigurációs problémák azonosításához.

-   [Naplózás, és az Azure Rights Management használati elemzése](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md)

Használhatja a [Azure Rights Management – üzembehelyezési menetrend](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) történő ellenőrzése, hogy további konfigurációs lépéseket forgassa előtt célszerű [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] felhasználók és rendszergazdák. Ha nincs más konfigurációs lépéseket kíván megtekinteni, [Azure Rights Management használata](../Topic/Using_Azure_Rights_Management.md) a sikeres telepítés támogatása a szervezet működési útmutatást.

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

