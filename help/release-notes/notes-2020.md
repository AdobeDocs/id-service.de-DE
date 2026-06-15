---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 216
ht-degree: 91%

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
* Die Funktion zur Erkennung `Internet-Explorer (IE)` Version wurde aktualisiert, um ein von `ESLint` gemeldetes Problem zu beheben.
Behebung von Leistungsproblemen bei `Internet-Explorer (IE) 11`, wenn ECID Opt-in-`pre-approval` erhält und später aktualisiert wird.

## Version 4.5

* Ab Version 4.5 lehnt ECID alle leeren IDs ab, die an die `setCustomerIDs`-Methode gesendet werden.
* Es wurde ein Problem behoben, bei dem der Opt-in als `doesOptInApply=false` und `isIabContext=true` konfiguriert wurde.

Die monatlichen Versionshinweise zu allen Produkten finden Sie unter [Versionshinweise für Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de).

