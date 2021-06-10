---
description: Implementieren Sie den Opt-in-Dienst als einheitlichen Bezugspunkt für Experience Cloud-Lösungen (bei Opt-in als „Kategorien“ bezeichnet), um zu ermitteln, ob Cookies auf dem Gerät eines Besuchers erstellt werden dürfen.
title: Einrichten des Opt-in-Dienstes
exl-id: 6e8a6531-9924-4523-a842-cb4614a7a7a0
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 99%

---

# Einrichten des Opt-in-Dienstes {#setting-up-opt-in-service}

Implementieren Sie den Opt-in-Dienst als einheitlichen Bezugspunkt für Experience Cloud-Lösungen (bei Opt-in als „Kategorien“ bezeichnet), um zu ermitteln, ob Cookies auf dem Gerät eines Besuchers erstellt werden dürfen.

Der Opt-in-Dienst ist eine JavaScript-Bibliothek, die mit Experience Cloud ID (ECID) verknüpft ist und in Visitor JS im globalen `adobe`-Objekt als `adobe.optIn`-Objekt enthalten ist. Nachdem Sie den Opt-in-Dienst installiert haben, können Sie festlegen, ob ein Besucher allen Adobe-Lösungen gleichzeitig zustimmen kann oder die Lösungen dem Besucher einzeln angezeigt werden, um seine Zustimmung einzuholen. Der Opt-in-Dienst zur Zustimmungsverwaltung kann mit verschiedenen Konfigurationen abhängig von Ihren speziellen Datenschutzanforderungen implementiert werden.

Mit dem Opt-in-Dienst können Sie festlegen, ob ein Besucher allen Adobe-Lösungen gleichzeitig zustimmen kann oder die Lösungen dem Besucher einzeln angezeigt werden, um seine Zustimmung einzuholen. Sobald der Genehmigungsprozess abgeschlossen und vom Kunden aufgezeichnet wurde, können CMP-Besuchergenehmigungen von allen Adobe-Lösungen abgerufen werden, um mit entsprechenden Zustimmungsaufrufen zu reagieren.

## Voraussetzungen  {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID Version 4.0.

   [Laden](https://github.com/Adobe-Marketing-Cloud/id-service/releases) Sie unsere neueste ECID-Version herunter.

1. Unterstützungsbibliotheken:

   * ECID 4.0 oder höher
   * AppMeasurement 2.11 oder höher
   * DIL 9.0
   * AT.js Version 1.7.0
   * AT.js Launch-Erweiterung, Version 9.0
   * Für Analytics: App Measurement 2.11 mit Erweiterung 1.6
   * Für Target: Erweiterung 0.9.1

1. Machen Sie sich mit dem Framework zur Zustimmungsverwaltung vertraut, das Sie mit Opt-in verwenden, und stellen Sie sicher, dass Sie alle zusätzlichen Voraussetzungen überblicken.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Die Datenschutzanforderungen Ihrer Firma richten sich danach, für welche Art der GDPR-Konformität Sie sich entscheiden. Beachten Sie, welche vordefinierten Bibliotheken für die Datenschutz-Teams Ihrer Firma in Ordnung sind.

Wenn Sie [Adobe Launch](https://experienceleague.adobe.com/docs/launch/using/home.html) verwenden, nutzen Sie die [Opt-in-Erweiterung](../../implementation-guides/opt-in-service/launch.md), um den Opt-in-Dienst zu konfigurieren.

## Opt-in-Kategorien {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Die Opt-in-Voreinstellungen eines Besuchers beziehen sich auf eine Adobe Experience Cloud-Lösung, wobei jede Lösung einer Kategorie entspricht. Kategorien werden durch das `adobe.OptInCategories` Objekt bereitgestellt. Die ECID-Komponente entspricht beispielsweise `adobe.OptInCategories`. `ECID`. Die Definition von `adobe.OptInCategories` lautet:

Opt-in-Einstellungen werden pro Kategorie verwaltet, wobei jede Experience Cloud-Lösung einer Kategorie entspricht:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Mit dem Opt-in-Dienst können Sie die Berechtigungsvoreinstellungen der Besucher für jede Adobe-Lösung auf Ihrer Site festlegen. Das Objekt umfasst eine Bibliothek zum Speichern der Einstellungen eines Besuchers nach genehmigter Kategorie und unterstützt einen sequenziellen Ablauf, bei dem der Genehmigungsprozess Voreinstellungen zum Bestätigen oder Ablehnen jeder Kategorie erhält. Sie können festlegen, dass den Lösungen/Kategorien gleichzeitig oder einzeln zugestimmt wird. 
Die clientseitigen Bibliotheken aller Adobe-Lösungen sind vom Opt-in-Dienst abhängig. Es werden nur Cookies generiert, wenn eine Berechtigung dafür erteilt wurde. Opt-in unterstützt verschiedene Ansätze zur Bereitstellung und Aktualisierung von Zustimmungseinstellungen für den aktuellen Besucher. Dieser Abschnitt enthält Beispiele für die Festlegung von Opt-in-Dienstvoreinstellungen. Eine vollständige Liste der Funktionen und Parameter finden Sie in der [Opt-in-API-Referenz](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867).

Opt-in-Dienstkonfigurationen werden in der Visitor `getInstance()` JS-Funktion bereitgestellt, die das globale `adobe`-Objekt instanziiert. Im Folgenden werden die Visitor JS-[Konfigurationseinstellungen](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) für den Opt-in-Dienst aufgeführt.

**Beispiel für eine Opt-in-Konfiguration bei der Initialisierung des globalen `Visitor`-Objekts**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**Umgang mit Änderungen der Zustimmung**

Während Benutzer Ihre Site besuchen, können sie jederzeit Voreinstellungen zum ersten Mal festlegen oder ihre Voreinstellungen mithilfe Ihrer CMP ändern. Nachdem Besucher-JS mit den ursprünglichen Einstellungen initialisiert wurde, können die Berechtigungen des Besuchers geändert werden. Eine Liste der Funktionen zur Zustimmungsverwaltung finden Sie unter [Änderungen an den Zustimmungsparametern](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc).

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Opt-in-Workflows {#section-70cd243dec834c8ea096488640ae20a5}

Der Opt-in-Dienst unterstützt einen Workflow, bei dem Berechtigungen über mehrere Anfragezyklen erfasst werden können und Voreinstellungen einzeln festgelegt werden. Mit folgenden Funktionen und durch Festlegen von *true* für `shouldWaitForComplete` kann Ihre Lösung zunächst die Zustimmung für eine Kategorie oder Untergruppe von Kategorien erfassen und dann für die nächste Kategorie oder Untergruppe von Kategorien. Beim ersten Aufruf hat die Eigenschaft `adobe.optIn.status` den Wert *pending*, bis `adobe.optIn.complete()` am Ende des Workflows aufgerufen wird. Danach lautet der Status *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Siehe [Workflow-Konfigurationseinstellungen](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Opt-in-Berechtigungen des Benutzers prüfen {#section-f136a9024e054d84881e6667fb7c94eb}

Wenn Besucher ihre Berechtigungen ändern, müssen Sie das Ergebnis dieser Änderungen in Erfahrung bringen, um Ihre gespeicherten Zustimmungen mit den Änderungen am Opt-in-Dienst zu synchronisieren. Überprüfen Sie die Voreinstellungen Ihrer Besucher mithilfe der [Berechtigungsfunktionen](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155). Beispiel:

**fetchPermissions-Beispiel**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

In der [API-Dokumentation](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) erhalten Sie weitere Details zu diesen und anderen in diesem Dokument erwähnten Funktionen, Eigenschaften und Konfigurationen.

## Speichern von Besuchervoreinstellungen {#section-ef2884ae67e34879bf7c7c3372706c9f}

Der Opt-in-Dienst ist eine Möglichkeit zum Speichern von Zustimmungsvoreinstellungen, die für eine Entwicklungs- oder andere Umgebung geeignet ist, in der kein CRM verwendet werden kann. Wenn die Konfigurationseigenschaft `isOptInStorageEnabled` den Wert *true* hat, erstellt der Opt-in-Dienst ein Cookie im System des Besuchers innerhalb Ihrer Domäne.

Das `adobe.optIn`-Objekt ist zustandslos und bietet keinen Speichermechanismus. Stattdessen sollten Sie Adobe-Einverständniseinstellungen auf Ihrer vorhandenen Consent Management Platform (CMP) verwalten, falls diese die Speicherung benutzerdefinierter Daten ermöglicht. Oder Sie können die Besuchervoreinstellungen in einem Cookie im Browser von Besuchern speichern. Sie haben zwei Möglichkeiten, die Voreinstellungen des Benutzers an den Opt-in-Dienst zu übergeben:

* Wenn die Voreinstellungen von Besuchern mit Ihrer Lösung zum Speichern der Zustimmung, also einer CMP oder einem Cookie im Browser des Besuchers, zeitnah abgerufen werden können, dann können Sie diese während der Visitor-Initialisierung an den Opt-in-Dienst übergeben.
* Wenn das Abrufen der Voreinstellungen jedoch länger dauert oder aus anderen Gründen als asynchroner Prozess durchgeführt werden sollte, können Sie die `approve()` Funktion des Dienstes verwenden, um diese Einstellungen bereitzustellen, nachdem sie erfolgreich geladen wurden.
