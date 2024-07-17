---
description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Dient dazu, anderen Lösungen (Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange auf eine Antwort des ID-Diensts gewartet werden soll.
keywords: ID-Dienst
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 100%

---

# loadTimeout{#loadtimeout}

Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Dient dazu, anderen Lösungen (Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange auf eine Antwort des ID-Diensts gewartet werden soll.

**Syntax:** ` loadTimeout: *`Intervall in Millisekunden`*`

Der Standardwert ist 30.000 Millisekunden (30 Sekunden). Es wird dringend empfohlen, den Standardwert *nicht* zu ändern.

>[!NOTE]
>
>Aufrufe des ID-Dienstes erfolgen asynchron im Verhältnis zu anderem, nicht von Adobe stammendem Code auf der Seite. Infolgedessen ändert die Erhöhung oder Verringerung des Zeitüberschreitungsintervalls nicht die Rate, mit der Ihre Seite Inhalte wiedergibt. Lange Zeitüberschreitungsintervalle können sich auf die Seitenladezeit auswirken, die von den üblichen Netzwerküberwachungs-Tools gemessen wird; aber die Wiedergabedauer bleibt jedoch hiervon unberührt.

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
