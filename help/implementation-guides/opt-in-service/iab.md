---
description: Verbinden der Consent Management Platform (CMP) mit dem Audience Manager-Plugin der Opt-in-Funktion für das IAB Transparency and Consent Framework (TCF).
seo-description: Verbinden der Consent Management Platform (CMP) mit dem Audience Manager-Plugin für IAB Transparency and Consent Framework (TCF).
seo-title: (Beta) Nutzung von Opt-in-Diensten mit IAB Framework
title: (Beta) Nutzung von Opt-in-Diensten mit IAB Framework
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: ab85467ad0f9f661c472eb373809c699c4b9130f

---


# (Beta) Nutzung von Opt-in-Diensten mit IAB Framework {#beta-using-opt-in-services-with-iab-framework}

Schließen Sie die Consent Management Platform (CMP) mit dem Audience Manager-Plugin für IAB TCF von Opt-in an.

Audience Manager-Kunden, die das [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) verwenden, können ihre Consent Management Platform (CMP) mit dem Opt-in-Audience Manager-Plugin für IAB TCF verbinden. Opt-in ist eine Funktion, die in die JavaScript-Bibliothek von ECID eingebettet ist und abhängig von den in einer CMP festgelegten Besuchervoreinstellungen einzelne Adobe-Lösungsbibliotheken deaktivieren kann. Wenn das Audience Manager-Plugin für IAB TCF mit der ECID-Bibliothek implementiert wird, werden die Besucherpräferenzen aus Ihrer IAB-konformen CMP automatisch dem Opt-in zugeordnet. Diese Einstellungen ermöglichen es, Audience Manager-basierte Bibliotheken (DIL und ECID) und zugehörige Anrufe nach Erhalt der Zustimmung zu aktivieren.

## Implementieren einer CMP mit IAB-Unterstützung {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Führen Sie folgende Schritte aus, um das Opt-in-Objekt in die IAB-Zustimmung zu integrieren:

1. Implementieren Sie eine CMP, die das IAB unterstützt und [als IAB-Anbieter registriert ist](https://vendorlist.consensu.org/vendorlist.json), oder entwickeln Sie intern eine CMP, die den IAB-Spezifikationen entspricht, und registrieren Sie diese bei IAB Europe.
1. Definieren/Laden Sie `__cmp`, bevor Sie Adobe-JS laden.

Weitere Details finden Sie in den [Dokumenten des Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Enable the Audience Manager plug-in for IAB TCF within your ECID Javascript Library {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in ist nur in ECID 4.0 oder höher verfügbar.

Verwenden Sie Adobe Experience Platform Launch, um sowohl Opt-in als auch das Audience Manager-Plugin für IAB TCF für Ihre Site zu implementieren. Wenn Sie IAB für Opt-in manuell aktivieren, vergewissern Sie sich, dass für die folgenden Einstellungen im Visitor-Objekt „true“ festgelegt ist:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Sobald die Einstellungen ordnungsgemäß konfiguriert sind, werden die ECID- und DIL-Bibliotheken abhängig von den Zustimmungskriterien des CMP- und IAB-Framework aktiviert bzw. deaktiviert.

>[!IMPORTANT]
>
>Audience Manager benötigt eine Zustimmung für die *Zwecke 1, 2 und 5 und die Zustimmung des Anbieters*, um Cookies bereitzustellen und ID-Synchronisationen zu starten bzw. zu berücksichtigen. Weitere Informationen zum Audience Manager-Plugin für IAB TCF in der Audience Manager-Dokumentation [finden Sie](https://docs.adobe.com/help/en/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)hier.

For more information on how to validate both Opt-in and the Audience Manager plug-in for IAB TCF, check use case #4 in the validation guide [here](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwandte Dokumentation {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): Hier finden Sie weitere Informationen zum IAB-Standard.
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) – Hier finden Sie weitere Informationen zu Opt-in, einer erforderlichen Komponente für die Zustimmungsverwaltung in Platform-Lösungen
* Unterstützung des IAB Transparency and Consent Framework (TCF) in [Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Ihre Auswahlmöglichkeiten bezüglich Datenschutz](https://www.adobe.com/privacy/opt-out.html#customeruse) – Ihre Benutzer haben auch die Möglichkeit, die Datenerfassung mit anderen globalen Opt-out-Tools abzulehnen. Globales Opt-out hat Vorrang vor der Opt-in- und IAB-Überprüfung.

