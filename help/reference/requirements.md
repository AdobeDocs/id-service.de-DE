---
description: Lesen Sie diesen Abschnitt, um sicherzustellen, dass Sie die richtigen Lösungen, Dienste und Codeversionen verwenden, die der Experience Cloud Identity-Dienst erfordert.
keywords: ID-Dienst
title: Voraussetzungen für den Experience Cloud Identity-Service
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: ht
source-wordcount: '731'
ht-degree: 100%

---

# Voraussetzungen für den Experience Cloud Identity-Service {#requirements-for-the-experience-cloud-id-service}

Lesen Sie diesen Abschnitt, um sicherzustellen, dass Sie die richtigen Lösungen, Dienste und Codeversionen verwenden, die der Experience Cloud Identity-Dienst erfordert.

## Anforderungen für die Gewährleistung einer erfolgreichen und unterstützten Implementierung {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Bei einer erfolgreichen, unterstützten Implementierung werden die Codeanforderungen erfüllt (oder übertroffen) und die in der [!DNL Adobe]-Hilfe aufgeführten Anweisungen befolgt. Eine nicht unterstützte Implementierung führt zu unerwarteten Ergebnissen und hindert die Kundenunterstützung und unsere Technikerteams daran, Sie bei der Fehlersuche und Lösung Ihrer Probleme mit dem ID-Dienst zu unterstützen.

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Art der Implementierung </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Standard</a> </p> </td> 
   <td colname="col2"> <p>Für eine Standardimplementierung im Dynamic Tag Management (DTM) müssen Sie: </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> den Einbettungskopfzeilencode im Abschnitt <span class="codeph">&lt;head&gt;</span> auf Ihrer Seite platzieren. </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2">den Einbettungsfußzeilencode vor dem schließenden <span class="codeph">&lt;/body&gt;</span>-Tag platzieren. </li> 
    </ul> <p>Eine Standardimplementierung wird nicht unterstützt, wenn Sie: </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> einen dieser DTM-Einbettungscodes an einer anderen Stelle im Markup- und/oder Seitencode platzieren. </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> DTM-Code mit asynchronen Methoden, Aufrufen/Callback-Methoden oder Wrappern anhängen, hinzufügen oder laden. </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">mehrere Instanzen von Einbettungscode auf derselben Seite einfügen. </li> 
    </ul> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dtm/using/client-side/deployment.html?lang=de" format="https" scope="external">Hosting – Registerkarte „Einbetten“</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> Benutzerdefinierte Implementierungen </a> </p> </td> 
   <td colname="col2"> <p>Bei nicht standardmäßigen oder manuellen Implementierungen müssen Sie den ID-Dienst gemäß den in diesem Handbuch beschriebenen Verfahren einrichten. Wie bei den oben genannten DTM-Richtlinien führt unsachgemäßes Platzieren und Laden von Code zu einer nicht unterstützten Implementierung. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Experience Cloud-Voraussetzungen: Organisations-ID  {#section-a02f537129a64ffbb690d5738d360c26}

Zur Verwendung des ID-Diensts muss Ihr Unternehmen für die [!DNL Experience Cloud] freigeschaltet sein und über eine Organisations-ID verfügen. Gehen Sie die folgende Liste durch, wenn Sie sich bezüglich des [!DNL Experience Cloud]-Status Ihrer Organisation nicht sicher sind und Ihre Organisations-ID herausfinden möchten.

>[!IMPORTANT]
>
>Wichtig: Bei der Organisations-ID wird die Groß-/Kleinschreibung beachtet. Zudem muss sie genau in der Form verwendet werden, in der sie bereitgestellt wird.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud-Status </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Aktiviert</b> </p> </td> 
   <td colname="col2"> <p>Wenn Ihr Unternehmen für <span class="keyword">Experience Cloud</span> freigeschaltet ist, Sie jedoch keine Organisations-ID besitzen, erhalten Sie weitere Informationen unter <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=de" format="https" scope="external">Organisations-ID</a> (führen Sie einen Bildlauf zu <i>Organisations-ID ermitteln</i> aus). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Nicht sicher</b> </p> </td> 
   <td colname="col2"> <p> Sollten Sie sich nicht sicher sein, welchen <span class="keyword">Experience Cloud</span>-Status Ihr Unternehmen hat, fragen Sie die das Adobe-Konto verwaltende Person, ob das Unternehmen sich unter <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a> mit einer Adobe ID anmelden kann. Funktioniert die Anmeldung, ist das Unternehmen freigeschaltet, und ein Administrator kann die Organisations-ID lesen. Die Organisations-ID finden Sie im Abschnitt „Administrationsseite“ in der <a href="https://docs.adobe.com/help/de-DE/core-services/interface/experience-cloud.html" format="https" scope="external">Experience Cloud-Verwaltung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Nicht aktiviert</b> </p> </td> 
   <td colname="col2"> <p> Sollte Ihr Unternehmen für die Experience Cloud nicht freigeschaltet sein, finden Sie weitere Informationen zum Einstieg unter <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=de" format="https" scope="external">Core Services – So aktivieren Sie Ihre Lösungen</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics-Voraussetzungen: Regionale Datenerfassung (Regional Data Collection, RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Alle Tracking-Server wurden auf RDC umgestellt, so dass es nicht notwendig ist, den Analytics-Tracking-Server zu wechseln. [Weitere Infos...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=de)

## Code-Bibliotheken und Versionsvoraussetzungen {#section-ad7542a4317d430fa79fc6b095beb84d}

In den folgenden Abschnitten sind die minimalen Code-Versionen aufgeführt, die für die Verwendung des [!DNL Experience Cloud] ID-Diensts erforderlich sind.

>[!TIP]
>
>Sie sollten anstelle der erforderlichen minimalen die neuesten Codeversionen verwenden.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud-Lösung </th> 
   <th colname="col3" class="entry"> Code-Bibliothek </th> 
   <th colname="col4" class="entry"> Versionsanforderungen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Experience Cloud</span> ID-Dienst</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 oder höher </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>Siehe <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=de" format="https" scope="external">AppMeasurement für JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 oder höher </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> „s_code.js“</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Hinweis:<span class="keyword"> Die s_code-Version H.27 von Analytics</span> wird im Zuge der Veröffentlichung des ID-Diensts Version 1.6.0 nicht mehr unterstützt. Nehmen Sie ein Upgrade Ihres Codes auf die neueste Version von AppMeasurement vor. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Video Heartbeat </p> <p>Siehe <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de" format="https" scope="external">Video Heartbeat 2.x für JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> Siehe <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=de" format="https" scope="external">Data Integration Library</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Siehe <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-technical.html?lang=de" format="https" scope="external">mbox-Code</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Siehe <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js/how-atjs-works.html?lang=de" format="https" scope="external">at.js-Implementierung</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## SDK-Anforderungen für Android und iOS  {#section-73b2446fba8e463888642c7d7dfd94f1}

Für den ID-Dienst sind mindestens die unten aufgeführten SDK-Versionen erforderlich.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Sie sollten anstelle der erforderlichen minimalen die neuesten Codeversionen verwenden.

Ihr SDK-Code muss für den ID-Dienst aktiviert werden. Aktivieren und laden Sie den neuesten SDK-Code für jede Anwendung über Ihr [Adobe Mobile Services](https://mobilemarketing.adobe.com/)-Konto herunter. Siehe auch:

* [Optionen für SDK-Besucher-ID-Dienst konfigurieren](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=de)
* [SDK-Methoden für Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=de)
* [SDK-Methoden für iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=de)

>[!MORELIKETHIS]
>
>* [Code-Bibliothek](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

