---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 99%

---

# Versionshinweise zu Experience Cloud – 2020 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Service.

## Version 5.1.1

* Patch-Fehlerbehebung für das Setzen des AMCV-Cookies mit `SameSite=None`, wenn VisitorJS in einen iFrame geladen wird.

## Version 5.1.0

* Hinzufügen der Konfiguration `sameSiteCookie`, um das `SameSite`-Attribut des AMCV-Cookies zu spezifizieren. Diese Konfiguration unterstützt die folgenden Werte für das `SameSite`-Attribut:
   * `Strict`
   * `Lax`
   * `None`

Weitere Informationen zu diesen Attributwerten finden Sie unter [web.dev](https://web.dev/samesite-cookies-explained/) und [SameSite-Aktualisierungen durch die Chromium-Projekte](https://www.chromium.org/updates/same-site/).

## Version 5.0.1

* Patch-Fehlerbehebung für das Einschließen eines Flags `d_cf`, wenn eine neue Zeichenfolge für IAB-Einverständnis an die Datenerfassungs-Edges von Adobe gesendet wird.

## Version 5.0.0

* Visitor 5.0.0 mit Unterstützung für `IAB 2.0`.

## Version 4.6

* Markierung `loadSSL` standardmäßig aktiviert. Alle Aufrufe von Identity Service sind standardmäßig auf `https` gesetzt.  Kunden können den Wert auf „false“ setzen, wenn sie Identity Services auf HTTP von ihren `non-ssl`-Seiten aufrufen möchten.
* Die Funktion zur Erkennung der `Internet-Explorer (IE)`-Version wurde aktualisiert, um ein von `ESLint` gemeldetes Problem zu beheben.
Fehlerbehebung für ein Performance-Problem in `Internet-Explorer (IE) 11`, wenn ECID mit der OptIn-`pre-approval` versehen und später aktualisiert wurde.

## Version 4.5

* Ab Version 4.5 lehnt ECID alle leeren IDs ab, die an die `setCustomerIDs`-Methode gesendet werden.
* Es wurde ein Problem behoben, bei dem der Opt-in als `doesOptInApply=false` und `isIabContext=true` konfiguriert wurde.

Die monatlichen Versionshinweise zu allen Produkten finden Sie unter [Versionshinweise für Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de).
