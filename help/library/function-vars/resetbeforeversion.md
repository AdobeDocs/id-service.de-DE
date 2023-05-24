---
description: Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.
keywords: ID-Dienst
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 100%

---

# resetBeforeVersion{#resetbeforeversion}

Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.

Wenn Sie die Version Ihres ID-Diensts als Wert der Variablen `resetBeforeVersion` übergeben, werden veraltete ECIDs aus den clientseitigen IDs gelöscht.

Einige Bedingungen, wie z. B. Sitzungs-Timeouts, können dazu führen, dass eine Client-seitige ID generiert wird, ohne dass der ID-Dienst eine Server-seitige ID erhält. In diesem Fall wird eine verwaiste Client-seitige ID vom ID-Dienst verfolgt, ohne dass eine Domain-übergreifende Verfolgung oder ordnungsgemäße Synchronisierung mit anderen Lösungen möglich wäre. Durch dieses Verhalten wird die Version im aktuellen AMCV-Cookie mit dem Wert von `resetBeforeVersion` verglichen. Wenn das Cookie nicht vorhanden ist oder die Version des Cookies kleiner (älter) als die neueste veröffentlichte Version von `resetBeforeVersion` ist, dann wird das AMCV-Cookie entfernt und der ID-Dienst fordert eine neue ECID an.

Bei Besuchern mit Drittanbieter-Demdex-Cookies im Browser wird geprüft, ob die ECID korrekt mit der UUID im Demdex-Cookie generiert wurde. Wenn sich diese Prüfung als zutreffend erweist, wird die neue ECID identisch sein und der Besucher wird als neu angesehen. Wenn aus irgendeinem Grund die bereinigte ECID nicht mit dem Demdex-Cookie generiert wurde oder kein Demdex-Cookie vorhanden ist, erhält der Besucher eine neue ECID und wird als neu angesehen.

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
