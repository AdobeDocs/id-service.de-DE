---
description: Eine Übersicht darüber, wie der Experience Platform Identity Service mit der Legacy-Analytics-ID funktioniert.
keywords: ID-Dienst
seo-description: Eine Übersicht darüber, wie der Experience Platform Identity Service mit der Legacy-Analytics-ID funktioniert.
seo-title: Analytics und Experience Cloud ID-Anforderungen
title: Analytics und Experience Cloud ID-Anforderungen
uuid: 28 beed 16-7 ef 9-4824-8 e 82-853930756 eca
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Analytics und Experience Cloud ID-Anforderungen{#analytics-and-experience-cloud-id-requests}

Eine Übersicht darüber, wie der Experience Platform Identity Service mit der Legacy-Analytics-ID funktioniert.

## Zusammenfassung {#section-64d8523ff7634cb987d0c6480f587dd3}

Historisch gesehen wurde der Experience Platform Identity Service eng in Adobe Analytics integriert. Er ist auch weiterhin zentraler Bestandteil von Analytics, erfüllt jedoch nun wichtige Funktionen für andere Lösungen und Eigenschaften der [!DNL Experience Cloud]. Aufgrund dieser historischen Veraltung funktioniert die Prüfung auf oder das Schreiben einer Analytics-ID etwas anders als im allgemeinen Prozess, der unter [How the Experience Platform Identity Service Requests and Sets IDs…. beschrieben wird.](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a) Weitere Informationen zur Reihenfolge der Vorgänge zum Prüfen von IDs finden Sie unter [Einstellen von Analytics- und Experience Cloud-IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## AMCV-Cookie ist im Browser nicht gesetzt {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Wenn das [!DNL Experience Cloud]-Cookie (AMCV) nicht vorhanden ist, generiert ein ID-Dienstaufruf an [!DNL Adobe] eine Antwort, die davon abhängt, ob eine ältere Analytics-ID vorhanden ist oder nicht. Die Legacy-[!DNL Analytics]-ID wird im [s_vi-Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) gespeichert. In der folgenden Tabelle wird beschrieben, wie IDs basierend auf dem Status des s_ vi-Cookies in das AMCV-Cookie geschrieben werden.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status des s_vi-Cookies </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> s_vi-Cookie nicht festgelegt</b> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst weist Besuchern eine <span class="keyword">Experience Cloud</span> ID (MID) zu. Mittels der MID werden Ihre Besucher in <span class="keyword">Analytics</span> und anderen <span class="keyword">Experience Cloud</span>-Lösungen identifiziert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>s_vi-Cookie festgelegt</b> </p> </td> 
   <td colname="col2"> <p>Wenn ein Site-Besucher mit einem s_ vi-Cookie zuerst auf den Experience Platform Identity Service trifft, wird dieser Dienst: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">schreibt der Dienst die <span class="keyword">Analytics</span>-ID im s_vi-Cookie in den AMCV-Cookie. Sie wird als <span class="keyword">Analytics</span>-ID (AID) geschrieben. Diese Aktion beeinflusst Ihre Besucherzählung <i>nicht</i>.  Besucher werden von <span class="keyword">Analytics</span> weiterhin anhand der Legacy-IDs identifiziert. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">schreibt der Dienst die MID in den AMCV-Cookie. Mit der MID werden Benutzer lösungsübergreifend identifiziert. </li> 
    </ul> <p> <p>Hinweis: Mit einer <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> Übergangsphase</a>enthält die Antwort des Rechenzentrums stets eine Legacy-ID, die im s_ vi-Cookie gespeichert wird. Während der Übergangsphase wird die Legacy-ID als AID-Wert in den AMCV-Cookie geschrieben. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Benutzer, die vom s_ fid-Cookie identifiziert werden, verfügen nicht über ihren Legacy-FID-Wert in das AMCV-Cookie. Bei einem s_fid-Cookie werden Benutzer migriert, als sei kein s_vi-Cookie vorhanden (siehe oben), und sie werden als neue Besucher Ihrer Site angezeigt. Weitere Informationen finden Sie unter [Analytics-Cookies](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

## AMCV-Cookie ist im Browser gesetzt {#section-01c088fc565c4b24ba1722c7cc240310}

Ist der AMCV-Cookie vorhanden, wird die MID von als [!DNL Analytics]-Identifikator verwendet, falls kein Legacy-[!DNL Analytics]Analytics-Wert im Cookie vorhanden ist.
