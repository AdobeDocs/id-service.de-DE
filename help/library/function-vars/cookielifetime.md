---
description: Mit dieser Variablen können Sie das standardmäßige Lebensdauerintervall für das AMCV-Cookie überschreiben.
keywords: ID-Dienst
seo-description: Mit dieser Variablen können Sie das standardmäßige Lebensdauerintervall für das AMCV-Cookie überschreiben.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd 945 db 3-429 a -4625-ac 3 f -69 ac 259377 a 3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieLifetime{#cookielifetime}

Mit dieser Variablen können Sie das standardmäßige Lebensdauerintervall für das AMCV-Cookie überschreiben.

Standardmäßig laufen [!DNL Experience Cloud] ID-Dienst-Cookies nach 24 Monaten ab. Legen Sie den Zeitraum in Sekunden fest.

**Syntax:**` cookieLifetime: *`Lebensdauer in Sekunden`*`

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```

