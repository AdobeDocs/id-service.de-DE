---
description: Mit dieser Funktion können Sie die Experience Cloud ID eines Besuchers domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst implementiert haben und Inhaber der Quell- und Zieldomäne sein. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: ID-Dienst
title: appendVisitorIDsTo (domänenübergreifendes Tracking)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: f185ae10dac686b6986b171aef8a46a574484283
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 100%

---

# appendVisitorIDsTo (domänenübergreifendes Tracking){#appendvisitoridsto-cross-domain-tracking}

>[!TIP]
>
>Das Domain-übergreifende Tracking funktioniert nicht wie gewünscht, wenn die ECID anfangs (oder zuvor) abgelehnt wird. Die vorhandenen IDs, die entweder per URL übergeben oder zuvor im Cookie vorhanden waren, werden nicht überprüft, da davon ausgegangen wird, dass es sich hierbei um die IDs handelt, bei denen die Zustimmung auf „NEIN“ gesetzt war.

Mit dieser Funktion können Sie die Experience Cloud ID eines Besuchers domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst implementiert haben und Inhaber der Quell- und Zieldomäne sein. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Domänenübergreifendes Tracking von Benutzern, wenn Browser Drittanbieter-Cookies blockieren </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Codebeispiel für das Anhängen von Besucher-IDs </a> </li> 
 </a> </li> 
</ul>

<!-- <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) and SDK Support -->

## Domänenübergreifendes Tracking von Benutzern, wenn Browser Drittanbieter-Cookies blockieren {#section-7251d88befd440b4b79520e33c5aa44a}

Der ID-Dienst schreibt ein Cookie von Drittanbietern in den Browser, wenn eine Person Ihre Site besucht (siehe [Cookies und der Experience Cloud Identity Service](../../introduction/cookies.md)). Das Erstanbieter-Cookie enthält die MID, eine eindeutige ID für diesen Besucher. Das Drittanbieter-Cookie enthält eine andere ID, die vom ID-Dienst verwendet wird, um die MID zu generieren. Wenn ein Browser diesen Drittanbieter-Cookie blockiert, kann der Service folgende Aktionen nicht durchführen:

* Erneutes Generieren der eindeutigen ID für diesen Site-Besucher, wenn dieser zu einer anderen Domain navigiert.
* Verfolgen von Besuchern über verschiedene Domänen Ihres Unternehmens hinweg.

Um dieses Problem zu lösen, implementieren Sie ` Visitor.appendVisitorIDsTo( *`url`*)`. Mit dieser Eigenschaft kann der ID-Dienst Site-Besucher über mehrere Domänen hinweg verfolgen, selbst wenn deren Browser Drittanbieter-Cookies blockieren. Funktionsweise:

* Wenn ein Besucher zu Ihren anderen Domänen navigiert, fügt ` Visitor.appendVisitorIDsTo( *`url`*)` die MID als Abfrageparameter in der URL-Umleitung von der ursprünglichen Domain zur Zieldomäne hinzu.
* Der ID-Dienst-Code auf der Zieldomäne extrahiert die MID aus der URL, statt bei Adobe eine neue Besucher-ID anzufordern. Diese Anforderung schließt die Drittanbieter-Cookie-ID ein, die in diesem Fall nicht verfügbar ist.
* Der ID-Dienst-Code auf der Zielseite verwendet die übergebene MID, um den Besucher zu verfolgen.

Weitere Informationen finden Sie im Codebeispiel.

## Codebeispiel für das Anhängen von Besucher-IDs  {#section-62d55f7f986542b0b9238e483d50d7b0}

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

<!-- >[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with ` Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` -->

<!-- ## Dynamic Tag Management (DTM) and SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Set the appendVisitorIDTo Function in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html?lang=de" format="https" scope="external"> Android ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html?lang=de" format="https" scope="external"> iOS ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> -->
