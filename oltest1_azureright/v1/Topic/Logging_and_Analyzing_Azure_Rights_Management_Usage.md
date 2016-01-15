---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Napl&#243;z&#225;s, &#233;s az Azure Rights Management haszn&#225;lati elemz&#233;se
Ez a témakör információk segítségével megismerheti, hogyan használhatja a naplózást az Azure Rights Management (Azure RMS) használatát. Az Azure Rights Management szolgáltatás be tud jelentkezni minden kérelemnél, hogy a szervezet az Azure Rights Management központi telepítését támogatja a felhasználók, a Rights Management-rendszergazdák a szervezet által végrehajtott műveletek és a Microsoft által végrehajtott műveletek kérelmek teszi.

Ezeket a naplókat, Azure Rights Management támogatásához a következő üzleti helyzetekben használhatja:

-   Az üzleti insights elemzése.

    Azure Rights Management naplófájlba írja az Ön Azure-tárolás figyelembe naplók W3C bővített naplófájl formátumban. Ezek a naplók a kiválasztott tára történő majd irányíthatók (például egy adatbázis, az online analitikus feldolgozási (OLAP) rendszer vagy a rendszer térkép csökkentése) elemezheti az adatokat, illetve olyan jelentések elkészítését. Például akkor tudta azonosítani az RMS által védett adatokat használja. Megadhatja, milyen RMS által védett adat személyek érik el, és milyen eszközökről, és helyét. Alapján meggyőződhet arról, hogy személyek is sikeresen beolvasta a védett tartalomhoz. Kik elolvasta egy fontos dokumentum védett szintén azonosíthatja.

-   Ez a figyelő a visszaélés.

    Az Azure Rights Management-naplózási információkat érhető el az Ön közel valós időben, így folyamatosan figyelheti a vállalat használata a Rights Management. 99,9 naplók %-át egy RMS által kezdeményezett művelet 15 percen belül érhetők el.

    Például előfordulhat, hogy szeretne értesítést, ha nincs olvasási RMS által védett adat utalhat, hogy egy rosszindulatú felhasználó versenytársakhoz értékesítheti információkat gyűjt, amelyek szabványos munkaidőn kívüli személyek hirtelen növekedését. Vagy, ha ugyanazon felhasználó látszólag éri el az adatokat rövid időn belül, amelyek jelezhetik, hogy két különböző IP-címet a felhasználói fiók feltörték-e.

-   Eseményeknél elemezhetjük.

    Ha az adatok memóriavesztés, akkor valószínűleg rákérdez, akik a legutóbb elért adott dokumentumok és milyen információkat adta a gyanús személy hozzáférési nemrég. Ezek a kérdések típus válaszolhat, Azure Rights Management és naplózását, mert a felhasználók védett tartalmat kell mindig a Rights Management licenc megszerzéséhez dokumentumokat és képeket, még akkor is, ha ezeket a fájlokat e-mailben áthelyezték vagy USB-meghajtók vagy egyéb tárolóeszközök másolni Azure Rights Management által védett megnyitásához. Ez azt jelenti, hogy használható Azure Rights Management naplók adatok végleges forrásaként eseményeknél analysis Azure Rights Management használatával az adatok védelme.

> [!NOTE]
> Ha az Önt érdeklő csak az Azure Rights Management, és hajtsa végre a felügyeleti feladatok naplózását nem szeretne nyomon követni a felhasználók hogyan használják a Rights Management, használhatja a [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) Azure Rights Management Windows PowerShell-parancsmagot.
> 
> A magas szintű használati jelentéseket tartalmazó is használhatja az Azure-portálon **RMS használati**, **RMS legaktívabb felhasználók**, **RMS eszköz használata**, és **RMS-kompatibilis alkalmazással való használat**. Ezek a jelentések eléréséhez az Azure portálról kattintson **Active Directory**, jelölje be és nyissa meg a könyvtárat, és kattintson **jelentések**,

A következő részekben olvashat Azure Rights Management használat naplózása.

-   [Azure Rights Management használati naplózásának engedélyezése](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [Hozzáférés, és az Azure Rights Management használati naplók használata](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [Az Azure Rights Management napló tárolási kezelése](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [Delegálja a hozzáférést az Azure Rights Management használati eseménynaplók](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [Az Azure Rights Management használati naplók értelmezése](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [A Windows PowerShell-hivatkozás](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>Azure Rights Management használati naplózásának engedélyezése
Azure Rights Management használat naplózása nem kötelező, így szeretne használni, ha adott lépéseket kell végrehajtania. Azure Rights Management használat naplózása használatakor nincs változás a Rights Management működése, és a naplózási folyamat maga szabad. Azonban meg kell adnia egy Azure-tárfiókjába a naplókat, és a tárolás felszámított.

Megkezdése előtt győződjön meg arról, hogy a használat naplózása Azure Rights Management használata a következő előfeltételek teljesüléséről:

|Követelmény|További információ|
|---------------|----------------------|
|Az IT-felügyelt előfizetés, amely tartalmazza az Azure Rights Management|A szervezet által felügyelt Microsoft Azure Rights Management előfizetéssel kell rendelkeznie. RMS egyéni felhasználók számára használó szervezetek Azure Rights Management használat naplózása nem használható.<br /><br />Ha a szervezet használja az RMS egyéni felhasználók számára, akik, Azure Rights Management használat naplózása biztosít RMS egyéni felhasználók számára átalakítása előfizetéssé Microsoft Azure Rights Management nagyon fontos üzleti oka.<br /><br />Az előfizetések, amely tartalmazza az Azure RMS kapcsolatos további információkért tekintse meg a [Felhő előfizetések, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) szakasz a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) témakör.<br /><br />Az egyes személyek RMS kapcsolatos további információkért lásd: [RMS egyének és az Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|Azure-előfizetés|Azure Azure és elegendő tárterület egy előfizetést az Azure Rights Management naplók kell rendelkeznie.|
|A Windows PowerShell Azure Rights Management|Még nem tette meg ezt, töltse le és telepítse a Windows PowerShell-modul Azure Rights Management. A Windows PowerShell-parancsmagok használandó konfigurálhatja és kezelheti az Azure Rights Management használati naplókat.<br /><br />További információ: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).|
Az alábbi eljárás segítségével hozzon létre egy Azure storage-fiókot, és adja meg a tárolási fiók használatához a Rights Management naplók Azure lépéseivel Azure Rights Management használati naplózás engedélyezéséhez.

> [!NOTE]
> Ez az eljárás feltételezi, hogy rendelkezik-e az Azure-fiók. Azure Rights Management használat naplózása támogatja az egyes fiókokat, de ajánlott eljárásként használja a munkahelyi vagy iskolai fiókok. Ezenkívül javasoljuk, hogy a Rights Management naplók dedikált tárfiók létrehozása. A tároló elérési kulcsainak Azure Rights Management, és esetleg másokkal meg kell osztania, ha azok lesz a naplófájlokat is használhatja.
> 
> Az Azure tárolás kapcsolatos további információkért tekintse meg a [tárolási Azure dokumentációjában](http://azure.microsoft.com/documentation/services/storage/).

#### A tárfiók létrehozása és az Azure Rights Management használati naplózásának engedélyezése

1.  Jelentkezzen be a [Azure-portálon](https://manage.windowsazure.com/).

2.  Válassza ki **tárolási**.

    > [!TIP]
    > Ha ez a beállítás nem jelenik meg, ellenőrizze, hogy az Azure-előfizetés mellett a Rights Management előfizetéshez.

3.  Kattintson **tárolási fiók létrehozása** és a **URL-cím**, adjon meg egy egyedi nevet a tárolási fiók, és ha szükséges, módosítsa a **helye: AFFINITÁSCSOPORT** hogy az megfeleljen az adott régióban.

4.  Kattintson a **OK**, és várjon, amíg megjelenik a tároló neve, állapota **Online**.

5.  Kattintson a **elérési kulcsainak kezelése**.

6.  Az a **elérési kulcsainak kezelése** párbeszédpanelt, amelyik az elsődleges és másodlagos elérési kulcsainak jeleníti meg az elsődleges hozzáférési kulcsot a vágólapra másolja, és zárja be a párbeszédpanelt.

7.  Indítsa el a Windows PowerShell a **Futtatás rendszergazdaként** beállítást. Futtassa a [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) parancs az Azure Rights Management szolgáltatáshoz való kapcsolódáshoz:

    ```
    Connect-AadrmService
    ```

8.  Használja a [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) parancsot adja meg, ha meg szeretné tartani az Azure Rights Management használati naplók cseréje *&lt; Access_Key &gt;* és az elsődleges hozzáférési kulcsot a 6. lépésben átmásolt és *&lt; StorageAccount &gt;* a 3. lépésében létrehozott tárfiók nevét:

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. Használja a [engedélyezése-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx) parancs Azure Rights Management használati naplózás engedélyezése:

    ```
    Enable-AadrmUsageLogFeature
    ```
    Megjelenik az üzenet: **A használati napló funkció engedélyezve van a tartalomvédelmi szolgáltatás.**

Most, hogy a használat naplózása engedélyezve van, az Azure Rights Management megkezdi a szervezet összes műveleteket, és menti ezt az információt a tárolási fiók. Mielőtt ezt a pontot ügyfélnaplózási információ nem érhető el.

## <a name="BKMK_AccesAndUseLogs"></a>Hozzáférés, és az Azure Rights Management használati naplók használata
Azure Rights Management BLOB sorozataként naplók ír az Azure-tárfiókjába. Minden egyes blob tartalmaz egy vagy több naplórekordokat, W3C bővített naplófájl formátumban. A blob neve olyan számok, és a sorrendben, ahol azok létre lettek hozva. A [Az Azure Rights Management használati naplók értelmezése](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret) a jelen dokumentum szakasz tartalmaz további információt a napló tartalmát, és a létrehozásukat.

Is telhet, amíg az Azure Rights Management művelet után jelennek meg a tárfiók-naplókat. A legtöbb naplók 15 percen belül jelenik meg.

A tárolási fiók, amelyet az Azure Rights Management használati naplók hozott létre például egy postaláda és közvetlenül a tárolási fiók olvasását támogatja, de nincs optimalizálva, így használható. Ehelyett a lehető legjobb teljesítmény és a költségek csökkentése érdekében azt javasoljuk, hogy a naplók helyi tárolóra, például egy helyi mappába, adatbázis, töltse le, vagy a tárház térkép csökkentésére.

A használati naplók kétféle módon tölthető le:

-   A Windows PowerShell-parancsmag [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx).

    Ez a legegyszerűbb a használati naplók eléréséhez. Ez a parancsmag minden blob letöltése fájlként egy olyan helyre, akkor adja meg, a számítógép letölti a naplókat.

-   Használja a [Azure Storage szolgáltatás SDK](http://www.windowsazure.com/en-us/develop/net/) saját egyéni alkalmazás letöltéséhez a naplók írni.

    Egyéni alkalmazás több, mint a Get-AadrmUsageLogs parancsmag rugalmasságot biztosítanak. Például előfordulhat, hogy szeretné a letöltés naplók átadhatja valaki vagy folyamat, amely nem használható az Azure Rights Management rendszergazdai hitelesítő adatokkal. Vagy kérdezze le a valós idejű naplók, mert helytelen a figyelni kívánt érdemes.

#### A használati naplók letöltése a PowerShell használatával

-   Indítsa el a Windows PowerShell a **Futtatás rendszergazdaként** lehetőséget, majd futtassa **Get-AadrmUsageLog –Path &lt;location&gt;**. Például a nevű mappa létrehozása után **logs** E-meghajtón:

    -   Az összes elérhető naplók letöltése a E:\logs mappába: `Get-AadrmUsageLog -Path "e:\logs"`

    -   Egy adott porttartomány BLOB letöltése: `Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

Ezek a parancsmagok futtatásakor a Windows PowerShell letöltött utolsó blob nevét jeleníti meg. Rendelhet a név egy változó, amely lehetővé teszi, hogy futtassa a Get-AadrmUsageLog hurkot vagy egy feladat ütemezése, a növekményes naplók letöltése minden alkalommal.

Példa:

**PS C:\ &gt; $LastBlobName = Get-AadrmUsageLog – elérési út "e:\logs"**

**1527**

**PS C:\ &gt; $LastBlobName**

**1527**

> [!TIP]
> Is összesítheti összes letöltött naplófájl alkalmazásba CSV-formátum használatával [Microsoft napló elemző](http://www.microsoft.com/download/details.aspx?id=24659), amelynek célja, hogy a különböző jól ismert napló formátumok közötti átváltásra. Ezzel az eszközzel adatokat konvertálása SYSLOG formátumba, és importálja azt az adatbázis is. Az eszköz telepítése után futtassa **LogParser.exe /?** a Súgó és az adatokat ezzel az eszközzel. Például előfordulhat, hogy futtassa az alábbi parancs futtatásával importálja az összes információt a .log fájl formátumra: **logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**.

Felfüggesztése, és használati naplózás folytatásához. Naplózási felfüggesztésekor Azure Rights Management megőrzi a tárolási fiók adatait, így könnyen folytathatja naplózás újból.

#### Felfüggesztése és folytatása a használat naplózása

-   Naplózási felfüggesztése, használja a következő parancsmagot: [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   A naplózás folytatásához használja az alábbi parancsmagot: [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   Ellenőrizze a naplózás engedélyezve vagy letiltva, használja a következő parancsmagot: [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    Érték **Igaz** azt jelenti, hogy az használati naplózás engedélyezve van-e az Azure Rights Management és érték **hamis** azt jelenti, hogy a használat naplózása le van tiltva.

## <a name="BKMK_ManageStorage"></a>Az Azure Rights Management napló tárolási kezelése
A tárolóhely, amellyel az Azure Rights Management naplók tartsa felszámítani.

Az Azure Rights Management nincs automatikus felügyeleti a használati naplófájlok nem. Ha nincs a művelet a tárolási fiók megmaradnak. Azonban a helymegtakarítás, és csökkentheti a tárolási költségek csökkentését, előfordulhat, hogy szeretné törölni őket, miután letöltötte azokat. Vagy választhatja, hogy mely fájlok törléséhez. Egy kivétellel Azure Rights Management nem használja ezeket a naplófájlokat, így nincsenek korlátozások kapcsolatban, ha segítségével törölheti.

A fájl, amely akkor kell törölni (vagy módosítani) nevű **metaadatok** amely szerepel a **rms-metaadatok** tároló. Az Azure Rights Management a blob a használt utolsó blob számát nyomon követésére használ. Ha ez a fájl törlődik, Azure Rights Management naplókat, új tárolója kezdődik a blob-számnak 1-től kezdődő, és későbbi letöltések a Get-AadrmUsageLog parancsmaggal ebben a tárolóban követve töltheti le a naplófájlokat. Emiatt a naplók az eredeti tárolóban maradnak, de árva. Töltse le az árva naplók csak úgy az Azure tárolás SDK használatára.

> [!TIP]
> Helyett az Azure Rights Management napló tárolás kezelésére saját magát, a a fiók nevét és a hozzáférési kulcs megosztása delegálhatja a kezelési funkciót egy másik vállalat. További információ: a [Delegálja a hozzáférést az Azure Rights Management használati eseménynaplók](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate) később című szakaszában talál.

Bizonyos esetekben a kívánt előfordulhat, hogy a tároló elérési kulcsainak újragenerálása. Példa:

-   A vállalat az Azure Rights Management használati naplók felügyelő módosítása

-   Azt feltételezi, hogy a hozzáférési kulcs sérült integritású.

Ha ez történik, a rendszer használatakor a másodlagos hozzáférési kulcsot (az azt feltételezi, hogy az elsődleges hozzáférési kulcsot korábban a) a szolgáltatás folytonosságának biztosításához. Ha újragenerálni a hozzáférési kulcs, amely korábban nem használt, majd konfigurálnia Azure Rights Management használata az új kulccsal. Az alábbi eljárás segítségével generálni a másodlagos hozzáférési kulcsot, és konfigurálhatja az Azure Rights Management rá:

#### A másodlagos hozzáférési kulcs újragenerálása

1.  Jelentkezzen be a [Azure-portálon](https://manage.windowsazure.com/).

2.  Válassza ki **tárolási**.

3.  Kattintson a **elérési kulcsainak kezelése**.

4.  A a **elérési kulcsainak kezelése** párbeszédpanelen kattintson a **újbóli** mellett a másodlagos hozzáférési kulcsot, és az új másodlagos hozzáférési kulcsot a vágólapra másolása.

5.  Indítsa el a Windows PowerShell és a a **Futtatás rendszergazdaként** lehetőséget, és használja a [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) konfigurálása az új hozzáférési kulcs használatához Azure Rights Management parancsmag cseréje *&lt; StorageAccount &gt;* a tárolási fiók nevével és *&lt; Access_Key &gt;* előbb másolt másodlagos rendszer újragenerálta a hozzáférési kulccsal rendelkező:

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > Bár a parancs futtatásakor lehet váltani egy másik tárolási fiókot, ez a művelet orphans a korábbi naplókat, és többé nem lesznek elérhetők legyenek a Set-AadrmUsageLogStorageAccount parancsmag vagy hasonló felügyeleti parancsokat és funkciókat.

6.  Vissza a **elérési kulcsainak kezelése** párbeszédpanel mezőbe generálni az elsődleges hozzáférési kulcsot.

## <a name="BKMK_Delegate"></a>Delegálja a hozzáférést az Azure Rights Management használati eseménynaplók
Hozzáférés a fiók nevét és a hozzáférési kulcs megosztása delegálhatja a RMS naplókat. Előfordulhat, hogy szeretne egy másik rendszergazda felhasználó, a fejlesztők saját a szervezeten belüli vagy egy független szoftverszállító (ISV) hozzáférési delegálása. Nem rendelkeznek a RMS rendszergazdai hitelesítő adatait, mert a Get-AardrmUsageLog parancsmag nem használhatják az RMS-naplók letöltése. Ehelyett a Windows Storage szolgáltatás SDK kell használják a naplók letöltése. Másik lehetőségként írják alkalmazás, olvassa el a naplók közvetlenül az Azure Storage szolgáltatásból.

Rendkívül biztonságos megosztása a fiók nevét és a hozzáférési kulcs ily módon, ha a tárolási fiók van hozzárendelve az RMS-naplók. Annak ellenére, hogy más felhasználók is a hozzáférési kulcsot, nem használhatják a más tárfiók eléréséhez vagy használatához az RMS bérlői fiókját.

## <a name="BKMK_Interpret"></a>Az Azure Rights Management használati naplók értelmezése
Az alábbi információk segítségével az Azure Rights Management használati naplók értelmezni.

### A tárolási fiók elrendezés
Az első alkalommal Azure Rights Management naplók ír a tárolási fiók létrehozza a következő két tárolókban:

-   **Rms-metaadatok**: Ebben a tárolóban Azure Rights Management számára van fenntartva. Nem módosítása vagy törlése a tárolóban.

-   **Rms - naplók - &lt; guid &gt;**: Ebben a tárolóban, ahol Azure Rights Management hoz létre, és menti a naplókat. Az ebben a tárolóban lévő összes fájlt biztonságosan törölni, ha már nincs szüksége a naplózási adatok, amelyek tartalmazzák.

Az idő múlásával Azure Rights Management lehet, hogy hozzon létre további **Rms - naplók - &lt; guid &gt;** tárolók. Például ha a **Rms-metaadatok** tároló megsérül vagy véletlenül törlődik, Azure Rights Management visszaállítja a tartalmát, és létrehoz egy új **Rms - naplók - &lt; guid &gt;** összes későbbi napló tárolója. A régi naplókat a régi tárolóban nem törlődnek, de árván marad.

### A naplófájl-sorozat
Az Azure Rights Management BLOB sorozataként naplófájlba írja a naplókat. Minden egyes blob tartalmaz egy vagy több naplórekordokat, kiterjesztett W3C-napló formátumban.

Minden egyes blob neve az a szám. Az első blob belül minden naplózási tároló 000000001 neve. Minden egyes blob egymás után neve a sorrendet, amelyben létrehozták. Minden egyes blob tartalmaz egy vagy több naplófájl rögzíti. Minden egyes naplórekord rendelkezik UTC időbélyeggel, amely azt jelzi, ha a vonatkozó kérés Azure Rights Management által állítása és kiszolgálása között.

> [!IMPORTANT]
> Az Azure Rights Management naplózási rendszer biztosítanak a naplók gyorsan ahelyett, hogy szigorú sorrendben van optimalizálva. A BLOB sorrendjét, valamint egy blob lévő rekordok sorrendjét helytelen időrendi sorrendben lehet. A csak a BLOB egymás után elnevezése azért lehetővé teszik, hogy hatékonyan letölteni azokat növekményes.
> 
> Két lehetséges napló feladatütemezési eredmények példák:
> 
> -   A naplófájl rögzíti a blob 000000004 időrendi sorrendben átfedést előfordulhat, hogy a naplófájl rögzíti a blob 000000003. Szélsőséges esetben az összes naplófájl rögzíti a blob 000000004 előfordulhat, hogy létrejöttek 000000003 blobban található rekordok napló előtt.
> -   A blob második naplórekord első naplórekord előtt előfordulhat, hogy létrejöttek, de írt-tároló fordított sorrendben.

Előtt elemezni az Azure Rights Management használati naplókat, javasoljuk, hogy töltse le a napló importálása egy tárház, ahol a naplók a timestamp alapján rendezheti. A naplók letöltendő további információkért lásd: a [Hozzáférés, és az Azure Rights Management használati naplók használata](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs) című szakaszában talál.

A naplók nem feltétlenül időrendi, de a legtöbb írt a kérelem 15 percen belül, a naplók a timestamp kívánt azonosításakor, mert hozzá az Önt érdeklő idő 15 perc. Ezek a naplók majd letölteni. Ezt a stratégiát követi biztosítania kell, hogy a naplók szinte minden beolvasása.

Ne feledje, hogy egy másik dolgot, hogy az egyes naplórekord időbélyegzőt-e a helyi idő az Azure Rights Management szolgáltatás, amely a kérelem feldolgozása. Azure Rights Management több kiszolgálón fut, több adatközpontban, mert egyes esetekben a naplók előfordulhat, hogy úgy tűnik, hogy helytelen sorrendben, akkor is, ha ezek a timestamp szerint rendezi. Azonban a különböző van, kis- és általában egy percen belül. A legtöbb esetben ez nem a problémát, amelynek a napló elemzés probléma lenne.

### A blob formátum
Minden egyes blob W3C bővített naplófájl formátumban van. Az alábbi két sort kezdődik:

**#Software: RMS**

**#Version: 1.1**

Az első sor azonosítja, hogy ezek a naplók Azure Rights Management. A második sor azonosítja, hogy a blob többi követi a 1.1-es verziója megadását. Javasoljuk, hogy olyan alkalmazásokat, amelyek elemezni ezek a naplók két sort ellenőrizze a blob többi elemezni a folytatás előtt.

A harmadik sor enumerálása mezőnevek lapok elválasztott listáját:

**#Fields: dátum szerinti idő sorazonosító kérelem-típus felhasználói azonosítót eredménye Korrelációazonosító tartalom-id tulajdonosa-e-mailek kibocsátó sablonazonosító fájlnév dátum közzétett c-info c ip-**

Az ezt követő sorok egy naplórekordot. A mező értékének ugyanabban a sorrendben, mint az előző sor kerül, és lapok el egymástól. Az alábbi táblázat segítségével értelmezni a mezőket.

|Mező neve|W3C adattípus:|Leírás|Példa érték|
|-------------|------------------|----------|---------------|
|dátum|Dátum|UTC dátum, amikor a kérelem állítása és kiszolgálása között.<br /><br />A forrás, a helyi idő azon a kiszolgálón, a kérelem és kiszolgálása között.|2013-06-25|
|idő|Idő|UTC idő 24 órás formátumban, amikor a kérelem állítása és kiszolgálása között.<br /><br />A forrás, a helyi idő azon a kiszolgálón, a kérelem és kiszolgálása között.|21:59:28|
|sor-azonosító|Szöveg|A naplórekord egyedi GUID azonosítója.<br /><br />Ez az érték akkor hasznos, ha a naplók vagy naplók másolása egy másik formátumra összesíteni.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|kérés-típusa|Neve|Az RMS API-t, hogy a kért neve.|AcquireLicense|
|felhasználó-azonosító|Karakterlánc|A felhasználó, aki a kérést.<br /><br />Az érték az egyetlen idézőjelek közé. Bizonyos kérelemtípusoknál fel a névtelen, ebben az esetben az értéke ".|"joe@contoso.com"|
|eredmény|Karakterlánc|"Sikeres" Ha a kérelem sikeres volt kiszolgált.<br /><br />A hiba típusa egyetlen idézőjelek közé, ha a kérelem végrehajtása sikertelen.|"Sikeres"|
|korrelációs-azonosító|Szöveg|Az RMS ügyfél és kiszolgáló napló egy adott kérelem esetén közötti közös GUID.<br /><br />Ez az érték lehet hasznos ügyfél problémák elhárítása érdekében.|cab52088-8925-4371-be34-4b71a3112356|
|tartalom-azonosító|Szöveg|GUID, amely azonosítja a védett tartalom (például egy dokumentum) kapcsos zárójelek közé.<br /><br />Ez a mező értéke csak akkor, ha a kérelem-típus AcquireLicense, és az összes többi kérelem üres.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|tulajdonos-e-mailek|Karakterlánc|A dokumentum tulajdonosa e-mail címe.|Alice@contoso.com|
|kibocsátó|Karakterlánc|A dokumentum kibocsátó e-mail címe.|Alice@contoso.com (vagy) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com "|
|Sablon-azonosító|Karakterlánc|A dokumentum védelmére használt sablon azonosítója.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|Fájlnév|Karakterlánc|A dokumentum védett fájl nevét.|TopSecretDocument.docx|
|Dátum közzétett|Dátum|Az dátum, amikor a dokumentum védett.|2015-10-15T21:37:00|
|c-információ|Karakterlánc|A kérés ügyfél platformja adatait.<br /><br />A megadott karakterlánc (például az operációs rendszer vagy a böngésző) alkalmazástól függően változik.|"MSIPC; verzió = 1.0.623.47; Alkalmazásnév = WINWORD. EXE; AppVersion = 15.0.4753.1000; AppArch = x 86; OSName = Windows; OSVersion = 6.1.7601; OSArch = amd64 "|
|az ip-c|Cím|IP-cím, az ügyfél, amely a kérelmet.|64.51.202.144|

#### A felhasználói azonosítót mező kivételek
A felhasználói azonosítót mező általában jelzi, hogy a felhasználó, aki a kérést, de van két kivétel ahol az érték nem felel meg a tényleges felhasználói:

-   Az érték **"microsoftrmsonline @&lt; YourTenantID &gt;. &lt; régió &gt; hagyatkozni. aadrm.com"**.

    Ez azt jelenti, hogy az Office 365 szolgáltatáshoz, például az Exchange online-hoz, vagy a Sharepoint Online lehetővé teszi a kérelmet. A karakterlánc *&lt; YourTenantID &gt;* van a GUID azonosító a bérlő és *&lt; régió &gt;* a régió, ahol a bérlő regisztrálva van-e. Például **na** jelöli az Észak-amerikai **EU-s** jelöli Európa, és **hozzáférési pont** ázsiai jelöli.

-   Ha az RMS-összekötőt használja.

    Ez az összekötő érkező kéréseket az egyszerű szolgáltatásnév RMS automatikusan állít elő, amikor telepíti az RMS-összekötő naplózza.

#### Tipikus kérelem típusok
Az Azure Rights Management többféle kérelmet, de a következő táblázat azokat a legtöbb általánosan használt kérelem valamelyikének.

|Kérés típusa|Leírás|
|----------------|----------|
|AcquireLicense|ügyfél Windows-alapú számítógépről RMS által védett tartalom licencet kér.|
|AcquirePreLicense|egy ügyfelet, a felhasználó nevében kér RMS által védett tartalom licenccel.|
|AcquireTemplates|hívás érkezett beolvasások sablonok azonosítók sablon alapján történő|
|AcquireTemplateInformation|hívás érkezett az azonosítók a sablon lekérni a szolgáltatásból.|
|AddTemplate|hívás történik az Azure portálról vegyen fel egy sablont.|
|BECreateEndUserLicenseV1|egy hívását mobileszközről hozzon létre egy végfelhasználói licencszerződés.|
|BEGetAllTemplatesV1|hívás mobileszközről (háttér) történik az összes sablon beszerzéséhez.|
|Hitelesítés|az ügyfél a tartalom védelemre van tanúsító.|
|Visszafejtése|az ügyfél megpróbál a RMS által védett tartalom visszafejtéséhez.|
|DeleteTemplateById|törölni egy sablon által sablon. hívás történik az Azure portálról|
|ExportTemplateById|hívás történik, az Azure portálról azonosító sablon alapján történő sablon exportálása|
|FECreateEndUserLicenseV1|hasonló a AcquireLicense kérelmet, de a mobileszközökről.|
|FECreatePublishingLicenseV1|megegyeznek a mobil ügyfelek hitelesítés és GetClientLicensorCert kombinált.|
|FEGetAllTemplates|hívás történik, (előtér-) mobileszközről lekérni a sablonokat.|
|GetAllTemplates|beolvasni az összes sablon hívás történik az Azure portálról.|
|GetClientLicensorCert|az ügyfél Windows-alapú számítógépről egy közzétételi (később használt tanúsítvány tartalom védelméhez) kér.|
|GetConfiguration|az Azure PowerShell-parancsmag neve megszerezni az Azure RMS bérlői konfigurációját.|
|GetConnectorAuthorizations|hívás történik, az az RMS-összekötők beolvasni a konfigurációt a felhőből.|
|GetTenantFunctionalState|az Azure portálon, ellenőrzi, hogy aktiválva van-e az Azure RMS.|
|GetTemplateById|hívás történik az Azure portálról adja meg a sablon azonosítója. szerezzen egy sablon|
|ExportTemplateById|hívás sablon exportálása azonosító sablon megadásával történik az Azure portálról|
|FindServiceLocationsForUser|egy hívását lekérdezni URL-címek, a hitelesítés vagy AcquireLicense hívásához használt.|
|ImportTemplate|hívás sablon importálása az Azure portálról történik.|
|ServerCertify|hívás a kiszolgáló hitelesítésére az RMS-kompatibilis ügyfél (például SharePoint) történik.|
|SetUsageLogFeatureState|egy hívás a használati naplózás engedélyezéséhez.|
|SetUsageLogStorageAccount|hívás történik az Azure RMS naplók elérési útja.|
|SignDigest|egy hívás egy kulcs az aláíráshoz célokra használatakor. Ezt nevezik általában egyszer AcquireLicence (vagy FECreateEndUserLicenseV1) hitelesítés, és GetClientLicensorCert (vagy FECreatePublishingLicenseV1).|
|UpdateTemplate|hívás történik az Azure portálról frissítse a meglévő sablon.|

## <a name="BKMK_PowerShell"></a>A Windows PowerShell-hivatkozás
A következő Windows PowerShell-parancsmagok segítségével könnyebben konfigurálható és használható Azure Rights Management használat naplózása:

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

További információ a Windows PowerShell használatával az Azure Rights Management: [Az Azure Rights Management felügyelete a Windows PowerShell használatával](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Lásd még
[Azure Rights Management használata](../Topic/Using_Azure_Rights_Management.md)

