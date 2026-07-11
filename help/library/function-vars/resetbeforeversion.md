---
description: Mit dieser Konfiguration können Sie verwaiste oder veraltete ECIDs (ECIDs) löschen, je nachdem, welche Version des Besucher-ID-Service aktualisiert wird.
keywords: Besucher-ID-Service
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 257
ht-degree: 41%

---

# resetBeforeVersion{#resetbeforeversion}

Mit dieser Konfiguration können Sie verwaiste oder veraltete ECIDs (ECIDs) löschen, je nachdem, welche Version des Besucher-ID-Service aktualisiert wird.

Wenn Sie Ihre Version des Besucher-ID-Service als Wert der `resetBeforeVersion`-Variablen angeben, werden veraltete ECIDs aus Client-seitigen IDs gelöscht.

Einige Bedingungen, wie Sitzungs-Timeouts, können manchmal dazu führen, dass eine Client-seitige ID generiert wird, ohne dass der Besucher-ID-Service eine Server-seitige ID erhält. In diesem Fall wird eine verwaiste Client-seitige ID vom Besucher-ID-Service verfolgt, ohne dass domänenübergreifend verfolgt oder eine ordnungsgemäße Synchronisierung mit anderen Lösungen möglich ist. Durch dieses Verhalten wird die Version im aktuellen AMCV-Cookie mit dem Wert von `resetBeforeVersion` verglichen. Wenn das Cookie nicht vorhanden ist oder die Version des Cookies niedriger (älter) als die neueste veröffentlichte Version von `resetBeforeVersion` ist, wird das AMCV-Cookie entfernt und der Besucher-ID-Dienst fordert eine neue ECID an.

Bei Besuchern mit Drittanbieter-Demdex-Cookies im Browser wird geprüft, ob die ECID korrekt mit der UUID im Demdex-Cookie generiert wurde. Wenn sich diese Prüfung als zutreffend erweist, wird die neue ECID identisch sein und der Besucher wird als neu angesehen. Wenn aus irgendeinem Grund die bereinigte ECID nicht mit dem Demdex-Cookie generiert wurde oder kein Demdex-Cookie vorhanden ist, erhält der Besucher eine neue ECID und wird als neu angesehen.

**Syntax:** `resetBeforeVersion = "3.3"`

**Codebeispiel**

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
  
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

