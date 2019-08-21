---
description: Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.
keywords: ID-Dienst
seo-description: Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetBeforeVersion{#resetbeforeversion}

Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.

Wenn Sie die Version Ihres ID-Diensts als Wert der Variablen `resetBeforeVersion` übergeben, werden veraltete ECIDs aus den clientseitigen IDs gelöscht.

Unter bestimmten Bedingungen, beispielsweise bei Sitzungs-Timeouts, kann eine clientseitige ID generiert werden, ohne dass der ID-Dienst eine serverseitige ID erhält. In diesen Fällen verfolgt der ID-Dienst eine verwaiste clientseitige ID, für die kein domänenübergreifendes Tracking oder eine Synchronisierung mit anderen Lösungen möglich ist. Durch dieses Verhalten wird die Version im aktuellen AMCV-Cookie mit dem Wert von `resetBeforeVersion` verglichen. Wenn das Cookie nicht vorhanden ist oder die Version des Cookies kleiner (älter) als die neueste veröffentlichte Version von `resetBeforeVersion` ist, dann wird das AMCV-Cookie entfernt und der ID-Dienst fordert eine neue ECID an.

Bei Besuchern mit Drittanbieter-Demdex-Cookies im Browser wird geprüft, ob die ECID korrekt mit der UUID im Demdex-Cookie generiert wurde. Wenn dies zutrifft, dann bleibt die neue ECID gleich und der Besucher gilt als neu. Wenn die zu löschende ECID aus einem beliebigen Grund nicht mithilfe des Demdex-Cookies generiert wurde oder wenn kein Demdex-Cookie vorhanden ist, erhält der Besucher eine neue ECID und gilt als neu.

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

