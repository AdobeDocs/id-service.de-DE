---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
keywords: ID Service
seo-description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
seo-title: Versionshinweise für 2020
title: Versionshinweise für 2020
translation-type: ht
source-git-commit: 25a9af7a28462bc0bd26cf4a5a58203e76a83366

---


# Experience Cloud – Versionshinweise 2020 {#release-notes}

Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts (ECID).

## Version 4.5

* Ab Version 4.5 lehnt ECID alle leeren IDs ab, die an die `setCustomerIDs`-Methode gesendet werden. (CORE-38828)
* Es wurde ein Problem behoben, bei dem der Opt-in fälschlicherweise als `doesOptInApply=false` und `isIabContext=true.` konfiguriert wurde. (CORE-38351)