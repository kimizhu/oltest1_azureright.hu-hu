---
description: na
keywords: na
title: Helping Users to Protect Files by Using Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
---
# A felhaszn&#225;l&#243;k f&#225;jlok Azure Rights Management haszn&#225;lat&#225;val seg&#237;ti.
Miután rendszerbe, és a szervezet Azure Rights Management (Azure RMS) konfigurált, adjon meg útmutató és súgó a felhasználók, a rendszergazdák és a segélyszolgálat:

-   **Végfelhasználói információk:**

    Megadása esetén a felhasználók tudja, hogy mikor és hogyan lehet védetté tenni, dokumentumok és a bizalmas információkat tartalmazó e-maileket. Ha lehetséges, adja meg ezeket az adatokat a meglévő munkafolyamatok, hogy a további lépéseket teljesen új folyamatok bemutatása helyett egy már megszokott folyamat is tartalmazza. Ügyeljen arra, hogy a értesítheti előnyeit (és a kockázatok), amelyek az üzleti, valamint amikor azok kell védeni fájlok és az e-maileket útmutatást nyújtó jellemző. Ha a konfigurált [egyéni sablonok](http://technet.microsoft.com/library/dn642472.aspx), válassza ki, ha a sablon nevét és leírását nem elegendő, válassza ki a megfelelő, hogy melyiket kapcsolatos útmutatást.

    > [!TIP]
    > A végfelhasználók számára videók példa:
    > 
    > -   [Azure RMS felhasználói élmény](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Azure RMS-dokumentum követési és visszavonása](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Rendszergazda információk:**

    Egyes alkalmazások automatikusan információk védelme érdekében alkalmazásához használja a házirendek és a rendszergazdák konfiguráló beállításokat tartalmaz. Ezeket az alkalmazásokat előfordulhat, hogy kell más kezelő rendszergazdák számára az alkalmazások és a szolgáltatások útmutatást. További tudnivalókért tekintse meg a [Hogyan alkalmazások támogatják a Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) és [Azure Rights Management alkalmazások konfigurálása](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

-   **Súgó a segélyszolgálati információk:**

    A segélyszolgálat a leghasznosabb eszközök egyik a [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   Súgó a segélyszolgálati operátorok futtatható az Azure RMS-rendszergazda kapcsolóval, és kérhetnek a felhasználók az Azure RMS felhasználói kapcsolóval futtatásához. Ez az eszköz nem csak problémák azonosításához, de is hárítsa el a problémákat, hogy megtalálja, és még nem oldódik meg, ha a rekord nyomkövetési naplók.

    Védett dokumentumok teljes jogosultsággal eléréséhez törvényes kérések esetén, például a jogi részleg vagy egy manager után egy alkalmazott kilépett a szervezet, egy kérelem ellenőrizze, hogy a segélyszolgálat rendelkezik kéréséhez ezt az Azure RMS használatával folyamatok [felügyelő felhasználó funkció](https://technet.microsoft.com/en-us/library/mt147272.aspx).

    Ezenkívül ezek a jellemző problémák, amelyek a jelentés előfordulhat, hogy a felhasználók:

    -   **Bejelentkezés a Súgó:**

        Felhasználók kérheti a hitelesítő adatokat, ha Azure RMS kell hitelesíteni a felhasználót, és nem használhatja a gyorsítótárazott hitelesítő adatokat. Ennek az lehet, a felhasználó munka vagy iskolai fiók és az Office 365 szolgáltatáshoz nevű program vagy az Azure Active Directory-bérlő tartozik társított jelszó. Nem lesz a Microsoft-fiók (korábbi nevén Microsoft Live ID azonosító) vagy a személyes e-mail fiókjába, mivel ezek jelenleg nem támogatottak Azure RMS által. Adja meg a felhasználók és a segélyszolgálat használni, amikor a felhasználók felszólítást kapnak hitelesítő adatok ezek az alkalmazások használata az Azure RMS mely fiókjára vonatkozó utasításokat.

    -   **Problémák védelme vagy a tartalom fel:**

        Győződjön meg arról, hogy a felhasználó rendelkezik a megfelelő utasításokat az alkalmazások, hogy azokat használni, és használ, alkalmazások és eszközök Azure RMS által támogatott. Támogatott alkalmazások és eszközök kapcsolatos további információkért tekintse meg a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md).

        Ha a felhasználók hibaüzenet jelenik meg, közben védelem, vagy a tartalmakat, kérje meg futtatni a [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) Azure RMS felhasználóként.

        Ha a felhasználók jelentést, hogy azok is megnyithatja a védett tartalom, de nem rendelkezik a szükséges jogosultságokkal, kérje meg futtatni a [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) Azure RMS felhasználóként töltse le és a sablonok megtekintéséhez. Ez akkor győződjön meg arról, hogy azok sikeresen letöltött a sablonok, és milyen jogosultságokkal, hogy a sablonok adja meg. Lehet, hogy a probléma, hogy a felhasználó nem szerepel a megfelelő csoport, amely a sablon van beállítva, vagy az, hogy a sablont kell-e a újrakonfigurálásához szükséges, a felhasználó számára.

Az alkalmazás-specifikus adatokat az alábbi szakaszok segítségével a felhasználók bizalmas dokumentumok és az e-maileket védelme.

## A Rights Management megosztóalkalmazás használata a információk védelme
A Rights Management (RMS) megosztó alkalmazás a felhasználók számára védelmét, és helyet igényelne a védett tartalom, ha az Office 2010 használata szükséges, de az összes számítógép és a mobil eszközök, amely támogatja az Azure RMS is ajánlott.

Kívül megkönnyíti a felhasználók fontos dokumentumok, az RMS-megosztó alkalmazás lehetővé teszi, hogy a felhasználók nyomon követheti a dokumentum, amely azokat a védelme, és ha szükséges, visszavonni az őket a hozzáférést.

Az alkalmazás használata a Windows rendszerű számítógép tudnivalókat lásd: a [a Rights Management megosztási alkalmazás felhasználói útmutató](http://technet.microsoft.com/library/dn339006.aspx).

Mobil eszközök, tekintse meg a [gyakran ismételt kérdések a Microsoft Rights Management Mobile platformok megosztó alkalmazás](http://technet.microsoft.com/dn451248).

> [!TIP]
> A magas szintű példa forgatókönyv képernyőképek, tekintse meg a [Az utazó felhasználók biztonságos megosztása mellékletek felhasználók](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_SharingApp) szakasz a [Mi az Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) című témakört.

## Office 365, az Office 2016 vagy az Office 2013 információk védelméről használata
Ha az Azure RMS használ, és nem telepítette a Rights Management megosztóalkalmazás, a felhasználók nem látják a **védett megosztás** gombra a menüszalagon vagy **védelem** megkönnyíti a fájlok védelme, hogy a fájl-Explorer programból. Ezek a felhasználók számára azok ezek hasonló utasításokat kell követnie.

> [!TIP]
> Annak érdekében, hogy az alkalmazás-specifikus Súgó és a vonatkozó információk védelméről használata ezeket az alkalmazásokat utasítások megkereséséhez keressen **IRM** alkalmazás neve és verziója.

#### A dokumentum Word 2013 védelme

1.  Microsoft Word hozzon létre egy új dokumentumot.

2.  A a **fájl** menü kattintson **információ**, kattintson a **dokumentum védelme**, kattintson **hozzáférés korlátozása**, és válassza a sablont gyorsan alkalmazása a megfelelő használati jogok, vagy válassza a **hozzáférés korlátozása** és válassza ki azt a használati jogok, saját maga.

    > [!NOTE]
    > Ha ez a Rights Management használt először, akkor forduljon a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] szolgáltatás, és a rendszer bekéri az Office Tartalomvédelmi ügyfél konfigurálása a hitelesítő adatok.

3.  Mentse a dokumentumot.

Mások megnyitni a dokumentumot, ha azok először hitelesíteni. A dokumentum megnyitása nem engedélyezett, ha a dokumentum nem nyitható meg. Nyissa meg a dokumentumot jogosultak, ha megnyitja a használata korlátozott jogok érvényesek, hogy a felhasználó számára megadott. Például egy felhasználásának jobbra megtekintési, hogy a felhasználó szerkesztése, vagy mentse a dokumentumot, még akkor is, ha először egy másik helyre másolja. A használati jogok korlátozás fejléc használatával a dokumentum tetején jelennek meg. A szalagcím jeleníthet meg az engedélyeket, amelyek a dokumentum, vagy azt előfordulhat, hogy adjon meg egy hivatkozás megjeleníteni azokat.

#### Az Outlook 2013 és az Exchange Online e-mailt védelme

1.  Belül az Outlook hozzon létre egy új üzenetet a címzett a szervezeten belül intézett.

2.  Az a **Beállítások** fülre, kattintson a **engedély**, majd válassza ki a beállítást. Példa: **Nem továbbít**, **&lt; cég neve &gt; - bizalmas** vagy **&lt; cég neve &gt; – csak a bizalmas nézet**.

3.  Az üzenet elküldése.

Hasonló módon a védett dokumentum megjelenítése, ha az e-mail üzenetet kapja meg a címzett először hitelesítik. Jogosultak az e-mail üzenet jelenik meg, ha megnyitja a használata korlátozott jogok érvényesek, hogy a felhasználó számára megadott. Ha például a kiválasztott **nem továbbítandó**, az előre gomb a menüszalagon nem érhető el.

#### Az Outlook Web alkalmazással e-mail üzenet védelme

1.  Az Outlook Web alkalmazásban hozzon létre egy új levelek intézett egy címzett a szervezeten belül.

2.  Kattintson a  **...**,  kattintson a **engedélyek beállítása**, majd válassza ki a beállítást. Példa: **Nem továbbít**, **ne válaszoljon az összes**, **&lt; cég neve &gt; - bizalmas** vagy **&lt; cég neve &gt; – csak a bizalmas nézet**.

3.  Az üzenet elküldése.

Hasonló módon a védett dokumentum megjelenítése, ha az e-mail üzenetet kapja meg a címzett először hitelesítik. Jogosultak az e-mail üzenet jelenik meg, ha megnyitja a használata korlátozott jogok érvényesek, hogy a felhasználó számára megadott. Például, ha a kiválasztott **el nem válasz mindenkinek**, a **Válasz mindenkinek** az üzenet ablakában lehetőség nem érhető el.

## Lásd még
[Azure Rights Management használata](../Topic/Using_Azure_Rights_Management.md)

