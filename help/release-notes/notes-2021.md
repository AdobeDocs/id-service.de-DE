---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: tm+mt
source-wordcount: '113'
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
