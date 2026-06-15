---
description: Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.
keywords: ID-Dienst
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 87%

---

# resetBeforeVersion{#resetbeforeversion}

Diese Konfiguration ermöglicht Ihnen, verwaiste oder veraltete Experience Cloud IDs (ECIDs) basierend auf der Version des ID-Diensts, die aktualisiert wird, zu löschen.

Wenn Sie die Version Ihres ID-Diensts als Wert der Variablen `resetBeforeVersion` übergeben, werden veraltete ECIDs aus den clientseitigen IDs gelöscht.

Einige Bedingungen, wie z. B. Sitzungs-Timeouts, können dazu führen, dass eine Client-seitige ID generiert wird, ohne dass der ID-Dienst eine Server-seitige ID erhält. In diesem Fall wird eine verwaiste Client-seitige ID vom ID-Dienst verfolgt, ohne dass eine Domain-übergreifende Verfolgung oder ordnungsgemäße Synchronisierung mit anderen Lösungen möglich wäre. Durch dieses Verhalten wird die Version im aktuellen AMCV-Cookie mit dem Wert von `resetBeforeVersion` verglichen. Wenn das Cookie nicht vorhanden ist oder die Version des Cookies niedriger (älter) als die neueste veröffentlichte Version von `resetBeforeVersion` ist, wird das AMCV-Cookie entfernt und der ID-Service fordert eine neue ECID an.

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

