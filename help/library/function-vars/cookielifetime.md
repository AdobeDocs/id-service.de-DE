---
description: Mit dieser Variablen können Sie das standardmäßige Lebensdauerintervall für das AMCV-Cookie überschreiben.
keywords: ID Service
seo-description: Mit dieser Variablen können Sie das standardmäßige Lebensdauerintervall für das AMCV-Cookie überschreiben.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 100%

---


# cookieLifetime{#cookielifetime}

Mit dieser Variablen können Sie das standardmäßige Lebensdauerintervall für das AMCV-Cookie überschreiben.

Standardmäßig laufen [!DNL Experience Cloud] ID-Dienst-Cookies nach 24 Monaten ab. Legen Sie den Zeitraum in Sekunden fest.

**Syntax:** ` cookieLifetime: *`Lebensdauer in Sekunden`*`

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

