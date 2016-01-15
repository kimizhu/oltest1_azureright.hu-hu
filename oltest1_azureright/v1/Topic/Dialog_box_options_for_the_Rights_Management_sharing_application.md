---
description: na
keywords: na
title: Dialog box options for the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
---
# A Rights Management megoszt&#243;alkalmaz&#225;s p&#225;rbesz&#233;dpanel be&#225;ll&#237;t&#225;sai
Ezt az információt segítségével, akkor adja meg a beállításokat az RMS-megosztó alkalmazás a **védelem hozzáadása** párbeszédpanel vagy a **védett megosztás** párbeszédpanel megnyitásához. Látni fogja az ezen a párbeszédpanelen mezőben, ha Ön [osztani egy fájl védelme](http://technet.microsoft.com/library/dn574735.aspx) vagy [helyen egy fájl védelme](http://technet.microsoft.com/library/dn574733.aspx) és válassza az egyéni engedélyek.

> [!IMPORTANT]
> Ha a beállításokat lát eltérnek a itt dokumentált, valószínűleg nem rendelkezik telepített megosztási alkalmazás legújabb verzióját. Letöltheti a legújabb verzióját a [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) oldalon.
> 
> Honnan meg, hogy van-e a legújabb verzióra? Keressen **a Microsoft Rights Management megosztóalkalmazás** felsorolt programok és szolgáltatások, és tekintse meg a megfelelő verziószám. Tekintse meg, és a beállítások a táblázatban, a verzióját kell legalább **1.0.1770.0**. Ellenőrizheti, hogy a legújabb verziója szám a letöltési lapra.

A választható lehetőségek, kívül is felmerülhet:

-   [Mi az automatikusan létrehozott .ppdf fájlhoz?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)

-   [Mi az általános védelmi és beépített (natív) protection közötti különbség?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative)

|A beállítás|Leírása|
|---------------|-----------|
|**A FELHASZNÁLÓK**|Ha még nem már megadott Outlook e-mail cím, írja be a lehet megnyitni a fájlt kívánt személyek e-mail címét.<br /><br />A szervezet a Rights Management (AD RMS) helyszíni verzióját használja, ha az Itt adhatja meg az e-mail címekre csak a szervezeten belüli személyek. Ha ez vonatkozik, és próbálja beállítani a külső e-mail cím, a vállalati konfiguráció lehetővé teszi, hogy a védett tartalom csak a vállalaton belüli megosztását értesítő üzenet jelenik meg. Azonban ha a szervezet Azure RMS használ, ezekre az e-mail címekre lehet a szervezeten belüli személyek, vagy egy másik szervezet tagjai.<br /><br />Például: janetm@contoso.com; p.dover@Fabrikam.com|
|**Általános védelmi**|Ha ezt a lehetőséget választja, az azt jelenti, hogy a kiválasztott fájl nem lehet natív módon védetté tenni. További tudnivalókért tekintse meg. [Mi az általános védelmi és beépített (natív) protection közötti különbség?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative) a jelen témakörben található.|
|**Viewer – csak a nézet**<br /><br />**Felülvizsgáló – megtekintése és szerkesztése**<br /><br />**Társ Szerző – nézet, a Szerkesztés, a másolás és a nyomtatás**<br /><br />**Társ tulajdonos – minden engedély** **Note:** Ezekkel a beállításokkal rendelkezik a előtt a nevét, a kerekítés ikon képviselt egy globális földgolyó méretét. Az ikon szolgál, mert általában valamelyikét választja ki ezeket a beállításokat a melléklet, hogy valaki egy másik szervezet küldésekor.|Válassza ki az alábbi lehetőségek egyikét, ha azt szeretné, hogy a jogok a védett dokumentum meghatározásához. Kattintson az egyes beállítások megtekintéséhez leírását.<br /><br />Ha úgy dönt, az alábbi lehetőségek egyikét, csak a felhasználók megadott **felhasználók** a megfelelő engedélyekkel rendelkezik adja meg, ha megnyitása és használata a dokumentumot. Például ha azok továbbítani valaki másnak, a dokumentum nem nyitja meg.|
|Házirend-sablonok, amely a rendszergazda konfigurálja.<br /><br />Ha például a vállalat nevét a Contoso, Ltd.: **Contoso, Ltd. - csak a bizalmas megtekintése** **Note:** Ezek a beállítások egy office felépítése határoz meg, amely a nevet, mielőtt egy szögletes ikon rendelkezik. Erre az ikonra használatos, mert általában valamelyikét választja ki ezeket a beállításokat a melléklet, hogy valaki a szervezet küldésekor.|Ha dokumentumot oszt működik, akik a szervezetben, tekintse meg az elérhető sablonok, amely a rendszergazda konfigurálja. Válassza ki az egyik ezek a dokumentum nem lehet megosztott saját szervezetén kívül.<br /><br />Ha úgy dönt, az alábbi lehetőségek egyikét, a rendszergazda határozza meg a jogok a dokumentum, és azt, aki megnyitható.|
|**Ezeket a dokumentumokat lejárati dátuma**|Jelölje be ezt a lehetőséget csak időérzékeny fájlok, amelyek a kiválasztott felhasználók nem kell egy Ön által megadott dátum után nyissa meg. Továbbra is fogja tudni megnyitni az eredeti fájlt, de éjfél (a jelenlegi időzóna), a megadott napon, után mások nem tudják megnyitni a fájlt.<br /><br />Ez a lehetőség nem érhető el, ha egy csoportházirend-sablon, amely a rendszergazda konfigurálja.|
|**E-mailt, ha valaki megpróbálja megnyitni ezeket a dokumentumokat**|**Note:** Ez a beállítás előzetes használatban van.<br />Válassza ezt a lehetőséget, ha azt szeretné, hogy e-mailek Ha értesítést szeretne kapni valaki megpróbálja megnyitni a dokumentumot, amit a védelme. Az e-mailt jelezni fogja, akik próbált megnyitni, amikor, és hogy sikeres volt-e azokat.<br /><br />Ez a beállítás csak akkor, ha a szervezet használ az Azure RMS érhető el. Ha a szervezet a Rights Management (AD RMS) helyszíni verzióját használja, ezt a beállítást nem jelenik meg.|
|**Nekem azonnal visszavonni az ezeket a dokumentumokat való hozzáférés engedélyezése**|Válassza ezt a lehetőséget, ha lehetséges, hogy a dokumentum nyomon követése a webhely használatával később visszavonni a hozzáférést a dokumentumok kell, és a visszavont tanúsítványok a következőre azonnal érvénybe lépnek. Azonban beállítás Ez a beállítás azt jelenti, amíg a dokumentum nem vonták vissza, a felhasználók mindig internetkapcsolat szükséges olvasni a dokumentumot, minden alkalommal, azok-e férni. Előfordulhat, hogy bizonyos esetekben, ahol a felhasználók nem tud kapcsolódni az eszközt az internethez, és felhasználók nem tudja olvasni a dokumentum megfelelően.<br /><br />Válassza ezt a lehetőséget, ha továbbra is vonhatja a dokumentumok később, a dokumentum követési webhely használatával. Azonban a felhasználók nem mindig kell az internetkapcsolatot a dokumentum olvasásakor, mert nem tudják azonnal, hogy a dokumentum visszavonva, és olvassa el, amíg a következő hitelesítéshez az Azure RMS továbbra is. Alapértelmezés szerint, hogy valaki továbbra is olvasható egy védett dokumentum, amely már a visszavont napok maximális száma 30 nap, de a rendszergazda módosíthatja ezt az értéket kevesebb vagy 30 nap-nál nagyobbnak kell lennie.<br /><br />Ez a beállítás csak akkor, ha a szervezet használ az Azure RMS érhető el. Ha a szervezet a Rights Management (AD RMS) helyszíni verzióját használja, ezt a beállítást nem jelenik meg.|

## <a name="BKMK_GenericNative"></a>Mi az általános védelmi és beépített (natív) protection közötti különbség?

-   Ha Ön **általánosságban a fájl védelmét**, a fájl nem nyitható meg a jogosulatlan személyek. De után a hitelesített felhasználók nyissa meg a fájlt, azok sikerült majd továbbítja másoknak nem védett, vagy menti, amely mások hozzáférhet helyen. Azok, azonban egy üzenet jelenik meg, amely meghatározza, milyen jogosultságokkal rendelkeznek a fájlt, és ezek tiszteletben kell, de a védelem nem kényszeríthető. Általánosságban a fájl védelmét, amikor ezen kívül nem az engedélyek engedélyezési további korlátozhatják. Például a tartalom nem korlátozhatják a csak a nézet a, vagy nem a nyomtatás.:

    > [!NOTE]
    > Általánosságban a védett fájl mindig van egy fájlnévkiterjesztést, **.pfile**.

-   Az összehasonlítás, használatakor a **beépített (natív) védelmi** Rights Management alkalmazásokkal, amely támogatja ezt a (például az Office-fájlok), a védelem vonatkozik a fájl még akkor is, ha a fájlt a rendszer elküldi a valaki más vagy egy másik helyre mentett. És abban az esetben, ha ezek a fájlok, korlátozó engedélyeket használhatja például az csak olvasható, vagy az engedély szerkesztése, de nem nyomtatás, vagy másolja. Válassza ki például **Viewer – csak a nézet**, így a tartalom nem szerkeszthető, nyomtató, vagy másolja.

További technikai tudnivalókért tekintse meg a [Védelmi – natív és általános szintek](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) szakasz a [A Rights Management megosztási alkalmazás rendszergazda guide](../Topic/Rights_Management_sharing_application_administrator_guide.md).

## <a name="BKMK_PPDF"></a>Mi az automatikusan létrehozott .ppdf fájlhoz?

-   Védett fájl e-mailek (a védett megosztás) által közösen használja, ha az RMS-megosztó az alkalmazás automatikusan létrehoz egy **.ppdf** verziója, a Word, az Excel, a PowerPoint vagy a PDF-fájl. Ez az, hogy egy csak olvasható védett fájl verzióját, amely csak a hitelesített felhasználók is megnyithatja, és biztosítja, hogy a címzett mindig tudja olvasni a melléklet, még akkor is, ha a mobil eszköz, amely nem tartalmaz, amely natív módon támogatja a Rights Management alkalmazás használnak. Ezek a felhasználók az RMS-megosztó alkalmazás telepítve van, nyújtó azokat nem fogja tudni olvasni azokat a melléklet.

    Ebben az esetben eltérően általánosságban a védett fájl, a használat korlátozással. A címzett nem fogja tudni menteni a fájlt a jelen verziójában, és továbbítja azokat a melléklet, hogy valaki másnak, ha az eredeti korlátozások marad, a dokumentumot. Lesz, hogy csak azok a felhasználók, hogy a védett dokumentum volt hitelesített megnyitható.

    > [!NOTE]
    > .Ppdf fájl automatikusan jön létre, ha megosztani a védett (megosztás által e-mailek), de nem jön létre, ha az Ön helyi védelem.

## Példák és más utasítások
Előfordulhat, hogy hogyan használhatja a Rights Management megosztó alkalmazás- és útmutató utasításokat a, tekintse meg az alábbi szakaszok a Rights Management megosztási alkalmazás felhasználói útmutató:

-   [Példák az RMS-megosztó alkalmazás használatával](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Választható?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Lásd még
[A Rights Management megosztási alkalmazás felhasználói útmutató](../Topic/Rights_Management_sharing_application_user_guide.md)

