---
description: Verbinden Sie ihre CMP (Approval Management Platform) mit dem IAB-Plugin für die Anmeldung.
seo-description: Verbinden Sie ihre CMP (Approval Management Platform) mit dem IAB-Plugin für die Anmeldung.
seo-title: (Beta) Verwenden von Anmeldediensten mit IAB Framework
title: (Beta) Verwenden von Anmeldediensten mit IAB Framework
uuid: 8 df 39 d 9 c-c 016-490 e-b 4 db-d 02 e 4044 b 480
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# (Beta) Verwenden von Anmeldediensten mit IAB Framework{#beta-using-opt-in-services-with-iab-framework}

Verbinden Sie ihre CMP (Approval Management Platform) mit dem IAB-Plugin für die Anmeldung.

Audience Manager-Kunden, die [IAB-Transparenz- und -bestätigungsframework (TCF) verwenden,](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) können ihre CMP (Approval Management Platform) mit dem IAB-Plugin für die Anmeldung verbinden. Die Teilnahme an der Teilnahme ist eine Funktion, die in der ECID javascript-Bibliothek eingebettet ist und die einzelnen Adobe-Lösungsbibliotheken je nach den in einer CMP festgelegten Besuchervoreinstellungen deaktivieren kann. Wenn das IAB-Plugin mit der ECID-Bibliothek implementiert ist, werden die Benutzerpräferenzen aus Ihrem IAB-kompatiblen CMP automatisch der Teilnahme zugeordnet. Diese Voreinstellungen ermöglichen die Aktivierung von Audience Manager-basierten Bibliotheken (DIL und ECID) und zugeordneten Aufrufen, wenn die Zustimmung erhalten wird.

## Implementieren einer CMP mit IAB-Unterstützung {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Führen Sie folgende Schritte aus, um das Opt-in-Objekt in die IAB-Zustimmung zu integrieren:

1. Implementieren Sie eine CMP, die IAB unterstützt und [als IAB-Anbieter registriert ist](https://vendorlist.consensu.org/vendorlist.json), oder entwickeln Sie intern eine CMP, die den IAB-Spezifikationen entspricht, und registrieren Sie diese bei IAB Europe.
1. Definieren/Laden Sie das Laden `__cmp` von Adobe JS.

Weitere Details finden Sie in den [Dokumenten des Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Aktivieren des IAB-Plug-ins in Ihrer ECID-Javascript-Bibliothek {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Die Teilnahme ist nur in ECID 4.0 + verfügbar.

Verwenden Sie Adobe Launch, um sowohl Opt-in als auch das IAB-Plug-in für Ihre Site zu implementieren. Informationen zur Einrichtung der Launch-Erweiterung finden Sie in der [Dokumentation zur ECID-Opt-in-Erweiterung](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/).

Wenn Sie IAB für Opt-in manuell aktivieren, vergewissern Sie sich, dass für die folgenden Einstellungen im Visitor-Objekt „true“ festgelegt ist:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Sobald die Einstellungen ordnungsgemäß konfiguriert sind, werden die ECID- und DIL-Bibliotheken abhängig von den Zustimmungskriterien des CMP- und IAB-Framework aktiviert bzw. deaktiviert.

>[!IMPORTANT]
>
>Audience Manager benötigt eine Zustimmung für die *Zwecke 1, 2 und 5 und die Zustimmung des Anbieters*, um Cookies bereitzustellen und ID-Synchronisationen zu starten oder zu berücksichtigen. Weitere Informationen zum IAB-Plugin in der Audience Manager-Dokumentation** [finden Sie hier](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)**.

Weitere Informationen zum Validieren des Opt-in-Objekts und des IAB-Plug-ins finden Sie in Nutzungsszenario 4 des Validierungsleitfadens [**hier** ](../../mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwandte Dokumentation {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): Hier finden Sie weitere Informationen zum IAB-Standard.
* [Adobe Opt-in](../../mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): Hier finden Sie weitere Informationen zu Opt-in, einer erforderlichen Komponente für die Zustimmungsverwaltung in Plattformlösungen.
* Unterstützung des IAB Transparency and Consent Framework (TCF) in [Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Ihre Auswahlmöglichkeiten bezüglich Datenschutz](https://www.adobe.com/privacy/opt-out.html#customeruse): Eine weitere Option, die Ihren Benutzern zum Schutz ihrer Daten zur Verfügung steht, ist die Möglichkeit, die Datenerfassung mit anderen globalen Opt-out-Tools abzulehnen. Globales Opt-out hat Vorrang vor der Opt-in- und IAB-Überprüfung.

