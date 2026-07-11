---
description: Mit dieser Funktion können Sie die ECID domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion verwenden zu können, müssen Sie den Besucher-ID-Service implementiert haben und Eigentümer der Quell- und Ziel-Domains sein. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: Besucher-ID-Service
title: appendVisitorIDsTo (domänenübergreifendes Tracking)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
TQID: https://experienceleague.adobe.com/F4rWmYj6NidX861-qU8KI9RRbdwNdzP0x4CZUxPZfYw
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
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 432
ht-degree: 61%

---

# appendVisitorIDsTo (domänenübergreifendes Tracking){#appendvisitoridsto-cross-domain-tracking}

>[!TIP]
>
>Das Domain-übergreifende Tracking funktioniert nicht wie gewünscht, wenn die ECID anfangs (oder zuvor) abgelehnt wird. Die vorhandenen IDs, die entweder per URL übergeben oder zuvor im Cookie vorhanden waren, werden nicht überprüft, da davon ausgegangen wird, dass es sich hierbei um die IDs handelt, bei denen die Zustimmung auf „NEIN“ gesetzt war.

Mit dieser Funktion können Sie die ECID domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion verwenden zu können, müssen Sie den Besucher-ID-Service implementiert haben und Eigentümer der Quell- und Ziel-Domains sein. Verfügbar in `VisitorAPI.js` Version 1.7.0 oder höher.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Domänenübergreifendes Tracking von Benutzern, wenn Browser Drittanbieter-Cookies blockieren </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Codebeispiel für das Anhängen von Besucher-IDs </a> </li> 
 </a> </li> 
</ul>

## Domänenübergreifendes Tracking von Benutzern, wenn Browser Drittanbieter-Cookies blockieren {#section-7251d88befd440b4b79520e33c5aa44a}

Der Besucher-ID-Dienst schreibt ein Cookie von Drittanbietern in den Browser, wenn eine Person Ihre Site besucht (siehe [Cookies und der Besucher-ID-Dienst](../../introduction/cookies.md) ). Das Erstanbieter-Cookie enthält die MID, eine eindeutige ID für diesen Besucher. Das Drittanbieter-Cookie enthält eine weitere ID, die vom Besucher-ID-Service zum Generieren der MID verwendet wird. Wenn ein Browser dieses Drittanbieter-Cookie blockiert, kann der Besucher-ID-Dienst:

* Erneutes Generieren der eindeutigen ID für diesen Site-Besucher, wenn dieser zu einer anderen Domain navigiert.
* Verfolgen von Besuchern über verschiedene Domänen Ihres Unternehmens hinweg.

Um dieses Problem zu lösen, implementieren Sie `Visitor.appendVisitorIDsTo( *`url`*)`. Mit dieser Eigenschaft kann der Besucher-ID-Dienst Website-Besucher über mehrere Domains hinweg verfolgen, selbst wenn ihre Browser Drittanbieter-Cookies blockieren. Funktionsweise:

* Wenn ein Besucher zu Ihren anderen Domänen navigiert, fügt `Visitor.appendVisitorIDsTo( *`url`*)` die MID als Abfrageparameter in der URL-Umleitung von der ursprünglichen Domain zur Zieldomäne hinzu.
* Der Besucher-ID-Dienst-Code in der Ziel-Domain extrahiert die MID aus der URL, anstatt eine Anfrage für die ID dieses Besuchers an Adobe zu senden. Diese Anforderung schließt die Drittanbieter-Cookie-ID ein, die in diesem Fall nicht verfügbar ist.
* Der Besucher-ID-Dienst-Code auf der Zielseite verwendet die übergebene MID, um den Besucher zu verfolgen.

Weitere Informationen finden Sie im Codebeispiel.

## Codebeispiel für das Anhängen von Besucher-IDs {#section-62d55f7f986542b0b9238e483d50d7b0}

Der folgende Beispiel-Code kann Ihnen bei den ersten Schritten mit der Funktion `appendVisitorIDsTo` helfen:

>[!TIP]
>
>Dieser Code kann im Editor für benutzerspezifischen Code platziert werden, der Teil der Adobe Analytics-Erweiterung ist, oder oben in [AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=de).

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- 
>[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with `Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the Visitor ID Service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, ECID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` 
-->

<!--
## SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android Visitor ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS Visitor ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> 
-->

