---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.
keywords: domänenübergreifende Verfolgung; ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e 92 ce 1 f 5-67 a 4-476 c -9 d 04-41 d 4 e 96 b 1592
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.

**Syntax:**` `Disablethirdpartycalls: true | false «(Standard ist `false`.)

Bei `disableThirdPartyCalls: true` gibt der ID-Dienst keine Aufrufe an andere Domänen aus.

**Zielsetzung**

Diese Variable richtet sich an Kunden:

* die verhindern müssen, dass der ID-Dienst Aufrufe über ihre sicheren, authentifizierten Seiten ausführt,
* deren Site-Besucher über eine Experience Cloud ID (MID) verfügen müssen,
* deren andere Experience Cloud-Lösungen ordnungsgemäß funktionieren müssen.

**Implementierungsstrategie**

Da andere Experience Cloud-Lösungen auf der MID basieren, ruft der ID-Dienst Adobe zum Zurückgeben und Festlegen dieser ID auf. Wenn Sie verhindern müssen, dass der ID-Dienst Aufrufe über authentifizierte Abschnitte Ihrer Website tätigt, sollten Sie diese erforderlichen Aufrufe über Seiten zulassen, für die zunächst keine Authentifizierung erforderlich ist. Wenn Ihr Sitebesucher über eine MID verfügt, können Sie `disableThirdPartyCalls= true` im ID-Dienstcode auf die authentifizierten Abschnitte Ihrer Site festlegen. Es wird hierbei angenommen, dass die meisten, wenn nicht sogar alle Ihrer Kunden vor dem Zugriff auf sichere Bestandteile Ihrer Site zu einer Authentifizierungsseite navigieren.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

