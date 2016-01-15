---
description: na
keywords: na
title: View and use files that have been protected by Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5fa4666-6906-405a-9e0c-2c52d4cd27c8
---
# Megtekint&#233;se &#233;s haszn&#225;lata a Rights Management v&#233;dett f&#225;jlok
Ha a [a számítógépen telepítve van a Rights Management (RMS) megosztóalkalmazás](https://technet.microsoft.com/library/dn574734%28v=ws.10%29.aspx), egyszerűen dupla kattintással megtekintheti a védett fájl. Lehet, hogy a fájl egy e-mailt a mellékletet, vagy a fájl Explorer használatakor megjelenhet.

> [!NOTE]
> Megtekintheti, hogy a védett fájlt, mielőtt RMS kell először győződjön meg arról, hogy Ön jogosult a fájl, amely hajtja végre a felhasználónév és jelszó bejelölésével megtekintése. Egyes esetekben ez lehetséges, hogy kerülnek a gyorsítótárba, és nem jelenik meg a kérdés, hogy a hitelesítő adatokat kér. Egyéb esetben bekéri a hitelesítő adatok megadására.
> 
> Ha a szervezet nem használja, vagy az Azure Rights Management (Azure RMS), vagy az Active Directory tartalomvédelmi szolgáltatások, egy ingyenes fiókra, amely a hitelesítő adatait fogadja el, így úgy is megnyithatja, amelyek segítségével az RMS által védett fájlokat jelentkezhet:
> 
> -   Alkalmazása ehhez a fiókhoz, kattintson a hivatkozásra, jelentkezhet [egyének az RMS](http://go.microsoft.com/fwlink/?LinkId=309469).
> 
>     Hozza létre, ha egy személyes e-mail cím helyett a vállalati e-mail címét használja. Ha most jelentkezik, mert azt egy védett melléklet el lett küldve, használja ugyanazt az e-mail címet, használt e-mail üzenetet küldeni.
> -   További tudnivalókért tekintse meg a [RMS egyének és a Windows Azure Rights Management](http://technet.microsoft.com/library/dn592127.aspx).

## <a name="BKMK_ViewPFILE"></a>Védett fájl megtekintése
Fájl Intéző vagy a melléklet tartalmazó e-mail üzenetet segítségével, kattintson duplán a védett fájlt, és adja meg a hitelesítő adatait, ha a kéri.

Ha a fájl, de különböző kiterjesztésű két verzió jelenik meg, nyissa meg a kiterjesztésű fájl egy .ppdf fájl csak akkor, ha a másik fájl nem nyitható meg. A .ppdf verziója nem nyitható meg vagy, ha először telepíteni a [RMS-megosztó alkalmazás](http://technet.microsoft.com/library/dn574734.aspx), amely tudja, amelyek egy .ppdf kiterjesztésű fájlok megnyitását.

> [!NOTE]
> További tudnivalókért tekintse meg a "[Mi az automatikusan létrehozott .ppdf fájlhoz?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)".

Hogyan a fájl megnyitása attól függ, hogy hogyan azt védett, amely megadható, hogy a fájl kiterjesztése megtekintésével. Minden esetben a fájl megnyitásakor előfordulhat, hogy naplózni, és mindaddig, amíg védett ellenőrzött marad. Ezenkívül a fájl e-mail mellékletként lett elküldve, ha a küldő előfordulhat, hogy értesítést által e-mailt a fájl megnyitásakor.

|Fájlnévkiterjesztést, és a védelem|További információ|
|--------------------------------------|----------------------|
|A fájl egy **.pfile** a fájl kiterjesztése.<br /><br />A fájl általánosságban védett.|A fájl megnyitásakor, ha azt látja, hogy egy **védett fájl** párbeszédpanel, amely bemutatja, akik védett, hogy a fájlt, és tartsa tiszteletben az együttes tulajdonos engedélyeket megosztási alkalmazásból. Kattintson a **megnyitása** olvasni a fájlt.<br /><br />![](../Image/ADRMS_MSRMSApp_PfilePermission.png)|
|A fájl egy **.ppdf** kiterjesztés, vagy a szöveg vagy kép védett fájl (például **.ptxt** vagy **.pjpg**).<br /><br />A fájl natív módon védett csak olvasható másolata.|A fájl megnyitása a megjelenítő, amely telepíti az RMS-megosztó alkalmazás használatával. Ez a fájl csak olvasható, még akkor is, ha egy másik helyre menti, vagy nevezze át.|
|Más kiterjesztésű fájlokat.<br /><br />A fájl védett natív módon.|A fájl megnyitása az eredeti fájlnévkiterjesztést társított alkalmazás használatával, és a korlátozás szalagcím akkor jelenik meg, a fájl tetején. A szalagcím jeleníthet meg az engedélyeket, amelyek a fájlt, vagy azt előfordulhat, hogy adjon meg egy hivatkozás megjeleníteni azokat. Például előfordulhat, hogy megjelenik a következő ahol kell kattintania **engedély jelenleg korlátozva** megtekintheti a tényleges engedélyeket, amelyek a fájlt, és a mások által elérhető:<br /><br />![](../Image/ADRMS_MSRMSApp_RestrictedAccess.png)|
Kiterjesztések, amely támogatja a Rights Management teljes listáját lásd a [Támogatott fájltípusok és kiterjesztések](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes) területén, a  [A Rights Management megosztási alkalmazás rendszergazda guide](../Topic/Rights_Management_sharing_application_administrator_guide.md). A fájlnévkiterjesztés nem szerepel a listában, ha a webes keresés segítségével tekintse meg, ha-e a fájlnév kiterjesztését, amely egy másik alkalmazás által támogatott.

> [!NOTE]
> Ha a letöltés után erősítse meg, hogy a fájl a Rights Management által védett, és a fájl nem nyitható meg, és használja a [RMS Analyzer eszközt](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Kövesse a megjelenő utasításokat az eszköz tekintse meg a problémákat a számítógépen, amely megakadályozza a védett dokumentum megnyitása.

## <a name="BKMK_UserDefined"></a>Használatára, amely (például a Szerkesztés és a Nyomtatás a fájl) a védett fájlok
Ha a védett fájl megnyitása után nem csak olvasható kívánt (például szerkesztése, másolása és nyomtatás):

|Fájlnévkiterjesztést|Utasítások|
|------------------------|--------------|
|A fájl egy **.pfile** a fájl kiterjesztése.|A megnyitott fájl mentéséhez, és adjon egy új fájlnévkiterjesztést, amely nincs társítva a használni kívánt alkalmazáshoz.<br /><br />Például a fájl segítségével, hogy a fájl neve document.vsdx.pfile védett, ha a fájl megtekintése, és a fájl Intéző, mentse a fájlt document.vsdx.<br /><br />Az új fájl már nem védett. Ha azt szeretné, hogy lássa el védelemmel, kézzel kell ehhez. További tudnivalókért tekintse meg a [Az eszközön a fájl védelme &#40;helyi védelem&#41; a Rights Management megosztóalkalmazás használatával](../Topic/Protect_a_file_on_a_device__protect_in-place__by_using_the_Rights_Management_sharing_application.md).|
|A fájl egy **.ppdf** kiterjesztés, vagy a szöveg vagy kép védett fájl (például **.ptxt** vagy **.pjpg**).|Csak megtekinteni tudja a fájlt, és ha átnevezése vagy áthelyezhető, a védelmi marad, a fájl.|
|Más kiterjesztésű fájlokat.|Az eszköz olyan alkalmazást, amely használja ezeket a fájlokat a Rights Management megértette kell rendelkeznie. Ezek az alkalmazások nevezzük az RMS-enlightened alkalmazások. Példák az alkalmazásokat Office 2016, az Office 2013 és az Office 2010 (például a Word, Excel, PowerPoint és az Outlook) alkalmazások, amelyek a Rights Management vannak enlightened. De a Rights Management is előfordulhat, hogy alkalmazások, amelyek nem a Microsofttól származik, például a szoftver vállalatokat és a saját üzleti sor alkalmazások enlightened.<br /><br />Alkalmazások, amelyek a Rights Management ismernie a fájl megnyitását, amely más Rights Management által védett vannak-e enlightened enlightened alkalmazások. Azok a alkalmazott őket, még akkor is, ha a fájl szerkesztése, vagy egy másik fájlnevet, vagy egy másik helyre menti a védelmi is megmarad. Ezek az alkalmazások lehetővé teszik, hogy a fájlt, az engedélyek, amelyek jelenleg a fájl alapján használja, úgy, hogy ha a fájl engedélyeit, ehhez. Előfordulhat például, szerkessze a fájlt, de nyomtatni nem tud.|

## Példák és más utasítások
Előfordulhat, hogy hogyan használhatja a Rights Management megosztó alkalmazás- és útmutató utasításokat a, tekintse meg az alábbi szakaszok a Rights Management megosztási alkalmazás felhasználói útmutató:

-   [Példák az RMS-megosztó alkalmazás használatával](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Választható?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Lásd még
[A Rights Management megosztási alkalmazás felhasználói útmutató](../Topic/Rights_Management_sharing_application_user_guide.md)

