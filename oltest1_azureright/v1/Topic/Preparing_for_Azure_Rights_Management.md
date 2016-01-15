---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Azure Rights Management elők&#233;sz&#237;t&#233;se
A felhő-előfizetési regisztrált és a szervezeti fiókkal kell létrehozni után [!INCLUDE[o365_1](../Token/o365_1_md.md)] vagy az Azure Active Directoryban, készen áll ahhoz, hogy a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] szolgáltatás.

Azonban a telepítést előtt győződjön meg arról, hogy a következő helyen:

-   Felhasználói fiókok és csoportok a felhőben, amely kézzel kell létrehozni, vagy az automatikusan létrehozott, és hogy szinkronizálni az Active Directory tartományi szolgáltatások (AD DS).

    A helyszíni fiókok és a csoportok szinkronizálásakor nem minden attribútumok kell szinkronizálni. Tekintse meg az attribútumokat, amelyek az Azure RMS szinkronizálni kell listáját, ez [Azure RMS szakasz](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) származó az Azure Active Directory dokumentációjában olvasható. A központi telepítési megkönnyítése érdekében azt javasoljuk, hogy [Azure AD-csatlakozás](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) a helyszíni kapcsolódás Azure Active Directoryban, de a könyvtárak segítségével bármely directory szinkronizálási módszert, amely ugyanazt az eredményt éri el.

-   A felhő Rights Management szolgáltatással használni kívánt levelek engedélyezve csoportok. Ezek a beépített csoportok lehet, vagy manuálisan létrehozott a Rights Management használó felhasználók tartalmazó csoportok.

    Ha az Exchange Online, hoz létre, és használja a csoportok levelek engedélyezve van az Exchange felügyeleti központ használatával. Ha rendelkezik az Active Directory tartományi szolgáltatások, és az Azure AD szinkronizálása, hoz létre, és mail-támogatással rendelkező csoportokat, amelyek a biztonsági csoportok vagy a terjesztési csoportok használja.

## A Rights Management engedélyezése
Alapértelmezés szerint [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] le van tiltva, amikor regisztrálja magát a [!INCLUDE[o365_2](../Token/o365_2_md.md)] vagy az Azure AD-fiók. Ahhoz, hogy [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] a szervezetben, aktiválnia kell a szolgáltatást. További tudnivalókért tekintse meg a [Az Azure Rights Management aktiválása](../Topic/Activating_Azure_Rights_Management.md).

## Lásd még
[Azure Rights Management konfigurálása](../Topic/Configuring_Azure_Rights_Management.md)

