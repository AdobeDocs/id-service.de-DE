---
description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird für andere Lösungen verwendet (z. B. Analytics, Audience Manager, Target usw.) Wie lange auf eine Antwort des ID-Service gewartet wird.
keywords: ID-Dienst
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 143
ht-degree: 69%

---

# loadTimeout{#loadtimeout}

Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird für andere Lösungen verwendet (z. B. Analytics, Audience Manager, Target usw.) Wie lange auf eine Antwort des ID-Service gewartet wird.

**Syntax:** `loadTimeout: *`Intervall in Millisekunden`*`

Der Standardwert ist 30.000 Millisekunden (30 Sekunden). Es wird dringend empfohlen, den Standardwert *nicht* zu ändern.

>[!NOTE]
>
>Aufrufe des ID-Dienstes erfolgen asynchron im Verhältnis zu anderem, nicht von Adobe stammendem Code auf der Seite. Infolgedessen ändert die Erhöhung oder Verringerung des Zeitüberschreitungsintervalls nicht die Rate, mit der Ihre Seite Inhalte wiedergibt. Lange Zeitüberschreitungsintervalle können sich auf die Seitenladezeit auswirken, die von den üblichen Netzwerk-Monitoring-Tools gemessen wird; aber die Wiedergabedauer bleibt jedoch hiervon unberührt.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

