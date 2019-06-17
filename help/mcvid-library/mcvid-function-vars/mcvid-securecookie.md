---
description: Eine optionale boolesche Kennzeichnung, die dem AMCV-Cookie das Attribut „Secure“ hinzufügt.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die dem AMCV-Cookie das Attribut „Secure“ hinzufügt.
seo-title: secureCookie
title: secureCookie
uuid: 995 d 19 f 6-9 c 9 d -4493-9 c 9 c -545 b 0 b 5696 b 0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# secureCookie{#securecookie}

Eine optionale boolesche Kennzeichnung, die dem AMCV-Cookie das Attribut „Secure“ hinzufügt.

Dieses Konfigurationsattribut ist in Version 3.3.0 der `visitorAPI` verfügbar.

>[!NOTE]
>
>Die `SecureCookie` Konfiguration funktioniert nicht bei nicht geschützten Domänen und kann dazu führen, dass Sie die MID-Werte für Besuche, die ein ungesichertes Protokoll verwenden, nicht erhalten. Für die `secureCookie`-Konfiguration sollte `true` nur dann festgelegt werden, wenn Sie sicher sind, dass alle Seiten und untergeordneten Domänen stets ein sicheres Protokoll verwenden.

**Syntax:**`secureCookie: true | false` (Standard)

**Codebeispiel**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

