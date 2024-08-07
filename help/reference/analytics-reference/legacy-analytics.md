---
description: Eine Übersicht darüber, wie der Experience Cloud Identity Service mit Legacy-Analytics-IDs funktioniert.
keywords: ID-Dienst
title: Analytics und Experience Cloud ID-Anforderungen
exl-id: 8c682159-e23a-4641-9ffd-e0028dc2f305
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# Analytics und Experience Cloud ID-Anforderungen{#analytics-and-experience-cloud-id-requests}

Eine Übersicht darüber, wie der Experience Cloud Identity Service mit Legacy-Analytics-IDs funktioniert.

## Zusammenfassung  {#section-64d8523ff7634cb987d0c6480f587dd3}

In der Vergangenheit war der Experience Cloud Identity Service eng in Adobe Analytics eingebunden. Er ist auch weiterhin zentraler Bestandteil von Analytics, erfüllt jedoch nun wichtige Funktionen für andere Lösungen und Eigenschaften der [!DNL Experience Cloud]. Aufgrund dieses Umstands funktioniert das Suchen oder Schreiben einer Analytics-ID etwas anders als mit dem unter [Anfordern und Festlegen von IDs durch den Experience Cloud Identity Service](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a) beschriebenen allgemeinen Prozess. Weitere Informationen zur Reihenfolge der Vorgänge zum Überprüfen von IDs finden Sie unter [Einrichten von Analytics- und Experience Cloud IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## AMCV-Cookie ist im Browser nicht gesetzt {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Wenn das [!DNL Experience Cloud]-Cookie (AMCV) nicht vorhanden ist, generiert ein ID-Dienstaufruf an [!DNL Adobe] eine Antwort, die davon abhängt, ob eine Legacy-Analytics-ID vorhanden ist oder nicht. Die Legacy-[!DNL Analytics] ID ist im [s_vi-Cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=de) gespeichert. In der folgenden Tabelle wird beschrieben, wie IDs basierend auf dem Status des s_ vi-Cookies in das AMCV-Cookie geschrieben werden.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> s_vi-Cookie-Status </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> s_vi-Cookie ist nicht festgelegt</b> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst weist Besuchern eine <span class="keyword">Experience Cloud</span> ID (MID) zu. Mittels der MID werden Ihre Besucher in <span class="keyword">Analytics</span> und anderen <span class="keyword">Experience Cloud</span>-Lösungen identifiziert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>s_vi-Cookie festgelegt</b> </p> </td> 
   <td colname="col2"> <p>Stößt ein Site-Besucher mit einem s_vi-Cookie erstmals auf den Experience Cloud Identity Service: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">schreibt der Service die <span class="keyword">Analytics</span>-ID im s_vi-Cookie in den AMCV-Cookie. Sie wird als <span class="keyword">Analytics</span>-ID (AID) geschrieben. Diese Aktion beeinflusst Ihre Besucherzählung <i>nicht</i>. Besucher werden von <span class="keyword">Analytics</span> weiterhin anhand der Legacy-IDs identifiziert. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">schreibt der Service die MID in das AMCV-Cookie. Die MID identifiziert Benutzer lösungsübergreifend. </li> 
    </ul> <p> <p>Hinweis: Bei einer <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">Übergangsphase</a> ist in der Antwort des Rechenzentrums stets eine Legacy-ID enthalten, die im s_vi-Cookie gespeichert wird. Während der Übergangsphase wird die Legacy-ID als AID-Wert in den AMCV-Cookie geschrieben. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Für Benutzer, die durch ein s_fid-Cookie identifiziert werden, findet keine Migration des Legacy-FID-Werts in den AMCV-Cookie statt. Bei einem s_fid-Cookie werden Benutzer migriert, als sei kein s_vi-Cookie vorhanden (siehe oben), und sie werden als neue Besucher Ihrer Site angezeigt. Weitere Informationen finden Sie unter [Analytics-Cookies](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=de).

## AMCV-Cookie ist im Browser gesetzt {#section-01c088fc565c4b24ba1722c7cc240310}

Ist das AMCV-Cookie vorhanden, wird die MID von als [!DNL Analytics]-Identifikator verwendet, falls kein Legacy-[!DNL Analytics] Analytics-Wert im Cookie vorhanden ist.
