---
description: 'Der Experience Platform Identity Service bietet eine universelle, beständige ID, die Ihre Besucher für alle Lösungen in der Experience Cloud identifiziert. '
keywords: ID-Dienst
seo-description: Der Adobe Experience Platform Identity Service bietet eine universelle, beständige ID, die Ihre Besucher für alle Lösungen in der Experience Cloud identifiziert. Sie kann ID-Generierungscode für Dienste wie Analytics, Audience Manager, Target und andere Experience Cloud-Lösungen oder -Funktionen ersetzen.
seo-title: Experience Platform-Identitätsdienst
title: Experience Platform-Identitätsdienst
uuid: b 68194 b 5-e 549-4 f 6 f-bfaf -7744926 aeaac
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Experience Platform-Identitätsdienst {#experience-cloud-id-service}

Der Experience Platform Identity Service (ID-Dienst) stellt eine universelle, beständige ID bereit, die Ihre Besucher für alle Lösungen in der Experience Cloud identifiziert. Sie kann ID-Generierungscode für Dienste wie Analytics, Audience Manager, Target und andere Experience Cloud-Lösungen oder -Funktionen ersetzen.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Erste Schritte</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local">Übersicht  </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Anforderungen für den Experience Platform Identity Service </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Standardimplementierung mit DTM </a> </li> 
     </ul> </p> <p><b>Javascript-Bibliotheken des Experience Cloud ID-Diensts</b> </p> <p>Javascript für den Experience Platform Identity Service finden Sie unter: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external"> https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Neue oder vorgestellte Funktionen</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Opt-in-Dienst</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local">Häufig gestellte Fragen (FAQ)</a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>Mitteilungen:</b> </p> 
     <p> <p>Wichtig: Die Unterstützung von ID-Diensten für Internet Explorer 6, 7 und 8 wird nicht mehr unterstützt und wird in einer zukünftigen Version eingestellt. </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>Versionshinweise</b> </p> <p><b>Version 4.0</b> vom 12. Februar 2019 beinhaltet den <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> "Opt-in" -Dienst,</a> der verwendet wird, um zu identifizieren, ob Sie beim Besuch Ihrer Site ein Cookie auf dem Gerät oder Browser eines Benutzers platzieren können. </p> <p>Die Version vom 18. Januar 2018 enthält die JavaScript-Aktualisierung auf Version 3.0.0 und aktualisierte API-Methoden. Siehe <a href="library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> Disableidsyncs</a> und <a href="library/function-vars/disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disablethirdpartycookies</a>. </p> 
    <draft-comment> 
     <p>Die Version vom Oktober 2017 enthält keine Codeänderungen oder Aktualisierungen für den ID-Dienst. ID-Dienst-Code bleibt bei v 2.5 unverändert. </p> 
    </draft-comment> 
    <draft-comment> 
     <p> Die Version vom September 2017 erhöht den Code des ID-Diensts auf v 2.5. </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Neue Funktionen und Fehlerbehebungen finden Sie in den <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">Experience Cloud-Versionshinweisen</a>. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Versionshinweise zu älteren Versionen finden Sie unter <a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">Frühere Versionshinweise</a>. </li> 
     </ul> </p> <p> <b>Experience Cloud-Ressourcen</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Adobe Datenschutzcenter</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe-Schulungen und -Lernprogramme</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> Produktdokumentation – Startseite</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

