---
description: na
keywords: na
title: Decommissioning and Deactivating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
---
# Le&#225;ll&#237;t&#225;s&#225;ra, &#233;s az Azure Rights Management inaktiv&#225;l&#225;s&#225;r&#243;l
Mindig irányítását, hogy a szervezet tartalmat védő használatával vannak [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), és úgy dönt, akkor már nem szeretné használni, ez az információvédelmi megoldás, ha rendelkezik-e a biztosítékot, hogy meg nem zárható ki korábban védett tartalmat. Folyamatos korábban védett tartalomhoz való hozzáférés nem szükséges, ha egyszerűen inaktiválhatja a szolgáltatást, és lehetővé teszi az Azure Rights Management az előfizetés lejár. Például lenne megfelelő Miután végrehajtotta tesztelési [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] Mielőtt éles környezetben telepítené.

Azonban ha előzőleg telepített [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] üzemi környezetben, győződjön meg arról, hogy az Azure Rights Management bérlői kulcsának egy példánya van ehhez az előfizetés lejárta előtt és a szolgáltatás inaktiválása előtt, mert ezzel biztosíthatja, hogy őrizheti után Azure Rights Management által védett tartalomhoz való hozzáférést a szolgáltatás inaktiváltuk. A kerüljön a saját kulcs-megoldása (BYOK) ahol létrehozása és kezelése a saját Hardvermodult kulcs használata esetén az Azure Rights Management bérlői kulcs már lesz. De volt kezelve, a Microsoft (alapértelmezett), ha a bérlő kulcs exportálása vonatkozó utasításokat lásd [A Azure Rights Management bérlői kulcs műveletek](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md) témakör.

> [!TIP]
> Az előfizetés lejárta után is az Azure Rights Management bérlői hosszabb ideig fel a tartalom elérhető marad. Azonban már nem fogja tudni a bérlő kulcs exportálása.

Ha az Azure Rights Management bérlői kulccsal rendelkezik, telepítheti a Rights Management (AD RMS) helyszíni és importálása a bérlő kulcs megbízható közzétételi tartomány (TPD). Választhat leszerelése az Azure Rights Management-telepítés a következő beállításokat:

|Ez vonatkozik, ha...|… tegye a következőket:|
|------------------------|---------------------------|
|Az összes felhasználóinak tartalomvédelmi szolgáltatás használatának folytatásához, de használja az Azure RMS → használata helyett egy helyszíni megoldás|Használja a [Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) parancsmag közvetlen meglévő felhasználók a helyszíni telepítésére, ha ez a módosítás után védett tartalmak igényelnek. Felhasználók automatikusan használja az Active Directory tartalomvédelmi szolgáltatások telepítése a védett tartalmakat.<br /><br />A felhasználók számára, hogy ez a módosítás előtt védett tartalmakat, az ügyfelek átirányítása a helyszíni központi telepítés használatával a **LicensingRedirection** Office 2016 vagy Office 2013, az ismertetett beállításkulcs a [felderítési szakasz szolgáltatás](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) RMS ügyfél központi telepítési megjegyzések és a **LicenseServerRedirection** beállításkulcs az Office 2010, a következő témakörben ismertetett módon [Office beállításjegyzék-beállítások](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Szeretné leállítani a Rights Management technológiák használatával, teljesen →|Adjon meg egy kijelölt rendszergazdához [felhasználói jogok Szuper](https://technet.microsoft.com/library/mt147272.aspx) és a személynek a [RMS védelmi eszköz](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Ez a rendszergazda ezután az eszköz segítségével tömeges-visszafejtési fájlok és mappák, hogy éppen nem védett vissza a fájlokat, és ezért a tartalomvédelmi technológiával, mint például a Azure RMS vagy Active Directory tartalomvédelmi szolgáltatások nélkül olvasható Azure Rights Management által védett. Ez az eszköz Azure RMS és AD RMS, is használható, hogy jogosult-e a kiválasztott fájlok előtt visszafejtése vagy az Azure RMS vagy együttes inaktiválása után.|
|Nem lehet azonosítani a Azure RMS által védett fájlokat, vagy azt szeretné, hogy minden felhasználó automatikusan beolvasásához → nem talált meg minden védett fájlok|A beállításjegyzék-beállítást az összes ügyfélszámítógépen telepíteni a **LicensingRedirection** Office 2016 és Office 2013, az ismertetett beállításkulcs a [felderítési szakasz szolgáltatás](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) RMS ügyfél központi telepítési jegyzetek a és a **LicenseServerRedirection** beállításkulcs az Office 2010, a következő témakörben ismertetett módon [Office beállításjegyzék-beállításokat](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Annak megakadályozásához, hogy a felhasználók úgy, hogy az új fájlok védelme egy másik beállításjegyzék-beállítást is telepíthet **DisableCreation** a **1**, leírtak szerint [Office beállításjegyzék-beállítások](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Azt szeretné, hogy azokat a fájlokat, a kihagyott → volt ellenőrzött, kézi helyreállítási szolgáltatás|Támogatás a kijelölt felhasználók helyreállítási csoportokban [felhasználói jogok Szuper](https://technet.microsoft.com/library/mt147272.aspx) így azok a [RMS védelmi eszköz](http://www.microsoft.com/en-us/download/details.aspx?id=47256) hogy ezeket a fájlokat a normál felhasználók által kért feloldásához.<br /><br />Minden számítógépen, telepítse a beállításjegyzék-beállítást annak megakadályozása, hogy a felhasználók új fájlok védelme beállításával **DisableCreation** a **1**, leírtak szerint [Office beállításjegyzék-beállítások](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
A táblázatban szereplő eljárásokat kapcsolatos további információkért lásd a következőket:

-   Információt AD RMS és a központi telepítési hivatkozik: [Active Directory tartalomvédelmi szolgáltatások – áttekintés](https://technet.microsoft.com/library/hh831364.aspx).

-   Az Azure RMS bérlői kulcs TPD fájlként importálása útmutatásért lásd: [megbízható közzétételi tartomány hozzáadása](https://technet.microsoft.com/library/cc771460.aspx).

-   Az Azure RMS áttelepítés URL-Címének beállítása a Windows PowerShell moduljának telepítése lásd: [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Amikor készen áll a szervezet az Azure RMS szolgáltatás inaktiválása, kövesse az alábbi utasításokat.

## A Rights Management inaktiválásával
Használja az alábbi eljárások egyikét inaktiválása [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Használhatja a Windows PowerShell-parancsmag [letiltása-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), inaktiválása [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Az Office 365 felügyeleti központban a Rights Management inaktiválása

1.  [a munkahelyi vagy iskolai fiókkal jelentkezzen be Office 365](https://portal.office.com/) amely az Office 365-telepítés rendszergazdája.

2.  Ha nem jelennek meg automatikusan az Office 365 felügyeleti központban jelölje ki az alkalmazás indítója ikon bal felső sarkában, majd válassza **Admin**. A **Admin** mozaik csak a rendszergazdák Office 365 jelenik meg.

    > [!TIP]
    > Felügyeleti központ talál segítséget [kapcsolatos az Office 365 felügyeleti központban - rendszergazda súgó](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  A bal oldali panelen bontsa ki a **SZOLGÁLTATÁSBEÁLLÍTÁSOK**.

4.  Kattintson a **Rights Management**.

5.  Az a **RIGHTS MANAGEMENT** lap **kezelése**.

6.  Az a **a rights management** lapján kattintson **inaktiválása**.

7.  Ha a rendszer kéri **szeretné inaktiválni a Rights Management?**, kattintson a **inaktiválása**.

Most látnia **Rights Management nincs aktiválva** és a beállítás aktiválásához.

#### Az Azure portálról Rights Management inaktiválása

1.  Jelentkezzen be a [hagyományos Azure portál](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  Kattintson a bal oldali ablaktáblában **ACTIVE DIRECTORY**.

3.  Az a **az active directory** lap **RIGHTS MANAGEMENT**.

4.  Jelölje ki a könyvtárat, kezelheti a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], kattintson a **INAKTIVÁLJA**, majd erősítse meg a műveletet.

A **RIGHTS MANAGEMENT állapot** most meg kell jelenítenie **Inaktív** és a **INAKTIVÁLJA** beállítás cserélődik **AKTIVÁLÁSA**.

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

