---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Azure Rights Management – &#252;zembehelyez&#233;si menetrend
Az alábbi lépések segítségével előkészítése valósítja meg és kezelheti a szervezet Azure Rights Management (Azure RMS).

Azonban csak kívánt gyorsan próbálja meg az Azure RMS saját magának, ha inkább, mint az időtúllépés összegző éles környezetben, lásd: [Rövidített oktatóprogram Azure Rights Management](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> A következő lépések végrehajtása előtt meg kell vizsgálni [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md).

## 1. lépés: Győződjön meg arról, hogy rendelkezik-e, amely tartalmazza az Azure Rights Management-előfizetéssel
Előfizetés tartalmazó egynél több típus [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Tekintse meg a [Felhő előfizetések, amelyek támogatják az Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) szakasz a [Az Azure Rights Management követelményei](../Topic/Requirements_for_Azure_Rights_Management.md) című témakört, és ellenőrizze, hogy az előfizetés tartalmaz, amely a használni kívánt a szervezet által a táblára hivatkozó funkcióját [Rights Management szolgáltatások (RMS) összehasonlítás ajánlatok](https://technet.microsoft.com/dn858608).

## 2. lépés: A bérlő fiók használata a Rights Management előkészítése
Mielőtt elkezdené használni [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], hajtsa végre a következő előkészítése:

1.  Győződjön meg arról, hogy Azure vagy az Office 365-bérlőben tartalmazza-e a felhasználói fiókokat, és a csoportokat, amelyek hitelesíti a felhasználókat a szervezet az Azure RMS által használt. Ha szükséges, ezek fiók és a csoportok létrehozása, vagy szinkronizálhatók a helyszíni Directory. További tudnivalókért tekintse meg a [Azure Rights Management előkészítése](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  Dönthet úgy, hogy szeretne-e a Microsoft kezelése a bérlői kulcs (alapértelmezett), vagy létrehozása és kezelése a bérlői kulcs magát (a, a saját kulcs, vagy a BYOK előbbre néven ismert). Vegye figyelembe, hogy jelenleg nem használható BYOK használatakor az Exchange Online. További tudnivalókért tekintse meg a [Tervezés és végrehajtási a Azure Rights Management bérlői kulcs](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Telepítse a Windows PowerShell modul a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] legalább egy számítógépen, amelyen a csatlakozik az internethez. Ez a lépés most, vagy később teheti meg. További tudnivalókért tekintse meg a [A Windows PowerShell telepítése Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Ha a jelenleg a helyszíni Rights Management szolgáltatások használata esetén: Áthelyezés a felhőbe a kulcsok, sablonok és URL-cím az áttelepítés végrehajtásához. További tudnivalókért tekintse meg a [Áttelepítés Active Directory tartalomvédelmi szolgáltatások az Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  A Rights Management aktiválása, úgy, hogy a szolgáltatás használatának is elindítható. A szakaszolt központi telepítésének szükség, ha a felhasználó bevezetési vezérlők használat korlátozása az egyes felhasználóknak konfigurálása. További tudnivalókért tekintse meg a [Az Azure Rights Management aktiválása](../Topic/Activating_Azure_Rights_Management.md).

Szükség esetén fontolja meg, hogy a következők:

-   Egyéni sablonok, ha az alapértelmezett tartalomvédelmi házirend-sablonok nem megfelelőek a szervezetben. Ez a lépés most, vagy később teheti meg. További tudnivalókért tekintse meg a [Az Azure Rights Management egyéni sablonok konfigurálása](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   A naplózás, hogy a szervezet hogyan használja a Rights Management figyelheti használatát. Ez a lépés most, vagy később teheti meg. További tudnivalókért tekintse meg a [Naplózás, és az Azure Rights Management használati elemzése](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## 3. lépés: Az alkalmazások és a Rights Management szolgáltatások konfigurálása
Az alkalmazások konfigurálása a Rights Management megosztóalkalmazás, és a tartalomvédelmi (szolgáltatás IRM) szolgáltatásokat a SharePoint Online vagy az Exchange Online támogatásának engedélyezése telepítése tartalmazhat. További tudnivalókért tekintse meg a [Azure Rights Management alkalmazások konfigurálása](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Ha a fájlok, amelyek az Azure RMS megvédi folyamatokhoz igénylő meglévő IT-szolgáltatások – adatok fejlesztő megelőzése (DLP) megoldások, például a tartalom titkosítási átjárók (CEG), és a kártevőirtó termékek – kell az Azure RMS felügyelő felhasználó szolgáltatásfiókok konfigurálása. További tudnivalókért tekintse meg a [Fő felhasználók konfigurálása az Azure Rights Management és felderítési szolgáltatásokat vagy adatok helyreállítása](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Ha a helyszíni szolgáltatások Azure Rights Management szolgáltatással használni kívánt, telepítse, és a Rights Management-összekötő konfigurálását. További tudnivalókért tekintse meg a [Az Azure Rights Management összekötő telepítése](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## 4. lépés: Közzététele, és a védett tartalmakat
Most készen közzététele, és a védett tartalmakat, és jelentkezzen be a vállalata hogyan használja a Rights Management. További tudnivalókért tekintse meg a [Azure Rights Management használata](../Topic/Using_Azure_Rights_Management.md).

## 5. lépés: Szükség esetén a Rights Management felügyelete bérlői fiókja
Használandó megkezdése előtt [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], előfordulhat, hogy a Keresés a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] modul a Windows PowerShell-parancsfájl segítségével, vagy a felügyeleti módosítások automatizálására hasznos. További tudnivalókért tekintse meg a [Az Azure Rights Management felügyelete a Windows PowerShell használatával](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

