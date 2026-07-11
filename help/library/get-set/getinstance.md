---
description: getInstance gibt ein Besucher-ID-Objekt für die angegebene IMS-Organisations-ID zurück. Dies ist erforderlich, um das Besucher-ID-Objekt zu initialisieren, das AppMeasurement über s.visitor zur Verfügung gestellt wird.
keywords: Besucher-ID-Service
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
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
source-wordcount: 230
ht-degree: 55%

---

# getInstance{#getinstance}

getInstance gibt ein Besucher-ID-Objekt für die angegebene IMS-Organisations-ID zurück. Dies ist erforderlich, um das Besucher-ID-Objekt zu initialisieren, das AppMeasurement über s.visitor zur Verfügung gestellt wird.

**Syntax**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*Wichtig:* Instanziieren Sie die Visitor-Funktion nicht mit `var visitor = new Visitor`. Sie müssen den richtigen, hier aufgeführten Funktionsaufruf verwenden. Gilt für die `VisitorAPI.js` Code-Bibliothek Version 3.0 oder höher.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Wenn von `getInstance` keine bestehende Instanz gefunden wird, wird eine neue Instanz erstellt und zurückgegeben. Dies ähnelt der [`s_gi()`-Funktion &#x200B;](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=de) AppMeasurement.

**Häufige Anwendung**

Die Besucher-ID-Service-API verwaltet eine Liste aller Instanzen, die für jede IMS-Organisations-ID erstellt wurden. Wenn das Programm, das die Besucher-ID-Service-API verwendet, keinen Verweis auf die Instanz übergibt, kann es diese Instanz finden, indem es `getInstance` aufruft, anstatt eine neue Instanz zu erstellen. Damit ist auch die Unterstützung mehrerer Instanzen für verschiedene Organisationen mit derselben Webseite oder Anwendung möglich.

Dies ist für Programme nützlich, die keine klare `init` haben, aber an mehreren Stellen in die Besucher-ID-Service-API aufrufen müssen. Sie können `getInstance` an sämtlichen Orten aufrufen und der erste ausgeführte Aufruf führt zur Erstellung der Instanz. Die bestehende Instanz wird durch nachfolgende Aufrufe zurückgegeben.

