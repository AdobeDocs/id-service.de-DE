---
description: Eine optionale boolesche Kennzeichnung, die dem AMCV-Cookie das Attribut „Secure“ hinzufügt.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die dem AMCV-Cookie das Attribut „Secure“ hinzufügt.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---

# secureCookie {#securecookie}

Eine optionale boolesche Kennzeichnung, die dem AMCV-Cookie das Attribut „Secure“ hinzufügt.

Dieses Konfigurationsattribut ist in Version 3.3.0 der `visitorAPI` verfügbar.

>[!NOTE]
>
>Die `SecureCookie`-Konfiguration funktioniert nicht in ungesicherten Domänen und kann dazu führen, dass Sie die MID-Werte für Besuche, die ein unsicheres Protokoll verwenden, nicht erhalten. Für die `secureCookie`-Konfiguration sollte `true` nur dann festgelegt werden, wenn Sie sicher sind, dass alle Seiten und untergeordneten Domänen stets ein sicheres Protokoll verwenden.

**Syntax:** `secureCookie: true | false` (Standard)

**Codebeispiel**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
