---
description: na
keywords: na
title: Administering Azure Rights Management by Using Windows PowerShell
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
---
# Az Azure Rights Management fel&#252;gyelete a Windows PowerShell haszn&#225;lat&#225;val
Bár Microsoft aktiválhatja [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) használatával a [!INCLUDE[o365_2](../Token/o365_2_md.md)] felügyeleti központban vagy a hagyományos Azure portálon is használhatja a Windows PowerShell-modul a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] Ehhez (AADRM).

Miután aktiválta [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], továbbá a szolgáltatás felügyeleti nem feltétlenül szükséges. Azonban bizonyos speciális konfigurációs esetekben előfordulhat, hogy használja a Windows PowerShell-modul [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. A következő táblázat felsorolja az egyes Windows PowerShell használatával speciális konfigurációs forgatókönyvre. Mindegyik kapcsolatos további információkat az elérhető parancsmagok teljes listáját lásd: [Azure Rights Management parancsmagok](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Ha szeretné-e a Windows PowerShell moduljának telepítéséhez [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], lásd: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Is van egy kiegészítő Windows PowerShell-modul **RMSProtection**, amely az Azure RMS és AD RMS támogatja. Ez a modul védelme és védelmének eltávolítása több fájlt, így például tömeges védheti mappában lévő összes fájlok támogatja. További információ: a [Parancsprogram-beállítások felügyelő felhasználó](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md#BKMK_RMSProtectionModule) szakasz a [Fő felhasználók konfigurálása az Azure Rights Management és felderítési szolgáltatásokat vagy adatok helyreállítása](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md) témakör.

|Ha módosítania kell...|.. a következő parancsmagok tevékenységben|
|--------------------------|----------------------------------------------|
|A helyszíni Rights Management (AD RMS- vagy Windows RMS) át [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Importálás – AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|A létesítése vagy bontása a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatást a szervezet számára.|[Csatlakozás AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Kapcsolat bontása AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Létrehozása és kezelése a saját bérlői kulcs – a kerüljön a saját kulcs (BYOK) forgatókönyv.|[AadrmKey hozzáadása](http://msdn.microsoft.com/library/azure/dn629418.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Be- és kikapcsolása a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatást a szervezet számára.|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|A dokumentumkövetési hely Azure Rights Management engedélyezése vagy letiltása.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Bevezetési vezérlők az Azure Rights Management fázisos központi telepítés konfigurálása.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Hozzon létre és kezelheti a szervezet jogmegadási sablonok.|[AadrmTemplate hozzáadása](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Exportálás-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Importálás – AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[Új AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Konfigurálja a szervezet védő tartalom érhető el (használja licenc érvényességi) internetkapcsolat nélkül napok maximális száma.|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|A felügyelői szolgáltatása kezelése [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] a szervezet számára.|[Enable-AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[AadrmSuperUser hozzáadása](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629405.aspx)|
|Kezelheti a felhasználók és csoportok felügyeletére jogosult a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatást a szervezet számára.|[AadrmRoleBasedAdministrator hozzáadása](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Get naplózása [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] a szervezet felügyeleti feladatokat.|[Get-AadrmAdminLog](http://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Jelentkezzen és naplózása használati elemzése [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Enable-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629421.aspx)<br /><br />[Get-AadrmUsageLog](http://msdn.microsoft.com/library/azure/dn629401.aspx)<br /><br />[Get-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629425.aspx)<br /><br />[Get-AadrmUsageLogLastCounterValue](http://msdn.microsoft.com/library/azure/dn629423.aspx)<br /><br />[Get-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629419.aspx)<br /><br />[Set-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629426.aspx)<br /><br />[Disable-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629404.aspx)|
|Megjeleníti az aktuális [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatáskonfiguráció a szervezet számára.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Telepítse át a szervezet a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] egy helyszíni AD RMS telepítése.|[Set-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

## Lásd még
[Azure Rights Management](../Topic/Azure_Rights_Management.md)

