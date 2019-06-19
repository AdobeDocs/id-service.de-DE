---
description: Implementieren Sie den Opt-in-Dienst als einzelner Referenzpunkt, der von Experience Cloud-Lösungen (als Kategorien bei der Teilnahme bezeichnet) verwendet wird, um zu bestimmen, ob Cookies auf dem Gerät eines Besuchers erstellt werden sollen.
seo-description: Implementieren Sie den Opt-in-Dienst als einzelner Referenzpunkt, der von Experience Cloud-Lösungen (als Kategorien bei der Teilnahme bezeichnet) verwendet wird, um zu bestimmen, ob Cookies auf dem Gerät eines Besuchers erstellt werden sollen.
seo-title: Einrichten des Opt-In-Dienstes
title: Einrichten des Opt-In-Dienstes
uuid: f 1 c 27139-cef 2-4122-af 12-c 839 cfc 82 e 6 e
translation-type: tm+mt
source-git-commit: 746f8937c59d318dcf7245c7f8484884974601dc

---


# Einrichten des Opt-In-Dienstes{#setting-up-opt-in-service}

Implementieren Sie den Opt-in-Dienst als einzelner Referenzpunkt, der von Experience Cloud-Lösungen (als Kategorien bei der Teilnahme bezeichnet) verwendet wird, um zu bestimmen, ob Cookies auf dem Gerät eines Besuchers erstellt werden sollen.

Der Anmeldedienst ist eine javascript-Bibliothek, die mit dem Adobe Experience Platform Identity Service gebündelt ist und in Visitor JS im globalen `adobe` Objekt als `adobe.optIn` Objekt vorhanden ist. Mit dem installierten Opt-in-Dienst können Sie angeben, ob ein Besucher die Adobe-Lösungen auf einmal auswählen kann oder ob Lösungen in einer Sequenz für die einzelnen Benutzer angezeigt werden sollen. Mit der Genehmigungsverwaltungsfunktion können Sie mit verschiedenen Konfigurationen für Ihre spezifischen Datenschutzanforderungen arbeiten.

Mit dem Opt-in-Dienst können Sie angeben, ob ein Besucher Adobe-Lösungen auf einmal auswählen kann oder ob Lösungen in einer Sequenz für die einzelnen Benutzer angezeigt werden sollen. Sobald der Genehmigungsprozess abgeschlossen und vom Kunden aufgezeichnet wurde, können CMP-Besuchergenehmigungen von allen Adobe-Lösungen abgerufen werden, um mit entsprechenden Zustimmungsaufrufen zu reagieren.

## Voraussetzungen {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID Version 4.0.

   Laden Sie die neueste ECID-Version [herunter](https://github.com/Adobe-Marketing-Cloud/id-service/releases).

1. Unterstützende Bibliotheken:

   * ECID 4.0 oder höher
   * AppMeasurement 2.11 oder höher
   * DIL 9.0
   * AT.js Version 1.7.0
   * AT.js-Launch-Erweiterung Version 9.0
   * AppMeasurement 2.11 mit Erweiterung 1.6 für Analytics
   * Erweiterung 0.9.1 für Target

1. Machen Sie sich mit dem Zustimmungsverwaltungs-Framework, das Sie mit Opt-in verwenden, und allen weiteren Voraussetzungen vertraut.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Die Datenschutzanforderungen Ihres Unternehmens enthalten die Einzelheiten zur Einhaltung der DSGVO in Ihrem Unternehmen. Achten Sie darauf, welche Bibliotheken die Datenschutzteams in Ihrem Unternehmen zulassen, solange noch keine Zustimmung vorliegt.

Wenn Sie [Adobe Launch](https://docs.adobelaunch.com/) verwenden, nutzen Sie die [Teilnahme an der](../../implementation-guides/opt-in-service/launch.md) Teilnahme an der Anmeldung.

## Kategorien für die Teilnahme {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Die Opt-in-Voreinstellungen eines Besuchers beziehen sich auf eine Adobe Experience Cloud-Lösung, wobei jede Lösung einer Kategorie entspricht. Kategorien werden durch das Objekt `adobe.OptInCategories` bereitgestellt. Die ECID-Komponente entspricht beispielsweise `adobe.OptInCategories`. `ECID`. Die Definition von `adobe.OptInCategories` lautet:

Opt-in-Einstellungen werden pro Kategorie verwaltet, wobei jede Experience Cloud-Lösung einer Kategorie entspricht:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Mit dem Anmeldungs-Service können Sie die Berechtigungseinstellungen der Besucher pro einzelnen auf Ihrer Site verwendeten Lösungen festlegen. Das Objekt umfasst eine Bibliothek zum Speichern der Einstellungen eines Besuchers nach genehmigter Kategorie und unterstützt einen sequenziellen Ablauf, bei dem der Genehmigungsprozess Voreinstellungen zum Bestätigen oder Ablehnen jeder Kategorie erhält. Sie können festlegen, dass den Lösungen/Kategorien gleichzeitig oder einzeln zugestimmt wird.
clientseitige Bibliotheken von Adobe-Lösungen hängen vom Opt-in-Dienst ab und generieren keine Cookies, es sei denn, die Lösung hat eine Berechtigung. Opt-in unterstützt verschiedene Ansätze zur Bereitstellung und Aktualisierung von Zustimmungseinstellungen für den aktuellen Besucher. In diesem Abschnitt finden Sie Beispiele zum Festlegen der Voreinstellungen für den Opt-in-Dienst. Eine vollständige Liste der Funktionen und Parameter finden Sie in der [Anmeldeapi-Referenz](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) .

Die Opt-in-Dienstkonfigurationen werden in der Funktion &quot;Visitor JS `getInstance()` «bereitgestellt, die das globale `adobe` Objekt instanziiert. Im Folgenden werden die JS- [Konfigurationseinstellungen für Besucher](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) für den Opt-in-Dienst aufgeführt.

**Beispiel für eine Opt-in-Konfiguration bei der Initialisierung des globalen`Visitor`-Objekts**

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

**Zustimmungsänderungen verarbeiten**

Besucher können jederzeit während des Besuchs Ihrer Site erstmals Voreinstellungen festlegen oder ihre Voreinstellungen mithilfe Ihrer CMP ändern. Nachdem Visitor JS mit den Anfangseinstellungen initialisiert wurde, können die Berechtigungen des Besuchers geändert werden. Siehe [Änderungen an der Einwilligung](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) für eine Liste der Funktionen zur Genehmigungsverwaltung.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Abmeldearbeitsabläufe {#section-70cd243dec834c8ea096488640ae20a5}

Der Anmeldedienst unterstützt einen Arbeitsablauf, in dem Berechtigungen über mehr als einen Anforderungszyklus erfasst werden können und die Voreinstellungen einzeln angegeben werden. Mit folgenden Funktionen und durch Festlegen von *true* für `shouldWaitForComplete` kann Ihre Lösung zunächst die Zustimmung für eine Kategorie oder Untergruppe von Kategorien erfassen und dann für die nächste Kategorie oder Untergruppe von Kategorien. Ab dem ersten Aufruf wird die `adobe.optIn.status` Eigenschaft *ausstehend,* bis `adobe.optIn.complete()` sie am Ende des Flusses aufgerufen wird. Danach lautet der Status *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Siehe [Workflow-Konfigurationseinstellungen](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Opt-in-Berechtigungen des Benutzers prüfen {#section-f136a9024e054d84881e6667fb7c94eb}

Wenn Ihre Besucher Änderungen an ihren Berechtigungen vornehmen, benötigen Sie Einblicke in die resultierenden Berechtigungen, um Ihren Bestätigungsstore mit den Änderungen zu synchronisieren, die in der Anmeldung vorgenommen wurden. Prüfen Sie die Voreinstellungen Ihrer Besucher mit [Berechtigungsfunktionen](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155). Beispiel:

**Beispiel für „fetchPermissions“**

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

In der [API-Dokumentation](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) erhalten Sie weitere Details zu diesen und anderen in diesem Dokument erwähnten Funktionen, Eigenschaften oder Konfigurationen.

## Speichern von Besuchervoreinstellungen {#section-ef2884ae67e34879bf7c7c3372706c9f}

Der Anmeldedienst bietet eine Option zum Speichern der Voreinstellungen für die Genehmigung, die für eine Entwicklungsumgebung oder eine Umgebung, in der es nicht möglich ist, ein CRM-System zu verwenden, gespeichert werden kann. Wenn Sie die Konfigurationseigenschaft `isOptInStorageEnabled` als *&quot;true&quot; auswählen,* löst sie den Anmeldungs-Dienst aus, um ein Cookie auf dem System des Besuchers innerhalb Ihrer Domäne zu erstellen.

Das `adobe.optIn`-Objekt ist zustandslos und bietet keinen Speichermechanismus. Stattdessen müssen Sie die Adobe-Zustimmungseinstellungen in Ihrer bestehenden Consent Management Platform (CMP) verwalten, wenn diese die Speicherung benutzerdefinierter Daten ermöglicht. Sie können die Besuchervoreinstellungen auch in einem Cookie im Browser des Besuchers speichern. Sie haben zwei Möglichkeiten zum Bereitstellen der Benutzervoreinstellungen für den Opt-in-Dienst:

* Wenn Ihre Persistenzlösung, ob es sich um ein CMP oder ein Cookie im Browser des Besuchers handelt, ein zeitnaher Abruf der Besuchervoreinstellungen ermöglicht, können Sie diese dem Opt-in-Dienst während der Besucherinitialisierung bereitstellen.
* Wenn das Abrufen jedoch ein langwieriger Prozess sein kann oder andernfalls als asynchrone Verarbeitung am besten bedient wird, können Sie die Funktion des Dienstes `approve()` verwenden, um diese Einstellungen zu senden, sobald sie erfolgreich geladen wurden.

