---
description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Dient dazu, anderen Lösungen (Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange auf eine Antwort des ID-Diensts gewartet werden soll.
keywords: ID-Dienst
seo-description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Dient dazu, anderen Lösungen (Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange auf eine Antwort des ID-Diensts gewartet werden soll.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
exl-id: 485264f4-ee24-4042-8be3-259e70462110
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '169'
ht-degree: 100%

---

# loadTimeout {#loadtimeout}

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
