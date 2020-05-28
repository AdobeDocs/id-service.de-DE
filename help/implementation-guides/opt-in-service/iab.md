---
description: Verbinden der Consent Management Platform (CMP) mit dem Audience Manager-Plugin der Opt-in-Funktion für das IAB Transparency and Consent Framework (TCF).
seo-description: Verbinden der Consent Management Platform (CMP) mit dem Audience Manager-Plugin für IAB Transparency and Consent Framework (TCF).
seo-title: Nutzung von Opt-in-Diensten mit IAB Framework
title: Nutzung von Opt-in-Diensten mit IAB Framework
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 66%

---


# Nutzung von Opt-in-Diensten mit IAB Framework {#using-opt-in-services-with-iab-framework}

Verbinden der Consent Management Platform (CMP) mit dem Audience Manager-Plugin der Opt-in-Funktion für IAB TCF.

Audience Manager-Kunden, die das [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) verwenden, können ihre Consent Management Platform (CMP) mit dem Opt-in-Audience Manager-Plugin für IAB TCF verbinden. Opt-in ist eine Funktion, die in die JavaScript-Bibliothek von ECID eingebettet ist und abhängig von den in einer CMP festgelegten Besuchervoreinstellungen einzelne Adobe-Lösungsbibliotheken deaktivieren kann. Wenn das Audience Manager-Plug-in für die IAB-TCF mit der ECID-Bibliothek implementiert ist, werden die Voreinstellungen des Besuchers in Ihrem CMP, der die IAB-TCF unterstützt, automatisch der Opt-in-Funktion zugeordnet. Diese Einstellungen ermöglichen es, Audience Manager-basierte Bibliotheken (DIL und ECID) und zugehörige Anrufe nach Erhalt der Zustimmung zu aktivieren.

## Implementieren einer CMP mit IAB-Unterstützung {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Damit das Opt-In mit dem IAB-TCF integriert werden kann, müssen Sie Folgendes ausführen:

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. Definieren/Laden Sie `__cmp`, bevor Sie Adobe-JS laden.

Weitere Details finden Sie in den [Dokumenten des Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Aktivieren Sie das Audience Manager-Plugin für IAB TCF in Ihrer ECID-Javascript-Bibliothek {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Die Teilnahme ist nur in ECID 4.0+ verfügbar.

Verwenden Sie Adobe Experience Platform Launch, um sowohl Opt-in als auch das Audience Manager-Plugin für IAB TCF für Ihre Site zu implementieren. Wenn Sie IAB für die manuelle Teilnahme aktivieren, überprüfen Sie, ob die folgenden Einstellungen im Besucher-Objekt auf &quot;true&quot;gesetzt sind:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Sobald die Einstellungen korrekt konfiguriert sind, werden die ECID- und DIL-Bibliotheken je nach Genehmigungskriterien des CMP und der IAB-TCF aktiviert/deaktiviert.

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. Weitere Informationen zum Audience Manager-Plugin für IAB TCF finden Sie in der Audience Manager-Dokumentation [hier](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

Weitere Informationen zum Validieren des Opt-in-Objekts und des Audience Manager-Plugins für IAB TCF finden Sie in Nutzungsszenario 4 des Validierungsleitfadens [hier](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwandte Dokumentation {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): Hier finden Sie weitere Informationen zum IAB-Standard.
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) – Hier finden Sie weitere Informationen zu Opt-in, einer erforderlichen Komponente für die Zustimmungsverwaltung in Platform-Lösungen
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [Ihre Auswahlmöglichkeiten bezüglich Datenschutz](https://www.adobe.com/de/privacy/opt-out.html#customeruse) – Ihre Benutzer haben auch die Möglichkeit, die Datenerfassung mit anderen globalen Opt-out-Tools abzulehnen. Globale Ausschlussoption hat Vorrang vor der TCF-Überprüfung für die Teilnahme und die IAB

