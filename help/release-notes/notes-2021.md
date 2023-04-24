---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2021
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 27%

---

# Experience Cloud Identity Service - Versionshinweise 2021

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.

## Besucher 5.3.0

In der Version Visitor 5.3.0 wurden folgende Aktualisierungen vorgenommen:

* Der Algorithmus wurde aktualisiert, um eine lokale ECID zu generieren.
* Neueste Opt-in-Funktion mit `Secure` und `SameSite` Flags für Datenschutz-Cookie.
* Patch-Korrektur für ein Firefox-Browserproblem, wenn eine Seite in einen untergeordneten iFrame geladen wird.

## Besucher 5.2.0

Die folgenden Aktualisierungen wurden in der Version Visitor 5.2.0 hinzugefügt:

* Mit dieser Version wird ein Ereignis eingeführt `onRecieveEcid`, der aufgerufen wird, wenn eine ECID vom Identity Service empfangen wird. Beispiel:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
