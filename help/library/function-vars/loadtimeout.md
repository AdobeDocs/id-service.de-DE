---
description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Dient zum Ermitteln anderer Lösungen (z. B. Analytics, Audience Manager, Zielgruppe usw.) wie lange auf eine Antwort des ID-Diensts gewartet wird.
keywords: ID-Dienst
seo-description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Dient zum Ermitteln anderer Lösungen (z. B. Analytics, Audience Manager, Zielgruppe usw.) wie lange auf eine Antwort des ID-Diensts gewartet wird.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 15%

---


# loadTimeout{#loadtimeout}

Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Dient zum Ermitteln anderer Lösungen (z. B. Analytics, Audience Manager, Zielgruppe usw.) wie lange auf eine Antwort des ID-Diensts gewartet wird.

**Syntax:** ` loadTimeout: *`Intervall in Millisekunden`*`

Der Standardwert ist 30.000 Millisekunden (30 Sekunden). Es wird dringend empfohlen, den Standardwert nicht zu ändern.**

>[!NOTE]
>
>Aufrufe des ID-Dienstes erfolgen asynchron im Verhältnis zu anderem, nicht von Adobe stammendem Code auf der Seite. Infolgedessen ändert die Erhöhung oder Verringerung des Zeitüberschreitungsintervalls nicht die Rate, mit der Ihre Seite Inhalte wiedergibt. Lange Timeout-Intervalle können sich jedoch auf die Seitenladezeit auswirken, die von den üblichen Netzwerküberwachungstools gemessen wird, aber die Wiedergabedauer bleibt hiervon unberührt.

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

