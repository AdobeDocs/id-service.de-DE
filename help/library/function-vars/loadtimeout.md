---
description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird verwendet, um anderen Lösungen (z. B. Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange sie auf eine Antwort des ID-Diensts warten müssen.
keywords: ID-Dienst
seo-description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird verwendet, um anderen Lösungen (z. B. Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange sie auf eine Antwort des ID-Diensts warten müssen.
seo-title: loadTimeout
title: loadTimeout
uuid: f 627 e 044-bd 73-49 a 4-8 a 90-6 d 19 aa 566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# loadTimeout{#loadtimeout}

Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird verwendet, um anderen Lösungen (z. B. Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange sie auf eine Antwort des ID-Diensts warten müssen.

**Syntax:**` loadTimeout: *`interval in milliseconds`*`

Der Standardwert beträgt 30.000 Millisekunden (30 Sekunden). Es wird dringend empfohlen, dass Sie den Standardwert *nicht* ändern.

>[!NOTE]
>
>Aufrufe des ID-Diensts sind asynchron in Bezug zu anderen, nicht-Adobe-Code auf der Seite. Somit wirkt sich die Erhöhung oder Herabsetzung des Ablaufzeitraums nicht darauf aus, mit welcher Geschwindigkeit Ihre Seite Inhalte bereitstellt. Lange Ablaufzeiträume können sich auf die Ladezeit der Seite auswirken, die von geläufigen Netzwerküberwachungswerkzeugen gemessen wird, jedoch nicht auf die Bereitstellungszeit.

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

