---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# A Windows PowerShell telep&#237;t&#233;se Azure Rights Management
Használja a következő információkat a segítenek a Windows PowerShell telepítse a Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

Ez a Windows PowerShell-modul segítségével felügyelheti [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] használatával a parancssorból bármilyen számítógépen, hogy van-e internetkapcsolata és, amely megfelel az Előfeltételek felsorolt, a következő szakaszban. A Windows PowerShell [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] automatizálásra scripting támogatja, vagy a speciális konfigurációs forgatókönyvek szükséges lehet. A felügyeleti feladatokat, és a modul támogató konfigurációk további tájékoztatásért lásd: [Az Azure Rights Management felügyelete a Windows PowerShell használatával](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Előfeltételek
Ez a táblázat felsorolja az előfeltételek telepítése és használata a Windows PowerShell for [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Követelmény|További információ|
|---------------|----------------------|
|Verziószámú, amely támogatja a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Adminisztráció modul|Ellenőrizze a támogatott operációs rendszerek listáját a **Rendszerkövetelmények** szakasza a [lap letöltése a Azure Rights Management felügyeleti eszköz](http://go.microsoft.com/fwlink/?LinkId=257721).|
|A Windows PowerShell minimális verziója: 2.0|Támogatja a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Adminisztráció modul a Windows PowerShell 2.0-s bevezetett.<br /><br />Alapértelmezés szerint a legtöbb Windows operációs rendszer telepítése legalább Windows PowerShell 2.0-s verzióját. Ha a Windows PowerShell 2.0 telepítése van szüksége, tekintse meg a [telepítse a Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx). **Tip:** Beírásával futó Windows PowerShell verziójának megerősítése **$PSVersionTable** Windows PowerShell munkamenetben.|
|A Microsoft .NET-keretrendszer minimális verziója: 4.5 **Tip:** A Microsoft .NET Framework jelen verziójában része az újabb operációs rendszerek, így csak akkor kell a manuálisan kell telepítenie, ha az ügyfél operációs rendszere kisebb, mint a Windows 8.0, vagy a kiszolgálói operációs rendszer Windows Server 2012-nél kisebb.|Ha ez nem telepítette, letöltheti a [a Microsoft .NET-keretrendszer 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Ez a Microsoft .NET-keretrendszer verziója szükséges osztályok részénél, amely a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Adminisztráció modul használ.|
|Microsoft Online Services – bejelentkezési segéd 7.0|A Microsoft Online Services bejelentkezési segédje meg kell adni a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] hitelesítés.<br /><br />További tudnivalókért tekintse meg a [Download Center: Microsoft Online Services az informatikai szakemberek RTW Segéd](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## A Rights Management Adminisztráció modul telepítése

1.  Nyissa meg a Microsoft Download Center és [Töltse le az Azure Rights Management felügyeleti eszközt](https://go.microsoft.com/fwlink/?LinkId=257721), amely tartalmazza a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] Adminisztráció modul Windows Powershellhez.

2.  A helyi mappában, ahol le, és menti a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] telepítő fájl, kattintson duplán a végrehajtható fájl, amely az Azure AD Rights felügyeleti felügyeleti telepítő varázsló elindításához le a Platform (WindowsAzureADRightsManagementAdministration_x64 vagy WindowsAzureADRightsManagementAdministration_x86.exe).

3.  A varázsló befejezéséhez.

A Windows PowerShell [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] most már telepítve van.

## További lépések
Tekintse meg, mely parancsmagok érhetők el, indítsa el a Windows PowerShell a **Futtatás rendszergazdaként** lehetőséget, és írja be a következőt:

```
Get-Command -Module aadrm
```
Használata `the Get-Help <cmdlet_name>` parancsot egy adott parancsmag súgójában.

További információ:

-   Teljes listáját a parancsmagok érhető el: [Azure Rights Management parancsmagok](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Fő konfigurációs forgatókönyvek, amely támogatja a Windows PowerShell listája: [Az Azure Rights Management felügyelete a Windows PowerShell használatával](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Konfigurálása parancs futtatása előtt a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] szolgáltatást, csatlakoznia kell a szolgáltatás segítségével a [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) parancsmagot. Ha befejezte, hogy a kívánt konfigurációs parancsok fut, leválasztása a szolgáltatás használatával a [kapcsolat bontása-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmagot.

> [!NOTE]
> Ha még nem aktiválta [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], ehhez a szolgáltatás segítségével csatlakozás után a [engedélyezése-történő együttműködésre](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) parancsmagot.

## Lásd még
[Az Azure Rights Management felügyelete a Windows PowerShell használatával](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

