---
description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird verwendet, um anderen Lösungen (z. B. Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange sie auf eine Antwort des ID-Diensts warten müssen.
keywords: ID-Dienst
seo-description: Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird verwendet, um anderen Lösungen (z. B. Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange sie auf eine Antwort des ID-Diensts warten müssen.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# loadTimeout{#loadtimeout}

Legt ein Zeitüberschreitungsintervall in Millisekunden fest. Wird verwendet, um anderen Lösungen (z. B. Analytics, Audience Manager, Target usw.) mitzuteilen, wie lange sie auf eine Antwort des ID-Diensts warten müssen.

**Syntax:** ` loadTimeout: *`Intervall in Millisekunden`*`

Der Standardwert beträgt 30.000 Millisekunden (30 Sekunden). Es wird dringend empfohlen, dass Sie den Standardwert *nicht* ändern.

>[!NOTE]
>
>Aufrufe des ID-Dienstes erfolgen asynchron im Verhältnis zu anderem, nicht von Adobe stammendem Code auf der Seite. Somit wirkt sich die Erhöhung oder Herabsetzung des Ablaufzeitraums nicht darauf aus, mit welcher Geschwindigkeit Ihre Seite Inhalte bereitstellt. Lange Ablaufzeiträume können sich auf die Ladezeit der Seite auswirken, die von geläufigen Netzwerküberwachungswerkzeugen gemessen wird, jedoch nicht auf die Bereitstellungszeit.

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

