---
description: Lesen Sie diesen Abschnitt, um sicherzustellen, dass Sie die richtigen Lösungen, Services und Codeversionen verwenden, die der Besucher-ID-Service erfordert.
keywords: Besucher-ID-Service
title: Voraussetzungen für den Besucher-ID-Service von Adobe
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 724
ht-degree: 39%

---

# Voraussetzungen für den Besucher-ID-Service von Adobe {#requirements-for-the-experience-cloud-id-service}

Lesen Sie diesen Abschnitt, um sicherzustellen, dass Sie die richtigen Lösungen, Services und Code-Versionen verwenden, die der Besucher-ID-Service erfordert.

## Anforderungen für die Gewährleistung einer erfolgreichen und unterstützten Implementierung {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Eine erfolgreiche, unterstützte Implementierung erfüllt (oder überschreitet) die Code-Anforderungen und folgt den Anweisungen, wie sie in der Adobe-Hilfe angezeigt werden. Eine nicht unterstützte Implementierung führt zu unerwarteten Ergebnissen und verhindert, dass die Kundenunterstützung und unsere Entwicklungsteams Sie bei der Fehlerbehebung oder Lösung Ihrer Probleme mit dem Besucher-ID-Service unterstützen.

### Standardmäßige Implementierungen

Siehe [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) in der Adobe Experience Platform-Datenerfassung für Ihre Standardimplementierung.

### Nicht standardisierte Implementierungen

Bei nicht standardmäßigen oder manuellen Implementierungen müssen Sie den Besucher-ID-Dienst wie in diesem Handbuch beschrieben einrichten. Wie bei den Standard-Implementierungsrichtlinien oben führt eine falsche Code-Platzierung und ein falsches Laden zu einer nicht unterstützten Implementierung.

## CX-Unternehmensanforderungen: IMS-Organisations-ID {#section-a02f537129a64ffbb690d5738d360c26}

Um den Besucher-ID-Dienst verwenden zu können, muss Ihr Unternehmen für CX Enterprise aktiviert sein und über eine IMS-Organisations-ID verfügen. Überprüfen Sie die folgende Liste, wenn Sie sich bezüglich des CX Enterprise-Status Ihres Unternehmens nicht sicher sind und Ihre IMS-Organisations-ID finden müssen.

>[!IMPORTANT]
>
>Bei der IMS-Organisations-ID wird zwischen Groß- und Kleinschreibung unterschieden und sie muss genau wie angegeben verwendet werden.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX Enterprise-Status </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Aktiviert</b> </p> </td> 
   <td colname="col2"> <p>Wenn Ihr Unternehmen für CX Enterprise aktiviert ist, Sie jedoch nicht über Ihre IMS-Organisations-ID verfügen, finden Sie weitere Informationen unter <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=de" format="https" scope="external"> Organisations-</a> (scrollen Sie nach unten zum Abschnitt <i>Suchen Ihrer Organisations-ID</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Nicht sicher</b> </p> </td> 
   <td colname="col2"> <p> Wenn Sie den CX-Enterprise-Status Ihres Unternehmens nicht kennen, fragen Sie die Person, die Ihr Adobe-Konto verwaltet, ob sich Mitglieder Ihres Unternehmens unter <a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a> mit einer Adobe ID anmelden können. Wenn möglich, sind Sie aktiviert und ein Administrator kann Ihre IMS-Organisations-ID anzeigen. Die IMS-Organisations-ID finden Sie im Abschnitt „Administration-Seite“ in <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=de" format="https" scope="external"> CX Enterprise Administration</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Nicht aktiviert</b> </p> </td> 
   <td colname="col2"> <p> Wenn Ihr Unternehmen für CX Enterprise nicht aktiviert ist, finden Sie weitere Informationen zum Einstieg unter <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=de" format="https" scope="external"> Core Services - </a> Lösungen . </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics-Voraussetzungen: Regionale Datenerfassung (Regional Data Collection, RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Alle Tracking-Server wurden auf RDC umgestellt, so dass es nicht notwendig ist, den Analytics-Tracking-Server zu wechseln. [Weitere Infos...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=de)

## Code-Bibliotheken und Versionsvoraussetzungen {#section-ad7542a4317d430fa79fc6b095beb84d}

In den folgenden Abschnitten werden die minimalen Code-Versionen aufgelistet, die zur Verwendung des Besucher-ID-Service erforderlich sind.

>[!TIP]
>
>Sie sollten anstelle der erforderlichen minimalen die neuesten Codeversionen verwenden.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX Enterprise-Lösung </th> 
   <th colname="col3" class="entry"> Code-Bibliothek </th> 
   <th colname="col4" class="entry"> Versionsanforderungen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Besucher-ID-Service</b> </p> </td> 
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
   <td colname="col4"> <p>H.27 </p> <p> <p>Hinweis: <span class="keyword"> Analytics</span> s_code Version H.27 wird mit Version 1.6.0 des Besucher-ID-Service nicht mehr unterstützt. Aktualisieren Sie Ihren Code auf die neueste Version von AppMeasurement. </p> </p> </td> 
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
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Siehe <a href="https://experienceleague.adobe.com/de/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">mbox-Code</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Siehe <a href="https://experienceleague.adobe.com/de/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">at.js-Implementierung</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## SDK-Anforderungen für Android und iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Der Besucher-ID-Dienst benötigt mindestens die unten aufgeführten SDK-Versionen.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Sie sollten anstelle der erforderlichen minimalen die neuesten Codeversionen verwenden.

Ihr SDK-Code muss für den Besucher-ID-Dienst aktiviert sein. Aktivieren und laden Sie den neuesten SDK-Code für jede Anwendung über Ihr [Adobe Mobile Services](https://mobilemarketing.adobe.com/)-Konto herunter. Siehe auch:

* [Optionen für SDK-Besucher-ID-Dienst konfigurieren](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=de)
* [SDK-Methoden für Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=de)
* [iOS SDK-Methoden](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=de)

>[!MORELIKETHIS]
>
>* [Code-Bibliothek](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
