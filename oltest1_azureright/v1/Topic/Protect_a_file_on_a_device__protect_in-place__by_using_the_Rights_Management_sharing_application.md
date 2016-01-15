---
description: na
keywords: na
title: Protect a file on a device (protect in-place) by using the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33920329-5247-4f6c-8651-6227afb4a1fa
---
# Az eszk&#246;z&#246;n a f&#225;jl v&#233;delme (helyi v&#233;delem) a Rights Management megoszt&#243;alkalmaz&#225;s haszn&#225;lat&#225;val
Ha a fájl helyben, felülírja az eredeti, nem védett fájlt. Hagyja a fájlt, amennyiben, másolja azt egy másik mappába vagy eszköz, vagy a mappát, hogy van, és marad, hogy a fájl védett megosztás. Ön sikerült is csatolhat a védett fájlt egy e-mailt, bár az ajánlott lehet osztani a védett fájl e-mailek módja közvetlenül a fájl Explorer vagy az Office alkalmazás (lásd [A Rights Management megosztóalkalmazás használatával e-mail megosztott fájl védelme](../Topic/Protect_a_file_that_you_share_by_email_by_using_the_Rights_Management_sharing_application.md)).

> [!TIP]
> Ha a fájlok védelme hibákat jelennek, olvassa el [gyakran ismételt kérdések a Microsoft Rights Management megosztó alkalmazás for Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

## Az adott eszközön fájl védelme (helyi védelem)

1.  A fájl Intéző válassza ki a egy fájlt lehet védetté tenni. Kattintson a jobb gombbal, válassza **védelme az RMS**, majd válassza ki **védelem**. Példa:

    ![](../Image/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Ha nem látja a **védelme az RMS** lehetőséget, valószínű, hogy az RMS-megosztó alkalmazás nincs telepítve a számítógépen, vagy a telepítés befejezéséhez újra kell indítani a számítógépet. Az RMS-megosztó alkalmazás telepítésével kapcsolatos további tudnivalókért tekintse meg a [Töltse le és telepítse a Rights Management megosztóalkalmazás](../Topic/Download_and_install_the_Rights_Management_sharing_application.md).

2.  A következők közül:

    -   Válasszon ki egy csoportházirend-sablon: Ezek az előre meghatározott engedélyeket, amelyek a hozzáférési és használati általában korlátozhatják a szervezet számára. Például, ha a szervezet neve "Contoso, Ltd", előfordulhat, hogy látható **Contoso, Ltd. - csak bizalmas nézet**. Ha ez az első alkalommal védelme a fájl ezen a számítógépen, először válassza ki a **vállalat által megadott engedélyek** a sablonok letöltéséhez.

        Amikor legközelebb rákattint a **védelem** lehetőséget, látni fogja, válassza a legfeljebb 10 sablonok. Ha nincsenek elérhető legfeljebb 10 sablonokat, és a kívánt nem jelenik meg, kattintson a **vállalat által megadott engedélyek** letöltése, és tekintse meg az összes sablon.

        Amikor kiválaszt egy csoportházirend-sablon, védhető több fájl, és egy mappát. Amikor kiválaszt egy mappát, az összes adott mappában lévő fájlok automatikusan kijelölt védelmi, de abban a mappában létrehozott új fájlok nem lesz automatikusan védett.

    -   Válasszon **egyéni engedélyek**: Válassza ezt a lehetőséget, ha a sablonok nem a védelmet nyújtanak, amely van szüksége, vagy explicit módon adja meg a védelmi beállításokat saját maga kívánja. Adja meg a beállításokat, ezt a fájlt a kívánt a [hozzáadása párbeszédpanel védelmi](http://technet.microsoft.com/library/dn574738.aspx), és kattintson a **Alkalmaz**.

3.  Előfordulhat, hogy gyorsan lásd a egy párbeszédpanel, annak megállapítása, hogy a fájl védelmét, és az aktuális fájl Explorer adja vissza. A kijelölt fájlt vagy fájlokat most már védett. Bizonyos esetekben (ha hozzáadása védelmi változik meg a fájl kiterjesztése) fájl Explorer az eredeti fájlt lecserél egy új fájlt, amelynek a Rights Management protection zárolás ikonra. Példa:

    ![](../Image/ADRMS_MSRMSApp_Pfile.png)

Ha később kell eltávolítani a fájl védelmét, tekintse meg a [A Rights Management megosztóalkalmazás használatával egy fájl védelmének megszüntetése](../Topic/Remove_protection_from_a_file_by_using_the_Rights_Management_sharing_application.md).

## Példák és más utasítások
Előfordulhat, hogy hogyan használhatja a Rights Management megosztó alkalmazás- és útmutató utasításokat a, tekintse meg az alábbi szakaszok a Rights Management megosztási alkalmazás felhasználói útmutató:

-   [Példák az RMS-megosztó alkalmazás használatával](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Választható?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Lásd még
[A Rights Management megosztási alkalmazás felhasználói útmutató](../Topic/Rights_Management_sharing_application_user_guide.md)

