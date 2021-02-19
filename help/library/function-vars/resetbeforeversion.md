---
description: Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.
keywords: ID-Dienst
seo-description: Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 61%

---


# resetBeforeVersion{#resetbeforeversion}

Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.

Wenn Sie die Version Ihres ID-Diensts als Wert der Variablen `resetBeforeVersion` übergeben, werden veraltete ECIDs aus den clientseitigen IDs gelöscht.

Einige Bedingungen, wie z. B. Sitzungs-Timeouts, können dazu führen, dass eine clientseitige ID generiert wird, ohne dass der ID-Dienst erfolgreich eine serverseitige ID erhält. In diesem Fall wird eine verwaiste clientseitige ID vom ID-Dienst verfolgt, ohne dass eine domänenübergreifende Verfolgung oder ordnungsgemäße Synchronisierung mit anderen Lösungen möglich wäre. Durch dieses Verhalten wird die Version im aktuellen AMCV-Cookie mit dem Wert von `resetBeforeVersion` verglichen. Wenn das Cookie nicht vorhanden ist oder die Version des Cookies kleiner (älter) als die neueste veröffentlichte Version von `resetBeforeVersion` ist, dann wird das AMCV-Cookie entfernt und der ID-Dienst fordert eine neue ECID an.

Bei Besuchern mit Drittanbieter-Demdex-Cookies im Browser wird geprüft, ob die ECID korrekt mit der UUID im Demdex-Cookie generiert wurde. Wenn sich diese Prüfung als zutreffend erweist, wird die neue ECID identisch sein und der Besucher wird als neu betrachtet. Wenn aus irgendeinem Grund die ausgeräumte ECID nicht mit dem Demdex-Cookie generiert wurde oder kein Demdex-Cookie vorhanden ist, erhält der Besucher eine neue ECID und wird als neu betrachtet.

**Syntax:** `resetBeforeVersion = "3.3"`

**Codebeispiel**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

