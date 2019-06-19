---
description: Mit dieser Funktion können Sie die Experience Cloud ID domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst implementiert haben und Inhaber der Quell- und Zieldomäne sein. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: ID-Dienst
seo-description: Mit dieser Funktion können Sie die Experience Cloud ID domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst implementiert haben und Inhaber der Quell- und Zieldomäne sein. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
seo-title: appendVisitorIDsTo (domänenübergreifendes Tracking)
title: appendVisitorIDsTo (domänenübergreifendes Tracking)
uuid: 06 b 453 ee -73 c 5-4625-82 d 9-877 ad 2 b 4 f 702
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# appendVisitorIDsTo (domänenübergreifendes Tracking){#appendvisitoridsto-cross-domain-tracking}

Mit dieser Funktion können Sie die Experience Cloud ID domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst implementiert haben und Inhaber der Quell- und Zieldomäne sein. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Domänenübergreifendes Tracking von Benutzern, wenn Browser Drittanbieter-Cookies blockieren </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Codebeispiel für das Anhängen von Besucher-IDs </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) und SDK-Unterstützung </a> </li> 
</ul>

## Domänenübergreifendes Tracking von Benutzern, wenn Browser Drittanbieter-Cookies blockieren {#section-7251d88befd440b4b79520e33c5aa44a}

Der ID-Dienst schreibt ein Erst- und Drittanbieter-Cookie in den Browser, wenn eine Person Ihre Site besucht (siehe [Cookies und Experience Platform Identity Service](../../introduction/cookies.md) ). Der Erstanbieter-Cookie enthält die MID, eine eindeutige ID für diesen Besucher. Der Drittanbieter-Cookie enthält eine andere ID, die vom ID-Dienst verwendet wird, um die MID zu generieren. Wenn ein Browser diesen Drittanbieter-Cookie blockiert, kann der Dienst folgende Aktionen nicht durchführen:

* Neugenerieren einer eindeutigen ID für den Site-Besucher, wenn dieser zu einer anderen Domäne navigiert
* Verfolgen von Besuchern über verschiedene Domänen hinweg, deren Inhaber Ihre Organisation ist

Um dieses Problem zu beheben, implementieren Sie ` Visitor.appendVisitorIDsTo( *`URL`*)`. Mit dieser Eigenschaft kann der ID-Dienst Site-Besucher über mehrere Domänen hinweg nachverfolgen, selbst wenn die jeweiligen Browser Drittanbieter-Cookies blockieren. Funktionsweise:

* Wenn der Besucher zu Ihren anderen ` Visitor.appendVisitorIDsTo( *`Domänen`*)` navigiert, wird die MID als Abfrageparameter in der URL-Umleitung aus der ursprünglichen Domäne an die Zieldomäne angehängt.
* Der ID-Dienstcode auf der Zieldomäne extrahiert die MID aus der URL, statt bei Adobe eine neue Besucher-ID anzufordern. Diese Anforderung schließt die Drittanbieter-Cookie-ID ein, die in diesem Fall nicht verfügbar ist.
* Der ID-Dienstcode auf der Zielseite verwendet die übergebene MID zum Nachverfolgen des Besuchers.

Details erhalten Sie im Codebeispiel.

## Codebeispiel für das Anhängen von Besucher-IDs {#section-62d55f7f986542b0b9238e483d50d7b0}

Das folgende Beispiel kann Ihnen dabei helfen, mit ` Visitor.appendVisitorIDsTo( *`der URL zu beginnen`*)`. Wenn dies richtig implementiert wird, sollte Ihr JavaScript-Code etwa wie im folgenden Beispiel aussehen.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## Dynamic Tag Management (DTM) und SDK-Unterstützung {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Unterstützung für </th> 
   <th colname="col2" class="entry"> Hier finden Sie  </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Einrichten der appendVisitorIDTo-Funktion in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/android/mc_methods.html" format="https" scope="external"> ID-Dienst-Methoden für Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/ios/mc_methods.html" format="https" scope="external"> ID-Dienst-Methoden für iOS </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
