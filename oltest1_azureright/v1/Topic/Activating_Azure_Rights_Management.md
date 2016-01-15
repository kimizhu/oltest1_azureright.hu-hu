---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Az Azure Rights Management aktiv&#225;l&#225;sa
Ha aktiválja [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), a szervezet megkezdheti a fontos adatok védelméhez az alkalmazások és szolgáltatások, amelyek támogatják a Ez az információvédelmi megoldás használatával. A rendszergazdák is kezelése és figyelése a védett fájlok és az e-mailek, amely a szervezet tulajdonosa. Engedélyeznie kell [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] a tartalomvédelmi (IRM) szolgáltatásokat Office, a SharePoint és az Exchange belül, és semmilyen személyes vagy bizalmas fájl védelme megkezdése előtt.

Ha azt szeretné, ha többet szeretne megtudni Azure Rights Management a szolgáltatás aktiválása előtt – például, milyen üzleti problémák ez megoldja-e, néhány jellemző használati esetek, és hogyan működik – lásd: [Mi az Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Aktiválása előtt [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], győződjön meg arról, hogy a szervezet rendelkezik-e, amely tartalmaz service-csomag [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatásokat. Ha nem, nem fogja tudni Azure RMS aktiválása.
> 
> További információ: a [Felhő előfizetések, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) szakasz a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) témakör.

Miután aktiválta Azure RMS, a szervezet minden felhasználója adatvédelem alkalmazni a fájljaik és az összes felhasználó meg tudja nyitni (felhasználni), amely az Azure RMS által védett fájlok. Azonban ha azt szeretné, korlátozhatja adatvédelem, akik alkalmazhat fázisos központi telepítés bevezetési vezérlők használatával. További információ: a [Bevezetési vezérlők fázisos központi telepítés konfigurálása](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) című szakaszában talál.

## A Rights Management aktiválása
A következő eljárások segítségével aktiválni [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

> [!TIP]
> Használhatja a Windows PowerShell-parancsmag [engedélyezése-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), hogy aktiválja a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Az Office 365 felügyeleti központban a Rights Management aktiválása

1.  Miután az Office 365 terv, amely tartalmazza a Rights Management, aláírt [a munkahelyi vagy iskolai fiókkal jelentkezzen be Office 365](https://portal.office.com/) amely az Office 365-telepítés rendszergazdája.

2.  Ha nem jelennek meg automatikusan az Office 365 felügyeleti központban jelölje ki az alkalmazás indítója ikon bal felső sarkában, majd válassza **Admin**. A **Admin** mozaik csak a rendszergazdák Office 365 jelenik meg.

    > [!TIP]
    > Felügyeleti központ talál segítséget [kapcsolatos az Office 365 felügyeleti központban - rendszergazda súgó](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  A bal oldali panelen bontsa ki a **SZOLGÁLTATÁSBEÁLLÍTÁSOK**.

4.  Kattintson a **Rights Management**.

    > [!NOTE]
    > Ez a beállítás nem jelenik meg, a, mert a terv vagy a termék verziója nem támogatja a Rights Management, vagy azt van még nem frissített támogatásához a Rights Management lehet.
    > 
    > Az információk a [Felhő előfizetések, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) szakasz a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) a témakörhöz, és erősítse meg a támogatási szolgálathoz. Ha a csomag vagy a termék verziója támogatott, de nem látja a Rights Management beállítás, lehet, mert a szolgáltatás még nem frissítette. További információ a probléma, küldjön e-mail üzenetet a [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  Az a **RIGHTS MANAGEMENT** lap **kezelése**.

6.  Az a **a rights management** lapján kattintson **aktiválása**.

7.  Ha a rendszer kéri **szeretné aktiválni a Rights Management?**, kattintson a **aktiválása**.

Most látnia **Rights management aktiválva van** és inaktiválja beállítás.

#### A hagyományos Azure portálról Rights Management aktiválása

1.  Az Azure-fiók aláírása után [Jelentkezzen be az Azure hagyományos](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  Kattintson a bal oldali ablaktáblában **ACTIVE DIRECTORY**.

3.  Az a **az active directory** lap **RIGHTS MANAGEMENT**.

4.  Jelölje ki a könyvtárat, kezelheti a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], kattintson a **AKTIVÁLÁSA**, majd erősítse meg a műveletet.

    > [!NOTE]
    > Ha az aktiválás hibaüzenet jelenik meg, mert a terv vagy a termék verziója nem támogatja lehet [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Az információk a [Felhő előfizetések, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) szakasz a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) a témakörhöz, és erősítse meg az RMS-támogatás. További információ a probléma, küldjön e-mail üzenetet a [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

A **RIGHTS MANAGEMENT állapot** most meg kell jelenítenie **aktív** és a **AKTIVÁLÁSA** beállítás cseréli **INAKTIVÁLJA**.

### A Rights Management állapotát és hibaleírások hagyományos Azure portálon
Továbbá a **Active** állapotát, amely azt jelzi, hogy a Rights Management szolgáltatás engedélyezve van, és használatra kész, előfordulhat, hogy is látható **Inaktív**, **nem érhető el**, vagy **nem engedélyezett**.

|Állapot érték|Leírás|
|-----------------|----------|
|**Aktív**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] engedélyezve van, és használatra kész.|
|**Inaktív**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] le van tiltva, és a szervezet fájlok védelméhez kell aktiválni.|
|**Nem érhető el**|A [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatás nem működik. Próbálkozzon újra később.|
|**Nem engedélyezett**|Nincs engedélye állapotának megtekintése a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatás. Például a fiók ki van zárva, vagy nem áll a kijelölt bérlő számára a globális rendszergazdai.|

## <a name="BKMK_OnboardingControls"></a>Bevezetési vezérlők fázisos központi telepítés konfigurálása
Fájlok védelme azonnal Azure RMS segítségével minden felhasználó nem szeretné, ha felhasználói bevezetési vezérlők használatával beállíthatja a [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) Windows PowerShell-parancsot. Ez a parancs előtt, vagy az Azure RMS aktiválása után futtathatja.

> [!IMPORTANT]
> Ez a parancs használatához rendelkeznie kell legalább verzió **2.1.0.0** a [Azure RMS Windows PowerShell-modul](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> A telepített verzió megadásával ellenőrizheti: **(Get-Module aadrm –ListAvailable).Version**

Például ha csak a rendszergazdák a "IT-részleg" csoport (fbb99ded-32a0-45f1-b038-38b519009503 Objektumazonosítója rendelkező) szeretné kezdetben tud védeni a tartalom tesztelési célra használja a következő parancsot:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Vegye figyelembe, hogy a konfigurációs beállítás, meg kell adnia egy csoport; egyes felhasználók nem adható meg.

Vagy ha biztos szeretne lenni abban, hogy csak a megfelelő licencét az Azure RMS Alkalmazást használó felhasználók védheti tartalom:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
A bevezetési vezérlők használatakor a szervezet minden felhasználója mindig felhasználhat védett tartalmakat, a felhasználók részhalmazát által védett, de azok nem fogja tudni alkalmazni adatvédelem magukat az ügyfélalkalmazások. Például nem látják az Office-ügyfelek az alapértelmezett sablonokat, hogy a rendszer automatikusan közzéteszi Azure RMS aktiválásakor, vagy beállíthat egyéni sablont.  Kiszolgálóoldali alkalmazások, mint például az Exchange, az RMS-integráció ugyanazt az eredményt eléréséhez a saját felhasználói vezérlők is alkalmazható.

## Az alábbi lépéseket
Most, hogy Ön már aktiválva [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] a szervezet használja a [Azure Rights Management – üzembehelyezési menetrend](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) ellenőrzésére, hogy vannak-e más konfigurációs lépéseket, amelyek hasznosak lehetnek, mielőtt forgassa ehhez a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] felhasználók és rendszergazdák. Például előfordulhat, hogy használandó [egyéni sablonok](http://technet.microsoft.com/library/dn642472.aspx) ahhoz, hogy a felhasználók az adatvédelem alkalmazandó fájlok könnyebben, csatlakozzon a helyszíni kiszolgálók [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] telepítésével a [RMS összekötő](http://technet.microsoft.com/library/dn375964.aspx), és központi telepítése a [Rights Management megosztóalkalmazás](http://technet.microsoft.com/library/jj585031.aspx) amely támogatja az összes eszközön lévő összes fájltípus védelmét. Office-szolgáltatások, például az Exchange online-hoz és a SharePoint Online további konfigurálást igényel, mielőtt használhatná a tartalomvédelmi szolgáltatással (IRM) funkciókat. Azonban, ha nincs más konfigurációs lépések, amelyek kell, hogy [Azure Rights Management használata](../Topic/Using_Azure_Rights_Management.md) a sikeres telepítés támogatása a szervezet működési útmutatást.

Azzal kapcsolatban, hogy az alkalmazások hogyan működnek a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], lásd: [Hogyan alkalmazások támogatják a Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

