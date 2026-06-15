---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
TQID: https://experienceleague.adobe.com/AB8VuYn9X41P9REJ8C215GzBRtH66lb35i-q1PNbZfU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 110
ht-degree: 100%

---

# Versionshinweise zu Experience Cloud Identity Service – 2021

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Service.

## Visitor 5.3.0

In der Version Visitor 5.3.0 wurden folgende Aktualisierungen vorgenommen:

* Der Algorithmus wurde aktualisiert, um eine lokale ECID zu generieren.
* Neuestes Opt-in mit `Secure`- und `SameSite`-Flags für Datenschutz-Cookie.
* Fehlerbehebung für ein Problem mit dem Firefox-Browser, wenn eine Seite in einen untergeordneten iFrame geladen wird.

## Visitor 5.2.0

Die folgenden Aktualisierungen wurden in der Version Visitor 5.2.0 hinzugefügt:

* Mit dieser Version wird eine Ereignis-`onReceiveEcid` eingeführt, die aufgerufen wird, wenn eine ECID vom Identity Service empfangen wird. Beispiel:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```

