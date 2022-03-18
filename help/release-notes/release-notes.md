---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '132'
ht-degree: 100%

---

# Versionshinweise zu Experience Cloud – 2020 {#release-notes}

Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity Services (ECID).

## Version 4.6

* Markierung `loadSSL` standardmäßig aktiviert. Alle Aufrufe von Identity Service sind standardmäßig auf `https` gesetzt.  Kunden können den Wert auf „false“ setzen, wenn sie Identity Services auf HTTP von ihren `non-ssl`-Seiten aufrufen möchten.
* Die Funktion zur Erkennung der `Internet-Explorer (IE)`-Version wurde aktualisiert, um ein von `ESLint` gemeldetes Problem zu beheben.
Fehlerbehebung für ein Leistungsproblem in `Internet-Explorer (IE) 11`, wenn ECID mit der OptIn-`pre-approval` versehen und später aktualisiert wurde.

## Version 4.5

* Ab Version 4.5 lehnt ECID alle leeren IDs ab, die an die `setCustomerIDs`-Methode gesendet werden.
* Es wurde ein Problem behoben, bei dem der Opt-in als `doesOptInApply=false` und `isIabContext=true` konfiguriert wurde.

Die monatlichen Versionshinweise zu allen Produkten finden Sie unter [Versionshinweise für Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de).
