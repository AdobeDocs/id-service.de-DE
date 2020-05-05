---
description: Vor Verwendung des Experience Cloud Identity-Diensts sollten Sie wissen, wie dieser Dienst das Besucher-Tracking auf mehreren Domänen beeinflusst, und die potenziellen Probleme bei der Datenerfassung mit verschiedenen Methoden oder mittels JavaScript-Dateien kennen.
keywords: ID Service
seo-description: Vor Verwendung des Experience Cloud Identity-Diensts sollten Sie wissen, wie dieser Dienst das Besucher-Tracking auf mehreren Domänen beeinflusst, und die potenziellen Probleme bei der Datenerfassung mit verschiedenen Methoden oder mittels JavaScript-Dateien kennen.
seo-title: Entscheidungspunkte bei der Migration zum Experience Cloud Identity-Dienst
title: Entscheidungspunkte bei der Migration zum Experience Cloud Identity-Dienst
uuid: ee56b5de-fcf3-4cfb-9e53-762af7c4d2ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Entscheidungspunkte bei der Migration zum Experience Cloud Identity-Dienst

Vor Verwendung des Experience Cloud Identity-Diensts sollten Sie wissen, wie dieser Dienst das Besucher-Tracking auf mehreren Domänen beeinflusst, und die potenziellen Probleme bei der Datenerfassung mit verschiedenen Methoden oder mittels JavaScript-Dateien kennen.

Ihre Antworten auf die Fragen in diesem Abschnitt helfen Ihnen dabei, weitere Migrationsschritte zu bestimmen.

## Haben Sie einen Datenerfassungs-CNAME?

Viele Kunden können im Rahmen der ID-Dienst-Migration einen Datenerfassungs-CNAME eliminieren.

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
   <td colname="col2"> <p>In der nächsten Frage können Sie entscheiden, ob Sie einen Datenerfassungs-CNAME eliminieren möchten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Ohne CNAME </p> </td> 
   <td colname="col2"> <p>Springen Sie zu <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">Wenn kein Datenerfassungs-CNAME vorhanden ist: Verwenden Sie *.2o7.net oder *.sc.omtrdc.net als Datenerfassungsserver?</a> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Wenn Sie über einen Datenerfassungs-CNAME verfügen, haben Sie dann mehrere Domänen?

Wenn Sie über mehrere Domänen verfügen, die Daten an *dieselbe Report Suite* senden, wird die Datenerfassung mit einem CNAME empfohlen. Auf diese Weise können Sie Besucher domänenübergreifend verfolgen. Wenn Sie Daten über eine einzelne Domäne erfassen, hat die Aufrechterhaltung eines Datenerfassungs-CNAME keinen Vorteil.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Erfassen von Daten aus </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Mehrere Domänen </p> </td> 
   <td colname="col2"> <p>Wenn Sie Besucher domänenübergreifend verfolgen und außerdem über eine Haupteinstiegssite verfügen, auf der Kunden identifiziert werden können, bevor sie andere Domänen besuchen, sollten Sie weiterhin Ihren Datenerfassungs-CNAME verwenden. Eine genaue Erläuterung finden Sie im Abschnitt <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">Datenerfassungs-CNAMEs und domänenübergreifendes Tracking</a>. </p> <p>Beachten Sie, dass Sie zwei zusätzliche Tracking-Server-Parameter (<span class="codeph">visitor.marketingCloudServer</span> und <span class="codeph">visitor.marketingCloudServerSecure</span>) angeben müssen, um einen CNAME mit dem ID-Dienst zu konfigurieren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eine einzelne Domäne </p> </td> 
   <td colname="col2"> <p>Wenn Sie mit einer einzelnen Domäne arbeiten, können Sie einen Datenerfassungs-CNAME eliminieren, wenn Sie ihn nicht mehr verwalten möchten. Es müssen jedoch keine Änderungen vorgenommen werden, wenn Ihr CNAME funktioniert. </p> <p>Wenn Sie den CNAME entfernen: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Sicherstellen, dass der neue Tracking-Server <a href="https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external">RDC-kompatibel</a> ist. </li> 
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
   <th colname="col1" class="entry"> Datenerfassung mit </th> 
   <th colname="col2" class="entry"> Erforderliche Aktionen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Mehrere Analytics-JavaScript-Dateien </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Andere Datenerfassungsmethoden </li> 
    </ul> </td> 
   <td colname="col2"> <p>Sie sollten eine Übergangsphase für den Besucher-ID-Dienst konfigurieren, damit Sie den Besucher-ID-Dienst für jede JavaScript-Datei und andere Datenerfassungsbibliotheken bereitstellen können. Siehe <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">Übergangsphase für den ID-Dienst</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eine einzelne Analytics-JavaScript-Datei </p> </td> 
   <td colname="col2"> <p>Sie können Ihre einzelne JavaScript-Datei aktualisieren, um den Besucher-ID-Dienst ohne Übergangsphase zu verwenden. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Verwenden Sie nicht unterstützte Datenerfassungsmethoden?

Möglicherweise müssen Sie die Verfolgung von Links aktualisieren oder eine Migration von Silverlight aus durchführen.

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
   <td colname="col2"> <p>Kein. Der <span class="keyword">Experience Cloud</span> ID-Dienst unterstützt diese Datenerfassungsmethoden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>Sie müssen Silverlight ersetzen, wenn Benutzer auf Silverlight-Inhalte und andere Abschnitte Ihrer Site zugreifen können, die den <span class="keyword">Experience Cloud</span> ID-Dienst nutzen. Silverlight wird vom ID-Dienst nicht unterstützt. </p> <p> Wenn Sie einen Silverlight-basierten Videoplayer verfolgen, stellt der Anbieter wahrscheinlich JavaScript-APIs bereit, die Sie stattdessen verwenden können. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Hartkodierte Bild-Tags </p> </td> 
   <td colname="col2"> <p>Aktualisieren Sie hartcodierte Links, um JavaScript zu verwenden. </p> </td> 
  </tr> 
 </tbody> 
</table>

