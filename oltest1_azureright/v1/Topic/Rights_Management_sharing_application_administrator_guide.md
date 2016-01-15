---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# A Rights Management megoszt&#225;si alkalmaz&#225;s rendszergazda guide
Használja a következő információkat, ha Ön felelős a Microsoft Rights Management megosztóalkalmazás a vállalati hálózatra, vagy ha azt szeretné, hogy további technikai információk szerepel, mint a [A Rights Management megosztási alkalmazás felhasználói útmutató](../Topic/Rights_Management_sharing_application_user_guide.md) vagy [gyakran ismételt kérdések a Microsoft Rights Management megosztó alkalmazás for Windows](http://go.microsoft.com/fwlink/?LinkId=303971):

-   [A Microsoft Rights Management megosztóalkalmazás az automatikus telepítés](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [A telepítés sikeres ellenőrzése](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [Távolítsa el a parancsok](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [Automatikus frissítések megjelenítése](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [Csak Azure RMS: Dokumentum-követés konfigurálása](#BKMK_DocumentTracking)

    -   [Active Directory tartalomvédelmi szolgáltatások csak: Több e-mail tartomány a szervezeten belüli támogatása](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [A Microsoft Rights Management megosztóalkalmazás technikai áttekintése](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [Védelmi – natív és általános szintek](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [Támogatott fájltípusok és kiterjesztések](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [Az alapértelmezett védelmi szint fájlok módosítása](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> Ha új az RMS-megosztási alkalmazás, illetve további adatokat keres, tekintse meg a [az RMS-hogyan védi a fájltípusainak – az RMS-megosztó alkalmazás használatával](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app).

Az RMS-megosztó alkalmazás oka az Azure RMS, dolgozni a legmegfelelőbb a központi telepítési konfiguráció küldő védett mellékletek, a felhasználók egy másik a szervezet és a beállítások, például az e-mail értesítések és a dokumentum a visszavont tanúsítványok követési támogatja.  Azonban néhány korlátozásokkal, is működik a verziójával helyszíni AD RMS. Az Azure RMS és az Active Directory tartalomvédelmi szolgáltatások által támogatott szolgáltatások átfogó összehasonlítása, tekintse meg a [Azure Rights Management összevetésével történik, és az Active Directory tartalomvédelmi szolgáltatások](https://technet.microsoft.com/library/jj739831.aspx). Ha az Active Directory tartalomvédelmi szolgáltatások, és szeretné az Azure RMS áttelepíteni, tekintse meg a [áttelepítése az Active Directory tartalomvédelmi szolgáltatások Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx).

## <a name="BKMK_ScriptedInstall"></a>A Microsoft Rights Management megosztóalkalmazás az automatikus telepítés
Az RMS-megosztási alkalmazás Windows verzióval egy parancsfájlalapú telepítés, amely lehetővé teszi a vállalati telepítések alkalmas.

A csak Előfeltételek telepítések, hogy a számítógépek futtatásához a Windows 7 SP1 vagy újabb verzióját, és az, hogy a Microsoft Framework, minimális 4.0-s verziója telepítve van-e. Ha telepíteni a Microsoft .NET-keretrendszer 4.0-s verziója van szüksége, akkor [Töltse le a Microsoft Download Center a telepítéshez](http://www.microsoft.com/download/details.aspx?id=17718).

#### Az RMS-megosztó alkalmazás automatikus központi letöltése

1.  Nyissa meg a [Microsoft Rights Management megosztóalkalmazás Windows](http://www.microsoft.com/download/details.aspx?id=40857) a Microsoft Download Center lapra, majd kattintson az **letöltése**.

2.  Válassza ki, és a szükséges fájlok letöltése. Nincsenek a két ügyfél telepítési csomagok: egy a Windows 64 bites (Microsoft Rights Management megosztási alkalmazás x64.zip), és egy másik Windows 32 bites (Microsoft Rights Management megosztó alkalmazás x86.zip).

3.  Bontsa ki a fájlokat a tömörített telepítési csomagok, például dupla kattintással. Ezután másolja a kibontott fájlok ügyfélszámítógépek által elérhető hálózati hely.

A telepítő csomagok számára az RMS-megosztó alkalmazás támogatja a különböző központi telepítések esetében, és többek között a következők:

|Leírása|Központi telepítési forgatókönyv|
|-----------|------------------------------------|
|A Microsoft Online – bejelentkezési segéd|Szükséges a következők:<br /><br />-   Az Office 2010 és az Azure RMS<br />-   Office 2013 és az Azure RMS, ha nincs telepítve a [2015. június 9. frissítse az Office 2013](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Gyorsjavítás az Office (KB 2596501)|Szükséges a következők:<br /><br />-   Az Office 2010 és az Azure RMS<br />-   Az Office 2010 és az Active Directory Directory tartalomvédelmi szolgáltatások|
|Gyorsjavítás ahhoz, hogy az AD RMS-ügyfél 1.0 Azure RMS (KB 2843630) használata|Szükséges a következők:<br /><br />-   Az Office 2010 és az Azure RMS<br />-   Az Office 2010 és az Active Directory Directory tartalomvédelmi szolgáltatások|
|AD RMS-ügyfelet, és az RMS-megosztó alkalmazás|Szükséges a következők:<br /><br />-   Office 2016 vagy az Office 2013 és az Azure RMS vagy az Active Directory Directory tartalomvédelmi szolgáltatások<br />-   Az Office 2010 és az Azure RMS<br />-   Az Office 2010 és az Active Directory Directory tartalomvédelmi szolgáltatások<br />-   RMS-megosztó alkalmazás és az Office bővítmény csak|
|Office-bővítmény a menüszalag|Szükséges a következők:<br /><br />-   Office 2016 vagy az Office 2013 és az Azure RMS vagy az Active Directory Directory tartalomvédelmi szolgáltatások<br />-   Az Office 2010 és az Azure RMS<br />-   Az Office 2010 és az Active Directory Directory tartalomvédelmi szolgáltatások<br />-   RMS-megosztó alkalmazás és az Office bővítmény csak|
|Azure Active Directory tartalomvédelmi szolgáltatások előkészítő eszköz|Szükséges a következők:<br /><br />-   Az Office 2010 és az Azure RMS|
Az alábbi eljárásokkal azonosítja a parancsok, az RMS-megosztó alkalmazás a központi telepítési forgatókönyvekben telepítéséhez szükséges:

-   **Office 2016 vagy az Office 2013 és az Azure RMS vagy az Active Directory Directory tartalomvédelmi szolgáltatások**

    Futnak, hogy a felhasználók Office 2016 vagy az Office 2013, a szervezet Azure RMS vagy az Active Directory Tartalomvédelmi használ, és a felhasználók más szervezetek Azure RMS vagy az Active Directory Tartalomvédelmi használó együttműködhet.

-   **Az Office 2010 és az Azure RMS**

    A felhasználók az Office 2010 futnak, és a szervezet használ az Azure RMS felhasználók együttműködhet más szervezetek Azure RMS vagy az Active Directory Tartalomvédelmi használó.

-   **Az Office 2010 és az Active Directory Directory tartalomvédelmi szolgáltatások**

    A felhasználók az Office 2010 fut, a szervezet használja az Active Directory tartalomvédelmi szolgáltatások és a felhasználók együttműködhet más szervezetek, aki az Azure RMS használatához.

-   **RMS-megosztó alkalmazás és az Office bővítmény csak**

    Futnak, hogy a felhasználók Office 2016, az Office 2013 vagy az Office 2010, a szervezet használja az Active Directory tartalomvédelmi szolgáltatások, és a felhasználóknak nem kell együttműködhet más szervezetek, aki az Azure RMS használatához. Ez a telepítési lehetővé teszi, hogy csak a megosztás telepíthet alkalmazás és az Office bővítmény.

> [!NOTE]
> Forgatókönyvekben Ha a szervezet Active Directory tartalomvédelmi szolgáltatások fut, a felhasználók védett tartalom fogadni a más szervezetek Azure RMS használó, de a felhasználók nem küldhető védett tartalom, a felhasználók a szervezet használó Azure RMS. Azonban ha a szervezet Azure RMS fut, a felhasználók számára is küldeni és fogadni védett tartalom a más szervezetek.

Minden alkalommal a telepítés befejezéséhez újra kell indítania a számítógépet. A paranccsal például a leállítási elindíthatja az automatikus újraindítására /i.

#### Az RMS-megosztó alkalmazás Office 2016 vagy Office 2013, és az Azure RMS vagy az Active Directory Directory tartalomvédelmi szolgáltatások telepítése

-   Minden olyan számítógépen, amelyre telepíteni kívánja az RMS-megosztó alkalmazás és a kapcsolódó összetevők, megemelt jogosultsági futtassa a következő parancsot:

    ```
    setup.exe /s
    ```

Sikeres ellenőrzéséhez tekintse meg a [A telepítés sikeres ellenőrzése](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) szakaszban, a jelen témakörben található.

#### Az RMS-megosztó alkalmazás az Office 2010 és az Azure RMS telepítése

1.  A globális rendszergazdának kell lennie az Office 365 vagy az Azure Active Directory-bérlőben, így beszerezheti a szervezet hitelesítő szolgáltatás URL-címe az Azure Active Directory tartalomvédelmi szolgáltatások előkészítő eszköz futtatásával. Ez az eszköz csak egyszer kell futtatni egy számítógépen. Az RMS-megosztó alkalmazás minden olyan számítógépen telepíti fogja használni a hitelesítési szolgáltatás URL-címe:

    1.  Bejelentkezés a számítógépre helyi rendszergazdai fiók használatával.

    2.  Azokon a számítógépeken [Töltse le és telepítse a Microsoft Online bejelentkezési segédje](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  A következő parancsot tekintse meg a megjelenített a képernyőn megjelenő a hitelesítő szolgáltatás URL-címe, amely akkor másolhat, és mentse a következő lépés:

        -   A Windows 8.1 és a Windows 8, a 64 bites:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   A Windows 8.1 és a Windows 8 32 bites:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Windows 7, a 64 bites:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Ez a parancs kérhetik adja meg Azure hitelesítő adatait. Ha a számítógép nem tagja egy tartománynak, bekéri. Ha a számítógép egy tartomány tagja, az eszköz lehet gyorsítótárazott hitelesítő adatokat használjon.

2.  Minden olyan számítógépen, amelyre telepíti az RMS-megosztó alkalmazás a következő parancsot megemelt jogosultsági:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Minden olyan számítógépen, amelyre telepíti az RMS-megosztó alkalmazás, a felhasználók a következő parancsot kell futtatnia (nem szükséges megemelt jogosultsági). Többféleképpen ennek eléréséhez, beleértve a felhasználók számára, hogy a parancsot (például egy e-mailt a hivatkozás vagy egy hivatkozást a Súgó a segélyszolgálati portálon) kéri, vagy a bejelentkezési parancsfájl hozzáadása:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Sikeres ellenőrzéséhez tekintse meg a [A telepítés sikeres ellenőrzése](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) szakaszban, a jelen témakörben található.

#### Az RMS-megosztó alkalmazás az Office 2010 és az Active Directory Directory tartalomvédelmi szolgáltatások telepítése

1.  Minden olyan számítógépen, amelyre telepíti az RMS-megosztó alkalmazás a következő parancsot megemelt jogosultsági:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Minden olyan számítógépen, amelyre telepíti az RMS-megosztó alkalmazás, a felhasználók a következő parancsot kell futtatnia (nem szükséges megemelt jogosultsági). Többféleképpen ennek eléréséhez, beleértve a felhasználók számára, hogy a parancsot (például egy e-mailt a hivatkozás vagy egy hivatkozást a Súgó a segélyszolgálati portálon) kéri, vagy a bejelentkezési parancsfájl hozzáadása:

    -   Windows 10, a Windows 8.1 és a Windows 8, a 64 bites:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   A Windows 10, a Windows 8.1 és a Windows 8 32 bites:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Windows 7, a 64 bites:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Sikeres ellenőrzéséhez tekintse meg a [A telepítés sikeres ellenőrzése](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) szakaszban, a jelen témakörben található.

#### Az RMS-megosztó alkalmazás és az Office bővítmény csak telepítése

1.  A telepítés a AD RMS-ügyfelet, és az RMS-megosztó alkalmazás, a következő parancs használatával:

    -   A Windows 64 bites:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   32 bites Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Példa: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Telepítse az Office bővítmény a következő parancsok használatával:

    -   Az Office 64 bites verziója:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Az Office 32 bites verziója:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Példa: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Sikeres ellenőrzéséhez tekintse meg a [A telepítés sikeres ellenőrzése](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) szakaszban, a jelen témakörben található.

### <a name="BKMK_verifyscripted"></a>A telepítés sikeres ellenőrzése
A telepítési naplófájlok segítségével ellenőrizze a sikeres telepítés.

##### A telepítés sikeres ellenőrizni a az RMS-megosztó alkalmazás Office 2016 vagy Office 2013, és az Azure RMS vagy az Active Directory Directory tartalomvédelmi szolgáltatások

-   Sikeres, a Setup.exe parancs minden a számítógépen, hogy a telepítési naplófájlban keressen **RMInstaller.log** a a *%temp%\RMS_installer_ &lt; guid &gt;* mappát, és azonosítsa a a kilépési kód.

    Sikeres telepítés van egy kilépési kód 0, és minden más érték azt jelzi, telepítése sikertelen volt.

    Példa naplófájl neve: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### A telepítés sikeres ellenőrizni az RMS-megosztó alkalmazás az Office 2010 és az Azure RMS számára

1.  Sikeres, a Setup.exe parancs minden a számítógépen, hogy a telepítési naplófájlban keressen **RMInstaller.log** a a *%temp%\RMS_installer_ &lt; guid &gt;* mappát, és azonosítsa a a kilépési kód.

    Sikeres telepítés van egy kilépési kód 0, és minden más érték azt jelzi, telepítése sikertelen volt.

    Példa naplófájl neve: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Ellenőrizze a RMSSetup.exe parancs sikeres, a felhasználó kell rendelkeznie a következő fájlok létrehozott azok *%localappdata%\microsoft\drm* mappa:

    -   TANÚSÍTVÁNY-gép-2048.drm

    -   TANÚSÍTVÁNY-Machine.drm

    -   Ügyféllicenc-&#42;.drm

    -   Beillesztése-&#42;.drm

    Példa: Ügyféllicenc-&#42;.drm fájl:

    **{1b9cfccf; k5b11; k4a10; kac15; k29b2b6980f4c} CLC-alice@isvtenant999.onmicrosoft.com-.drm**

##### A telepítés sikeres ellenőrizni a az RMS-megosztó alkalmazás az Office 2010 és az Active Directory Directory tartalomvédelmi szolgáltatások

1.  Sikeres, a Setup.exe parancs minden a számítógépen, ellenőrizze a telepítési naplófájlban található keresése a *%temp%\RMS_installer_ &lt; guid &gt;* mappát, és a kilépési kód azonosításához.

    Sikeres telepítés van egy kilépési kód 0, és minden más érték azt jelzi, telepítése sikertelen volt.

    Példa naplófájl neve: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Sikeres, a aadrmprep.exe parancs minden a számítógépen, ellenőrizze a telepítési naplófájlban a következő szöveg keresése: **aadrmprep.exe Kilépett állapotú sikeres**

    > [!NOTE]
    > Egyes esetekben ez a telepítési is futhat, kétszer; az első előfordulása nem sikerül, a második sikeres.

    Ha meg szeretné manuálisan tekintse meg a beállításjegyzéket, amely az eszköz, ezek a következők:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        ": ÖsszevonásiKezdőTartomány"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        ": ÖsszevonásiKezdőTartomány"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @= "&lt; hitelesítő URL-cím &gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser = "&lt; default_user &gt;"

##### A telepítés sikerült ellenőrizni az RMS-megosztó alkalmazás és az Office bővítmény csak a

1.  Ha ellenőrizni szeretné a Setup_ipviewer.exe parancs sikeres, a telepítési naplófájlban a következő szöveg keresése: **A telepítés sikeres vagy hiba állapot: 0**

    Sikeres telepítés sorok példa:

    **MSI (s) (F0:B8) [14:19:57:854]: Termék: Active Directory tartalomvédelmi szolgáltatásai 2.1 – a telepítés sikeresen befejeződött.**

    **MSI (s) (F0:B8) [14:19:57:854]: A termék telepítve a Windows Installer. Termék neve: Az Active Directory tartalomvédelmi szolgáltatásai 2.1. Termék verziószáma: 1.0.1179.1. Termék nyelve: 1033. Gyártó: A Microsoft Corporation. A telepítés sikeres vagy hiba állapot: 0.**

2.  Az Office bővítmény, minden a számítógépen, a sikeres ellenőrizni a telepítési naplófájlban a következő szöveg keresése: **A telepítés sikeres vagy hiba állapot: 0**

    Sikeres telepítés sorok példa:

    **MSI (s) (9C: 88) [18:49:04:007]: Termék: A Microsoft RMS Office-bővítmények – A telepítés sikeresen befejeződött.**

    **MSI (s) (9C: 88) [18:49:04:007]: A termék telepítve a Windows Installer. Termék neve: A Microsoft RMS Office-bővítmények. Termék verziószáma: 1.0.7. Termék nyelve: 1033. Gyártó: A Microsoft. A telepítés sikeres vagy hiba állapot: 0.**

### <a name="BKMK_uninstallscripted"></a>Távolítsa el a parancsok
A telepítési parancsokat, amelyek ezeket a telepítéshez szükséges nem minden támogatja, hogy az Eltávolítás parancsot. Az Active Directory tartalomvédelmi szolgáltatások ügyfél és a megosztóalkalmazás eltávolíthatja, és távolíthatók el az Office bővítmény. A következő parancsok segítségével távolítsa el ezeket az elemeket.

##### Az AD RMS-ügyfél és az RMS-megosztó alkalmazás eltávolítása

-   Használja a következő parancsokat:

    -   A Windows 64 bites:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   32 bites Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### Az Office bővítmény eltávolítása

-   Használja a következő parancsokat:

    -   Az Office 64 bites verziója:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Az Office 32 bites verziója:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>Automatikus frissítések megjelenítése
Alapértelmezés szerint a felhasználók értesítést, ha az RMS-megosztóalkalmazás újabb verzióját, és felszólítja az tölthető le. Az értesítés is letiltása, azáltal, hogy a következő beállításjegyzék szerkesztése:

1.  Navigáljon a **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** és ha nem már van ilyen, hozzon létre egy elnevezett **RmsSharingApp**.

2.  Válasszon **RmsSharingApp**, hozzon létre egy új DWORD értékét **AllowUpdatePrompt**, és adja meg az értéket **0**.

Az RMS-megosztási alkalmazás nem támogatja a WSUS, mert az alábbi eljárással segítségével tesztelheti az RMS-megosztó alkalmazás minden felhasználóra való telepítése előtt minden új verzióit:

1.  Azokon a számítógépeken az összes felhasználó, az automatikus frissítések letiltása parancsfájl futtatása. A rendszergazdák új verziója ellenőrzéséhez használata a számítógépeken nem a parancsfájl futtatása.

2.  Új verzió érhető el, ha a rendszergazdák tölthető le, és tesztelje.

3.  Ha a tesztelés, és az útmutató az automatikus központi telepítési utasításokat használatával merül szűnik meg, telepítse az az összes felhasználó számára a legújabb verzióra.

### <a name="BKMK_DocumentTracking"></a>Csak Azure RMS: Dokumentum-követés konfigurálása
Ha egy [amely támogatja a dokumentum követési előfizetés](https://technet.microsoft.com/en-us/dn858608), a dokumentum követési hely a szervezet összes felhasználójának alapértelmezés szerint engedélyezett.  Dokumentum nyomon követése, akik megpróbált hozzáférni a védett dokumentumok például az e-mail címekre információkat jeleníti meg, hogy a felhasználók megosztott, ha ezek a személyek próbált hozzáférni a, és azok helyét. Ha ezt az információt megjelenítése tilos a szervezet adatvédelmi követelményeit miatt, letilthatja a hozzáférést a dokumentum nyomon követése a webhely használatával a  [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) parancsmagot. Engedélyezheti újra a webhelyhez hozzáféréssel bármikor használatával a [engedélyezése-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037), és ellenőrizheti, hogy hozzáférési jelenleg engedélyezve van, vagy le van tiltva, használatával [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

 Ezek a parancsmagok futtatásához rendelkeznie kell legalább verziója **2.3.0.0** az Azure RMS-modul a Windows PowerShell környezethez.  Telepítési tudnivalókat lásd: [Azure Rights Management – telepítése a Windows PowerShell](https://technet.microsoft.com/library/jj585012.aspx).

> [!TIP]
> Ha korábban le, és a modul telepítve, ellenőrizze a verziószám: `(Get-Module aadrm –ListAvailable).Version`

a következő URL-címek követési dokumentum szolgálnak, és engedélyezni kell (például, vegye fel őket a megbízható helyek használata az Internet Explorer fokozott biztonság):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > ezt URL-cím van, a Bing maps.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>Active Directory tartalomvédelmi szolgáltatások csak: Több e-mail tartomány a szervezeten belüli támogatása
Ha az Active Directory tartalomvédelmi szolgáltatások használja, és több e-mail tartomány felhasználóknál az Ön szervezetén belül, talán miatt egyesülés vagy adatbeolvasási, ki kell választania a következő beállításjegyzék szerkesztése:

1.  Navigáljon a **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** és ha nem már van ilyen, hozzon létre egy elnevezett **RmsSharingApp**.

2.  Válassza ki **RmsSharingApp**, hozzon létre egy új Karakterláncsoros érték nevű **FederatedDomains**, majd a tartomány és a szervezet által használt összes altartományok hozzáadását. A helyettesítő karakterek nem használhatók.

    Példa: A vállalati Jóbor Szőlészet és Borászat rendelkezik a szokásos e-mail tartomány **cohovineyardandwinery.com**, de egyesülés, mert azok is használhatja az e-mailek tartományok **cohowinery.com**, **eastcoast.cohowinery.com**, és **cohovineyard**. Az a **FederatedDomains** érték, a rendszergazda adja meg: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Ha nem adja meg a beállításjegyzék módosítása, a felhasználók nem lehet a szervezet más felhasználók által védett tartalmakat. A beállításjegyzék szerkesztése Azure RMS használatakor nem szükséges.

## <a name="BKMK_AdminOverview"></a>A Microsoft Rights Management megosztóalkalmazás technikai áttekintése
A Microsoft Rights Management megosztóalkalmazás egy nem kötelező letölthető alkalmazás a Microsoft Windows és más platformokon, amely a következők:

-   Egyetlen fájl védelme vagy a tömeges protection több kijelölt mappában lévő fájlok a, valamint minden fájl.

-   A fájlt, és a gyakran használt szöveg és a kép fájltípusok beépített viewer bármilyen védelme teljes támogatása.

-   Általános védelmi fájlok, amelyek nem támogatják az RMS-védelmet.

-   Teljes együttműködés Office információkat a Rights Management szolgáltatás (IRM) használatával védett fájlokat.

-   A védett PDF-fájlok teljes együttműködés SharePoint, a FCI és a támogatott PDF szerkesztőeszközök használatával.

A Microsoft Rights Management megosztóalkalmazás használja az új [AD RMS-ügyfelet 2.1 futásidejű](http://www.microsoft.com/download/details.aspx?id=38396). Használatával a funkcióját biztosító AD RMS 2.1, a Microsoft Rights Management megosztóalkalmazás egyszerű protection, és a felhasználás felületet nyújt a végfelhasználók.

RMS. október 2013 kiadásával natív módon dokumentumok védelme az Office 2010 használatával és küldhet azokat egy másik vállalat igénybe vehet, majd azokat Azure RMS használatával, akik számára. Ezenkívül az ebben a kiadásban titkosítási mód 2, Active Directory tartalomvédelmi szolgáltatások használatakor kiválaszthatja RMS használata egyének és tartalmakat, amely az Azure RMS használja egy másik vállalat személyektől. Titkosítási mód 2 kapcsolatos további információkért tekintse meg a [AD RMS titkosítási mód](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

### <a name="BKMK_LevelsofProtection"></a>Védelmi – natív és általános szintek
A Microsoft Rights Management megosztóalkalmazás a következő táblázatban ismertetett két különböző szinteken protection támogatja.

|Védelem típusa|Natív|Általános|
|------------------|---------|-------------|
|Leírása|A szöveg, kép, a Microsoft Office (Word, Excel, PowerPoint) fájlok, PDF-fájlokat, és más alkalmazás fájltípusok, amely támogatja az Active Directory tartalomvédelmi szolgáltatások a natív protection biztosít egy magas szintű védelmet, mind a titkosítási tartalmazó és végrehajtási jogok (engedélyek).|Minden más alkalmazást és fájltípusok általános védelmi biztosít a szintű védelem, amely tartalmazza a mindkét fájl beágyazás a .pfile fájl típusa és a hitelesítési segítségével ellenőrizze, hogy ha a felhasználó jogosult-e a fájl megnyitásához.|
|Védelem|Teljes titkosított fájlok, és a védelmi kényszerítése a következő módon:<br /><br />-   Védett tartalom van megjelenítve, mielőtt a sikeres hitelesítés azok számára, akiknek a fájl révén e-mailek fogadására, vagy a hozzáférést kapnak a azt fájl vagy a megosztás-engedélyek kell elő.<br />-   Ezenkívül használati jogok és a beállított által a tartalom tulajdonosához, ha a védett fájlok házirend teljesen tartatja be a tartalmat jelenít meg a program vagy IP-cím Viewer (a védett szöveg és a kép fájlok), vagy a társított alkalmazást (az összes többi támogatott fájltípusok).|A következő módokon fájlvédelem kényszerítése:<br /><br />-   Mielőtt a védett tartalom van megjelenítve, a sikeres hitelesítés kell fordulhat elő, azok számára, akiknek engedélyezett megnyitni a fájlt, és a hozzáférést a megadott azt. Ha a hitelesítés nem sikerül, a fájl nem nyitható meg.<br />-   Használati jogok és a tartalom tulajdonosához által beállított házirend tájékoztatja a hitelesített felhasználóknak a kívánt felhasználási házirend jelennek meg.<br />-   Az engedélyezett felhasználók megnyitása és fájlokhoz naplózás akkor fordul elő, azonban nem használati jogok nem támogató rendelkező alkalmazások.|
|Alapértelmezett fájltípusok|Ez az, hogy a következő fájltípusú védelmét alapértelmezett szintje:<br /><br />-   Szöveg és a kép fájlok<br />-   A Microsoft Office (Word, Excel, a PowerPoint) fájlok<br />-   Hordozható dokumentum formátum (PDF)<br /><br />További tudnivalókért tekintse meg a következő szakaszban [Támogatott fájltípusok és kiterjesztések](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes).|Ez az alapértelmezett védelmi minden egyéb fájltípusok (például .vsdx, .rtf) keresztül teljes védelmet nem támogatott.|
Módosíthatja az alapértelmezett védelmi szint, amely az RMS-megosztási alkalmazás vonatkozik. Általános, hogy az általános a natív natív alapértelmezett szint módosítása, és még megakadályozza az RMS-megosztó alkalmazás alkalmazása a védelem. További tudnivalókért tekintse meg a [Az alapértelmezett védelmi szint fájlok módosítása](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection) szakaszban, a jelen témakörben található.

### <a name="BKMK_SupportFileTypes"></a>Támogatott fájltípusok és kiterjesztések
A következő táblázat felsorolja a Microsoft Rights Management megosztóalkalmazás által natív módon támogatott fájltípusok. Az ilyen típusú az eredeti kiterjesztésű akkor kerül, ha a védett natív vonatkozik, és ezeket a fájlokat válnak a csak olvasható.

Ezenkívül az RMS-megosztó natív módon a alkalmazás védi a Word, az Excel vagy a PowerPoint fájl megosztása révén a felhasználók védelme, amikor ez a művelet automatikusan létrehoz egy második fájlt, amely az eredeti, azonos nevű fájl, de a másolatát egy **.ppdf** kiterjesztésű ¹. Ez a fájl verziója biztosítja, hogy a címzett, aki az RMS-megosztó alkalmazás telepítése is mindig nyissa meg a fájlt, amelynek a natív protection alkalmazott.

Általánosságban védett fájlokat, az eredeti fájlnévkiterjesztést .pfile mindig változik.

> [!WARNING]
> Ha tűzfalak, a webalkalmazás-proxy vagy a biztonsági szoftver, amely nézze meg, és megfelelően kiterjesztések művelet végrehajtása, szükség lehet konfigurálni, ezek a támogatja-e új kiterjesztések.

|Eredeti fájlnévkiterjesztést.|RMS által védett fájlnévkiterjesztést|
|---------------------------------|-----------------------------------------|
|.txt|.ptxt|
|.XML|.pxml|
|.jpg|.pjpg|
|.JPEG|.ppng|
|PDF|.ppdf|
|.png|.ppng|
|grafikus|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jif|.pjif|
|.JT|.pjt|
¹ PDF-megjelenítő a Foxit által. Copyright © 2003-2014, Foxit Corporation.

A következő táblázat felsorolja a Microsoft Rights Management megosztóalkalmazás natív módon támogatja a Microsoft Office 2016, az Office 2013 és az Office 2010 típusú fájlokat. Ezeket a fájlokat a a fájlnévkiterjesztés változatlan marad, a fájl RMS által védett után.

|Office által támogatott fájltípusok|Office által támogatott fájltípusok|
|---------------------------------------|---------------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="BKMK_ChangeDefaultProtection"></a>Az alapértelmezett védelmi szint fájlok módosítása
Hogyan az RMS-megosztó alkalmazás védi a fájlokat a beállításjegyzék szerkesztésével módosítható. Például, amely támogatja a natív protection általánosságban az RMS-megosztási alkalmazás által védett fájlokat kényszerítheti.

Miért érdemes lehet Ennek okai:

-   És győződjön meg arról, hogy minden felhasználó azok mobileszközről a fájl megnyitható.

-   Győződjön meg arról, hogy a minden felhasználó a fájl megnyitható, ha egy alkalmazás nem rendelkeznek, amely támogatja a natív védelmét.

-   Hogy a művelet végrehajtása a fájlok a fájlnévkiterjesztés és a .pfile fájlnévkiterjesztést befogadásához újra kell konfigurálni, de nem lehet több fájlnév-kiterjesztéseket natív protection befogadásához újra kell konfigurálni a biztonsági rendszerek befogadásához.

Ehhez hasonlóan az RMS-megosztó alkalmazás natív protection alkalmazandó fájlokat, hogy alapértelmezés szerint az általános védelmi alkalmazott kényszerítheti. Ez lehet megfelelő, ha egy alkalmazás, amely támogatja az RMS API-k – például, egy sor üzleti a belső fejlesztők által írt vagy kérelem vásárolt a független szoftverszállító (ISV).

Az RMS-megosztó alkalmazás blokkolja a fájlok védelméről kényszerítheti is (nem vonatkozik a natív védelmi vagy általános védelmi). Például ennek oka az lehet szükséges, ha egy automatikus alkalmazás vagy a szolgáltatás, amely egy adott fájl tartalmának feldolgozásához nyissa meg kell rendelkeznie. Blokkolja a védelmét egy fájltípust, amikor a felhasználók nem lehet védetté tenni a fájlt, amelynél az adott fájltípushoz az RMS-megosztó alkalmazás használható. Próbálja meg, ha azok, hogy a rendszergazda megakadályozta a védelmet, és azok kell a Mégse gombra a művelet a védett fájlt üzenet jelenik meg.

Az RMS-megosztó alkalmazás általános védelmi alkalmazandó minden fájl, amely alapértelmezés szerint kellene lennie alkalmazott natív protection konfigurálásához adja meg a következő beállításjegyzék-módosítás:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Hozzon létre egy elnevezett **&#42;**.

    Ez a beállítás azt jelzi, hogy minden kiterjesztésű fájlokat.

2.  Az újonnan hozzáadott kulcsa **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\ &#42;**, hozzon létre egy új karakterlánc (REG_SZ) nevű értéket **titkosítási** amelynek a adatértéket **Pfile**.

    Ez a beállítás az RMS-megosztó alkalmazás alkalmazása általános védelmi eredményez.

Ezek a beállítások két az RMS-megosztó alkalmazás alkalmazása általános védelmi összes fájlok, amelyek egy fájlnévkiterjesztést eredményez. Ha ez a cél, a további beállítás nem szükséges. Azonban, hogy továbbra is a natív módon védett kivételek adott fájltípushoz adhatja meg. Ehhez hajtsa végre a, ki kell választania három további beállításjegyzék módosításának az egyes fájltípusok:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Adjon hozzá egy új kulcsot, hogy a fájl kiterjesztése (nélkül az előző időszak) nevét.

    Például, ha a fájlok, amelyek egy .docx kiterjesztésű, hozzon létre egy elnevezett kulcsot **DOCX**.

2.  Az újonnan hozzáadott fájl típusa kulcs (például **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), hozzon létre egy új DWORD-értéket nevű **AllowPFILEEncryption** amelynek értéke **0**.

3.  Az újonnan hozzáadott fájl típusa kulcs (például **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), hozzon létre egy új karakterlánc-értéket nevű **titkosítási** amelynek értéke **natív**.

Ezek a beállítások miatt minden fájl általánosságban védett fájlokat, amelyek egy .docx kiterjesztésű, amelyek az RMS-megosztási alkalmazás natív módon védett kivételével.

Ismételje meg ezeket a lépéseket más fájltípusok kivételnek határozza meg, mert használatát támogatja a natív protection, és nem szeretné, hogy azokat az RMS-megosztási alkalmazás általánosságban védendő kívánt.

Hasonló a beállításjegyzék módosításának más forgatókönyveknél tehetjük a értékének módosítása a **titkosítási** karakterlánc, amely támogatja a következő értékek:

-   **Pfile**: Általános védelmi

-   **Natív**: Natív védelem

-   **Off**: A védelem letiltása

## Lásd még
[A Rights Management megosztási alkalmazás felhasználói útmutató](../Topic/Rights_Management_sharing_application_user_guide.md)

