---
description: Erforderlich für mehrteilige Top-Level-Domänen, bei denen einer der letzten zwei Teile der URL mehr als 2 Zeichen umfasst.
keywords: ID-Dienst
seo-description: Erforderlich für mehrteilige Top-Level-Domänen, bei denen einer der letzten zwei Teile der URL mehr als 2 Zeichen umfasst.
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieDomain{#cookiedomain}

Erforderlich für mehrteilige Top-Level-Domänen, bei denen einer der letzten zwei Teile der URL mehr als 2 Zeichen umfasst.

**Syntax:** ` cookieDomain: " *`URL`*"` (Das `www` Präfix ist nicht erforderlich.)

**Anwendungsfall**

* Erforderlich: `www.example.com.uk`
* Nicht erforderlich: `www.example.co.uk`

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

