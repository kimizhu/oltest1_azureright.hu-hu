---
description: na
keywords: na
title: Configuring Usage Rights for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
---
# Haszn&#225;lati jogok konfigur&#225;l&#225;sa az Azure Rights Management
Védelem a fájlokat, vagy az e-maileket Azure Rights Management (Azure RMS) használatával és nem használhatja a sablont, konfigurálnia kell a használati jogok saját maga. Ezenkívül az Azure RMS egyéni sablonok konfigurálásakor választhat a használati jogok, a rendszer ezután automatikusan alkalmazza a sablon a felhasználók, a rendszergazdák által kiválasztásakor, vagy a szolgáltatások konfigurált. Például az Azure portál közül választhat szerepkörökbe, konfigurálja a használati jogok logikai csoportja, vagy úgy is konfigurálhatja a egyéni jogait.

Ez a témakör segítségével konfigurálja a használati jogok azt szeretné, hogy az alkalmazás használata, és megtudja, hogyan ezeknek a jogosultságoknak alkalmazások értelmezi.

## Használati jogok és leírása
A következő táblázat felsorolja és ismerteti a használati jogok, amely támogatja a Rights Management, és hogyan vannak használt, és úgy értelmezhető. Ebben a táblázatban a **köznapi név** általában van, előfordulhat, hogy hogyan megtekintheti a használat jobbra jelenik meg, vagy a hivatkozott, mint egy több felhasználóbarát egyszavas érték, amely a kódot a használt verziója (a **házirendjében kódolás** érték). A **API állandó vagy érték** MSIPC API-hívásban, használja az RMS-enlightened alkalmazás, amely a jobb oldali használatát, vagy a használat jobbra házirendet ad hozzá írásakor SDK neve.

|Köznapi név|A házirend-kódoláshoz|Leírása|Az Office egyéni jogok végrehajtása|Az Azure portál neve|Active Directory tartalomvédelmi szolgáltatások sablon neve|API állandó vagy érték|További információk|
|---------------|-------------------------|-----------|---------------------------------------|------------------------|---------------------------------------------------------------|--------------------------|-----------------------|
|Szerkesztés tartalom szerkesztése|DOCEDIT|Lehetővé teszi a felhasználó módosításához átrendezése, formázása vagy szűrje a tartalmat, az alkalmazás belül. Nem biztosít a jogot arra, hogy a mentse a módosított példányt.|Részeként a **módosítása** és **teljes hozzáférés** beállítások.|**Tartalom szerkesztése**|**Szerkesztése**|Nem alkalmazható|Az Office alkalmazások a jobb oldali is lehetővé teszi a felhasználó menteni a dokumentumot.|
|Mentés|SZERKESZTÉSE|Lehetővé teszi a felhasználó számára, hogy a dokumentum mentése a jelenlegi helyéről.|Részeként a **módosítása** és **teljes hozzáférés** beállítások.|**Fájl mentése**|**Mentés**|IPC_GENERIC_WRITEL "SZERKESZTÉS"|Az Office alkalmazások a jobb oldali is lehetővé teszi a felhasználó a dokumentum módosításához.|
|Megjegyzés|MEGJEGYZÉS|Lehetővé teszi, hogy a széljegyzeteket, vagy a Megjegyzések hozzáadása a tartalom lehetőséget.|Nincs megvalósítva|Nincs megvalósítva|Nincs megvalósítva|IPC_GENERIC_COMMENTL "MEGJEGYZÉS"|A jobb oldali érhető el a SDK érhető el, mint egy alkalmi házirend az RMS-védelmi modul a Windows PowerShell és néhány szoftver gyártójától alkalmazás valósított. Azonban nem széles körben használja, és Office alkalmazások által jelenleg nem támogatott.|
|Mentés másként exportálása|EXPORTÁLÁSA|Lehetővé teszi, hogy a tartalom mentéséhez egy másik fájl nevét (Mentés másként) lehetőséget. Attól függően, hogy az alkalmazást a fájl előfordulhat, hogy menti a védelem nélkül.|Részeként a **módosítása** és **teljes hozzáférés** beállítások.|**Tartalom (Mentés másként) exportálása**|**Exportálás (Mentés másként)**|IPC_GENERIC_EXPORTL "EXPORT"|A jobb oldali is lehetővé teszi, hogy a felhasználó végrehajtásához más exportálási beállítások az alkalmazások, például az **küld a OneNote**.|
|Előre|ELŐRE|Lehetővé teszi, hogy a lehetőséget, e-mail üzenetet továbbít, és a hozzá címzetteket, hogy a **a** és **másolat** sorokat.|A rendszer megtagadta a használata esetén a **nem továbbítandó** normál házirend.|**Előre**|**Előre**|"ELŐRE" IPC_EMAIL_FORWARDL.|A továbbító való továbbítani részeként más felhasználók jogot nem teszi lehetővé.|
|Teljes hozzáférés|TULAJDONOS|A dokumentum összes jogokat, és az összes elérhető műveletek végezhetők.|Mint a **teljes hozzáférés** egyéni lehetőséget.|**Teljes hozzáférés**|**Teljes hozzáférés**|IPC_GENERIC_ALLL "TULAJDONOS"|A segítségnyújtó lehet eltávolítani a védelmet.|
|Nyomtatás|NYOMTATÁS|Lehetővé teszi, hogy a beállítások, a tartalom nyomtatása.|Mint a **nyomtatási tartalom** az egyéni engedélyek lehetőséget. Címzett-beállítás.|**Nyomtatás**|**Nyomtatás**|IPC_GENERIC_PRINTL "NYOMTATÁS|Nincs további információ|
|Válasz|VÁLASZ|Lehetővé teszi, hogy a válasz egy e-mail ügyfél parancsa a módosításokat a **a** vagy **másolat** sorokat.|Nem alkalmazható|**Válasz**|**Válasz**|IPC_EMAIL_REPLY|Nincs további információ|
|Válasz mindenkinek|REPLYALL|Lehetővé teszi, hogy a **Válasz mindenkinek** beállítás az e-mailek Client, de a felhasználó hozzáadása a címzett nem teszi lehetővé a **a** vagy **másolat** sorok.|Nem alkalmazható|**Válasz mindenkinek**|**Válasz mindenkinek**|IPC_EMAIL_REPLYALLL "REPLYALL"|Nincs további információ|
|A nézet, a Megnyitás, Olvasás|A NÉZET|Lehetővé teszi, hogy a felhasználó, nyissa meg a dokumentumot, és tekintse meg a tartalmat.|Mint a **olvasható** egyéni házirend, **Nézet** lehetőséget.|**Tartalom megtekintése**|**A nézet**|IPC_GENERIC_READL "NÉZET"|Nincs további információ|
|Másolás|KIVONAT|Lehetővé teszi, hogy a beállítások adatok másolása a dokumentum ugyanabba vagy egy másik dokumentumot.|Mint a **olvasási hozzáféréssel rendelkező felhasználók másolása a tartalom engedélyezése** egyéni házirend-beállítást.|**Másolás és az Extract tartalom**|**Kivonat**|IPC_GENERIC_EXTRACTL "KIVONAT"|Az egyes alkalmazások is lehetővé teszi a teljes dokumentum nem védett formában kell menteni.|
|Jogok megtekintése|VIEWRIGHTSDATA|Lehetővé teszi a felhasználó számára, hogy a dokumentum alkalmazza a házirend.|Nincs megvalósítva|**Hozzárendelt jogok megtekintése**|**Jogok megtekintése**|IPC_READ_RIGHTSL "VIEWRIGHTSDATA"|Egyes alkalmazások figyelmen kívül hagyja.|
|Jogok módosítása|EDITRIGHTSDATA|Lehetővé teszi a felhasználó módosíthatja a házirend, amelyre a dokumentum vonatkozik. Tartalmaz, beleértve a védelem eltávolítása.|Nincs megvalósítva|**Jogok módosítása**|**Jogok szerkesztése**|IPC_WRITE_RIGHTSL "EDITRIGHTSDATA"|Nincs további információ|
|Lehetővé teszi makrók|OBJMODEL|Lehetővé teszi, hogy a makrók futtatásához, vagy más programozott vagy a távoli hozzáférést a tartalomhoz végrehajtására a dokumentum lehetőséget.|Mint a **programozott hozzáférés engedélyezése** egyéni házirend-beállítást. Címzett-beállítás.|**Lehetővé teszi makrók**|**Lehetővé teszi makrók**|Nem alkalmazható|Nincs további információ|

## Engedélyek szintek jogok
Egyes alkalmazások csoportba a használati jogok történő engedélyek szintek, így könnyebb válassza ki a használati jogok jellemzően használt együtt. Ezek a permisisons szintek súgó a felhasználóktól, összetettségét szintű absztrakt, így azok, válassza a beállítások, amelyek a szerepkör-alapú.  Például **felülvizsgáló** és **együttes Szerző**. Bár ezek a beállítások a jogok összefoglalása gyakran megjelenítése a felhasználók, előfordulhat, hogy nem tartoznak minden jobb, amely szerepel az előző táblázatban.

Használja az alábbi táblázat ezek engedélyek szintek listáját, és a bennük jogok teljes listáját.

|Engedélyek szintje|Alkalmazások|Jogok (köznapi név)|
|----------------------|----------------|-----------------------|
|Viewer|Azure portál<br /><br />Rights Management megosztóalkalmazás Windows|A nézet, a Megnyitás, Olvasás<br /><br />Válasz<br /><br />Válasz mindenkinek|
|Felülvizsgáló|Azure portál<br /><br />Rights Management megosztóalkalmazás Windows|A nézet, a Megnyitás, Olvasás<br /><br />Mentés<br /><br />Szerkesztés tartalom szerkesztése<br /><br />Reply<sup>*</sup><br /><br />Válasz mindenkinek<sup>*</sup><br /><br />Előre<sup>*</sup>|
|Társ Szerző|Azure portál<br /><br />Rights Management megosztóalkalmazás Windows|A nézet, a Megnyitás, Olvasás<br /><br />Mentés<br /><br />Szerkesztés tartalom szerkesztése<br /><br />Másolás<br /><br />Jogok megtekintése<br /><br />Jogok módosítása<br /><br />Lehetővé teszi makrók<br /><br />Mentés másként exportálása<br /><br />Nyomtatás<br /><br />Reply<sup>*</sup><br /><br />Válasz mindenkinek<sup>*</sup><br /><br />Előre<sup>*</sup>|
|Társ-tulajdonos|Azure portál<br /><br />Rights Management megosztóalkalmazás Windows|A nézet, a Megnyitás, Olvasás<br /><br />Mentés<br /><br />Szerkesztés tartalom szerkesztése<br /><br />Másolás<br /><br />Jogok megtekintése<br /><br />Jogok módosítása<br /><br />Lehetővé teszi makrók<br /><br />Mentés másként exportálása<br /><br />Nyomtatás<br /><br />Reply<sup>*</sup><br /><br />Válasz mindenkinek<sup>*</sup><br /><br />Előre<sup>*</sup><br /><br />Teljes hozzáférés|
<sup>*</sup> Nem alkalmazható a Rights Management megosztóalkalmazás Windows

## Az alapértelmezett sablonokat jogok
Az alapértelmezett sablonokat mellékelt jogosultságot a következők:

|Megjelenített név|Jogok (köznapi név)|
|---------------------|-----------------------|
|&lt; Szervezetnév &gt; – csak a bizalmas megjelenítése|A nézet, a Megnyitás, Olvasás|
|&lt; Szervezetnév &gt; - bizalmas|A nézet, a Megnyitás, Olvasás<br /><br />Mentés<br /><br />Szerkesztés tartalom szerkesztése<br /><br />Jogok megtekintése<br /><br />Lehetővé teszi makrók<br /><br />Előre<br /><br />Válasz<br /><br />Válasz mindenkinek|

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

