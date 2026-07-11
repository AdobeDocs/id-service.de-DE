---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service.
keywords: Besucher-ID-Service
title: Versionshinweise für 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 71%

---

# Versionshinweise für 2020 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service.

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

* Markierung `loadSSL` standardmäßig aktiviert. Alle Aufrufe an den Besucher-ID-Dienst sind standardmäßig `https`.  Kunden können dies auf „false“ setzen, wenn sie den Besucher-ID-Dienst auf HTTP über ihre `non-ssl` aufrufen möchten.
* Die Funktion zur Erkennung der `Internet-Explorer (IE)`-Version wurde aktualisiert, um ein von `ESLint` gemeldetes Problem zu beheben.Fehlerbehebung für ein Performance-Problem in `Internet-Explorer (IE) 11`, wenn ECID mit der OptIn-`pre-approval` versehen und später aktualisiert wurde.

## Version 4.5

* Ab Version 4.5 lehnt ECID alle leeren IDs ab, die an die `setCustomerIDs`-Methode gesendet werden.
* Es wurde ein Problem behoben, bei dem der Opt-in als `doesOptInApply=false` und `isIabContext=true` konfiguriert wurde.

Monatliche Versionshinweise zu [CX Enterprise](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de) finden Sie in den Versionshinweisen zu allen Produkten.

