---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# A Azure Rights Management b&#233;rlői kulcs műveletek
Attól függően, hogy a bérlői kulcs topológia (a Microsoft által felügyelt, vagy az ügyfél által felügyelt), amelyeknek eltérő szintű irányítási és a Microsoft Azure Rights Management (Azure RMS) bérlői kulcs felelősséget annak végrehajtását követően.

A saját bérlői kulcs kezelésekor Ez gyakran hivatkozik, amely szerint hozása a saját kulcsot (BYOK). Ezt a helyzetet, és a két bérlői kulcs topológiát közötti kiválasztásáról további tájékoztatásért lásd: [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

A következő táblázat milyen megteheti, attól függően, hogy a topológia, amelyek az Azure RMS-bérlői kulcs kiválasztotta műveleteket azonosítja.

|Életciklusra vonatkozó művelet|A Microsoft által felügyelt (alapértelmezett)|Az ügyfél által felügyelt (BYOK)|
|----------------------------------|-------------------------------------------------|------------------------------------|
|A bérlő kulcs visszavonása|Nincs (automatikus)|Nincs (automatikus)|
|Ismételt kulcs a bérlői kulcs|Igen|Igen|
|Készítsen biztonsági másolatot, és a bérlői kulcs helyreállítása|Nem|Igen|
|A bérlő kulcs exportálása|Igen|Nem|
|Megsértése válaszolni.|Igen|Igen|
Miután meghatározta, hogy mely topológia megvalósított, ezek a műveletek az Azure RMS-bérlői kulcs további információt a következő szakaszok egyikével.

## <a name="BKMK_MSManagedOperations"></a>A Microsoft által felügyelt: A bérlő kulcs életciklusra vonatkozó műveletek
A Microsoft Azure Rights Management (alapértelmezett) a bérlői kulcs kezeli, használja az alábbi szakaszok a életciklusra vonatkozó műveleteket, amelyek a topológia vonatkozó további információ:

-   [A bérlő kulcs visszavonása](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [Ismételt kulcs a bérlői kulcs](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [Készítsen biztonsági másolatot, és a bérlői kulcs helyreállítása](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [A bérlő kulcs exportálása](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [Megsértése válaszolni.](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>A bérlő kulcs visszavonása
Lemondani az Azure RMS, amikor Azure RMS leállítja a bérlői kulccsal, és nincs szükség műveletre Öntől.

### <a name="BKMK_MSRekey"></a>Ismételt kulcs a bérlői kulcs
Ismételt kulcskezelő is nevezik működés közbeni a kulcsot. Nem újra kulcs a bérlői kulcs nem valóban szükséges. Régebbi ügyfelek, például az Office 2010, nem tervezték, hogy a kulcs módosítások biztonságosan kezelni. Ebben az esetben törölnie kell az azokon a számítógépeken az RMS-állapot csoportházirend vagy egy egyenértékű mechanizmus használatával. Vannak azonban néhány törvényes az eseményeket, amelyek újra kulcs a bérlői kulcs lehet kényszeríteni. Példa:

-   A vállalati meg van felosztása két vagy több vállalat. Újra a a bérlői key kulcs, ha a az új vállalat nem rendelkezik, amely az alkalmazottak közzététele új tartalom elérése. A régi tartalom hozzáféréssel rendelkeznek a régi bérlői kulcs egy példányát.

-   Úgy véli, hogy a bérlői kulcsot (az Ön birtokában példány) fő példányát jutott.

A bérlő kulcs újra meghívja a Microsoft ügyfélszolgálathoz (CSS), és amely igazolja, hogy-e a bérlői rendszergazda is kulcs.

Ha újra a a bérlői key kulcs – új által védett az új bérlői kulccsal. Ez a szakaszolt módon történik, egy adott időn belül az egyes új tartalom továbbra is lehet védetté tenni, a régi bérlői kulccsal. Korábban a védett tartalom marad a régi bérlői kulcs védett. Támogatja ezt a helyzetet, hogy Azure RMS, hogy azt a régi tartalom licenceinek adhat megtartja a korábbi bérlői kulcsot.

### <a name="BKMK_MSBackup"></a>Készítsen biztonsági másolatot, és a bérlői kulcs helyreállítása
A Microsoft a bérlői kulcs biztonsági másolatának felelős, és nincs teendője, mint az Ön.

### <a name="BKMK_MSExport"></a>A bérlő kulcs exportálása
Az Azure RMS-beállításai, és a bérlői kulcs exportálása, ezeket a lépéseket utasításait követve:

##### 1. lépés: Kezdeményezze a exportálása

-   Ehhez hajtsa végre a, forduljon a Microsoft ügyfélszolgálathoz szolgáltatás (CSS). Meg kell igazolja, hogy a rendszergazda az Azure RMS-bérlőben.

##### 2. lépés: Várjon, amíg a ellenőrzése

-   A Microsoft azt ellenőrzi, hogy az RMS-bérlői kulcs kiadási vonatkozó kérését törvényes. A folyamat akár 3 hét is eltarthat.

##### 3. lépés: Kulcs utasításokat fogadásához CSS

-   Microsoft ügyfélszolgálathoz (CSS) fog küldeni a Azure RMS-beállításai, és a bérlői kulcsnak titkosítva egy .tpd kiterjesztésű jelszóval védett fájlban. Ehhez CSS először küld Önnek (mint az személy, aki az Exportálás kezdeményezése) egy eszköz által e-mailt. Futtatnia kell az eszközt a parancssorba a következő:

    ```
    AadrmTpd.exe -createkey
    ```
    Ez egy RSA kulcspár állít elő, és a nyilvános és titkos fele fájlként menti az aktuális mappában. Például: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** és **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Válaszolni az e-mailt a CSS, a fájl, amely kezdetű névvel rendelkezik csatolása **PublicKey**. CSS tovább küld TPD fájl egy .xml fájlként titkosított RSA-kulcs. A fájl másolása ugyanabban a mappában, mivel eredetileg futtatta a AadrmTpd eszköz, és futtassa ismét az eszközt, a fájl, amely kezdete használatával **PrivateKey** és az CSS-fájl. Példa:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    Ez a parancs kimenetét kell két fájlt: Az egyszerű szöveges jelszavát egy tartalmazza a jelszóval védett TPD, és az egyéb a jelszóval védett TPD saját magát. A kereszthivatkozást célokra, mindkét ugyanaz a GUID a nyilvános és titkos kulcs fájlokat, ha futtatta a AadrmTpd.exe - createkey parancs kell lennie:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Biztonsági mentés ezeket a fájlokat, és tárolják azokat biztonságosan, győződjön meg arról, hogy továbbra is visszafejteni a bérlői kulccsal védett tartalom. Továbbá, ha az Active Directory tartalomvédelmi szolgáltatások, importálhatja a TPD fájl (kezdődő fájl **ExportedTDP**) az Active Directory tartalomvédelmi szolgáltatások kiszolgálóhoz.

##### 4. lépés: Folyamatban lévő: A bérlő kulcs védelme

-   A bérlői kulcs megérkezése után jutottak jól védett, mert valaki kap hozzáférést, ha azok is visszafejteni az összes kulcs használatával védett dokumentumok.

    A bérlő kulcs exportálása azért, mert már nem szeretné használni az Azure RMS, a legjobb, ha most kapcsolja ki az RMS-bérlőben. Nem késleltetés ezzel után a bérlői kulcs, mert ez okokból segít csökkentheti minimálisra a következmények, ha a bérlői kulcs által valaki, akik nem kell azt. További tudnivalókért tekintse meg a [Leállítására, és az Azure Rights Management inaktiválásáról](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

### <a name="BKMK_MSBreach"></a>Megsértése válaszolni.
Nincs biztonsági, függetlenül attól, hogy hogyan erős, a rendszer teljes válasz folyamat megsértése nélkül. A bérlő kulcs előfordulhat, hogy módon sérült, vagy ellopásakor. Akkor is, ha az jól védett jól, biztonsági rések előfordulhat, hogy található aktuális generációs HSM technológia vagy aktuális kulcshossza és algoritmust.

A Microsoft termékei és szolgáltatásai a biztonsági események válaszolni dedikált csoport rendelkezik. Nincs incidens hiteles jelentést, amint ez a csoport végez, a vizsgálja meg a hatókör, a kiváltó ok és a megoldásokkal kapcsolatban. Incidens érint, az eszközök, majd a Microsoft értesíti az Azure RMS bérlői rendszergazdák e-mail címmel, amely az Ön által megadott, amikor Ön feliratkozott.

Ha megsértése, a legjobb elvégezhető művelet, amelyek átvehetik vagy a Microsoft függ-e a hatókör jogsértés; Ez a folyamat a Microsoft az Ön fog működni. A következő táblázat néhány tipikus helyzetekben és a legvalószínűbb válasz Bár a pontos válasz minden olyan információt, amely a vizsgálat során látszik függ.

|Esemény leírása|Legvalószínűbb válasz|
|-------------------|-------------------------|
|A bérlő kulcs kiszivárogtatott van.|Újból a kulcsot a bérlői kulcs. Tekintse meg a [Ismételt kulcs a bérlői kulcs](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey) szakaszban, a jelen témakörben található.|
|A illetéktelen személy vagy a kártevő szoftverek kapta meg a bérlői kulcs használati jogát, de a saját magát kulcs nem adta-e előfordulhat.|Ismételt kulcskezelő a bérlői kulcs nem ide súgó, és kiváltó okának elemzése szükséges. Ha egy folyamatot, vagy a szoftver hiba volt a jogosulatlan személy hozzáférjen a felelős, ez a helyzet kell oldható fel.|
|A RSA algoritmus, vagy a kulcs hossza vagy a próbálkozásos támadások felderített Vulnerability válik számítástechnikai megvalósítható.|Microsoft kell frissíteni az Azure RMS új algoritmusokat és hosszabb kulcshossza, amelyek rugalmas támogatásához, és kérje az ügyfeleknek, hogy azok a bérlő kulcsok megújítása.|

## <a name="BKMK_BYOKManagedOperations"></a>Az ügyfél által felügyelt: A bérlő kulcs életciklusra vonatkozó műveletek
Ha a bérlői kulcsot az Azure Rights Management kezelése (a hozás saját kulcs, vagy a BYOK, a helyzetet), a következő szakaszok használja a életciklusra vonatkozó műveleteket, amelyek a topológia vonatkozó további információ:

-   [A bérlő kulcs visszavonása](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [Ismételt kulcs a bérlői kulcs](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [Készítsen biztonsági másolatot, és a bérlői kulcs helyreállítása](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [A bérlő kulcs exportálása](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [Megsértése válaszolni.](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>A bérlő kulcs visszavonása
Lemondani az Azure RMS, amikor Azure RMS leállítja a bérlői kulccsal, és nincs szükség műveletre Öntől.

### <a name="BKMK_BYOKRekey"></a>Ismételt kulcs a bérlői kulcs
Ismételt kulcskezelő is nevezik működés közbeni a kulcsot. Nem újra kulcs a bérlői kulcs nem valóban szükséges. Régebbi ügyfelek, például az Office 2010, nem tervezték, hogy a kulcs módosítások biztonságosan kezelni. Ebben az esetben törölnie kell az azokon a számítógépeken az RMS-állapot csoportházirend vagy egy egyenértékű mechanizmus használatával. Vannak azonban néhány törvényes az eseményeket, amelyek újra kulcs a bérlői kulcs lehet kényszeríteni. Példa:

-   A vállalati meg van felosztása két vagy több vállalat. Újra a a bérlői key kulcs, ha a az új vállalat nem rendelkezik, amely az alkalmazottak közzététele új tartalom elérése. A régi tartalom hozzáféréssel rendelkeznek a régi bérlői kulcs egy példányát.

-   Úgy véli, hogy a bérlői kulcsot (az Ön birtokában példány) fő példányát jutott.

Ha újra a a bérlői key kulcs – új által védett az új bérlői kulccsal. Ez a szakaszolt módon történik, egy adott időn belül az egyes új tartalom továbbra is lehet védetté tenni, a régi bérlői kulccsal. Korábban a védett tartalom marad a régi bérlői kulcs védett. Támogatja ezt a helyzetet, hogy Azure RMS, hogy azt a régi tartalom licenceinek adhat megtartja a korábbi bérlői kulcsot.

Újra kulcs a bérlői kulcs, létrehozni, és az interneten keresztül, vagy az személy, hozzon létre egy új kulcsot bemutatott eljárások használatával a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) a szakasz az [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) című témakört.

### <a name="BKMK_BYOKBackup"></a>Készítsen biztonsági másolatot, és a bérlői kulcs helyreállítása
A bérlő kulcs biztonsági másolatának Ön felelősséggel. A bérlő kulcsot a az egy Thales HSM jönnek létre, ha biztonsági másolatot a kulcsot, egyszerűen csak készítsen biztonsági másolatot a lexikális elemekké alakítva kulcs fájl, a globális fájl és a rendszergazda kártyák.

Ha a kulcs kerüljenek-e a eljárásokat követve a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) a szakasz a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) témakör, az Azure RMS lexikális elemekké alakítva kulcsfájl elleni bármely Azure RMS csomópontok hiba áll fenn. Azonban nem javasoljuk, hogy ez egy teljes biztonsági mentés legyen. Például ha a kulcsot egy Thales HSM kívül egyszerű szöveges másolatát, Azure RMS nem lesz tudja beolvasni meg, mert csak egy nem lesznek helyreállíthatók másolatot.

### <a name="BKMK_BYOKExport"></a>A bérlő kulcs exportálása
BYOK használata esetén a bérlői kulcsot az Azure RMS nem lehet exportálni. A az Azure RMS-példány nem állíthatók helyre. Ha azt szeretné, törölje ezt a kulcsot, így már nem használható, forduljon a Microsoft ügyfélszolgálathoz szolgáltatás (CSS).

### <a name="BKMK_BYOKBreach"></a>Megsértése válaszolni.
Nincs biztonsági, függetlenül attól, hogy hogyan erős, a rendszer teljes válasz folyamat megsértése nélkül. A bérlő kulcs előfordulhat, hogy módon sérült, vagy ellopásakor. Akkor is, ha az jól védett jól, biztonsági rések előfordulhat, hogy található aktuális generációs HSM technológia vagy aktuális kulcshossza és algoritmust.

A Microsoft termékei és szolgáltatásai a biztonsági események válaszolni dedikált csoport rendelkezik. Nincs incidens hiteles jelentést, amint ez a csoport végez, a vizsgálja meg a hatókör, a kiváltó ok és a megoldásokkal kapcsolatban. Incidens érint, az eszközök, majd a Microsoft értesíti az Azure RMS bérlői rendszergazdák e-mail címmel, amely az Ön által megadott, amikor Ön feliratkozott.

Ha megsértése, a legjobb elvégezhető művelet, amelyek átvehetik vagy a Microsoft függ-e a hatókör jogsértés; Ez a folyamat a Microsoft az Ön fog működni. A következő táblázat néhány tipikus helyzetekben és a legvalószínűbb válasz Bár a pontos válasz minden olyan információt, amely a vizsgálat során látszik függ.

|Esemény leírása|Legvalószínűbb válasz|
|-------------------|-------------------------|
|A bérlő kulcs kiszivárogtatott van.|Újból a kulcsot a bérlői kulcs. Tekintse meg a [Ismételt kulcs a bérlői kulcs](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey) szakaszban, a jelen témakörben található.|
|A illetéktelen személy vagy a kártevő szoftverek kapta meg a bérlői kulcs használati jogát, de a saját magát kulcs nem adta-e előfordulhat.|Ismételt kulcskezelő a bérlői kulcs nem ide súgó, és kiváltó okának elemzése szükséges. Ha egy folyamatot, vagy a szoftver hiba volt a jogosulatlan személy hozzáférjen a felelős, ez a helyzet kell oldható fel.|
|A biztonsági az a jelenlegi generációs HSM technológia felderített.|A Microsoft frissítenie kell a HSMs. Ha feltételezi, hogy a biztonsági elérhető-e a kulcsok OK, a Microsoft utasítsa ügyfeleknek, hogy azok a bérlő kulcsok megújítása.|
|A RSA algoritmus, vagy a kulcs hossza vagy a próbálkozásos támadások felderített Vulnerability válik számítástechnikai megvalósítható.|Microsoft kell frissíteni az Azure RMS új algoritmusokat és hosszabb kulcshossza, amelyek rugalmas támogatásához, és kérje az ügyfeleknek, hogy azok a bérlő kulcsok megújítása.|

## Lásd még
[Azure Rights Management használata](../Topic/Using_Azure_Rights_Management.md)

