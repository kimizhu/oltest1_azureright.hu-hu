---
description: na
keywords: na
title: Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
---
# Fő felhaszn&#225;l&#243;k konfigur&#225;l&#225;sa az Azure Rights Management &#233;s felder&#237;t&#233;si szolg&#225;ltat&#225;sokat vagy adatok helyre&#225;ll&#237;t&#225;sa
A Microsoft felügyelő felhasználó szolgáltatása [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) biztosítja, hogy a meghatalmazott személyeket és szolgáltatásokat mindig képes-e olvasási és vizsgálja meg az adatokat, amelyek az Azure RMS védi a szervezetben. És ha szükséges, távolítsa el a védelmi, vagy módosítsa a korábban alkalmazott védelmét. Egy felügyelő felhasználó mindig a az összes használati licenceket, amely szerint a szervezete RMS-bérlői nyert a teljes tulajdonosi jogokkal rendelkezik. Ez a lehetőség van is nevezik "indoklást adatok felett", és karbantartása vezérelhetik a szervezet adatait a fontos eleme. Például használja ezt a funkciót az alábbi esetek bármelyike:

-   A munkavállaló kilép a szervezet, és olvassa el a fájlokat, amely azokat a védett van szüksége.

-   A rendszergazda eltávolítása az aktuális védelmi házirend fájlokat a konfigurált és egy új védelmi házirend alkalmazása a következőre.

-   Exchange Server index postaládával keresési műveletekhez szükséges.

-   Az adatok adatvesztés megelőzése (DLP) megoldások, a tartalom titkosítási átjárók (CEG) és a kártevőirtó termékek, amelyeket már védett fájlokat vizsgálja meg a meglévő informatikai szolgáltatások rendelkezik.

-   Tömeges visszafejtése fájlok naplózás, jogi vagy más megfelelőség oka van szüksége.

Alapértelmezés szerint a felügyelő felhasználó funkció nincs engedélyezve, és a felhasználók nem kapnak ehhez a szerepkörhöz. Engedélyezve van, automatikusan, ha a Rights Management-összekötő az Exchange konfigurálását, és nem futó az Exchange Online, a SharePoint Online vagy a SharePoint Server standard szolgáltatások szükséges.

Ha manuálisan a a felügyelő felhasználó funkció engedélyezéséhez van szüksége, használja a Windows PowerShell-parancsmag [engedélyezése-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), majd rendelheti a felhasználók (vagy szolgáltatásfiókok) használatával szükség esetén a [hozzáadása-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) parancsmagot. Egy vagy több felügyelő felhasználók számára a szervezet akkor is, de a hozzá kell adnia az egyes felhasználók; csoportok nem támogatottak.

> [!NOTE]
> Ha Ön még nem telepítette a Windows PowerShell modul a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], lásd: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Biztonsági gyakorlati tanácsok az felügyelő felhasználó funkció:

-   Korlátozza, és a figyelő a rendszergazdák számára, aki vannak hozzárendelve egy globális rendszergazda az Office 365 vagy az Azure RMS-bérlőben, vagy a akihez van rendelve a GlobalAdministrator szerepkör használatával a [hozzáadása-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) parancsmagot. Ezek a felhasználók a felügyelő felhasználó funkció engedélyezéséhez és hozzárendelése a felhasználók (és a magukat) felügyelő felhasználóként, és potenciálisan visszafejteni az összes fájlt, amely a szervezet védi.

-   Tekintse meg, hogy mely felhasználók és a szolgáltatásfiókok felügyelő felhasználók vannak hozzárendelve, használja a [Get-AadrmSuperUser parancsmag](https://msdn.microsoft.com/library/azure/dn629408.aspx).  Az összes felügyeleti műveletek, például a engedélyezése vagy letiltása a fő szolgáltatás és a felhasználók hozzáadása és eltávolítása felügyelő ki be vannak jelentkezve, és segítségével naplózható a [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) parancsot. Felügyelő felhasználók visszafejteni a fájlokat, amikor ez a művelet naplózva van-e, és a naplózható [a használat naplózása](https://technet.microsoft.com/library/dn529121.aspx).

-   Ha nincs szükség a felügyelő felhasználó funkció mindennapi szolgáltatások, a funkció engedélyezéséhez csak akkor, ha szükséges, és tiltsa le ismét használatával a [Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) parancsmagot.

A következő napló kivonat néhány példa a Get-AadrmAdminLog parancsmaggal bejegyzéseit mutatja. Ebben a példában a rendszergazda a Contoso Ltd igazolja, hogy a felügyelő felhasználó szolgáltatás le van tiltva, Richard Simone hozzáadja a felügyelő felhasználó, ellenőrzi, hogy Richard-e a konfigurált Azure RMS csak felügyelő felhasználó, majd lehetővé teszi, hogy a felügyelő felhasználó szolgáltatást úgy, hogy a Richard most fejti vissza a néhány fájlt, amely egy alkalmazott, aki most már kilépett a vállalat által védettek.

`2015-08-01T18:58:20	admin@contoso.com	GetSuperUserFeatureState	Passed	Disabled`
`2015-08-01T18:59:44	admin@contoso.com	AddSuperUser -id rsimone@contoso.com	Passed	True`
`2015-08-01T19:00:51	admin@contoso.com	GetSuperUser	Passed	rsimone@contoso.com`
`2015-08-01T19:01:45	admin@contoso.com	SetSuperUserFeatureState -state Enabled	Passed	True`

## <a name="BKMK_RMSProtectionModule"></a>Parancsprogram-beállítások felügyelő felhasználó
Gyakran valaki, akinek ki lett osztva a felügyelő felhasználó [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] kell eltávolítani a védelmet a több helyen több fájlból. Lehetséges, ehhez manuálisan is, akkor hatékonyabb (és gyakran megbízhatóbb), ez a parancsfájl. Ehhez [Töltse le az RMS-védelmi eszközt](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Ezután a  [védelem-RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) parancsmag, és [védelme-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx)   parancsmag szükség szerint.

> [!IMPORTANT]
> Bár az RMS-védelmi eszközt felügyelő felhasználók tömeges tervezték a védelem megszüntetéséhez fájlok helyreállítási célokra, az eszköz aktuális verziója nem támogatja a felhasználó hitelesítése az Azure RMS. Ez a korlátozás megoldásáig egyszerű szolgáltatásfiók Azure RMS jelentkezniük protection fájlok eltávolítása előtt kell használnia.  További információkat és utasításokat [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/azure/mt433202.aspx).

A parancsmagok használatával kapcsolatos további információkért tekintse meg a [RMS Protection parancsmagok](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> A RMSProtection a Windows PowerShell modul, amely az RMS-védelmi eszközzel alkalmazásáruházból eltér, és egészíti ki a fő [a Windows PowerShell modul Azure Rights Management](https://technet.microsoft.com/library/jj585027.aspx). Mind az Azure RMS, mind az Active Directory tartalomvédelmi szolgáltatások támogatja.

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

