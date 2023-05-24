---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2021
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
workflow-type: tm+mt
source-wordcount: '103'
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

* Mit dieser Version wird eine Ereignis-`onRecieveEcid` eingeführt, die aufgerufen wird, wenn eine ECID vom Identity Service empfangen wird. Beispiel:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
