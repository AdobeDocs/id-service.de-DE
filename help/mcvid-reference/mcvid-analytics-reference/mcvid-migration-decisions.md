---
description: Vor Verwendung des Experience Cloud ID-Diensts sollten Sie wissen, wie dieser Dienst das Besucher-Tracking über mehrere Domänen beeinflusst, und sich der potenziellen Probleme bei der Datenerfassung mit verschiedenen Methoden oder mittels JavaScript-Dateien bewusst sein.
keywords: ID-Dienst
seo-description: Vor Verwendung des Experience Cloud ID-Diensts sollten Sie wissen, wie dieser Dienst das Besucher-Tracking über mehrere Domänen beeinflusst, und sich der potenziellen Probleme bei der Datenerfassung mit verschiedenen Methoden oder mittels JavaScript-Dateien bewusst sein.
seo-title: Entscheidungspunkte bei der Migration zum Experience Cloud ID-Dienst
title: Entscheidungspunkte bei der Migration zum Experience Cloud ID-Dienst
uuid: ee56b5de-fcf3-4cfb-9e53-762af7c4d2ff
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Entscheidungspunkte bei der Migration zum Experience Cloud ID-Dienst

Vor Verwendung des Experience Cloud ID-Diensts sollten Sie wissen, wie dieser Dienst das Besucher-Tracking über mehrere Domänen beeinflusst, und sich der potenziellen Probleme bei der Datenerfassung mit verschiedenen Methoden oder mittels JavaScript-Dateien bewusst sein.

Ihre Antworten auf die Fragen in diesem Abschnitt helfen Ihnen dabei, weitere Migrationsschritte zu bestimmen.

## Ist ein Datenerfassungs-CNAME vorhanden?

Viele Kunden können mit der ID-Dienst-Migration Datenerfassungs-CNAMEs eliminieren.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Datenerfassungsmethode </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Mit CNAME </p> </td> 
   <td colname="col2"> <p>Weiter mit der nächsten Frage, um zu bestimmen, ob Sie den Datenerfassungs-CNAME eliminieren sollten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Ohne CNAME </p> </td> 
   <td colname="col2"> <p>Springen Sie zu <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">Wenn kein Datenerfassungs-CNAME vorhanden ist: Verwenden Sie *.2o7.net oder *.sc.omtrdc.net als Datenerfassungsserver?</a> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Wenn ein Datenerfassungs-CNAME vorhanden ist: Gibt es mehrere Domänen?

Sollten Sie über mehrere Domänen verfügen, die Daten an die *gleiche Report Suite* übermitteln, empfehlen wir die Erfassung mittels CNAME. Somit können Besucher domänenübergreifend verfolgt werden. Wenn Sie Daten zu einer einzigen Domäne erfassen, sind mit einem Datenerfassungs-CNAME keinerlei Vorteile verbunden.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Datenerfassung aus </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>mehreren Domänen </p> </td> 
   <td colname="col2"> <p>Wenn Sie Besucher domänenübergreifend verfolgen und außerdem eine Haupteinstiegssite nutzen, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, verwenden Sie den Datenerfassungs-CNAME weiter. Eine genaue Erläuterung finden Sie im Abschnitt <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">Datenerfassungs-CNAMEs und domänenübergreifendes Tracking</a>. </p> <p>Beachten Sie, dass Sie zwei zusätzliche Tracking-Server-Parameter (<span class="codeph">visitor.marketingCloudServer</span> und <span class="codeph">visitor.marketingCloudServerSecure</span>) angeben müssen, um einen CNAME mit dem ID-Dienst zu konfigurieren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>einer einzelnen Domäne </p> </td> 
   <td colname="col2"> <p>Die Arbeit mit einer einzigen Domäne bedeutet, dass Sie von einem Datenerfassungs-CNAME weg migrieren können, wenn Sie diese Methode nicht länger einsetzen möchten. Eine Migration ist jedoch nicht erforderlich, wenn Ihr CNAME problemlos funktioniert. </p> <p>Bei der Entfernung des CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Sicherstellen, dass der neue Tracking-Server <a href="https://marketing.adobe.com/resources/help/de_DE/whitepapers/rdc/" format="https" scope="external">RDC-kompatibel</a> ist. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Stellen Sie einige Monate vor Ihrer Migration zum <span class="keyword">Experience Cloud</span> ID-Dienst den CNAME auf einen RDC-Tracking-Server um. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>Verwenden Sie keinesfalls</i> einen <span class="codeph">*.2o7.net</span>-Tracking-Server. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Wenden Sie sich an die <a href="https://helpx.adobe.com/de/marketing-cloud/contact-support.html" format="https" scope="external">Kundenunterstützung</a>, wenn Sie Hilfe bei der Besuchermigration benötigen. Somit werden konsistente Besucherzahlen gewährleistet. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Gibt es mehrere Analytics-JavaScript-Dateien oder verfolgen Sie Flash-Anwendungen oder Videos?

Wenn die Site mehrere Analytics-JavaScript-Dateien, Flash-Anwendungen oder Videos enthält, die Daten an *dieselbe Report Suite* senden, konfigurieren Sie eine Übergangsphase, damit Besucher weiterhin mit einer Analytics-ID identifiziert werden, während Sie den [!DNL Experience Cloud] ID-Dienst einführen.

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Datenerfassungsmethode </th> 
   <th colname="col2" class="entry"> Erforderliche Aktionen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Mehrere Analytics-Javascript-Dateien </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Weitere Datenerfassungsmethoden </li> 
    </ul> </td> 
   <td colname="col2"> <p>Konfigurieren Sie eine Übergangsphase für den Besucher-ID-Dienst, damit Sie ihn für jede JavaScript-Datei und alle sonstigen Datenerfassungsbibliotheken bereitstellen können. Siehe <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local">Übergangsphase für den ID-Dienst</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Einzelne Analytics-JavaScript-Datei </p> </td> 
   <td colname="col2"> <p>Sie können die JavaScript-Datei ohne Übergangsphase für die Verwendung des Besucher-ID-Diensts aktualisieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Verwenden Sie nicht unterstützte Methoden für die Datenerfassung?

Unter Umständen müssen Sie das Linktracking aktualisieren oder Silverlight eliminieren.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Datenerfassungsmethode </th> 
   <th colname="col2" class="entry"> Erforderliche Aktionen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript und/oder Flash </p> </td> 
   <td colname="col2"> <p>Keine. Der <span class="keyword">Experience Cloud</span> ID-Dienst unterstützt diese Datenerfassungsmethoden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>Sie müssen Silverlight ersetzen, wenn Benutzer auf Silverlight-Inhalte und andere Abschnitte Ihrer Site zugreifen können, die den <span class="keyword">Experience Cloud</span> ID-Dienst nutzen. Silverlight wird nicht vom ID-Dienst unterstützt. </p> <p> Wenn Sie einen Silverlight-basierten Videoplayer verfolgen, stellt der Anbieter wahrscheinlich JavaScript-APIs bereit, die Sie stattdessen verwenden können. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Hartcodierte Bild-Tags </p> </td> 
   <td colname="col2"> <p>Aktualisieren Sie für die Verwendung von JavaScript hartcodierte Links. </p> </td> 
  </tr> 
 </tbody> 
</table>

