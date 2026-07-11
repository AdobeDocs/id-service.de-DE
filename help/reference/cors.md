---
description: Browser verwenden Cross Origin Resource Sharing (CORS) zum Anfordern von Ressourcen von einer Domain, die nicht der aktuellen Domain entspricht. Der Besucher-ID-Service unterstützt CORS-Standards, die diese Client-seitigen, ursprungsübergreifenden Ressourcenanforderungen ermöglichen. Der Besucher-ID-Dienst wird auf JSONP-Anfragen für ältere Browser oder Browser zurückgesetzt, die CORS nicht unterstützen.
keywords: Besucher-ID-Service
title: CORS-Unterstützung im Besucher-ID-Service von Adobe
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
TQID: https://experienceleague.adobe.com/eix2FaBue-Nf--wGzg5jBqB93QGIWtbM78Efjd8QZWM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 639
ht-degree: 65%

---

# CORS-Unterstützung im Besucher-ID-Service von Adobe {#cors-support-in-the-experience-cloud-id-service}

Browser verwenden Cross Origin Resource Sharing (CORS) zum Anfordern von Ressourcen von einer Domain, die nicht der aktuellen Domain entspricht. Der Besucher-ID-Service unterstützt CORS-Standards, die diese Client-seitigen, ursprungsübergreifenden Ressourcenanforderungen ermöglichen. Der Besucher-ID-Dienst wird auf JSONP-Anfragen für ältere Browser oder Browser zurückgesetzt, die CORS nicht unterstützen.

## Probleme mit Gleiche-Herkunft-Richtlinien und Besucher-ID-Service-Anfragen {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Eine Same-Origin-Policy ist eine Sicherheitskontrolle oder Einschränkung, die von einem Webbrowser erzwungen wird. Wenn sie auf dieser Ebene erzwungen wird, bestimmt der Webbrowser selbst, ob eine Anforderung von Ressourcen, die von einer Seite an eine andere gesendet wird, zulässig ist oder blockiert wird. Um festzustellen, ob es sich bei einer Anforderung um eine Anforderung mit derselben Herkunft handelt, vergleicht der Browser Folgendes:

* Uniform Resource Identifiers (URIs)
* Host-Namen (z. B. `http://www.my-webpage-example.com`)
* Port-Nummern (beispielsweise Port 80 und 440 für HTTP- und HTTPS-Anforderungen)

Der Browser lässt eine Anforderung zu, wenn beide Seiten dieselben Eigenschaften aufweisen, und blockiert die Ressourcenanforderung, wenn dies nicht der Fall ist.

## CORS behebt Probleme mit Gleiche-Herkunft-Richtlinien {#section-76c87ec3295d447bab220c84f138c235}

Cross Origin Resource Sharing (CORS) bietet eine sichere und effektive Möglichkeit, Ressourcen über verschiedene Domänen hinweg anzufordern. Die CORS-Spezifikation enthält eine Reihe von HTTP-Headern, die Browser zum Senden, Empfangen und Auswerten von Ressourcenanforderungen verwenden. Die Auswertung einer Ressourcenanforderung wird als *`preflight check`* bezeichnet. Mit dieser Prüfung können Browser und Server bestimmen, welche Anforderungen zulässig sind oder blockiert werden sollen. Die Preflight-Prüfung ist transparent für die mobile App bzw. API oder das Skript, die bzw. das eine Ressource anfordert. Zwei Header, die für den Ressourcenanforderungsprozess wichtig sind, sind:

* `Origin`: Ein Anforderungsheader, der die Anforderungsquelle ermittelt.
* `Access-Control-Allow-Origin`: Ein Antwortheader, der angibt, ob eine Ressource für den Anforderer freigegeben werden kann.

Im Folgenden wird die Funktionsweise dieser Header erläutert. Angenommen, in diesem Beispiel haben wir ein Finanzdienstleistungsunternehmen, das den Besucher-ID-Service auf seiner Website `www.finance-website.com` implementiert hat. Die folgende Tabelle definiert, wie die CORS-Anforderungs- und Antwort-Header den Zugriff auf eine Ressource prüfen.

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
   <td colname="col2"> <p>Beim Laden der Seite des Finanzunternehmens stellt der Browser eine Anforderung an <span class="codeph">dpm.demdex.net</span>. Dies ist ein Aufruf an die Domain der Datenerfassungs-Server (DCS), die vom Besucher-ID-Dienst verwendet werden. Diese Domain-übergreifende Anforderung enthält den Header: </p> <p> 
     <ul class="simplelist"> 
      <li> <code> Origin:https://www.finance-website.com</code> </li> 
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

In der folgenden Tabelle werden einige der Vorteile beschrieben, die CORS für Kunden bietet, die den Besucher-ID-Service verwenden.

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
   <td colname="col2"> <p>CORS verwendet <a href="https://developer.mozilla.org/de-DE/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a>, um Daten anzufordern und zu übertragen. Diese Methode ist sicherer als eine JSONP-Anfrage. Sie stellt sicher, dass es keine Möglichkeit gibt, beliebigen JavaScript-Code auszuführen, der in der Antwort des DCS enthalten sein könnte. Die CORS-Antwort-Payload „XMLHttpRequest“ wird vom Besucher-ID-Dienst JavaScript geparst und nicht einfach in einer Rückruffunktion ausgeführt. </p> <p> <p>Hinweis: Zum Akzeptieren von Cookies muss die Eigenschaft <span class="codeph">withCredentials</span> des Objekts <span class="codeph">XMLHttpRequest</span> auf <span class="codeph">true</span> festgelegt sein. Diese Eigenschaft wird in Chrome, Firefox, Internet Explorer (Version 10 und höher), Opera und Safari unterstützt. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Performance-Verbesserungen</b> </p> </td> 
   <td colname="col2"> <p>CORS hilft, die Performance zu verbessern, denn: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">Der Browser verwaltet Ressourcenanforderungen. Der Anfrageprozess ist für den Besucher-ID-Service transparent. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">Im Gegensatz zu asynchronen JSONP-Anfragen werden CORS-Anforderungen vom Browser nicht depriorisiert und in eine Warteschlange gestellt. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">Der Besucher-ID-Service antwortet gelassen. Das bedeutet, dass der Besucher-ID</span>Service der Seite Zugriff auf die erforderlichen Ressourcen gewährt, wenn eine URL als "<span class="codeph"> Origin“ übergeben wird. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

