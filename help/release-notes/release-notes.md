---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
keywords: ID Service
seo-description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
seo-title: Versionshinweise für 2020
title: Versionshinweise für 2020
translation-type: tm+mt
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Experience Cloud – Versionshinweise 2020 {#release-notes}

Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts (ECID).

## Version 4.6

* Flag `loadSSL` standardmäßig aktiviert. Alle Aufrufe des Identitätsdienstes sind `https` standardmäßig aktiviert.  Kunden können den Wert auf &quot;false&quot;setzen, wenn sie Identity Services auf ihrer `non-ssl` Seite http aufrufen möchten.
* Die Funktion zur Erkennung der `Internet-Explorer (IE)` Version wurde aktualisiert, um ein Problem zu beheben, das von `ESLint`Ihnen gemeldet wurde.
Behebung eines Leistungsproblems, das auftrat, wenn die ECID für OptIn `Internet-Explorer (IE) 11` aktiviert `pre-approval` und später aktualisiert wurde.

## Version 4.5

* Ab Version 4.5 lehnt ECID alle leeren IDs ab, die an die `setCustomerIDs`-Methode gesendet werden.
* Fixed an issue occurring when opt-in is configured as `doesOptInApply=false` and `isIabContext=true`.
