---
description: Browser verwenden Cross Origin Resource Sharing (CORS) zum Anfordern von Ressourcen von einer Domäne, die nicht der aktuellen Domäne entspricht. Der Experience Cloud Identity-Dienst unterstützt CORS-Standards, die diese clientseitigen, ursprungsübergreifenden Ressourcenanforderungen ermöglichen. Der ID-Dienst greift bei älteren Browsern oder Browsern ohne CORS-Unterstützung auf JSONP-Anforderungen zurück.
keywords: ID-Dienst
seo-description: Browser verwenden Cross Origin Resource Sharing (CORS) zum Anfordern von Ressourcen von einer Domäne, die nicht der aktuellen Domäne entspricht. Der Experience Cloud Identity-Dienst unterstützt CORS-Standards, die diese clientseitigen, ursprungsübergreifenden Ressourcenanforderungen ermöglichen. Der ID-Dienst greift bei älteren Browsern oder Browsern ohne CORS-Unterstützung auf JSONP-Anforderungen zurück.
seo-title: CORS-Unterstützung im Experience Cloud Identity-Dienst.
title: CORS-Unterstützung im Experience Cloud Identity-Dienst.
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# CORS-Unterstützung im Experience Cloud Identity-Dienst {#cors-support-in-the-experience-cloud-id-service}

Browser verwenden Cross Origin Resource Sharing (CORS) zum Anfordern von Ressourcen von einer Domäne, die nicht der aktuellen Domäne entspricht. Der Experience Cloud Identity-Dienst unterstützt CORS-Standards, die diese clientseitigen, ursprungsübergreifenden Ressourcenanforderungen ermöglichen. Der ID-Dienst greift bei älteren Browsern oder Browsern ohne CORS-Unterstützung auf JSONP-Anforderungen zurück.

## Probleme mit Gleiche-Herkunft-Richtlinien und ID-Dienstanforderungen {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Bei Gleiche-Herkunft-Richtlinien handelt es sich um durch einen Webbrowser erzwungene Sicherheitskontrollen oder Einschränkungen. Bei der Erzwingung auf dieser Ebene bestimmt der Webbrowser selbst, ob eine Anforderung für Ressourcen, die von einer Seite zur nächsten gestellt wurde, erlaubt oder blockiert wird. Um zu bestimmen, ob es sich bei einer Anforderung um eine Gleiche-Herkunft-Anforderung handelt, vergleicht der Browser Folgendes:

* Einheitlicher Bezeichner für Ressourcen (Uniform Resource Identifiers, URIs)
* Hostnamen (z. B. http://www.meine-webseite-beispiel.com)
* Portnummern (z. B. Port 80 und 440 für HTTP- und HTTPS-Anforderungen)

Der Browser erlaubt eine erfolgreiche Anforderung, wenn beide Seiten über dieselben Merkmale verfügen, und blockiert Ressourcenanforderungen, wenn dies nicht der Fall ist.

## CORS behebt Probleme mit Gleiche-Herkunft-Richtlinien {#section-76c87ec3295d447bab220c84f138c235}

CORS bietet eine sichere, effektive Möglichkeit, Ressourcen domänenübergreifend anzufordern. Die CORS-Spezifikation enthält eine Reihe von HTTP-Headern, die von Browsern zum Senden, Empfangen und Evaluieren von Ressourcenanforderungen verwendet werden. Die Evaluierung einer Ressourcenanforderung heißt *`preflight check`*. In dieser Prüfung können Browser und Server bestimmen, welche Anforderungen zulässig sind oder blockiert werden. Der Preflight-Check ist für die Anwendung, die API oder das Skript transparent, die bzw. das eine Ressource anfordert. Zwei im Ressourcenanforderungsprozess wichtige Header umfassen:

* `Origin`: Ein Anforderungsheader, der die Anforderungsquelle ermittelt.
* `Access-Control-Allow-Origin`: Ein Antwortheader, der angibt, ob eine Ressource für den Anforderer freigegeben werden kann.

Im Folgenden wird die Funktionsweise dieser Header erläutert. Angenommen, ein Finanzdienstleistungsunternehmen hat den [!DNL Experience Cloud] ID-Dienst auf der eigenen Site www.finance-website.com implementiert. In der folgenden Tabelle wird definiert, wie die CORS-Anforderungs- und -Antwortheader die Prüfung auf den Zugriff auf eine Ressource vornehmen.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Aktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Anforderung</b> </p> </td> 
   <td colname="col2"> <p>Beim Laden der Seite des Finanzunternehmens stellt der Browser eine Anforderung an <span class="codeph">dpm.demdex.net</span>. Hierbei handelt es sich um einen Aufruf der durch den ID-Dienst verwendeten Domäne der Datenerfassungsserver (DCS). Diese domänenübergreifende Anforderung enthält den Header: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin: https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Antwort</b> </p> </td> 
   <td colname="col2"> <p>Die Antwort von der DCS-Domäne enthält diese Header, durch das das Finanzunternehmen Sitezugriff auf die erforderlichen Ressourcen erhält: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

Siehe auch [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## Weitere Vorteile der Verwendung von CORS {#section-6f44f30694c44f95bf9854b8a2af8449}

In der folgenden Tabelle werden einige der Vorteile beschrieben, die CORS Kunden bietet, die den ID-Dienst verwenden.

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Vorteil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Erhöhte Sicherheit</b> </p> </td> 
   <td colname="col2"> <p>CORS verwendet <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" format="https" scope="external">XMLHttpRequest</a> zum Anfordern und Übertragen von Daten. Diese Methode ist sicherer als eine JSONP-Anforderung. Sie gewährleistet, dass es keine Möglichkeit gibt, willkürliche JavaScript-Elemente auszuführen, die möglicherweise in der Antwort vom DCS enthalten sind. Die CORS-XMLHttpRequest-Antwortnutzlast wird durch das ID-Dienst-JavaScript-Element analysiert und nicht einfach in einer Callback-Funktion ausgeführt. </p> <p> <p>Hinweis: Zum Akzeptieren von Cookies muss die Eigenschaft <span class="codeph">withCredentials</span> des Objekts <span class="codeph">XMLHttpRequest</span> auf <span class="codeph">true</span> festgelegt sein. Diese Eigenschaft wird in Chrome, Firefox, Internet Explorer (v10+), Opera und Safari unterstützt. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Leistungsverbesserungen</b> </p> </td> 
   <td colname="col2"> <p>CORS hilft aus den folgenden Gründen bei der Leistungsverbesserung: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">Der Browser verwaltet Ressourcenanforderungen. Der Anforderungsprozess ist transparent für den ID-Dienst. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">Im Gegensatz zu asynchronen JSONP-Anforderungen hebt der Browser weder die Priorisierung von CORS-Anforderung auf, noch setzt er sie in die Warteschlange. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">Der ID-Dienst reagiert tolerant. Wenn eine URL als <span class="codeph">Origin</span> weitergegeben wird, gewährt der ID-Dienst demnach der Seite Zugriff auf die erforderlichen Ressourcen. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

