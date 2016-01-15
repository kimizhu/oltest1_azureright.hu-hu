---
description: na
keywords: na
title: RMS Protection with Windows Server File Classification Infrastructure (FCI)
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
---
# RMS-v&#233;delmi Windows Server f&#225;jl besorol&#225;s infrastrukt&#250;r&#225;val (FCI)
Ez a cikk útmutatásért és a parancsfájl segítségével a Rights Management (RMS) ügyfél konfigurálása a Fájlkiszolgálói erőforrás-kezelő és a fájl besorolás infrastruktúra (FCI) használata az RMS-védelmi eszköz.

Ez a megoldások lehetővé teszi automatikusan védelme az összes Windows Server operációs rendszert futtató kiszolgálón fájl mappában lévő fájlok, vagy automatikusan a fájlok, amelyek megfelelnek egy adott feltételeknek védelme. Például fájlok, amelyek a bizalmas adatokat tartalmazó rendelkezik lett osztályozott. Ez a megoldás használja [Azure Rights Management](../Topic/Azure_Rights_Management.md) (Azure RMS) lehet védetté tenni a fájlokat, így ez a technológia a szervezetben telepített kell rendelkeznie.

> [!NOTE]
> Bár az Azure RMS tartalmaz egy [összekötő](https://technet.microsoft.com/library/dn375964.aspx) hogy támogatja a besorolás infrastruktúra fájl, az, hogy támogatja-e a megoldás csak a natív védelmi – például az Office-fájlok.
> 
> Támogatja a fájl besorolás infrastruktúra-összes fájltípusok, használnia kell a Windows PowerShell **RMS védelmi** modul, a cikkben leírtak szerint. Az RMS-védelmi parancsmagok az RMS-megosztó alkalmazás, például támogatja az általános védelmi, valamint a natív protection, ami azt jelenti, hogy minden fájl lehet védetté tenni. A különböző védelmi szintek kapcsolatos további információkért tekintse meg a [Védelmi – natív és általános szintek](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) szakasz a [A Rights Management megosztási alkalmazás rendszergazda guide](../Topic/Rights_Management_sharing_application_administrator_guide.md).

Az alábbi utasításokat a Windows Server 2012 R2 vagy a Windows Server 2012 vannak. Ha futtatja a Windows más támogatott verziója, szükség lehet néhány, az operációs rendszer verziója, és a cikkben szereplő közötti eltérések vonatkozó lépéseket igazítani.

## A Windows Server FCI az Azure RMS védelemre Előfeltételek
Az alábbi utasításokat Előfeltételek:

-   Minden fájl a kiszolgálón, ahol működik az erőforrás-kezelő fájl az fájl besorolás infrastruktúra:

    -   Fájlkiszolgálói erőforrás-kezelő egyik a Fájlszolgáltatások szerepkör szerepkör-szolgáltatások telepítése.

    -   Helyi mappa, amely tartalmazza a Rights Management szolgáltatással fájl jelölte meg. Ha például C:\FileShare.

    -   Az RMS-védelmi eszköz, beleértve az előfeltételeket, az eszköz (például az RMS-ügyfél) és az Azure RMS (például a fő szolgáltatásfiók) telepítését. További tudnivalókért tekintse meg a [RMS Protection parancsmagok](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Ha módosítani szeretné az alapértelmezett RMS adatvédelmi szintet (natív vagy általános) adott kiterjesztések, a beállításjegyzék módosította, leírtak szerint a [fájl API-konfigurációs](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx) oldalon.

    -   Ha egy proxykiszolgáló szükséges van aktív internetkapcsolat, a konfigurált számítógép beállításait. Példa: `netsh winhttp import proxy source=ie`

-   A konfigurált Azure Rights Management telepítéssel további előfeltételei leírtak szerint [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx). Pontosabban van az Azure RMS használatával egy egyszerű kapcsolódni a következő értékek:

    -   BposTenantId

    -   AppPrincipalId

    -   Szimmetrikus kulcs

-   A helyszíni Active Directory felhasználói fiókok szinkronizálta Azure Active Directoryban, vagy az Office 365, beleértve az e-mail címüket. Ez azért szükséges, elérni a fájlokat, miután azok FCI és az Azure RMS által védett igénylő előfordulhat, hogy minden felhasználó számára. Ha nem ez a lépés (például tesztkörnyezetben), a felhasználók hozzáférjenek, hogy ezek a fájlok blokkolhatja. Ha további információt a fiók konfigurálásának van szüksége, tekintse meg a [Azure Rights Management előkészítése](../Topic/Preparing_for_Azure_Rights_Management.md).

-   A Rights Management használt sablon, amelyet a fájlok jelölte meg. Győződjön meg arról, hogy tudja-e az ID ez a sablon segítségével a [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx) parancsmagot.

## Fájlkiszolgálói erőforrás-kezelő FCI konfigurálása az Azure RMS protection utasításokat
Kövesse az alábbi utasításokat automatikusan védelme érdekében a Windows PowerShell-parancsfájl segítségével egyéni feladat egy a mappában lévő összes fájlt. Hajtsa végre ezeket a lépéseket itt megadott sorrendben:

1.  A Windows PowerShell-parancsfájl mentése

2.  A Rights Management (RMS) besorolási tulajdonság létrehozása

3.  (Az RMS szolgáltatást besorolás) besorolás szabály létrehozása

4.  A besorolás ütemezésének megadása

5.  Egyéni felügyeleti feladat létrehozása (védelme fájlok, amelyek az RMS)

6.  A beállítások tesztelése manuálisan futtatja, a szabály, és a feladat

Az alábbi utasításokat végén a kijelölt mappában lévő összes fájlt, ha az egyéni tulajdonság RMS kerülnek osztályozásra, és ezeket a fájlokat majd kell Rights Management által védett. Az összetettebb konfigurációjának külön-külön védő bizonyos fájlokat, és nem mások majd létrehozhat vagy egy másik besorolást tulajdonság, és a szabály, egy fájl felügyeleti feladatot, amely csak azokat a fájlokat védő használni.

#### A Windows PowerShell-parancsfájl mentése

1.  Bontsa ki a [Fájlkiszolgálói erőforrás-kezelő FCI használatával az Azure RMS védelemre Windows PowerShell-parancsfájl](#BKMK_RMSProtection_Script) cikkben részében, és másolja a tartalmát. A parancsfájl tartalmának beillesztése, és a fájl neve **RMS-Protect-FCI.ps1** a saját számítógépen.

2.  Tekintse át a parancsfájlt, és a következő módosításokat:

    -   A következő karakterlánc, és lecseréli a saját AppPrincipalId használt keresése a [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) parancsmag kapcsolódni az Azure RMS:

        ```
        <enter your AppPrincipalId here>
        ```
        Például a parancsfájl utasítás ez:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)] [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Keresés a következő karakterlánc, és lecseréli a saját szimmetrikus kulcsot használata a [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) parancsmag kapcsolódni az Azure RMS:

        ```
        <enter your key here>
        ```
        Például a parancsfájl utasítás ez:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Keresés a következő karakterlánc, és lecseréli a saját BposTenantId (bérlői ID) használata a [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) parancsmag kapcsolódni az Azure RMS:

        ```
        <enter your BposTenantId here>
        ```
        Például a parancsfájl utasítás ez:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Ha a kiszolgáló fut a Windows Server 2012, előfordulhat, a RMSProtection modul a parancsfájl elején manuálisan betöltéséhez. Adja hozzá a következő parancsot (vagy ezzel egyenértékű, ha a "Program Files" mappa egy másik a C: meghajtón meghajtóra:

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  A parancsfájl alá. Ha nem írja alá a parancsfájl (biztonságosabb), konfigurálnia kell a Windows PowerShell a kiszolgálókat, futtassa a. Például a Windows PowerShell munkamenetet futtassa a **Futtatás rendszergazdaként** lehetőséget, és írja be: **Set-ExecutionPolicy Unrestricted**. Azonban a konfiguráció lehetővé teszi, hogy az összes aláíratlan parancsfájlok (kevésbé biztonságos).

    Bejelentkezés a Windows PowerShell-parancsfájlok kapcsolatos további információkért tekintse meg a [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) a PowerShell dokumentációs könyvtárában.

4.  Mentse a fájlt a helyi minden kiszolgálón fájl, amely az fájl besorolás infrastruktúra fájl rendszererőforrás-kezelő fog futni. Például, mentse a fájlt a **C:\RMS-Protection**. Ezt a fájlt biztonságos az NTFS-engedélyek használatával, így nem engedélyezett felhasználók nem módosítható.

Most készen áll elindítani a Fájlkiszolgálói erőforrás-kezelő konfigurálása.

#### A Rights Management (RMS) besorolási tulajdonság létrehozása

-   A Fájlkiszolgálói erőforrás-kezelő, besorolás felügyeleti, hozzon létre egy új helyi tulajdonság:

    -   **Name**: Típusa **RMS**

    -   **Leírás**:   Típusa **Rights Management protection**

    -   **Tulajdonságtípus**: Válasszon **Igen/nem**

    -   **Value**: Válasszon **Igen**

Most mi hozhat létre egy besorolás szabály, amely használja ezt a tulajdonságot.

#### (Az RMS szolgáltatást besorolás) besorolás szabály létrehozása

-   Hozzon létre egy új besorolás szabály:

    -   Az a **Általános** lap:

        -   **Name**: Típusa **Classify for RMS**

        -   **Engedélyezve**: Őrizze meg az alapértelmezett, amely, hogy ez a jelölőnégyzet be van jelölve.

        -   **Leírás**: Típus **Classify all files in the &lt;folder name&gt; folder for Rights Management**.

            Cserélje ki *&lt; Mappanév &gt;* a választott mappa nevét. Például **a C:\FileShare mappában lévő összes fájlt osztályozására a Rights Management**

        -   **Scope**: Adja meg a kiválasztott mappát. Például **C:\FileShare**.

            Jelölje be a jelölőnégyzeteket.

    -   Az a **besorolás** lap:

    -   **Besorolás metódus**: Válasszon **mappa osztályozó**

    -   **Tulajdonság** neve: Válasszon **RMS**

    -   Tulajdonság **érték**: Válasszon **Igen**

Bár is futtathatja a besorolási szabályok manuálisan, folyamatban lévő műveletek esetén érdemes Ez a szabály futtatásához ütemezés szerint, úgy, hogy az új fájlok kerülnek osztályozásra, ha az RMS-tulajdonság.

#### A besorolás ütemezésének megadása

-   Az a **automatikus osztályozás** lap:

    -   **Rögzített ütemezésének engedélyezése**: Jelölje be ezt a jelölőnégyzetet.

    -   Minden besorolás szabály futtatásához, ez kiterjed az új szabály-fájlok, amelyek az RMS-tulajdonság osztályozására ütemezésének konfigurálása.

    -   **Engedélyezése az új fájlok folyamatos besorolás**: Jelölje be ezt a jelölőnégyzetet, úgy, hogy az új fájlok kerülnek osztályozásra.

    -   Nem kötelező: Más módosítást kívánt, például a jelentések és értesítések beállítások konfigurálása.

A besorolás konfigurálása befejeződött, most készen áll konfigurálása az RMS-védelmi alkalmazandó fájlokat egy felügyeleti feladatot.

#### Egyéni felügyeleti feladat létrehozása (védelme fájlok, amelyek az RMS)

-   A **Fájlkezelési feladatok**, hozzon létre egy új fájlt felügyeleti feladatot:

    -   Az a **Általános** lap:

        -   **Tevékenység neve**: Típusa **Protect files with RMS**

        -   Megtartja a **engedélyezése** kiválasztott jelölőnégyzetet.

        -   **Leírás**: Típusa **Protect files in &lt;folder name&gt; with Rights Management and a template by using a Windows PowerShell script.**

            Cserélje ki *&lt; Mappanév &gt;* a választott mappa nevét. Például **C:\FileShare a Rights Management és a sablon fájljainak védelme a Windows PowerShell-parancsfájl segítségével**

        -   **Scope**: Válassza ki a kiválasztott mappát. Például **C:\FileShare**.

            Jelölje be a jelölőnégyzeteket.

    -   Az a **művelet** lap:

        -   **Type**: Válasszon **egyéni**

        -   **Végrehajtható fájl**: Adja meg a következőket:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Ha a Windows nem a C: meghajtón, módosítsa az elérési út, vagy a tallózással keresse meg ezt a fájlt.

        -   **Argumentum**: Adja meg a következőket, a saját &lt; elérési út &gt; értékeit és &lt; Sablonazonosító &gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Például ha a parancsfájl C:\RMS-Protection másolt, és a sablon azonosítója, akkor az Előfeltételek azonosított e6ee2481-26b9-45e5-b34a-f744eacd53b0, adja meg a következőket:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            Ez a parancs a **[forrásfájl elérési útvonalát]** és **[adatforrás fájl tulajdonos E-mail]** mindkét FCI-specifikus változók úgy írja be ezeket a fenti parancsban jelenjenek meg. A legelső FCI által automatikusan megadására szolgál az azonosított fájl a mappában, és a második pedig automatikusan beolvasni az e-mail cím, az azonosított fájl elnevezett tulajdonosának FCI. Ez a parancs ismétlődik minden fájl a mappában, amely ebben a példában, minden fájl emellett rendelkezik az RMS fájl besorolás tulajdonságként C:\FileShare mappában.

            > [!NOTE]
            > A **-OwnerMail [Source File Owner Email]** paraméter és érték gondoskodik arról, hogy a fájl eredeti tulajdonosa megkapta a fájlt a Rights Management tulajdonosának után a védett. Ez biztosítja, hogy az eredeti fájl tulajdonosa a saját fájlok összes Rights Management jogosultsággal rendelkezik-e. A tartományi felhasználók fájlt hoz létre, ha az e-mail cím van automatikusan lekéri a Active Directory segítségével a felhasználói fiók nevét a fájl tulajdonosa tulajdonság. Ehhez a fájlkiszolgálóhoz kell lennie a ugyanabban a tartományban, vagy a megbízható tartomány, a felhasználó.
            > 
            > Ha lehetséges, rendelje hozzá az eredeti tulajdonosok védett dokumentumok, győződjön meg arról, hogy ezek a felhasználók továbbra is, hogy azok a létrehozott fájlok teljes hozzáféréssel rendelkeznek. Azonban, ha a fenti [adatforrás fájl tulajdonos E-mail] változó és egy fájlt a nem rendelkezik definiált tulajdonosaként tartományi felhasználó (például egy helyi fiók létrehozásához használt a fájlt, így a tulajdonos jeleníti meg a rendszer), a parancsfájl sikertelen lesz.
            > 
            > Nem rendelkezik a tartományi felhasználók tulajdonosaként-fájlok esetén lehetősége van másolása, majd mentse ezeket a fájlokat magát a tartományi felhasználót, hogy a tulajdonos csak ezeket a fájlokat a válik. Vagy, akkor jogosult, ha a tulajdonos manuálisan módosíthatja.  Másik lehetőségként, megadhat egy adott e-mail címet, vagy (például a saját vagy egy csoport címe az IT-részleg) helyett a [adatforrás fájl tulajdonos E-mail] változó, ami azt jelenti, hogy minden fájl védetté tenni, ha ez a parancsfájl segítségével használandó Ez az e-mail cím határozza meg az új tulajdonos.

    -   **a parancsot, mint**: Válasszon **helyi rendszer**

    -   Az a **feltétel** lap:

        -   **Tulajdonság**: Válasszon **RMS**

        -   **Operátor**: Válasszon **egyenlő**

        -   **Value**: Válasszon **Igen**

    -   Az a **ütemezés** lap:

        -   **Run at**: Az előnyben részesített ütemezésének megadása.

            Bőségesen idő a parancsfájl végrehajtására. Bár ez a megoldás védi a mappában lévő összes fájlt, a parancsfájl futtatása egyszer, így minden alkalommal. Bár ez több időt vesz igénybe minden fájl védelme egyszerre, amely támogatja az RMS-védelmi eszköz, mint nagyobb teljesítményű esetén ez a fájl-fájl beállítás FCI. Például, hogy a védett fájlt is különböző tulajdonosok (megőrzi az eredeti tulajdonos) Ha az [adatforrás fájl tulajdonos E-mail] változó használjuk, és ez a fájl által művelet szükségessé válik, ha később módosítja a konfigurációt, külön-külön a mappában lévő összes fájlok helyett a fájlok védelme érdekében.

        -   **Folyamatosan fusson az új fájlok**: Jelölje be ezt a jelölőnégyzetet.

#### A beállítások tesztelése manuálisan futtatja, a szabály, és a feladat

1.  Futtassa a besorolási szabály:

    1.  Kattintson a **besorolási szabályok** &gt; **besorolás az összes futtatása**

    2.  Kattintson a **Várjon, amíg a besorolás befejezéséhez**, és kattintson a **OK**.

2.  Várjon, amíg a a **futó besorolás** a párbeszédpanel bezárásához és a automatikusan megjelenített jelentésben tekintse meg az eredményeket. Végrehajtásakor **1** számára a **Tulajdonságok** mező és a mappában lévő fájlok száma. Ellenőrizze a fájl Intéző használatával, és a kiválasztott mappában lévő fájlok tulajdonságainak ellenőrzése. A a **besorolás** lapjának végrehajtásakor **RMS** tulajdonság nevét és **Igen** a saját **érték**.

3.  A fájl felügyeleti feladat futtatása:

    1.  Kattintson a **Fájlkezelési feladatok** &gt; **-fájlok, amelyek az RMS védelme** &gt; **fájl felügyeleti feladat futtatása**

    2.  Kattintson a **várja meg a feladat végrehajtásához**, és kattintson a **OK**.

4.  Várjon, amíg a a **Fájlkezelési feladat futtatása** a párbeszédpanel bezárásához és a automatikusan megjelenített jelentésben tekintse meg az eredményeket. Megjelenik a kiválasztott mappájában lévő fájlok száma a **fájlok** mező. Győződjön meg arról, hogy a kiválasztott mappában lévő fájlok most RMS által védett. Például, ha a kiválasztott mappa C:\FileShare, írja be a következő egy Windows PowerShell munkamenetet, és győződjön meg arról, hogy fájlokat állapotú **UnProtected**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Hibaelhárítási tippek:
    > 
    > -   Ha azt látja, hogy **0** a jelentésben a mappában lévő fájlok száma helyett Ez azt jelzi, hogy a parancsfájl nem futott. Először ellenőrizze a parancsfájl magát a parancsfájl tartalmának ellenőrzése, és próbálja meg futtatni, tekintse meg, ha a hibák jelennek-e a Windows PowerShell ISE betöltésével. A parancsfájl a megadott argumentum nélkül megpróbálja csatlakozáshoz, és az Azure RMS hitelesítést.
    > 
    >     -   Ha a parancsfájl azt jelenti, hogy nem tudott-e kapcsolódni a Azure RMS, ellenőrizze az értékeket, az egyszerű szolgáltatásfiókjának, amely a parancsfájl megadott jeleníti meg.  Ez egyszerű szolgáltatásfiók létrehozásával kapcsolatban további tudnivalókért tekintse meg a második előfeltételként szükséges a [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)
    >     -   Ha a parancsfájl azt jelenti, hogy nem az Azure RMS csatlakozni, és az Azure régióra kívül Észak-Amerika, ellenőrizze a szerkesztett megfelelően a beállításjegyzéket ebben a konfigurációban. Ez egy hasznos teszt számára futtassa a Get-RMSTemplate közvetlenül a Windows PowerShell a kiszolgálón. A beállításjegyzék módosításának kapcsolatos további információkért tekintse meg a harmadik előfeltételként szükséges a [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx).
    > -   Ha saját maga a parancsfájl hiba nélkül fut a Windows PowerShell ISE, próbálja meg futtatni a következő PowerShell munkamenetből megadása egy fájl neve lehet védetté tenni, és a - OwnerEmail paraméter nélkül:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File <full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Ha a parancsfájl a Windows PowerShell-munkamenet sikeresen fut, győződjön meg a **végrehajtó** és **argumentum** a fájl felügyeleti feladat művelet.  Ha a megadott **- OwnerEmail [adatforrás fájl tulajdonos E-mail]**, távolítsa el ezt a paramétert.
    > 
    >         Ha a fájl-felügyeleti feladat sikeresen nélkül működik  **- OwnerEmail [adatforrás fájl tulajdonos E-mail]**, ellenőrizze, hogy a nem védett fájlokat rendelkezik-e a tulajdonosként fájl, tartományi felhasználó helyett **rendszer**.  Ehhez használja a **biztonsági** a fájl tulajdonságok fülre, és kattintson a **Speciális**. A **tulajdonos** értéke megjelenik a fájl után azonnal **neve**. Is győződjön meg arról, hogy a fájlkiszolgáló ugyanabban a tartományban, vagy a felhasználó e-mail címe az Active Directory tartományi szolgáltatásokból megtalálni megbízható tartományban van-e.
    > -   Ha azt látja, hogy a megfelelő számú fájlokat a jelentésben szereplő, de a fájlok nem védettek, próbálja meg a fájlok manuálisan védelme a használatával a [védelme-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) parancsmag, tekintse meg a jelennek-e ki a hibákat.

Ha meggyőződött, ezek a feladatok végrehajtása sikeresen befejeződött, bezárhatja fájl rendszererőforrás-kezelő. Új fájlok automatikusan védett, és minden fájl védi újra az ütemezések futtatásakor. Újra a fájl védett gondoskodik arról, hogy a módosításokat a sablon a fájlok érvényesek-e.

### <a name="BKMK_RMSProtection_Script"></a>Fájlkiszolgálói erőforrás-kezelő FCI használatával az Azure RMS védelemre Windows PowerShell-parancsfájl
Ez a szakasz tartalmaz a minta parancsprogram másolása és szerkesztéséhez, az előző részben leírtak szerint.

*&#42;&#42;A Jótállás kizárása&#42;&#42;: A minta parancsprogram alatt bármely Microsoft standard támogatás program vagy a szolgáltatás nem támogatott. A minta parancsprogram formájában kerül, mindenféle garancia nélkül.*

```
<# .SYNOPSIS Helper script to protect all file types with Azure RMS and FCI. .DESCRIPTION Protect files with Azure RMS and Windows Server FCI, using an RMS template ID. #> param( [Parameter(Mandatory = $false)] [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })] [string]$File, [Parameter(Mandatory = $false)] [string]$TemplateID, [Parameter(Mandatory = $false)] [string]$OwnerMail, [Parameter(Mandatory = $false)] [string]$AppPrincipalId = "<enter your AppPrincipalId here>", [Parameter(Mandatory = $false)] [string]$SymmetricKey = "<enter your key here>", [Parameter(Mandatory = $false)] [string]$BposTenantId = "<enter your BposTenantId here>" ) # script information [String] $Script:Version = 'version 1.0' [String] $Script:Name = "RMS-Protect-FCI.ps1" #global working variables [switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running. #**Functions (general helper)*************************************** function Get-ScriptName(){ return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1) } #**Functions (script specific)************************************** function Check-Module{ param ([String]$Module = $(Throw "Module name not specified")) [bool]$isResult = $False #try to load the module if (get-module -list -name $Module) { import-module $Module if (get-module -name $Module ) { $isResult = $True } else { $isResult = $False } } else { $isResult = $False } return $isResult } function Protect-File ($ffile, $ftemplateId, $fownermail) { [bool] $returnValue = $false try { If ($OwnerMail -eq $null -or $OwnerMail -eq "") { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId") } else { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId -OwnerEmail $fownermail $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail") } } catch { Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId") } return $returnValue } function Set-RMSConnection ($fappId, $fkey, $fbposId) { [bool] $returnValue = $false try { Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") $returnValue = $true } catch { Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") } return $returnValue } #**Main Script (Script)********************************************* Write-Host ("-== " + $Script:Name + " " + $Version + " ==-") $Script:isScriptProcess = $True # Validate Azure RMS connection by checking the module and then connection if ($Script:isScriptProcess) { if (Check-Module -Module RMSProtection){ $Script:isScriptProcess = $True } else { Write-Host ("The RMSProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } if ($Script:isScriptProcess) { #Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" ) if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) { Write-Host ("Connected to Azure RMS") } else { Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } #  Start working loop if ($Script:isScriptProcess) { if ( !(($File -eq $null) -or ($File -eq "")) ) { if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) { $Script:isScriptProcess = $False } } } # Closing if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"} write-host ("-== " + $Script:Name + " " + $Version + "  ==-") if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}
```

## A varázsló utasításait külön-külön védelme a fájlok módosítása
Ha a fenti útmutatás működik, akkor is majd nagyon könnyen bonyolultabb konfiguráció módosítására. Például a fájlok védelme a azonos parancsfájl használatával, de csak olyan személyes azonosításra alkalmas adatainak tartalmazó fájlokat, és talán válasszon ki egy sablont, amely jobban korlátozó jogokkal rendelkezik.

Ehhez tegye a beépített besorolási tulajdonságok (például **személyi azonosító adatok**), vagy hozzon létre a saját új tulajdonságot. Majd hozzon létre egy új szabály, amely használja ezt a tulajdonságot. Például előfordulhat, hogy válassza a **tartalom osztályozó**, válassza a **személyi azonosító adatok** tulajdonság értéke **magas**, és konfigurálja a karakterlánc- vagy kifejezés mintát, amely azonosítja a fájlt, konfigurálni kell a ehhez a tulajdonsághoz (például a karakterlánc "**születési idő dátum**").

Most kell tennie csak az új felügyeleti feladat létrehozása használó azonos parancsfájl de talán egy másik sablont, és konfigurálja az éppen konfigurált besorolási tulajdonság feltételét. Például a feltétellel, hogy mi a korábban beállított helyett (**RMS** tulajdonság, **egyenlő**, **Igen**), jelölje be a **személyi azonosító adatok** tulajdonság a a **operátor** értéke **egyenlő** és a **érték** a **magas**.

