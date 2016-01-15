---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# &#193;ttelep&#237;t&#233;s Active Directory tartalomv&#233;delmi szolg&#225;ltat&#225;sok az Azure Rights Management
A következő set utasítás használatával telepítse át az Active Directory tartalomvédelmi szolgáltatások (AD RMS) telepítés Azure Rights Management (Azure RMS). Az áttelepítés után felhasználók továbbra is hozzáférhet a dokumentumhoz, és e-mailek, hogy a szervezet Active Directory tartalomvédelmi szolgáltatások használatával védett, és újonnan védett tartalmat fogja használni az Azure RMS.

Nem biztos, hogy az AD RMS-áttelepítés a szervezet számára megfelelő?

-   Azure RMS, üzleti problémák megoldásában azt is megoldható, néz ki a rendszergazdák és a felhasználók és működésének bemutatását lásd: [Mi az Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

-   Egy Azure RMS AD RMS-sel szemben, lásd: [Azure Rights Management és az Active Directory tartalomvédelmi szolgáltatások összehasonlítása](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md).

## Az Azure RMS áttelepítése Active Directory tartalomvédelmi szolgáltatások előfeltételei
Azure RMS-nek az áttelepítés megkezdése előtt győződjön meg arról, hogy vannak-e az alábbi előfeltételek teljesülnek, és, hogy érti korlátozások.

|Követelmény|További információ|
|---------------|----------------------|
|A támogatott RMS telepítése|A Windows Server 2008, Windows Server 2012 R2 keresztül az AD RMS összes kiadására Azure RMS áttelepítést támogatják:<br /><br />-   Windows Server 2008 (x 86 vagy x 64)<br />-   Windows Server 2008 R2 (x 64)<br />-   Windows Server 2012 (x 64)<br />-   Windows Server 2012 R2 (x 64) **Note:** Ha a Windows Server 2003 fut a Windows RMS, ezen az operációs rendszer verziója lesz az támogatási 2015 során. Azure RMS áttelepítheti az RMS jelen verziójában, de ez a folyamat csak akkor, ha továbbra is támogatott az operációs rendszer támogatott. Megoldás akkor képes importálni a megbízható közzétételi tartomány (TPD) AD RMS által támogatott verzióra, és importálja újból a TPD az RMS 1.0 kompatibilitási beállítás megadása nélkül. Eltávolítható kapcsolatos további információkért lásd: [megbízható közzétételi tartomány](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)<br />Az összes érvényes Active Directory tartalomvédelmi szolgáltatások topológiák támogatottak:<br /><br />-   Egyetlen erdő, az RMS-fürt egyetlen<br />-   Egyetlen erdő esetén, több csak licencelési RMS-fürt<br />-   Több erdővel, több RMS-fürt **Note:** Alapértelmezés szerint több RMS-fürt egyetlen Azure RMS bérlőként át. Azt szeretné, hogy a különböző RMS bérlők, kell kezelni a különböző áttelepítések. A kulcs az RMS-fürt egynél több Azure RMS bérlő nem importálható.|
|Azure RMS, beleértve az Azure RMS bérlő (nincs aktiválva) futtatására vonatkozó összes követelmények|Lásd: [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Bár az Azure RMS bérlő kell rendelkeznie, mielőtt áttelepítené AD RMS, javasoljuk, hogy a felhasználó nem aktiválta a Rights Management szolgáltatás az áttelepítés előtt. Az áttelepítési folyamat tartalmazza az ebben a lépésben exportált kulcsok és sablonok az Active Directory tartalomvédelmi szolgáltatások, és importálja azokat az Azure RMS után. Azonban ha az Azure RMS már aktiválva van, továbbra is áttelepíthetők az AD RMS.|
|Az Azure RMS előkészítése:<br /><br />-   A helyszíni címtár között az Azure Active Directory címtár-szinkronizálás<br />-   Levelezési csoportok az Azure Active Directoryban|Lásd: [Azure Rights Management előkészítése](../Topic/Preparing_for_Azure_Rights_Management.md).|
|Ha Exchange Server (például átviteli szabályok és az Outlook Web Access) vagy a SharePoint Server tartalomvédelmi szolgáltatással (IRM) funkcióját használja az AD RMS szolgáltatással:<br /><br />-   Ha a tartalomvédelmi szolgáltatás nem lesz elérhető ezeken a kiszolgálókon rövid időn tervezése|E szolgáltatás használatához az Azure RMS ezeken a kiszolgálókon az áttelepítés után továbbra is. Azonban az áttelepítési műveleteket egyik átmenetileg letiltja a Tartalomvédelmi szolgáltatás telepítése és a-összekötő konfigurálása, konfigurálja újra a kiszolgálókat, és majd engedélyezze újra a tartalomvédelmi szolgáltatás.<br /><br />Ez a szolgáltatás csak megszakítás az áttelepítési folyamat során.|
A korlátozások vonatkoznak:

-   Bár az áttelepítési folyamat a kiszolgáló licencelési hardveres biztonsági modult (HSM)-tanúsítvány kulcsot az Azure RMS áttelepítését támogatja, az Exchange Online jelenleg nem támogatja ezt a konfigurációt. Ha az Exchange Online teljes Tartalomvédelmi szolgáltatás Azure RMS való áttelepítése után, az Azure RMS bérlői kulcsot kell [a Microsoft által felügyelt](http://technet.microsoft.com/library/dn440580.aspx). Másik lehetőségként hajthat végre a tartalomvédelmi szolgáltatás csökkentett az Exchange Online esetén az Azure RMS bérlői meg (BYOK) kezeli. Az Azure RMS Exchange Online használatával kapcsolatos további információkért lásd: [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration) az alábbi utasításokat.

-   Ha a szoftver- és az ügyfelek, amelyek nem támogatják az Azure RMS, nem fogják tudni védelme és Azure RMS által védett tartalmakat. Ellenőrizze a támogatott alkalmazások és az ügyfelek szakasz a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) témakör.

-   Ha importálja a helyszíni kulcsot az Azure RMS archivált (nincs megadva a TPD az importálási folyamat során az aktív legyen) és telepít át a felhasználók számára a fázisos áttelepítés kötegekben, újonnan az áttelepített felhasználók által védett tartalom nem lesz elérhető a felhasználók számára az Active Directory tartalomvédelmi szolgáltatások maradnak. Ebben az esetben amikor csak lehetséges, az áttelepítés rövid idő tartani, és át a felhasználók logikai kötegekben, úgy, hogy azok együttműködni egymással, ha azok együtt át.

    Ez a korlátozás nem vonatkozik beállításakor a TPD aktív az importálás során, mivel minden felhasználó tartalom védelméhez a azonos kulccsal. Ez a konfiguráció azt javasoljuk, mert lehetővé teszi, hogy minden felhasználó át függetlenül és a saját számítógépére.

-   Ha (például megbízható felhasználói tartományok vagy használatával összevonási) külső partnerekkel folytatott együttműködés, ezek is kell Azure RMS vagy egyszerre az áttelepítést, vagy a lehető leghamarabb később át. A folytatáshoz, hogy a szervezet Active Directory tartalomvédelmi szolgáltatások használatával korábban védett, akkor kell változtatásokat ügyfél konfigurációs hasonlóak, hogy a tartalom, és ez a dokumentum megtalálható eléréséhez.

    Miatt előfordulhat, hogy a partnerek lehetséges konfigurációs változatok a újrakonfigurálása pontos utasítások kívül esnek a hatókörön ehhez a dokumentumhoz. Segítségért forduljon a Microsoft ügyfélszolgálathoz (CSS).

## Az Azure RMS áttelepítése Active Directory tartalomvédelmi szolgáltatások lépései

|Áttelepítési lépés|További információ|
|----------------------|----------------------|
|**1. Töltse le az Azure RMS felügyeleti felügyeleti eszközei**|Útmutatásért lásd: [Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration).|
|**2. Az AD RMS konfigurációs adatok exportálja és importálja azt Azure RMS**|XML-fájlba exportálja a konfigurációs adatokat (kulcsok, sablonok, az URL-címek) AD RMS, majd töltse fel, hogy a fájl Azure RMS Import-AadrmTpd Windows PowerShell parancsmag használatával. További lépéseket is szükség lehet attól függően, hogy a a AD RMS-konfiguráció:<br /><br />-   Szoftver védett kulcs áttelepítési szoftver védett kulcsot: Központilag felügyelt, jelszó kulcsokat az Active Directory tartalomvédelmi szolgáltatások, a Microsoft által felügyelt Azure RMS bérlői kulcshoz. Ez a legegyszerűbb áttelepítési elérési útja és nincs további lépések szükségesek.<br />-   Kulcs áttelepítési HSM védett HSM védett kulcsot: Az AD RMS-ügyfél által felügyelt Azure RMS bérlői kulcs Hardvermodult által tárolt kulcsok (a "saját kulcsot kerüljön" vagy BYOK forgatókönyv). Ehhez a kulcs átvitele a helyszíni Thales HSM Azure RMS működnek további lépéseket.<br />-   Kulcs áttelepítési HSM védett szoftver védett kulcsot: Központilag felügyelt jelszó alapú kulcsokat az AD RMS-ügyfél által felügyelt Azure RMS bérlői kulcsot (a "saját kulcsot kerüljön" vagy BYOK forgatókönyv). Ehhez a legtöbb configuration, mert kell először bontsa ki a szoftver-kulcs, és importálja azt a helyszíni Hardvermodult és a további lépéseket, a kulcs átvitele a helyszíni Thales HSM Azure RMS működnek majd tegye.<br /><br />Útmutatásért lásd: [Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration).|
|**3. Az RMS-bérlő aktiválása**|Ha lehetséges tegye meg ezt a lépést, az importálási folyamat után, és nem előtt.<br /><br />További információt és útmutatást talál [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).|
|**4. Importált sablonok konfigurálása**|A jogmegadási sablonok importálásakor az állapotukat archiválva legyen. Ha azt szeretné, hogy a felhasználók láthatják, és a használatukat, módosítania kell a hagyományos Azure portálon közzétett sablon állapotot.<br /><br />Útmutatásért lásd: [Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration).|
|**5. Konfigurálja újra az Azure RMS Alkalmazást használó ügyfelek**|Windows-számítógépek AD RMS helyett az Azure RMS szolgáltatás használatára kell konfigurálni. Ha meg van kapcsolóprofil velük, amíg az Active Directory tartalomvédelmi szolgáltatások futtatása során ezt a lépést a szervezet számítógépeire, és partnerszervezet található számítógépekre vonatkozik.<br /><br />Továbbá, ha telepítette a [mobileszköz bővítmények](http://technet.microsoft.com/library/dn673574.aspx) mobileszközök, például az iOS-telefonok és Ipadek, Android telefonok és táblagépek, Windows phone és Mac számítógépek támogatásához el kell távolítania az SRV-rekordot a DNS-ben, amely használja az AD RMS ezek az ügyfelek átirányítva.<br /><br />Útmutatásért lásd: [Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration).|
|**6. Exchange Online IRM integráció konfigurálása**|Ez a lépés szükség, ha az Azure RMS Exchange Online használni kívánt.<br /><br />Útmutatásért lásd: [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration).|
|**7. Az RMS-összekötő telepítése**|Ez a lépés szükség, ha azt szeretné, hogy az alábbi helyszíni szolgáltatások az Azure RMS használata:<br /><br />-   Exchange-kiszolgáló (például átviteli szabályok és az Outlook Web Access)<br />-   SharePoint-kiszolgáló<br />-   Fájl besorolást infrastruktúra futtató Windows-kiszolgáló<br /><br />Útmutatásért lásd: [Step 7. Deploy the RMS connector](#BKMK_Step7Migration).|
|**8. Active Directory tartalomvédelmi szolgáltatások leszerelése**|Ha megerősítette, hogy minden ügyfél Azure RMS Alkalmazást használ, és többé nem érik el az AD RMS-kiszolgálókat, az AD RMS-telepítés képes leszerelni.<br /><br />Útmutatásért lásd: [Step 8. Decommission AD RMS](#BKMK_Step8Migration).|
|**9. Az Azure RMS bérlői kulcs újbóli kulcs**|Ez a lépés szükség, ha nem futottak a 2. kriptográfiai mód az áttelepítés előtt, és nem kötelező, de ajánlott tartalmazó összes az Azure RMS bérlői kulcs biztonságának védelme érdekében.<br /><br />Útmutatásért lásd: [Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>1. lépés: Töltse le az Azure Rights Management felügyeleti eszköz
Nyissa meg a Microsoft Download Center, és töltse le a [Azure Rights Management felügyeleti eszköz](http://go.microsoft.com/fwlink/?LinkId=257721), az Azure RMS felügyeleti modul Windows PowerShell benne.

### <a name="BKMK_Step2Migration"></a>2. lépés. Az AD RMS konfigurációs adatok exportálja és importálja azt Azure RMS
Ez a lépés két lépésből áll:

1.  A konfigurációs adatok exportálása az AD RMS (eltávolítható) a megbízható közzétételi tartomány exportálása .xml kiterjesztésű fájlba. Ez a folyamat megegyezik a összes.

2.  A konfigurációs adatok importálását az Azure RMS-nek. Van-e ezt a lépést, az aktuális Active Directory tartalomvédelmi szolgáltatások telepítési konfigurációt, és az Azure RMS bérlői kulcs előnyben részesített topológiájától függően a különböző folyamat.

#### Az AD RMS konfigurációs adatok exportálása
Hajtsa végre az alábbi eljárást az összes megbízható közzétételi tartomány védett tartalmak a szervezet összes AD RMS fürtökön. Nem kell futtatni a csak licencelési fürtökön.

> [!NOTE]
> Windows Server 2003 tartalomvédelmi használatakor utasítások helyett az alábbi eljárással [titkos kulcs exportálása kiszolgálólicenc-tanúsítvány, TUD, TPD és RMS](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) a a [való áttelepítését Windows RMS infrastruktúra különböző Active Directory tartalomvédelmi szolgáltatások](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) témakör.

###### A konfigurációs adatokat (megbízható közzétételi tartomány információk) exportálása

1.  Jelentkezzen be az AD RMS-fürt felhasználóként AD RMS-val felügyeleti engedélyekkel.

2.  Az Active Directory tartalomvédelmi szolgáltatások felügyeleti konzolról (**Active Directory tartalomvédelmi szolgáltatások**), bontsa ki az AD RMS-fürt neve, **megbízhatósági házirendek**, és kattintson a **megbízható közzétételi tartomány**.

3.  Az eredménypanelen jelölje ki a megbízható közzétételi tartomány és a Műveletek ablaktáblában kattintson a **megbízható közzétételi tartomány exportálása**.

4.  Az a **exportálása megbízható közzétételi tartomány** párbeszédpanel:

    -   Kattintson a **Mentés másként** és elérési útjával és az Ön által választott fájlnévvel mentse. Ellenőrizze, hogy **.xml** a fájl kiterjesztése (Ez a rendszer nem hozzáfűzi automatikusan).

    -   Adja meg, és erősítse meg egy erős jelszót. Ne feledje ezt a jelszót, mert, mert később szüksége lesz, ha a konfigurációs adatokat importál a Azure RMS.

    -   Nem jelölőnégyzet bejelölésével a megbízható tartományba mentés RMS 1.0-s verzióját.

Összes megbízható közzétételi tartomány exportálása, amikor készen áll az adatok importálása az Azure RMS a folyamat megkezdéséhez.

#### A konfigurációs adatok importálását az Azure RMS
A pontos eljárások ebben a lépésben az aktuális Active Directory tartalomvédelmi szolgáltatások telepítési konfigurációt, és az Azure RMS bérlői kulcs az előnyben részesített topológiát függenek.

Az aktuális AD RMS-telepítés fog használni egy, az alábbi konfigurációk a kiszolgáló kiszolgálólicenc-tanúsítvány kulcs:

-   Az AD RMS adatbázis jelszavas védelmet. Ez az alapértelmezett konfigurációt.

-   HSM védelmi Thales hardveres biztonsági modult (HSM) használatával.

-   HSM védelme eltérő Thales szállítótól hardveres biztonsági modult (HSM) használatával.

-   A jelszó egy külső titkosítási szolgáltató használatával védett.

> [!NOTE]
> Hardver biztonsági modulokat használó AD RMS-sel kapcsolatos további információkért lásd: [használata AD RMS hardveres biztonsági modulok](http://technet.microsoft.com/library/jj651024.aspx).

Az Azure RMS bérlői két fő topológia lehetőségek állnak rendelkezésére: Microsoft felügyeli a bérlő kulcs (**a Microsoft által felügyelt**) vagy a bérlői kulcs kezelheti (**az ügyfél által felügyelt**). A saját Azure RMS bérlői kulcs kezelésekor néha szerepel a "saját kulcsot kerüljön" (BYOK) és a hardveres biztonsági modult (HSM) a Thales igényel. További információ: a [Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey) szakasz a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) témakör.

> [!IMPORTANT]
> Exchange online-hoz nincs Azure RMS BYOK jelenleg kompatibilis.  Ha azt szeretné, az áttelepítés után BYOK használja, és tervezi használni az Exchange Online tudja, hogy, hogy hogyan ebben a konfigurációban csökkenti a Tartalomvédelmi szolgáltatás Exchange online-hoz. Tekintse át az információkat a [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) szakasz a  [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) a témakörhöz, és válassza ki a legjobb Azure RMS segítségével bérlői kulcsok topológia az áttelepítéshez.

A következő táblázat segítségével meghatározhatja az áttelepítéshez használandó melyik eljárást. Kombinációk, amelyek nem szerepelnek a listán nem támogatottak.

|Aktuális AD RMS telepítése|A választott Azure RMS bérlői kulcsok topológia|Áttelepítési utasítások|
|------------------------------|---------------------------------------------------|---------------------------|
|Az AD RMS-adatbázisban a jelszavas védelem|A Microsoft által felügyelt|Tekintse meg a **kulcs áttelepítési szoftver védett kulcs szoftver védett** a táblázat utáni eljárás.<br /><br />Ez a legegyszerűbb áttelepítési elérési utat, és csak igényel, a konfigurációs adatok átvitele Azure RMS.|
|HSM védelmi Thales nShield hardveres biztonsági modult (HSM) használatával|Az ügyfél által felügyelt (BYOK)|Tekintse meg a **kulcs áttelepítési HSM védett kulcs HSM védett** a táblázat utáni eljárás.<br /><br />Ehhez a BYOK toolset és lépéseket követve átvitele a helyszíni HSM a kulcsot az Azure RMS HSMs, majd a konfigurációs adatok átvitele az Azure RMS két csoportját.|
|Az AD RMS-adatbázisban a jelszavas védelem|Az ügyfél által felügyelt (BYOK)|Tekintse meg a **kulcs áttelepítési HSM védett kulcs szoftver védett** a táblázat utáni eljárás.<br /><br />Ehhez a BYOK toolset és lépéseket az első három különböző bontsa ki a kulcsot, és úgy, hogy a helyszíni Hardvermodult majd a helyszíni HSM a kulcsot az Azure RMS HSMs át, és végül Azure RMS át a konfigurációs adatok importálása.|
|HSM védelmi Thales eltérő szállítótól hardveres biztonsági modult (HSM) használatával|Az ügyfél által felügyelt (BYOK)|Vegye fel a kapcsolatot meg HSM vonatkozó utasítások a kulcs átvitele a HSM egy Thales nShield hardver biztonsági modul Hardvermodul módját. Kövesse az utasításokat a **kulcs áttelepítési HSM védett kulcs HSM védett** a táblázat utáni eljárás.|
|Jelszóval védett külső kriptográfiai szolgáltató használatával|Az ügyfél által felügyelt (BYOK)|Vegye fel a kapcsolatot, kriptográfiai szolgáltató vonatkozó utasítások a kulcs átvitele Thales nShield hardveres biztonsági modulra (HSM). Kövesse az utasításokat a **kulcs áttelepítési HSM védett kulcs HSM védett** a táblázat utáni eljárás.|
Ezek az eljárások megkezdése előtt győződjön meg arról, hogy hozzá tud férni az .xml-fájlok, amelyet korábban hozott létre a megbízható közzétételi tartomány exportálása során. Például ezek előfordulhat, hogy menteni egy USB-meghajtóra, amely az internethez csatlakozó munkaállomásra az AD RMS-kiszolgáló áthelyezése.

> [!NOTE]
> Azonban tárolja ezeket a fájlokat, a használata ajánlott eljárásokkal védelme érdekében, mivel ezeket az adatokat a titkos kulcsot tartalmaz.

##### Szoftver védett kulcs áttelepítési szoftver védett kulcs
Ezzel az eljárással az AD RMS konfigurációs importálásához Azure RMS, a Microsoft által felügyelt Azure RMS-bérlő kulcs eredményez.

###### A konfigurációs adatok importálása az Azure RMS

1.  Az internethez csatlakozó munkaállomáson töltse le és Azure RMS (2.1.0.0 minimális verzió), amely tartalmazza a Windows PowerShell-modul telepítése a [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) parancsmagot.

    > [!TIP]
    > Ha korábban letöltött és telepített, a modul, ellenőrizze a verziószámot futtatásával: `(Get-Module aadrm -ListAvailable).Version`

    A telepítési utasításokért lásd: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

2.  Indítsa el a Windows PowerShell a **Futtatás rendszergazdaként** lehetőséget, és használja a [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) parancsmag csatlakozni az Azure RMS szolgáltatás:

    ```
    Connect-AadrmService
    ```
    Ha a rendszer kéri, adja meg a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] bérlői rendszergazdai hitelesítő adatait (meg fogja használni, általában olyan fiókkal, amely egy globális rendszergazda Azure Active Directoryban, vagy az Office 365).

3.  Használja a [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) töltse fel az első parancsmag exportált megbízható közzétételi tartomány (.xml) fájl. Ha egynél több .xml fájlt, mert több megbízható közzétételi tartomány volt, válassza ki a fájlt, amely tartalmazza az exportált megbízható közzétételi tartomány kívánt tartalom védeni az áttelepítés után az Azure RMS segítségével. A következő parancsot használja:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Példa: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Ha a rendszer kéri, adja meg a jelszót, amelyet korábban megadott, és győződjön meg arról, hogy szeretné-e a művelet végrehajtására.

4.  A parancs befejeződése után ismételje meg a 3. lépés minden fennmaradó .xml fájl, amelyet hozott létre a megbízható közzétételi tartomány exportálása. Állítsa be ezeket a fájlokat, de **-Active** a **false** az importálási parancs futtatásakor. Példa: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Használja a [kapcsolat bontása-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) parancsmag le az Azure RMS szolgáltatás:

    ```
    Disconnect-AadrmService
    ```

Most már készen váltson [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Kulcs áttelepítési HSM védett HSM védett kulcs
Akkor importálhatja az Azure RMS eredményez az Azure RMS bérlői kulcs (BYOK) Ön által kezelt HSM kulcs és az AD RMS konfigurációs kétrészes eljárást.

A HSM kulcs először kell csomagot, így Azure RMS át, és importálja a konfigurációs adatok készen áll.

###### 1. rész: Csomag a HSM kulcsot, így Azure RMS átvitele készen áll

1.  Kövesse a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) szakasza a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), hajtsa végre az eljárást **létrehozása és átvitele a bérlő kulcs – az interneten keresztül** a következő kivételekkel:

    -   Ne hajtsa végre a lépéseket a **a bérlő kulcs létrehozása**, mert az AD RMS-telepítés a már rendelkezik a megfelelő. Azonosítsa a kulcs az Thales telepítési az AD RMS-kiszolgáló által használt kell, és használja ezt a kulcsot az áttelepítés során. Kulcs titkosított fájlok általában neve Thales **key_(keyAppName)_(keyIdentifier)** helyileg a kiszolgálón.

    -   Ne hajtsa végre a lépéseket a **a bérlő kulcsának átvitele Azure RMS**, amely használja az Add-AadrmKey parancsot.  Ehelyett az előkészített HSM kulcs helyez át, az exportált megbízható közzétételi tartomány az Import-AadrmTpd paranccsal feltöltésekor.

2.  Az internethez csatlakozó munkaállomáson Windows PowerShell-munkamenetben, csatlakoztassa újra az Azure RMS szolgáltatás.

Most, hogy a HSM kulcsot az Azure RMS előkészítése már készen áll a HSM kulcsfájl és az AD RMS konfigurációs adatok importálása.

###### 2. rész: A HSM kulcs és a konfigurációs adatok importálása a Azure RMS

1.  Továbbra is a munkaállomáson Internet-csatlakozás és a Windows PowerShell-munkamenetben töltse fel az első exportált megbízható közzétételi tartomány (.xml) fájlt. Ha egynél több .xml fájlt, mert több megbízható közzétételi tartomány volt, válassza ki az exportált megbízható közzétételi tartomány, amely megfelel a tartalom védelméhez, az áttelepítés után az Azure RMS használni kívánt HSM kulcsot tartalmazó fájlt. A következő parancsot használja:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Példa: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Ha a rendszer kéri, adja meg a jelszót, amelyet korábban megadott, és győződjön meg arról, hogy szeretné-e a művelet végrehajtására.

2.  A parancs befejeződése után ismételje meg minden fennmaradó hozott létre a megbízható közzétételi tartomány exportálása .xml fájl 1. lépés. Állítsa be ezeket a fájlokat, de **-Active** a **false** az importálási parancs futtatásakor.  Példa: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Használja a [kapcsolat bontása-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmag le az Azure RMS szolgáltatás:

    ```
    Disconnect-AadrmService
    ```

Most már készen váltson [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Kulcs áttelepítési HSM védett szoftver védett kulcs
Egy háromrészes importálásáról az AD RMS konfigurációs Azure RMS az Azure RMS bérlői kulcs (BYOK) Ön által kezelt eredményez.

Meg kell először a kiszolgáló kiszolgálólicenc-tanúsítvány kulcs beolvasni a konfigurációs adatokat és a kulcs át egy helyszíni Thales HSM majd csomag és a HSM kulcsának átvitele Azure RMS, és importálja a konfigurációs adatokat.

###### 1. rész: A kiszolgálólicenc-tanúsítvány beolvasni a konfigurációs adatokat, és importálja a kulcsot a helyszíni HSM

1.  Használja a következő lépéseket a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) szakasza a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) témakör:

    -   **Létrehozása és átvitele a bérlő kulcs – az interneten keresztül**: **Az internethez csatlakozó munkaállomás előkészítése**

    -   **Létrehozása és átvitele a bérlő kulcs – az interneten keresztül**: **A leválasztott munkaállomás előkészítése**

    Nem kövesse a bérlő kulcs létrehozása, mert már rendelkezik a megfelelő az exportált konfigurációs adatokat (.xml) fájl. Ehelyett fogja futtatni bontsa ki a kulcs a fájlból, és importálja azt a helyszíni HSM parancsot.

2.  A leválasztott munkaállomáson futtassa a következő parancsot:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Például a közép-európai: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    További információ:

    -   A ImportRmsCentrallyManagedKey paraméter azt jelzi, hogy a művelet a kiszolgálólicenc-tanúsítvány kulcs importálása.

    -   Ha a parancs nem adja meg a jelszót, a rendszer kérni azt adja meg.

    -   A KeyIdentifier paraméter a kulcs valódi nevét, amely hozza létre a nyilvánoskulcs-fájl nevét. Csak kisbetűs ASCII-karaktereket kell használnia.

    -   A ExchangeKeyPackage paraméter határozza meg a területhez kulcscsere kulcsa (KEK) csomagok BYOK kezdődő neveket-KEK - pkg-.

    -   A NewSecurityWorldPackage paraméter határozza meg a területhez biztonsági world csomagok BYOK kezdődő neveket-SecurityWorld - pkg-.

    Ezzel a paranccsal az eredmény a következő:

    -   Egy HSM kulcsfájl: &lt; KeyID &gt; %NFAST_KMDATA%\local\key_mscapi_

    -   RMS konfigurációs adatok fájlt, amely a kiszolgálólicenc-tanúsítvány eltávolítása: &lt; KeyID &gt; %NFAST_KMDATA%\local\no_key_tpd_ .xml

3.  Ha egynél több RMS konfigurációs adatfájlok, ismételje meg ezeket a fájlokat a hátralévő 2. lépés.

Most, hogy a kiszolgálólicenc-tanúsítvány kivonták úgy, hogy az egy HSM-alapú kulcsot, készen áll a csomag és vigye át az Azure RMS.

###### 2. rész: Csomag és a HSM kulcsának átvitele Azure RMS

1.  A következő lépésekkel a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) szakasza a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Létrehozása és átvitele a bérlő kulcs – az interneten keresztül**: **A bérlő kulcsát átviteli előkészítése**

    -   **Létrehozása és átvitele a bérlő kulcs – az interneten keresztül**: **A bérlő kulcsának átvitele Azure RMS**

Most, hogy a HSM kulcsot az Azure RMS átvitt már készen áll a csak az újonnan átvitt bérlői kulcs mutatót tartalmaz, amelyek az AD RMS konfigurációs adatok importálását.

###### 3. rész: A konfigurációs adatok importálását az Azure RMS

1.  Továbbra is a munkaállomáson internetre csatlakoztatott és a Windows PowerShell-munkamenetben másolja át az RMS konfigurációs fájlokat a kiszolgálólicenc-tanúsítvány eltávolítva (leválasztott munkaállomás %NFAST_KMDATA%\local\no_key_tpd_ &lt; KeyID &gt; .xml)

2.  Töltse fel az első fájlt. Ha egynél több .xml fájlt, mert több megbízható közzétételi tartomány volt, válassza ki az exportált megbízható közzétételi tartomány, amely megfelel a tartalom védelméhez, az áttelepítés után az Azure RMS használni kívánt HSM kulcsot tartalmazó fájlt. A következő parancsot használja:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Példa: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Ha a rendszer kéri, adja meg a jelszót, amelyet korábban megadott, és győződjön meg arról, hogy szeretné-e a művelet végrehajtására.

3.  A parancs befejeződése után ismételje meg a 2. lépés minden fennmaradó .xml fájl, amelyet hozott létre a megbízható közzétételi tartomány exportálása. Állítsa be ezeket a fájlokat, de **-Active** a **false** az importálási parancs futtatásakor. Példa: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Használja a [kapcsolat bontása-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmag le az Azure RMS szolgáltatás:

    ```
    Disconnect-AadrmService
    ```

Most már készen váltson [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>3. lépés. Az RMS-bérlő aktiválása
Ebben a lépésben utasításokat teljes foglalt a [Az Azure Rights Management aktiválása](../Topic/Activating_Azure_Rights_Management.md) témakör.

> [!TIP]
> Ha az Office 365-előfizetéssel rendelkezik, az Office 365 felügyeleti központban vagy a hagyományos Azure-portálon Azure RMS aktiválhatja. Javasoljuk, hogy a hagyományos Azure-portálon használja, mert ezen a felügyeleti portálon használni kívánt hajtsa végre a következő lépéssel.

**Mi történik, ha az Azure RMS bérlői már aktiválva van?** Az Azure RMS szolgáltatás már aktiválva van a szervezet számára, ha felhasználók előfordulhat, hogy rendelkezik már használt Azure RMS egy automatikusan létrehozott bérlői kulcsot (és az alapértelmezett sablon) tartalom védelméhez helyett a meglévő kulcsokat (és a sablonokat) AD RMS-en. Ennek valószínű, hogy az intraneten gyakran felügyelt számítógépeken fordulhat elő, mert azok automatikusan megtörténik az AD RMS infrastruktúrát. De olyankor, munkacsoporthoz tartozó számítógépekre vagy a számítógépek, amelyek ritkán az intraneten kapcsolódnak. Sajnos is nehezen azonosíthatja ezeket a számítógépeket, amelyek van, ezért javasoljuk, hogy a felhasználó nem aktiválta a szolgáltatás a konfigurációs adatokat importál az AD RMS előtt.

Ha segítségével azonosíthatja ezeket a számítógépeket a Azure RMS bérlő már aktiválva van, győződjön meg arról, hogy ezeken a számítógépeken, a CleanUpRMS_RUN_Elevated.cmd parancsfájl futtatása, 5. lépésben leírtak szerint. A parancsfájl futtatása kényszerítése azokat a felhasználói környezet újrainicializálásához így letöltik a frissített bérlői kulcs és az importált sablont.

### <a name="BKMK_Step4Migration"></a>4. lépés. Importált sablonok konfigurálása
Mivel az importált sablonok alapértelmezett állapotának **Archivált**, módosítania kell az ebben az állapotban kell lennie **közzétett** Ha azt szeretné, hogy a felhasználók Azure RMS Alkalmazást használja ezeket a sablonokat.

Emellett ha az AD RMS-sablonok a **ANYONE** csoporthoz, ez a csoport automatikusan eltűnik a sablonok importálásakor az Azure RMS; manuálisan kell hozzáadni a egyenértékű csoport vagy felhasználók és az importált sablont ugyanazokat a jogokat. Az Azure RMS egyenértékű csoport neve **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com**. Ez a csoport előfordulhat, hogy keresse meg például a következő, a Contoso: **AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**.

Ha nem biztos abban, hogy az AD RMS-sablonok tartalmazza BÁRKI csoporthoz, bontsa ki a  [PowerShell script to identify AD RMS templates that include the ANYONE group](#BKMK_ScriptForANYONE) szakasz ebben a lépésben másolja, és a minta PowerShell parancsfájl segítségével azonosíthatja ezeket a sablonokat. Windows PowerShell használatával az AD RMS-sel kapcsolatos további információkért lásd:  [Windows PowerShell használatával a rendszergazda az AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Megtekintheti a szervezet által automatikusan jönnek létre csoport másolja az alapértelmezett jogmegadási sablonok egyikét hagyományos Azure portálon, és azonosítsa a **felhasználónév** a a **jogok** lap. Azonban a hagyományos portál nem használható ehhez a csoporthoz hozzáadni a sablont, amely a manuálisan létrehozott vagy importált, és helyette kell használniuk az Azure RMS PowerShell alábbi lehetőségek közül:

-   Használja a [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) PowerShell-parancsmaggal a "AllStaff" csoport és a jogok megadása a jogok definíció objektumként, és futtassa a parancsot újból az egyes csoportok vagy felhasználók már jogokat a ANYONE csoport mellett az eredeti sablonnak. Majd adja hozzá ezeket jogok definíció objektumok a sablonok használatával a  [Set-AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) parancsmagot.

-   Használja a [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) sablon exportálása parancsmag egy. XML-fájl, amely szerkesztése hozzáadása a "AllStaff" csoport és a meglévő csoportok és a jogok jogosultsággal, és használja a [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) Azure RMS térni parancsmaggal importálja ezt a módosítást.

> [!NOTE]
> A "AllStaff" egyenértékű csoport nem pontosan azonos a ANYONE csoport tagja az Active Directory tartalomvédelmi szolgáltatások:  A "AllStaff" csoport összes olyan felhasználót tartalmazza az Ön Azure-bérlőhöz, mivel az a személy csoport tartalmazza az összes hitelesített felhasználó, aki a szervezeten kívüli lehet.
> 
> Ez a különbség a két csoport miatt szükség lehet a külső felhasználók mellett a "AllStaff" csoport is hozzáadható. A csoportok külső e-mail címek jelenleg nem támogatott.

Importál az AD RMS-sablonok keresse meg és ugyanúgy viselkednek, a hagyományos Azure-portálon hozhat létre egyéni sablonokkal. Importált sablonok közzé kell tenni, így azok a felhasználók és jelölje ki azokat az alkalmazásokat, vagy más változtatásokat végezni az sablonok módosításához lásd [Az Azure Rights Management egyéni sablonok konfigurálása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

> [!TIP]
> A egységesebb az áttelepítési folyamat során a felhasználók számára ne módosítsa az importált sablonok eltérő két módosítások; nem közzététele az Azure RMS két alapértelmezett sablont, és most új sablonokat hozhat létre. Ehelyett, várjon, amíg az áttelepítési folyamat befejeződött, és az AD RMS-kiszolgálók leszerelése.

#### <a name="BKMK_ScriptForANYONE"></a>Minta Windows PowerShell-parancsfájl, amely tartalmazza a ANYONE csoportot AD RMS-sablonok azonosításához
Ez a szakasz a minta parancsprogram azonosításához AD RMS-sablonok, amelyek a ANYONE csoport meghatározott, az előző szakaszban leírtak szerint.

*&#42;&#42;Jogi nyilatkozatot:&#42;&#42; Ez a mintaparancsprogram bármilyen Microsoft támogatási normál program vagy a szolgáltatás nem támogatott. Ez a mintaparancsprogram van megadva, a IS biztosít, mindenféle jótállás nélkül.*

```
import-module adrmsadmin New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force $ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate foreach($Template in $ListofTemplates) { $templateID=$Template.id $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright $templateName=$Template.DefaultDisplayName if ($rights.usergroupname -eq "anyone") { $templateName = $Template.defaultdisplayname write-host "Template " -NoNewline write-host -NoNewline $templateName -ForegroundColor Red write-host " contains rights for " -NoNewline write-host ANYONE  -ForegroundColor Red } } Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>5. lépést. Konfigurálja újra az Azure RMS Alkalmazást használó ügyfelek
A Windows rendszerű ügyfelek:

1.  [Töltse le az áttelepítési parancsprogramok](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Ezek a parancsfájlok állítsa vissza a Windows rendszerű számítógépeken a konfiguráció akkor fogják használni, az AD RMS helyett az Azure RMS szolgáltatás található.

2.  Kövesse az utasításokat az átirányítás parancsfájl (Redirect_OnPrem.cmd) az új Azure RMS bérlői mutasson a parancsfájl módosításával.

3.  A Windows rendszerű számítógépeken ezek a parancsfájlok futtatása emelt szintű engedélyekkel a felhasználó környezetében.

A mobileszközök és Mac számítógépek:

-   Távolítsa el az üzembe helyezett létrehozott DNS SRV-rekordok a [AD RMS mobileszköz-bővítményének](http://technet.microsoft.com/library/dn673574.aspx).

#### Az áttelepítési parancsprogramok által végrehajtott módosítások
Ez a szakasz a dokumentumok az áttelepítési parancsprogramok a módosításokat. Kizárólag tájékoztatási célt, vagy hibaelhárításhoz használható ezt az információt, vagy ha szeretné módosítani ezeket átvált a saját maga.

CleanUpRMS_RUN_Elevated.cmd:

-   Törölje a %userprofile%\AppData\Local\Microsoft\DRM és %userprofile%\AppData\Local\Microsoft\MSIPC mappákat, beleértve az almappákat, és a hosszú fájlnevekkel fájlokat tartalmát.

-   Törölje a tartalmát a következő beállításkulcsokat:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Törölje a következő beállításazonosítókat:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Hozzon létre minden egyes minden egyes, a következő helyek paraméterként megadott URL-cím a következő beállításazonosítókat:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Minden bejegyzés értéke REG_SZ **https://OldRMSserverURL/_wmcs/licensing** az adatokat a következő formátumban: **https://&lt;YourTenantURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt; YourTenantURL &gt;* formátuma a következő: **{GUID} .rms. [régió].aadrm.com**.
    > 
    > Példa:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Ez az érték azonosításával megtalálhatja a **RightsManagementServiceId** értéke, ha futtatja a [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) parancsmag az Azure RMS.

### <a name="BKMK_Step6Migration"></a>6. lépés. Az Exchange Online IRM integráció konfigurálása
Ha az Active Directory tartalomvédelmi szolgáltatások korábban importálta a TDP az Exchange online, el kell távolítania a TDP miután áttelepítette az Azure RMS ütköző sablonok és a házirendeket elkerülése érdekében. Ehhez használja a [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) Exchange Online-parancsmagot.

Ha úgy döntött, hogy az Azure RMS kulcs topológiája bérlői **felügyelt Microsoft**:

-   Tekintse meg a [Az Exchange Online: A tartalomvédelmi szolgáltatás konfigurációja](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline) szakasz a [Azure Rights Management alkalmazások konfigurálása](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) témakör. A szakasz tartalmazza azokat a tipikus parancsok futtatásához, amelyek az Exchange Online szolgáltatáshoz kapcsolódik, a bérlői kulcs importálja az Azure RMS és lehetővé teszi a Tartalomvédelmi szolgáltatás Exchange online-hoz. A lépések elvégzése után az Exchange Online funkciója RMS lesz.

Ha úgy döntött, hogy az Azure RMS kulcs topológiája bérlői **(BYOK) az ügyfél által felügyelt**:

-   Akkor lesz csökkentette RMS funkciót az Exchange Online leírtak szerint a [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) szakasz a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) témakör.

### <a name="BKMK_Step7Migration"></a>7. lépést. Az RMS-összekötő telepítése
Ha Exchange Server vagy a SharePoint-kiszolgáló a tartalomvédelmi szolgáltatással (IRM) funkciókat az AD RMS szolgáltatással használt, kell először tiltsa le a tartalomvédelmi szolgáltatás ezeken a kiszolgálókon, és távolítsa el az AD RMS-beállításai. Ezután telepítse a Rights Management (RMS) összekötő, mely úgy működik, mint a helyszíni kiszolgálók és az Azure RMS közötti kommunikációs felületet (továbbító).

Végül az ezt a lépést, ha több eltávolítható importálta e-mailek védelméhez használt Azure RMS kell manuálisan a beállításjegyzék szerkesztése összes eltávolítható URL-címet átirányítja az RMS-összekötő az Exchange Server számítógépen.

> [!NOTE]
> Megkezdése előtt ellenőrizze, hogy az RMS-összekötő "helyszíni támogató kiszolgálók Azure RMS" támogatja a helyszíni kiszolgálók támogatott verziói a [Alkalmazások, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) szakasza a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) témakör.

##### Tiltsa le a tartalomvédelmi szolgáltatás Exchange-kiszolgálókon, és távolítsa el az AD RMS-beállításai

1.  Minden egyes Exchange-kiszolgálón, keresse meg a következő mappát, és a mappában található összes bejegyzést törölni: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Az Exchange-kiszolgálók közül használni az Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) parancsmag első letiltja a Tartalomvédelmi szolgáltatások belső címzettek küldött üzenetek:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Az azonos parancsmag segítségével külső címzetteknek küldött üzenetek a Tartalomvédelmi szolgáltatások letiltása:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Ezután a azonos parancsmag segítségével a Microsoft Office Outlook Web Appjét és a Microsoft Exchange ActiveSync IRM letiltása:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Végezetül a azonos parancsmag segítségével törölje a jelet a gyorsítótárban tárolt tanúsítványok:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Minden egyes Exchange-kiszolgálón most alaphelyzetbe állítja az IIS, például a parancssor futtatása rendszergazdaként, és beírja az **iisreset**.

##### Tiltsa le a tartalomvédelmi szolgáltatás SharePoint-kiszolgálóra, és távolítsa el az AD RMS-beállításai

1.  Győződjön meg arról, hogy kiveszi a rendszerből származó RMS által védett dokumentumok. Ha nincsenek, kell válnak a jelen eljárás végén nem érhető el.

2.  A SharePoint központi felügyeleti webhely, az a **Gyorsindítás** részen kattintson **biztonsági**.

3.  Az a **biztonsági** lapra, és a **információk házirend** részen kattintson **tartalomvédelmi szolgáltatás beállítása**.

4.  A a **tartalomvédelmi** lapra, és a **tartalomvédelmi** területen jelölje be **ezen a kiszolgálón ne használja a tartalomvédelmi szolgáltatás**, kattintson a **OK**.

5.  A mappa \ProgramData\Microsoft\MSIPC\Server\ tartalmának törlése a SharePoint-kiszolgáló számítógépek minden*&lt; SharePoint Servert futtató fiók biztonsági azonosítója &gt;*.

##### Az RMS-összekötő telepítése és konfigurálása

-   Használja a következő témakör utasításait: a [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) témakör.

##### Csak az Exchange és több eltávolítható: A beállításjegyzék szerkesztése

-   Minden egyes Exchange-kiszolgálón manuálisan adja hozzá a következő beállításkulcsokat a minden további TPD importált, az RMS-összekötő TPD URL-címek átirányítása. Ezek a bejegyzések adott áttelepítési, és nem adhatók hozzá a kiszolgálókonfigurációs eszköz Microsoft RMS-összekötőhöz.

    Ha ezeket a módosításokat, használja a következő útmutatás szerint:

    -   Csere *ConnectorFQDN* az összekötő a DNS-ben megadott néven. Például **rmsconnector.contoso.com**.

    -   A HTTP vagy HTTPS előtaggal összekötő URL-CÍMÉT, attól függően, hogy e konfigurálta az összekötő HTTP vagy HTTPS használatával kommunikálnak a helyszíni kiszolgálókkal használható.

    **Az Exchange 2013:**

    |Beállításjegyzékbeli elérési utat|Típusa|Érték|Adatok|
    |-------------------------------------|----------|---------|----------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|REG_SZ|https://&lt;AD RMS intranetes licencelési URL-cím &gt;/_wmcs/licencelés|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/Licensing<br />-   https://&lt;connectorName&gt;/_wmcs/Licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|REG_SZ|https://&lt;AD RMS extranetes licencelési URL-cím &gt;/_wmcs/licencelés|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/Licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/Licensing|
    **Exchange Server 2010:**

    |Beállításjegyzékbeli elérési utat|Típusa|Érték|Adatok|
    |-------------------------------------|----------|---------|----------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|REG_SZ|https://&lt;AD RMS intranetes licencelési URL-cím &gt;/_wmcs/licencelés|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/Licensing<br />-   https://&lt;connectorName&gt;/_wmcs/Licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|REG_SZ|https://&lt;AD RMS extranetes licencelési URL-cím &gt;/_wmcs/licencelés|Attól függően, hogy a HTTP vagy HTTPS az Exchange server kiszolgálóról az RMS-összekötővel, a következők egyike:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/Licensing<br />-   https://&lt;connectorName&gt;/_wmcs/Licensing|

Miután végrehajtotta ezeket az eljárásokat, olvassa el a **További lépések** szakasz a [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) témakör.

### <a name="BKMK_Step8Migration"></a>8. lépésével. Active Directory tartalomvédelmi szolgáltatások leszerelése
Nem kötelező: Távolítsa el az Active Directory megakadályozza, hogy a számítógépek felderítésével infrastruktúráját helyszíni Rights Management szolgáltatás kapcsolódási pontja (SCP). Ez nem kötelező (például úgy, hogy az áttelepítés parancsprogram futtatása) beállított a beállításjegyzékben az átirányítás miatt. A szolgáltatáskapcsolódási pont eltávolításához használja az AD SCP regisztrálására eszközt a [Rights Management szolgáltatások felügyeleti eszközkészlet](http://www.microsoft.com/download/details.aspx?id=1479).

Az AD RMS-kiszolgálók tevékenység, például figyelése ellenőrzésével a [a rendszerállapot jelentés kérelmek](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [ServiceRequest táblázat](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) vagy [a felhasználói hozzáférés naplózásának védett tartalom](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Ha meggyőződött RMS ügyfelek már nem folytatott kommunikáció ezeket a kiszolgálókat és, hogy az ügyfelek sikeresen használ Azure RMS, az Active Directory tartalomvédelmi szolgáltatások kiszolgálói szerepkör eltávolítása ezen a kiszolgálón. Dedikált kiszolgáló használata, inkább a figyelmeztető lépésének első leállítása a kiszolgálók egy időn belül, és győződjön meg arról, hogy nincsenek-e jelentett, a szolgáltatás folytonosságának biztosításához, az ügyfelek miért nem használ Azure RMS vizsgálata során ezek a kiszolgálók újraindítását igénylő problémák.

Után az AD RMS-kiszolgálók leállítására, előfordulhat, hogy ki szeretné lehetőség nyílik tekintse át a sablonok hagyományos Azure portálon konszolidálni őket, hogy a felhasználók kevesebb választhat, vagy konfigurálja újra azokat, vagy új sablonokat is hozzáadhat. Ez lehet is az alapértelmezett sablonok közzététele egy időben. További információ: [Az Azure Rights Management egyéni sablonok konfigurálása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

### <a name="BKMK_Step9Migration"></a>9. lépést. Az Azure RMS bérlői kulcs újbóli kulcs
Ez a lépés áttelepítés befejeződik az AD RMS-telepítés volt használata az RMS titkosítási mód 1, mert újra kulcskezelő hoz létre egy új bérlő kulcsot használó RMS 2. kriptográfiai mód esetén szükséges. A titkosítási mód 1 Azure RMS segítségével csak az áttelepítési folyamat során támogatott.

Ez a lépés nem kötelező azonban ajánlott az áttelepítés után akkor is, ha a futtatása során, az RMS titkosítási mód 2, mert az Azure RMS bérlői kulcs potenciális biztonsági résekkel szemben az AD RMS-kulcsot a biztonságossá segít. Újra kulcsát az Azure RMS bérlői kulcsot (más néven "működés közbeni a kulcs"), amikor létrejön egy új kulcsot, és az eredeti kulcsra archiválva legyen. Mivel áthelyezése egyik kulcs nem fordulhat elő, azonnal, de néhány hétben nem megvárni, az eredeti kulcs megsértése gyanús azonban az RMS bérlői kulcs újbóli kulcsot a, amint az az áttelepítés.

Az újbóli kulcsát az Azure RMS bérlői kulcs:

-   Ha a Microsoft felügyeli az RMS bérlői kulcs: Hívja a Microsoft ügyfélszolgálathoz (CSS), és igazolni, hogy-e az RMS Bérlői rendszergazda.

-   Ha az RMS bérlői kulcs kezeli, (BYOK): Ismételje meg a BYOK eljárást előállításához és az interneten keresztül vagy a személy, hozzon létre egy új kulcsot.

Az RMS bérlői kulcs kezelésével kapcsolatos további információkért lásd: [A Azure Rights Management bérlői kulcs műveletek](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

