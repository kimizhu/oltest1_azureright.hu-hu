---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Az Active Directory Rights Management Services mobileszk&#246;z-bőv&#237;tm&#233;nye
Az Active Directory Rights Management Services (AD RMS) mobileszköz-bővítménye meglévő AD RMS-környezetben futtatható. Ez lehetővé teszi a mobileszközökkel rendelkező felhasználók számára, hogy védetté tehessék és használhassák a bizalmas adatokat, ha az eszközük támogatja a legújabb RMS-ügyfelet, és RMS-kompatibilis alkalmazásokat futtat. Ezen eszközök felhasználói számára többek között az alábbi lehetőségek érhetők el:

-   Különböző fájlformátumú (például .txt, .csv és .xml) védett szövegfájlok használata az RMS-megosztó alkalmazással.

-   Védett képfájlok (például .jpg, .gif és .tif) használata az RMS-megosztó alkalmazással.

-   Bármely általános védelemmel ellátott fájl (.pfile formátum) megnyitása az RMS megosztóalkalmazással.

-   Az eszközön lévő képfájlok védelme az RMS megosztóalkalmazással.

-   A Windows-alapú RMS-megosztó alkalmazással vagy egyéb RMS-kompatibilis alkalmazással védetté tett PDF-fájlok megnyitása mobileszközökhöz készült RMS-kompatibilis PDF-megjelenítővel.

-   Olyan RMS-kompatibilis alkalmazásokat biztosító szoftvergyártók egyéb alkalmazásainak használata, amelyek támogatják az RMS-t natív módon támogató fájltípusokat.

-   Olyan saját fejlesztésű RMS-kompatibilis alkalmazások használata, amelyek az RMS SDK használatával készültek.

> [!NOTE]
> Az RMS megosztóalkalmazást a Microsoft webhelyén, a [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) oldalról töltheti le.
> 
> Az RMS által támogatott különböző fájltípusokról további információt a Rights Management megosztóalkalmazás rendszergazdai kézikönyvének [Támogatott fájltípusok és fájlnévkiterjesztések](http://technet.microsoft.com/library/dn339003.aspx) című szakaszában talál.

Nem szükséges a mobileszköz-bővítmény védett e-mailek használatához vagy létrehozásához az eszközökön, ha azok Exchange ActiveSync IRM szolgáltatást támogató levelezőalkalmazásokat futtatnak. Az RMS és a mobileszközök natív támogatása az Exchange 2010 1. szervizcsomagjával kezdődően áll rendelkezésre.

Az alábbi szakaszok az Active Directory Rights Management Services (AD RMS) mobileszköz-bővítményének üzembe helyezéséhez nyújtanak útmutatást:

-   [Az AD RMS mobileszköz-bővítményének telepítési előfeltételei](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Az AD FS beállítása az AD RMS mobileszköz-bővítményének használatára](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Az AD FS beállítása az AD RMS mobileszköz-bővítményének használatára](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [A DNS SRV-rekordok megadása az AD RMS mobileszköz-bővítményéhez](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Az AD RMS mobileszköz-bővítményének telepítése](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Az AD RMS mobileszköz-bővítményének telepítési előfeltételei
Az AD RMS mobileszköz-bővítményének telepítése előtt győződjön meg arról, hogy ezek a feltételek teljesülnek.

|Követelmény|További információ|
|---------------|----------------------|
|Meglévő AD RMS-környezet Windows Server 2012 R2 vagy Windows Server 2012 rendszerben. **Note:** Az AD RMS szolgáltatásnak teljes értékű Microsoft SQL Server-alapú adatbázist kell használnia egy különálló kiszolgálón, nem pedig a belső Windows-adatbázist, amelyet gyakran ugyanazon a kiszolgálón használnak tesztelésre.|Az AD RMS-ről további dokumentációt a Windows Server könyvtár következő részében talál: [Active Directory Rights Management Services](http://technet.microsoft.com/library/hh831364.aspx).|
|Windows Server 2012 R2 rendszerben üzembe helyezett AD FS szolgáltatás|Az AD FS-ről további dokumentációt a Windows Server könyvtár következő részében talál: [Windows Server 2012 R2 AD FS telepítési útmutató](http://technet.microsoft.com/library/dn486820.aspx).<br /><br />Az AD FS-t konfigurálni kell a mobileszköz-bővítmény használatához. Az előfeltétel-ellenőrzővel kapcsolatos további tudnivalókért olvassa el ezen témakör [Az AD FS beállítása az AD RMS mobileszköz-bővítményének használatára](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) című részét.|
|SRV-rekordok a DNS-ben|Hozzon létre egy vagy több SRV-rekordot a vállalati tartományban vagy tartományokban:<br /><br />-   külön rekordot minden olyan e-mail tartomány utótagjához, amelyet a felhasználók használni fognak<br />-   külön rekordot az RMS-fürtök által használt minden teljes tartománynév esetében a tartalom védelméhez<br /><br />Amikor a felhasználók megadják az e-mail címüket a mobileszközükről, a rendszer a tartományi utótag alapján határozza meg, hogy az AD RMS infrastruktúrát vagy az Azure RMS-t kell-e használniuk. Amikor megtalálja az SRV-rekordot, átirányítja az ügyfeleket arra az AD RMS-kiszolgálóra, amelyik erre az URL-címre válaszol.<br /><br />Ha a felhasználók védett tartalmat tekintenek meg egy mobileszközön, az ügyfélalkalmazás az teljes tartománynévvel egyező rekordot keres a DNS-ben a tartalmat védetté tevő fürt URL-címében. A rendszer ekkor átirányítja az eszközt a DNS-rekordban megadott AD RMS-fürthöz, és beszerzi a licencet a tartalom megnyitásához. A legtöbb esetben az RMS-fürt ugyanaz az RMS-fürt lesz, amelyik védelemmel látta el a tartalmat.<br /><br />Az előfeltétel-ellenőrzővel kapcsolatos további tudnivalókért olvassa el ezen témakör [A DNS SRV-rekordok megadása az AD RMS mobileszköz-bővítményéhez](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) című részét.|
|A jelenleg támogatott ügyfelek:<br /><br />-   Az Androidhoz készült RMS megosztóalkalmazás legújabb verzióját futtató Android-alapú készülékek|A minimálisan szükséges verzió az Android 4.0.3.<br /><br />A [Microsoft Connect webhelyről](https://connect.microsoft.com/site1170/Downloads) töltse le az Androidra készült RMS megosztóalkalmazást, és telepítse közvetlenül a készülékre.|

### <a name="BKMK_ADFS"></a>Az AD FS beállítása az AD RMS mobileszköz-bővítményének használatára
Először konfigurálnia kell az AD FS-t, majd engedélyezni az Androidhoz készült RMS megosztóalkalmazást.

##### 1. lépés: Az AD FS konfigurálása

-   Az AD FS-t automatikusan beállíthatja az AD RMS mobileszköz-bővítmény támogatására egy Windows PowerShell-parancsprogram futtatásával, illetve manuálisan is megadhatja a konfigurációs beállításokat és értékeket:

    -   Az AD FS automatikus konfigurálásához másolja az alábbi szöveget a vágólapra, és illessze be egy Windows PowerShell-parancsfájlba, majd futtassa a parancsfájlt:

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Az AD FS manuális konfigurálásához használja az alábbi beállításokat:

        |Konfiguráció|Érték|
        |----------------|---------|
        |**Megbízható függő entitás**|api.rms.rest.com|
        |**Jogcímszabály**|**Attribútumtár**:  Active Directory<br /><br />**E-mail címek**:  E-mail cím<br /><br />**Egyszerű felhasználónév**:  UPN<br /><br />**Proxycím**:  https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### 2. lépés: Az Androidhoz készült RMS megosztóalkalmazás engedélyezése

-   Futtassa a következő Windows PowerShell-parancsot az Android készülékek támogatásának hozzáadásához:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>A DNS SRV-rekordok megadása az AD RMS mobileszköz-bővítményéhez
Minden felhasználók által használt e-mail tartományhoz létre kell hoznia DNS SRV-rekordokat. Ha minden felhasználó egyetlen szülőtartomány gyermektartományait használja, és ennek a folyamatos névtérnek minden felhasználója ugyanazt az RMS-fürtöt használja, akkor elegendő egyetlen SRV-rekordot használnia a szülőtartományban, és az RMS megkeresi a megfelelő DNS-rekordokat.

Az SRV-rekordok formátuma a következő: _rmsdisco._http._tcp. *&lt;e-mailutótag&gt;**&lt;portszám&gt;**&lt;RMSfürteljestartományneve&gt;*

Ha például a szervezetének felhasználói a

-   user@contoso.com

-   user@sales.contoso.com

-   user@fabrikam.com

e-mail címeket használják, és a contoso.com nem rendelkezik egy másik, az **rmsserver.contoso.com** nevű tartománytól eltérő, RMS-fürtöt használó gyermektartománnyal, akkor hozzon létre két DNS SRV-rekordot a következő értékekkel:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Az e-mail tartományokhoz létrehozott fenti DNS SRV-rekordokon kívül egy másik DNS SRV-rekordot is létre kell hoznia a felhasználói tartományokban. Ennek a rekordnak meg kell adnia a tartalmat védő RMS-fürt URL-címeit. Minden RMS által védett fájl tartalmaz egy URL-címet, amely arra a fürtre mutat, amelyik védetté tette a fájlt. A mobileszközök a DNS SRV-rekordot és a rekordban megadott URL-cím teljes tartománynevét használják annak az RMS-fürtnek a megkereséséhez, amely alkalmas a mobileszközök támogatására.

Ha például az **rmsserver.contoso.com** RMS-fürthöz tartozik, akkor hozzon létre egy DNS SRV-rekordot a következő értékekkel: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>Az AD RMS mobileszköz-bővítményének telepítése
Az AD RMS mobileszköz-bővítményének telepítése előtt győződjön meg arról, hogy teljesülnek az előző szakaszban ismertetett előfeltételek, és ismeri az AD FS-kiszolgáló URL-címét. Ezután tegye a következőket:

1.  Töltse le az AD RMS mobileszköz-bővítményét a [Microsoft Connect webhelyről](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  A Setup.exe fájlt futtatva indítsa el az Active Directory Rights Management Services mobileszköz-bővítményének telepítővarázslóját.

3.  Amikor a program kéri, adja meg a korábban konfigurált AD FS-kiszolgáló URL-címét.

4.  Végezze el a varázsló lépéseit.

Futtassa a varázslót a RMS-fürt minden csomópontján.

