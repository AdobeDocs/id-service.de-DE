---
description: Eine optionale boolesche Kennzeichnung, die dem AMCV-Cookie das Attribut „Secure“ hinzufügt.
keywords: ID-Dienst
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 100%

---

# secureCookie{#securecookie}

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
