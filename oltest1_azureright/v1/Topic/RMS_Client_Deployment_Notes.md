---
description: na
keywords: na
title: RMS Client Deployment Notes
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
---
# RMS-&#252;gyf&#233;l telep&#237;t&#233;si megjegyz&#233;sek
A tartalomvédelmi szolgáltatás-ügyfél (RMS-ügyfelet) verziója 2 a MSIPC ügyfél is nevezik. Szoftver Windows rendszerű számítógép kommunikáló a Microsoft Rights Management services helyszíni vagy a felhőben való hozzáférés és védelme használati adatok, alkalmazások és eszközök – tranzakciós belül a határokat a szervezet, vagy azok kívül felügyelt határokat. A szállítási címhez tartozó rendelkező kívül a [Rights Management megosztóalkalmazás Windows](https://technet.microsoft.com/library/dn919648.aspx), érhető el az RMS-ügyfél [egy választható le](http://www.microsoft.com/download/details.aspx?id=38396) amely, nyugtázási és a hozzá tartozó licencszerződés elfogadása szabadon terjeszthető a harmadik féltől származó szoftverek, hogy az ügyfelek védelmét, és a Rights Management szolgáltatások által védett tartalmakat.

Ez a témakör tartalmaz a következő szakaszok:

-   [Az RMS-ügyfél kiosztatlan](#BKMK_RedistributeInstaller)

-   [Az RMS-ügyfél telepítése](#BKMK_InstallClient)

-   [Az RMS-ügyfél kapcsolatos kérdések és válaszok](#BKMK_QA)

-   [RMS-ügyfél beállítások](#BKMK_Settings)

-   [Active Directory tartalomvédelmi szolgáltatások csak: Az RMS-ügyfél használandó korlátozása megbízható Active Directory Tartalomvédelmi kiszolgálók](#BKMK_UsingTrustedServers)

-   [RMS szolgáltatás felderítése](#BKMK_ServiceDiscovery)

## <a name="BKMK_RedistributeInstaller"></a>Az RMS-ügyfél kiosztatlan
Az RMS-ügyfél is szabadon terjeszti és más alkalmazások és az informatikai megoldások kapcsolt. Ha egy alkalmazás fejlesztői vagy a megoldás szolgáltató és kívánja terjeszteni az RMS-ügyfelet, két lehetőség áll rendelkezésére:

-   Ajánlott: Az alkalmazás telepítési az RMS-ügyfél telepítő beágyazni, és futtassa azt a csendes módban (a **/quiet** kapcsoló, a következő szakaszban részletes).

-   Adja meg az alkalmazás előfeltételként szükséges az RMS-ügyfelet. Ezzel a beállítással szükség lehet beszerzése, telepítéséhez és frissítse a számítógépeket az ügyfél csak akkor az alkalmazás, hogy a további tudnivalókat a felhasználók számára.

## <a name="BKMK_InstallClient"></a>Az RMS-ügyfél telepítése
Az RMS-ügyfél nevű telepítő végrehajtható fájl megtalálható **setup_msipc_***&lt; arch &gt;***.exe**, ahol *&lt; arch &gt;* vagy **x86** (az ügyfélszámítógépek 32 bites) vagy **x64** (a 64 bites ügyfélszámítógépek). A 64 bites (x 64) a telepítő a csomag telepíti, mind a 32 bites futásidejű végrehajtható egy 64 bites operációs rendszer telepítése a futó 32 bites alkalmazásokkal való kompatibilitás érdekében, valamint egy 64 bites futásidejű végrehajtható támogatja a natív 64 bites alkalmazásokat. A 32 bites (x 86) a telepítő nem fog futni egy 64 bites Windows-telepítés.

> [!NOTE]
> Telepítse az RMS-ügyfél, például a helyi számítógépen a Rendszergazdák csoport tagjának emelt szintű joggal kell rendelkeznie.

Az RMS-ügyfél által az alábbi telepítési módszerek valamelyikével telepítheti:

-   **Csendes mód.** Használatával a **/quiet** Váltás a parancssori kapcsolók részeként csendes telepítheti az RMS-ügyfél azokon a számítógépeken. A következő példában a telepítési csendes üzemmód az RMS-ügyfél egy 64 bites ügyfélszámítógépen:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Interaktív módban.** Ehelyett az RMS-ügyfél is telepítheti a GUI-alapú telepítőprogram az RMS Ügyféltelepítő varázsló által biztosított használatával. Ehhez kattintson duplán az RMS-ügyfél telepítőcsomag (**setup_msipc_***&lt; arch &gt;***.exe**), amelyhez lett másolt vagy a helyi számítógépen le a mappában.

## <a name="BKMK_QA"></a>Az RMS-ügyfél kapcsolatos kérdések és válaszok
A következő szakaszban az RMS-ügyfél és a válaszok kapcsolatos gyakori kérdések tartalmazza.

### Melyik operációs rendszereket támogatja az RMS-ügyfél?
Az RMS-ügyfél a következő operációs rendszerekben támogatott:

|Windows Server operációs rendszer|Ügyféloldali Windows operációs rendszer|
|-------------------------------------|-------------------------------------------|
|Windows Server 2012 R2|A Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 SP1 minimális|
|Windows Server 2008 (csak az AD RMS)|Windows Vista SP2 minimális (csak az AD RMS)|

### Melyik processzor vagy a platformok támogatja az RMS-ügyfél?
Az RMS-ügyfél x 86 és a platformok számítástechnika x 64 támogatott.

### Az RMS-ügyfelet futtató?
Alapértelmezés szerint az RMS-ügyfél telepítve van-e %ProgramFiles%\Active Directory Rights Management szolgáltatások ügyfél 2. &lt; a verziószáma kisebb &gt;.

### Milyen fájlok társítva az RMS-ügyfélszoftver?
A következő fájlokat telepíti az RMS-ügyfélszoftver részeként:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Mellett ezeket a fájlokat az RMS-ügyfél is telepít többnyelvű felhasználói felület (MUI) fájlok 44 nyelven. Támogatott nyelvek ellenőrzéséhez futtassa az RMS-ügyfél telepítése, és a telepítés befejezésekor, tekintse át az alapértelmezett elérési út alatt a többnyelvű támogatási mappák tartalmát.

### Az alapértelmezés szerint az RMS-ügyfél, támogatott operációs rendszer telepítése?
Szám Ez az RMS-ügyfél verziója egy választható le, amely telepíthető alkalmazásáruházból külön-külön számítógépeken futó a Microsoft Windows operációs rendszer támogatott verzióit.

### Az RMS-ügyfél automatikusan frissíti a Microsoft Update?
Ha ez az RMS-ügyfél telepítve van a csendes telepítés lehetőség használatával, a az RMS-ügyfél örökli a jelenlegi Microsoft Update-beállításokat. Ha az RMS-ügyfél a GUI-alapú telepítőprogram használatával telepítve van, az RMS-ügyfél telepítővarázsló kéri ahhoz, hogy a Microsoft Update.

## <a name="BKMK_Settings"></a>RMS-ügyfél beállítások
A következő szakaszban az RMS-ügyfél beállítások információt tartalmaz. Lehet, hogy ez az információ hasznos, ha az alkalmazások vagy az RMS-ügyfél használó szolgáltatások problémája van.

> [!NOTE]
> Egyes beállítások attól függ, hogy az RMS-enlightened alkalmazás fut-e egy ügyfélalkalmazás mód (például a Microsoft Word és az Outlook vagy a az RMS-megosztó alkalmazás) vagy a kiszolgáló mód alkalmazások (például a SharePoint és az Exchange).  A következő táblák, ezek a beállítások azonosítják **ügyfélmód** és **kiszolgáló mód**, illetve.

### Az RMS-ügyfél tárolja az ügyfélszámítógépeken licencek, ahol
Az RMS-ügyfél licencek tárolja a helyi lemezen, és is gyorsítótárába bizonyos információk a Windows beállításjegyzékében.

|Leírása|Ügyfél mód elérési utak|Kiszolgáló mód elérési utak|
|-----------|---------------------------|-------------------------------|
|Licenc tárolási helye|%localappdata%\Microsoft\MSIPC|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\*&lt; SID &gt;*\|
|Sablon tárolási helye|%localappdata%\Microsoft\MSIPC\Templates|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\Templates\*&lt; SID &gt;*\|
|Beállításjegyzék-helyhez|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local beállítások<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \*&lt; SID &gt;*|
> [!NOTE]
> *&lt; SID &gt;* van a biztonsági azonosítója (SID), a fiók, amely alatt a kiszolgálói alkalmazás fut. Például, ha az alkalmazás fiókkal fut-e a beépített hálózati szolgáltatás, cserélje ki *&lt; SID &gt;* a jól ismert (S-1-5-20), a fiók SID-értékkel.

### Az RMS-ügyfelet Windows beállításjegyzék-beállításai
Windows-beállításkulcsok segítségével beállítása vagy néhány RMS-ügyfél beállítások módosítása. Például az RMS-enlightened alkalmazások, amelyek az Active Directory tartalomvédelmi szolgáltatások kiszolgálókkal kommunikálni rendszergazdaként érdemes lehet frissíteni a vállalati szolgáltatás helyét (felülbírálás a AD RMS-kiszolgáló közzétételre kiválasztott) attól függően, hogy az Active Directory-topológia az ügyfélszámítógépen aktuális helyét. Vagy, érdemes lehet az ügyfélszámítógépen az RMS-enlightened alkalmazás probléma elhárítását segítő az RMS-nyomkövetés engedélyezése. A következő táblázat segítségével azonosítja a beállításjegyzék-beállítások, amelyek az RMS-ügyfél módosíthatja.

|A feladat|Beállítások|
|-------------|---------------|
|Active Directory tartalomvédelmi szolgáltatások csak: A vállalati szolgáltatás helyét, az ügyfélszámítógép frissítése|A következő beállításkulcsok frissítése:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />    REG_SZ: alapértelmezett<br />    **Érték:**&lt; http- vagy https-&gt; :// *RMS_Cluster_Name*/_wmcs/hitelesítő<br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />    REG_SZ: alapértelmezett<br />    **Érték:** &lt; http- vagy https-&gt; :// *RMS_Cluster_Name*/_wmcs/Licensing|
|Engedélyezése és letiltása a nyomkövetés|A frissítés a következő beállításjegyzék-kulcs:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />    REG_DWORD: Nyomkövetési<br />    **Érték:** 1-nyomkövetés, 0 letiltásához a nyomkövetés (alapértelmezett) engedélyezése|
|Sablonok frissítése napokban gyakoriságának módosítása|Milyen gyakran adja meg a következő beállításjegyzék-értékek frissülnek sablonok, ha nincs megadva a TemplateUpdateFrequencyInSeconds érték a felhasználó számítógépén.  Ezek az értékek egyike sem van beállítva, ha az alkalmazások az RMS-ügyfél (verzió 1.0.1784.0) segítségével lehet letölteni a sablonok alapértelmezett frissítési időköze 1 nap. Ez előtt verziónál 7 naponként, az alapértelmezett érték.<br /><br />**Ügyfélmód:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Érték:** Egész érték, amely megadja a közötti napok számát (legalább 1) letöltések.<br /><br />**Kiszolgáló mód:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Érték:** Egész érték, amely megadja a közötti napok számát (legalább 1) letöltések.|
|Módosíthatja a gyakorisága másodpercben sablonok frissítése **Important:** Ha ez meg van adva, a rendszer figyelmen kívül hagyja az érték frissítése a sablonok napokban. Adjon meg egy másik, vagy mindkettőt egyszerre nem.|Milyen gyakran adja meg a következő beállításjegyzék-értékek sablonok frissülnek, a felhasználó számítógépén. Ez az érték vagy az érték a gyakoriság módosítása a nap (TemplateUpdateFrequency) nincs megadva, az alapértelmezett frissítési időközt az RMS-ügyfél (verzió 1.0.1784.0) segítségével lehet letölteni a sablonok alkalmazások esetén 1 nap. Ez előtt verziónál 7 naponként, az alapértelmezett érték.<br /><br />**Ügyfélmód:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Érték:** Egész érték, amely megadja a közötti másodpercek számát (legalább 1) letöltések.<br /><br />**Kiszolgáló mód:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Érték:** Egész érték, amely megadja a közötti másodpercek számát (legalább 1) letöltések.|
|Active Directory tartalomvédelmi szolgáltatások csak: A következő közzétételi kérésére azonnal sablonok letöltése|Tesztelés és kiértékelések során szükség lehet az RMS-ügyfél-sablonokat letölteni a lehető legrövidebb időn belül. Ehhez hajtsa végre a, távolítsa el a következő beállításjegyzék-kulcs és az RMS-ügyfél fog töltse le a következő közzétételi kérésére azonnal sablonok ahelyett, várjon, amíg az idő, az TemplateUpdateFrequency beállításjegyzék beállításban megadott:<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; kiszolgálónév &gt; \Template **Note:** &lt; kiszolgálónév &gt; lehet külső (corprights.contoso.com) és a belső (corprights) URL-címek és ezért két különböző bejegyzéseket.|
|Active Directory tartalomvédelmi szolgáltatások csak: Összevont hitelesítési támogatásának engedélyezése|Ha az RMS-ügyfélszámítógép összevont megbízhatósági kapcsolat használatával csatlakozik egy Active Directory Tartalomvédelmi fürt, konfigurálnia kell a összevonási honos tartományt.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_SZ: : ÖsszevonásiKezdőTartomány<br />    **Érték:** Ez a bejegyzés értéke az egységes erőforrás-azonosító (URI) az összevonási szolgáltatás (például "https://fs-01.contoso.com").|
|Active Directory tartalomvédelmi szolgáltatások csak: A partner összevonási kiszolgálók, amelyek esetében az űrlapalapú hitelesítést a felhasználói bevitel támogatása|Alapértelmezés szerint az RMS-ügyfél beavatkozás nélküli üzemmódban működik és a felhasználói bevitel nem szükséges. A partner összevonási kiszolgálók, azonban lehet, hogy úgy, hogy megkövetelése a felhasználói bevitel ilyen űrlapalapú hitelesítés vállalja. Ebben az esetben, konfigurálnia kell az RMS-ügyfelet, hogy az összevont hitelesítési űrlap böngésző ablakban jelenik meg, és a felhasználó a hitelesítéshez van előléptetni, figyelmen kívül hagyja, hogy csendes mód.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_DWORD: EnableBrowser **Note:** Ha az összevonási kiszolgáló űrlapalapú hitelesítés használatára van konfigurálva, ez a kulcs meg kell adni. Ha az összevonási kiszolgáló integrált Windows-hitelesítés használatára van konfigurálva, akkor ez a kulcs nem szükséges.|
|Active Directory tartalomvédelmi szolgáltatások csak: Blokkolása ILS szolgáltatás fogyasztás|Alapértelmezés szerint az RMS-ügyfél lehetővé teszi, hogy a igénybe, a ILS szolgáltatás által védett tartalom, de konfigurálható, hogy az ügyfél számára, hogy blokkolja a szolgáltatás a következő beállításjegyzék-kulcs beállításával. Ha ezt a beállításkulcsot a ILS szolgáltatás blokkolása van beállítva, nyissa meg, és a ILS szolgáltatás által védett tartalmakat tett kísérletek ad vissza, a következő hiba miatt:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: **DisablePassportCertification**<br />    **Érték:** 1 blokkolása ILS felhasználás, 0, hogy a ILS-használat (alapértelmezett)|

### Az RMS-ügyfél sablon elosztásának kezelése
Sablonok megkönnyítik a felhasználók és a rendszergazdák számára, hogy gyorsan alkalmazása a Rights Management protection, és az RMS-ügyfél automatikusan letöltések sablonok az RMS-kiszolgálók, vagy a szolgáltatás, a következő mappába ennél a sablonok, az RMS-ügyfél nem bármely sablonok letöltése alapértelmezett helyéről, és nem ehelyett töltse le az ebben a mappában elhelyezett sablonok. Az RMS-ügyfél sablonok le a többi elérhető RMS-kiszolgálók továbbra is.

**Ügyfélmód:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Kiszolgáló mód:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\*&lt; SID &gt;*

Ez a mappa használatakor nem semmilyen különleges elnevezési szükséges, kivéve, hogy az RMS-kiszolgáló által a sablonok kell kiadni, vagy a szolgáltatás, és a .xml kiterjesztésű kell rendelkeznie. Például a Contoso-Confidential.xml vagy a Contoso-ReadOnly.xml olyan érvényes nevek.

## <a name="BKMK_UsingTrustedServers"></a>Active Directory tartalomvédelmi szolgáltatások csak: Az RMS-ügyfél használandó korlátozása megbízható Active Directory Tartalomvédelmi kiszolgálók
Lehet, hogy az RMS-ügyfél csak az adott megbízható Active Directory tartalomvédelmi szolgáltatások kiszolgálókon használatára, így a következő módosításokat a helyi számítógépen a Windows beállításjegyzékének korlátozva.

**RMS korlátozása ahhoz, hogy az ügyfél használata csak megbízható AD RMS-kiszolgálók**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Érték:** Ha meg van adva a nullától eltérő érték, az RMS-ügyfél csak a megadott kiszolgálókat, amelyek az TrustedServers és az Azure Rights Management szolgáltatás vannak beállítva lesz megbízható.

**A tagok hozzáadását a megbízható Active Directory tartalomvédelmi szolgáltatások kiszolgálók listája**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *&lt; URL_or_HostName &gt;*

    **Érték:** A beállításjegyzék-helyhez hozzáadott karakterlánc-érték vagy DNS-tartomány neve formátumú lehet (például **adrms.contoso.com**) vagy a teljes URL-cím a megbízható Active Directory tartalomvédelmi szolgáltatások kiszolgálók (például **https://adrms.contoso.com**). Ha a megadott URL-cím kezdete **https://**,  az RMS-ügyfél használandó SSL vagy TLS kapcsolatot létesíteni a megadott Active Directory tartalomvédelmi szolgáltatások-kiszolgálóval.

## <a name="BKMK_ServiceDiscovery"></a>RMS szolgáltatás felderítése
RMS szolgáltatás felderítése lehetővé teszi, hogy mely RMS-kiszolgáló vagy a szolgáltatás számára a kommunikációt a tartalom védelme előtt ellenőrizze az RMS-ügyfelet. Szolgáltatás felderítése is fordulhat elő, amikor az RMS-ügyfél a védett tartalom használ, de kevésbé valószínű, hogy fordulhat elő, mert a házirend, a tartalom csatolt tartalmaz, az elsődleges RMS-kiszolgáló vagy a szolgáltatás, és csak akkor, ha a művelet sikertelen nem az ügyfél futtassa szolgáltatás felderítése.

Szolgáltatás felderítése először megkeresi a Rights Management (AD RMS) helyszíni verzióját. Ha, amely nem sikerül, a szolgáltatás felderítése automatikusan megkeresi, az a Rights Management (Azure RMS) felhő verziója.

Egy helyszíni-telepítési szolgáltatás felderítése végrehajtásához az RMS-ügyfél ellenőrzi a következők:

1.  A Windows beállításjegyzékében a helyi számítógépen: Ha a szolgáltatás felderítési beállításai a beállításjegyzékben, először próbált ezeket a beállításokat.  Ezek a beállítások alapértelmezés szerint nincs konfigurálva a beállításjegyzékben.

2.  Active Directory tartományi szolgáltatások: Számítógép tartományhoz lekérdezi az Active Directory egy szolgáltatáskapcsolódási pontja (SCP). Ha Szolgáltatáskapcsolódási regisztrálva van, akkor az RMS-kiszolgáló URL-CÍMÉT adja vissza használni az RMS-ügyfél.

### Active Directory tartalomvédelmi szolgáltatások csak: Kiszolgálóoldali szolgáltatás felderítése engedélyezése az Active Directory segítségével
Ha a fiók nem rendelkezik megfelelő jogosultságokkal (a vállalati rendszergazdák és a helyi rendszergazda az Active Directory tartalomvédelmi szolgáltatások kiszolgáló), automatikusan regisztrálhatja a egy szolgáltatáskapcsolódási pontja (SCP), amikor telepíti az Active Directory tartalomvédelmi szolgáltatások gyökérkiszolgáló-fürt. Ha az erdő már létezik egy SCP, először előtt törölnie kell a meglévő SCP regisztrálhat, hogy egy új.

Regisztrálása, és törölje a Szolgáltatáskapcsolódási, a következő eljárással Active Directory tartalomvédelmi szolgáltatások telepítése után. Mielőtt elkezdené, győződjön meg arról, hogy a fiók rendelkezik-e a szükséges jogosultságokkal (a vállalati rendszergazdák és a helyi rendszergazda az Active Directory tartalomvédelmi szolgáltatások kiszolgáló).

##### Szolgáltatáskapcsolódási regisztrálása az Active Directoryban teszik lehetővé az Active Directory Tartalomvédelmi szolgáltatás felderítése

1.  Nyissa meg az Active Directory-szolgáltatások felügyeleti konzolon az Active Directory tartalomvédelmi szolgáltatások kiszolgálón:

    -   Ha a Windows Server 2008 R2 vagy a Windows Server 2008 használ, kattintson a **Start**, kattintson a **Felügyeleti eszközök**, és kattintson a **Active Directory tartalomvédelmi szolgáltatások**.

    -   Ha a Windows Server 2012 R2 vagy használata a Windows Server 2012, a Kiszolgálókezelő, kattintson a **Eszközök**, és kattintson a **Active Directory tartalomvédelmi szolgáltatások**.

2.  Az Active Directory tartalomvédelmi szolgáltatások konzolon kattintson a jobb gombbal az Active Directory Tartalomvédelmi fürt, és kattintson a **Tulajdonságok**.

3.  Kattintson a **SCP** fülre.

4.  Válassza ki a **módosítása SCP** jelölőnégyzetet.

5.  Válassza ki a **szolgáltatáskapcsolódási pontja beállítani a jelenlegi tanúsítási fürtre** lehetőséget, és kattintson a **OK**.

### Ügyféloldali szolgáltatás segítségével a Windows beállításjegyzékének engedélyezésével
Megoldásként Szolgáltatáskapcsolódási, vagy ha nem létezik Szolgáltatáskapcsolódási használatával konfigurálhatja a beállításjegyzék az ügyfélszámítógépen, hogy az RMS-ügyfél megkereséséhez az Active Directory tartalomvédelmi szolgáltatások kiszolgálója.

##### Ügyféloldali AD RMS szolgáltatás felderítése ahhoz, hogy a Windows beállításjegyzékének használatával

1.  Nyissa meg a Beállításszerkesztőt, Regedit.exe:

    -   A Futtatás ablakban az ügyfélszámítógépen írja be a **regedit**, és nyomja le az ENTER BILLENTYŰT, és nyissa meg a Beállításszerkesztőt.

2.  A beállításszerkesztőben keresse meg a **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > Ha egy 32 bites alkalmazás egy 64 bites számítógépen futtatja, az elérési utat a következők: 
    > **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  A ServiceLocation alkulcs létrehozása, kattintson a jobb gombbal **MSIPC**, mutasson a **Új**, kattintson a **kulcs**, majd írja be **ServiceLocation**.

4.  A EnterpriseCertification alkulcs létrehozása, kattintson a jobb gombbal **ServiceLocation**, mutasson a **Új**, kattintson a **kulcs**, majd írja be **EnterpriseCertification**.

5.  A vállalati hitelesítő URL-cím megadásához kattintson duplán a **(alapértelmezett)** érték alatti a **EnterpriseCertification** alkulcs, és amikor a **karakterlánc szerkesztése** párbeszédpanel jelenik meg, a **érték**, típusa &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Certification, és kattintson a **OK**.

6.  A EnterprisePublishing alkulcs létrehozása, kattintson a jobb gombbal **ServiceLocation**, mutasson a **Új**, kattintson a **kulcs**, majd írja be EnterprisePublishing.

7.  A vállalati közzététel URL-cím megadásához kattintson duplán a **(alapértelmezett)** , alatti a **EnterprisePublishing** alkulcs, és ha a **karakterlánc szerkesztése** párbeszédpanel megjelenik, írja be a **érték** a következő &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Licensing, és kattintson a **OK**.

8.  Zárja be a Beállításszerkesztőt.

Ha nincs megadva, a beállításjegyzékben az RMS-ügyfél nem találja Szolgáltatáskapcsolódási lekérdezése az Active Directory, az Active Directory Tartalomvédelmi szolgáltatás felderítési hívások sikertelen lesz.

### Átirányítás a kiszolgáló forgalom licencelés
Bizonyos esetekben előfordulhat, hogy kell forgalom átirányítási felderítésre szolgáltatás, például, ha két szervezetek amelyek egyesített, és a régi licencelési kiszolgáló egy szervezet visszavonásának, és átirányítja egy új licencelési kiszolgáló kell ügyfelek. Vagy az Azure RMS Active Directory tartalomvédelmi szolgáltatások át. Ahhoz, hogy a licencelési átirányítás, az alábbi eljárással.

##### Átirányítás licencelési segítségével a Windows beállításjegyzékének RMS engedélyezése

1.  Nyissa meg a Beállításszerkesztőt, Regedit.exe:

    -   A Futtatás ablakban az ügyfélszámítógépen írja be a **regedit**, és nyomja le az ENTER BILLENTYŰT, és nyissa meg a Beállításszerkesztőt.

2.  A beállításszerkesztőben keresse meg, hogy a következők egyikét:

    -   64 bites verziójának Office az x 64 platformra: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   A Microsoft Office x 64 32 bites verzióját platform: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Egy LicensingRedirection alkulcs létrehozása kattintson a jobb gombbal **Servicelocation**, mutasson a **Új**, kattintson a **kulcs**, majd írja be **LicensingRedirection**.

4.  A licencelési átirányítás megadásához kattintson a jobb gombbal a **LicensingRedirection** alkulcs, válassza **Új**, majd válassza ki **karakterlánc értéke**.  A **neve**, adja meg a korábbi kiszolgáló URL-cím licencelési és a **érték** adja meg az új kiszolgáló licencelési URL-cím.

    Át kell irányítani egy Fabrikam.com: Contoso.com kiszolgálóról licencelési, akkor előfordulhat, hogy írja be például a következő értékek:

    **Neve:** `https://contoso.com/_wmcs/licensing`

    **Érték:** `https://fabrikam.com/_wmcs/licensing`

    > [!NOTE]
    > Ha a régi licencelési kiszolgáló rendelkezik-intranetes és extranetes URL-cím megadott majd egy új nevet, és érték leképezési értékűre kell beállítani, a LicensingRedirection kulcs alatt ezeket URL-címeket is.

5.  Ismételje meg az előző lépésben kell átirányítja kiszolgálóira.

6.  Zárja be a Beállításszerkesztőt.

