---
description: 'Der Experience Cloud Identity-Dienst bietet eine universelle, beständige ID zum Identifizieren Ihrer Besucher über alle Experience Cloud-Lösungen hinweg. '
keywords: ID-Dienst
seo-description: Der Adobe Experience Cloud Identity-Dienst (ID-Dienst) bietet eine universelle, beständige ID zum Identifizieren Ihrer Besucher über alle Experience Cloud-Lösungen hinweg. Sie kann ID-Generierungs-Code für Services wie Analytics, Audience Manager, Target und andere Experience Cloud-Lösungen oder -Funktionen ersetzen.
seo-title: Experience Cloud Identity-Dienst
title: Experience Cloud Identity-Dienst
uuid: b68194b5-e549-4f6f-bfaf-7744926aeaac
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: b907ffcbfbb8851ce6279b614dc58c22f2ce9907
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 92%

---

# Adobe Experience Cloud Identity-Dienst {#experience-cloud-id-service}

Der Adobe Experience Cloud Identity-Dienst (ID-Dienst) bietet eine universelle, beständige ID zum Identifizieren Ihrer Besucher über alle Experience Cloud-Lösungen hinweg. Sie kann ID-Generierungs-Code für Services wie Analytics, Audience Manager, Target und andere Experience Cloud-Lösungen oder -Funktionen ersetzen.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Erste Schritte</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Übersicht </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Voraussetzungen für den Experience Cloud Identity-Dienst</a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Standardimplementierung mit DTM </a> </li> 
     </ul> </p> <p><b>Javascript-Bibliotheken des Experience Cloud ID-Diensts</b> </p> <p>JavaScript-Dateien für den Experience Cloud Identity-Dienst befinden sich unter: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Neue oder vorgestellte Funktionen</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Opt-in-Dienst</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Häufig gestellte Fragen (FAQ) </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>Versionshinweise</b> </p> <p><b>Version 4.4</b> vom 17. Juli 2019 beinhaltet Unterstützung des <a href="reference/hashing-support.md" format="dita" scope="local"> SHA-256-Hash-Algorithmus</a>, mit dem Sie Kunden-IDs oder E-Mail-Adressen importieren und Hash-IDs exportieren können.</p><p><b>Version 4.0</b> vom 12. Februar 2019 enthält den <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">Opt-in-Service</a>, mit dem festgestellt werden kann, ob Sie beim Besuch Ihrer Site ein Cookie auf dem Gerät oder Browser eines Benutzers platzieren können. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Neue Funktionen und Fehlerbehebungen finden Sie in den <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="https" scope="external">Experience Cloud-Versionshinweisen</a>. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Versionshinweise zu älteren Versionen finden Sie im Abschnitt <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="html" scope="external">Frühere Versionshinweise</a>. </li> 
     </ul> </p> <p> <b>Experience Cloud-Ressourcen</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/de/privacy.html" format="http" scope="external"> Adobe Datenschutzcenter</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=en" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/de/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe-Schulungen und -Lernprogramme</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/de/support/experience-cloud.html" scope="external" format="https"> Produktdokumentation – Startseite</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
