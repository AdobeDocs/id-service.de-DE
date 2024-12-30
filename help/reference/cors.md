---
description: Browser verwenden Cross Origin Resource Sharing (CORS) zum Anfordern von Ressourcen von einer Domain, die nicht der aktuellen Domain entspricht. Der Experience Cloud Identity Service unterstützt CORS-Standards, die diese clientseitigen, ursprungsübergreifenden Ressourcenanforderungen ermöglichen. Der ID-Dienst greift bei älteren Browsern oder Browsern ohne CORS-Unterstützung auf JSONP-Anforderungen zurück.
keywords: ID-Dienst
title: CORS-Unterstützung im Experience Cloud Identity Service.
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 98%

---

# CORS-Unterstützung im Experience Cloud Identity Service. {#cors-support-in-the-experience-cloud-id-service}

Browser verwenden Cross Origin Resource Sharing (CORS) zum Anfordern von Ressourcen von einer Domain, die nicht der aktuellen Domain entspricht. Der Experience Cloud Identity Service unterstützt CORS-Standards, die diese clientseitigen, ursprungsübergreifenden Ressourcenanforderungen ermöglichen. Der ID-Dienst greift bei älteren Browsern oder Browsern ohne CORS-Unterstützung auf JSONP-Anforderungen zurück.

## Probleme mit Gleiche-Herkunft-Richtlinien und ID-Dienstanforderungen {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Eine Same-Origin-Policy ist eine Sicherheitskontrolle oder Einschränkung, die von einem Webbrowser erzwungen wird. Wenn sie auf dieser Ebene erzwungen wird, bestimmt der Webbrowser selbst, ob eine Anforderung von Ressourcen, die von einer Seite an eine andere gesendet wird, zulässig ist oder blockiert wird. Um festzustellen, ob es sich bei einer Anforderung um eine Anforderung mit derselben Herkunft handelt, vergleicht der Browser Folgendes:

* Uniform Resource Identifiers (URIs)
* Hostnamen (beispielsweise http://www.meine-beispielwebsite.com)
* Port-Nummern (beispielsweise Port 80 und 440 für HTTP- und HTTPS-Anforderungen)

Der Browser lässt eine Anforderung zu, wenn beide Seiten dieselben Eigenschaften aufweisen, und blockiert die Ressourcenanforderung, wenn dies nicht der Fall ist.

## CORS behebt Probleme mit Gleiche-Herkunft-Richtlinien  {#section-76c87ec3295d447bab220c84f138c235}

Cross Origin Resource Sharing (CORS) bietet eine sichere und effektive Möglichkeit, Ressourcen über verschiedene Domänen hinweg anzufordern. Die CORS-Spezifikation enthält eine Reihe von HTTP-Headern, die Browser zum Senden, Empfangen und Auswerten von Ressourcenanforderungen verwenden. Die Auswertung einer Ressourcenanforderung wird als *`preflight check`* bezeichnet. Mit dieser Prüfung können Browser und Server bestimmen, welche Anforderungen zulässig sind oder blockiert werden sollen. Die Preflight-Prüfung ist transparent für die mobile App bzw. API oder das Skript, die bzw. das eine Ressource anfordert. Zwei Header, die für den Ressourcenanforderungsprozess wichtig sind, sind:

* `Origin`: Ein Anforderungsheader, der die Anforderungsquelle ermittelt.
* `Access-Control-Allow-Origin`: Ein Antwortheader, der angibt, ob eine Ressource für den Anforderer freigegeben werden kann.

Im Folgenden wird die Funktionsweise dieser Header erläutert. Angenommen, ein Finanzdienstleistungsunternehmen hat den [!DNL Experience Cloud] ID-Dienst auf der eigenen Site www.finance-website.com implementiert. Die folgende Tabelle definiert, wie die CORS-Anforderungs- und Antwort-Header den Zugriff auf eine Ressource prüfen.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Aktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Anfrage</b> </p> </td> 
   <td colname="col2"> <p>Beim Laden der Seite des Finanzunternehmens stellt der Browser eine Anforderung an <span class="codeph">dpm.demdex.net</span>. Dies ist ein Aufruf an die Domain der Datenerfassungs-Server (DCS), die vom ID-Dienst verwendet wird. Diese Domain-übergreifende Anforderung enthält den Header: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Herkunft:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Antwort</b> </p> </td> 
   <td colname="col2"> <p>Die Antwort der DCS-Domäne enthält die folgenden Header, die der Website des Finanzunternehmens Zugriff auf die erforderlichen Ressourcen gewähren: </p> <p> 
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
   <td colname="col2"> <p>CORS verwendet <a href="https://developer.mozilla.org/de-DE/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a>, um Daten anzufordern und zu übertragen. Diese Methode ist sicherer als eine JSONP-Anfrage. Sie stellt sicher, dass es keine Möglichkeit gibt, beliebigen JavaScript-Code auszuführen, der in der Antwort des DCS enthalten sein könnte. Die Payload der CORS XMLHttpRequest-Antwort wird vom JavaScript des ID-Dienstes analysiert und nicht einfach in einer Rückruffunktion ausgeführt. </p> <p> <p>Hinweis: Zum Akzeptieren von Cookies muss die Eigenschaft <span class="codeph">withCredentials</span> des Objekts <span class="codeph">XMLHttpRequest</span> auf <span class="codeph">true</span> festgelegt sein. Diese Eigenschaft wird in Chrome, Firefox, Internet Explorer (Version 10 und höher), Opera und Safari unterstützt. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Performance-Verbesserungen</b> </p> </td> 
   <td colname="col2"> <p>CORS hilft, die Performance zu verbessern, denn: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">Der Browser verwaltet Ressourcenanforderungen. Der Anforderungsprozess ist für den ID-Dienst transparent. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">Im Gegensatz zu asynchronen JSONP-Anfragen werden CORS-Anforderungen vom Browser nicht depriorisiert und in eine Warteschlange gestellt. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">Der ID-Dienst reagiert berechtigterweise. Wenn eine URL als <span class="codeph">Origin</span> weitergegeben wird, gewährt der ID-Dienst demnach der Seite Zugriff auf die erforderlichen Ressourcen. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
