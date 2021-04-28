---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
keywords: ID-Dienst
seo-description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
seo-title: Versionshinweise für 2020
title: Versionshinweise für 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '147'
ht-degree: 100%

---

# Experience Cloud – Versionshinweise 2020 {#release-notes}

Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts (ECID).

## Version 4.6

* Markierung `loadSSL` standardmäßig aktiviert. Alle Aufrufe von Identity Service sind standardmäßig auf `https` gesetzt.  Kunden können den Wert auf „false“ setzen, wenn sie Identity Services auf HTTP von ihren `non-ssl`-Seiten aufrufen möchten.
* Die Funktion zur Erkennung der `Internet-Explorer (IE)`-Version wurde aktualisiert, um ein von `ESLint` gemeldetes Problem zu beheben.
Fehlerbehebung für ein Leistungsproblem in `Internet-Explorer (IE) 11`, wenn ECID mit der OptIn-`pre-approval` versehen und später aktualisiert wurde.

## Version 4.5

* Ab Version 4.5 lehnt ECID alle leeren IDs ab, die an die `setCustomerIDs`-Methode gesendet werden.
* Es wurde ein Problem behoben, bei dem der Opt-in als `doesOptInApply=false` und `isIabContext=true` konfiguriert wurde.

Die monatlichen Versionshinweise zu allen Produkten finden Sie unter [Versionshinweise für Experience Cloud](https://docs.adobe.com/content/help/de-DE/release-notes/experience-cloud/current.html).
