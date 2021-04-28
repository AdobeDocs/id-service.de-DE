---
description: Referenz für die API der Opt-in-Bibliothek und die Konfigurationseinstellungen.
seo-description: Referenz für die API der Opt-in-Bibliothek und die Konfigurationseinstellungen.
seo-title: Opt-in-Referenz
title: Opt-in-Referenz
uuid: d5023a34-2f3e-464d-b21f-579b2f416ce6
exl-id: aa61aed7-695b-47e4-a922-9841e00aa09d
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '897'
ht-degree: 100%

---

# Opt-in-Referenz {#opt-in-reference}

Referenz für die API der Opt-in-Bibliothek und die Konfigurationseinstellungen.

Die Zustimmungseinstellungen werden den Opt-in-Funktionen als Kategorien zur Verfügung gestellt:

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## Opt-in-Konfigurationsparameter  {#section-d66018342baf401389f248bb381becbf}

In diesem Abschnitt wird die Opt-in-Konfiguration mithilfe der API beschrieben. Ein Großteil der Konfiguration und Implementierung kann über die Experience Platform Launch-Erweiterung vorgenommen werden.

Opt-in-Konfigurationen werden in der Visitor JavaScript-Funktion `getInstance()` bereitgestellt, die das globale `adobe`-Objekt instanziiert. Im Folgenden werden die Konfigurationen von Visitor JS im Zusammenhang mit dem Opt-in-Dienst aufgelistet.

**`doesOptInApply (boolean or function that evaluates to a boolean)`**

„false“ bedeutet, dass für Besucher kein Opt-in erforderlich ist. Dies führt dazu, dass Experience Cloud Cookies erstellt, unabhängig von den Kategorien, denen zugestimmt oder die abgelehnt wurden. Bei dieser Konfiguration wird Opt-in holistisch aktiviert oder deaktiviert.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

Definiert, welche Kategorien genehmigt oder abgelehnt sind, wenn der Besucher noch keine Voreinstellungen festgelegt hat, d. h. die Standardeinstellungen der Organisation.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

Die vom Besucher ausdrücklich festgelegten Voreinstellungen. Die Berechtigungen in dieser Konfiguration überschreiben die Standardeinstellungen der Organisation (`previousPermissions` überschreibt `preOptInApprovals`).

**`isOptInStorageEnabled (boolean)`**

Ermöglicht Opt-in, die Berechtigungen in einem Erstanbieter-Cookie (in der Domäne des aktuellen Kunden) zu speichern.

(Optional) **`optInCookiesDomain (string)`**

Erstanbieterdomäne oder untergeordnete Domäne, die für den Opt-in-Cookie verwendet wird (wenn für `isOptInStorageEnabled` „true“ festgelegt wurde).

(Optional) **`optInStorageExpiry (integer)`**

Anzahl der Sekunden, um die Standardablaufzeit von 13 Monaten zu überschreiben.

## Änderungen an den Zustimmungsparametern  {#section-c3d85403ff0d4394bd775c39f3d001fc}

Besucher Ihrer Site können Voreinstellungen jederzeit zum ersten Mal festlegen oder ihre Voreinstellungen mithilfe Ihrer CMP ändern. Nachdem Visitor JS mit den Ersteinstellungen initialisiert wurde, können die Berechtigungen des Besuchers mit den folgenden Funktionen geändert werden:

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Funktion, die alle Kategorien in einer Liste für einen Besucher genehmigt oder zulässt. Weitere Informationen zum Parameter „shouldWaitForComplete“ finden Sie unter [Opt-in-Workflow](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5).

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

Funktion, die alle angegebenen Kategorien für einen Besucher ausschließt oder ablehnt.

**`adobe.optIn.approveAll()`**

Wenn Ihre Anfrage nach einer Erlaubnis für die Erstellung Ihrer Website so formuliert ist, dass eine Besucheroberfläche Ihrer Website die Erlaubnis zur Erstellung von Cookies erteilt oder verweigert, verwenden Sie `approveAll()` oder `denyAll()`, bezogen auf deren Antwort.

**`adobe.optIn.denyAll()`**

Wenn Ihre Genehmigungsanfrage so formuliert ist, dass Besucher Ihrer Site die Berechtigung zum Erstellen von Cookies pauschal erteilen oder verweigern, verwenden Sie `approveAll()` oder `denyAll()`, je nach Antwort der Besucher.

## Parameter für Opt-in-Workflows {#section-2c5adfa5459c4e72b96d2693123a53c2}

Opt-in unterstützt einen Workflow, bei dem Berechtigungen über mehrere Anfragezyklen erfasst werden können, z. B. wenn Voreinstellungen einzeln festgelegt werden. Mit den folgenden Funktionen und durch Festlegen von *true* für `shouldWaitForComplete` kann Ihre Lösung zunächst die Zustimmung für eine Kategorie oder Untergruppe von Kategorien erfassen und dann für die nächste Kategorie oder Untergruppe von Kategorien. Beim ersten Aufruf hat die Eigenschaft `adobe.optIn.status` den Wert „pending“, bis `adobe.optIn.complete()` am Ende des Workflows aufgerufen wird. Danach lautet der Status *Complete*.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Funktion, die alle Kategorien in einer Liste für einen Besucher genehmigt oder zulässt.

`adobe.optIn.deny(categories, shouldWaitForComplete)`

Funktion, die alle angegebenen Kategorien für einen Besucher ausschließt oder ablehnt.

`adobe.optIn.complete()`

Funktion, die die fortlaufenden Aufrufe von approve() und deny() zu einer Anfrage zusammenführt, um die Voreinstellungen eines Besuchers festzulegen. Wenn Opt-in-Änderungen abonniert werden (siehe `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`), wird der Callback nur durch Aufrufen dieser Funktion ausgelöst.

## Parameter für Opt-in-Berechtigungen von Besuchern {#section-7fe57279b5b44b4f8fe47e336df60155}

Erfassen Sie die Opt-in-Berechtigungen eines Besuchers jederzeit mit einer der Berechtigungsfunktionen:

`adobe.optIn.permissions`

Ein Objekt, das alle Experience Cloud-Lösungen, die vom Besucher genehmigt oder abgelehnt wurden, als Kategorien aufführt.

`adobe.optIn.isApproved(categories)`

Wenn alle Kategorien genehmigt wurden, gibt diese Funktion „true“ zurück.

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

Rufen Sie die Liste der Berechtigungen asynchron ab. Der Rückruf wird mit Liste von Berechtigungen aufgerufen, sobald der Prozess zum Gewähren/Ablehnen von Berechtigungen abgeschlossen ist. Durch den Wert *true* für `shouldAutoSubscribe` erfasst der Callback alle zukünftigen Opt-in-Änderungen. Das Objekt `adobe.OptIn` verfügt über folgende Eigenschaften:

**`permissions`**

Ein Objekt, das alle Experience Cloud-Lösungen, die vom Besucher genehmigt oder abgelehnt wurden, als Kategorien aufführt. Beispiel: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* Ausstehend
* Geändert
* Fertig

**`doesOptInApply`**

„True“ oder „false“, abhängig von der Konfiguration, die Sie bei der Initialisierung angegeben haben

**`isPending`**

„True“ oder „false“, je nach Statuswert. Opt-in-Berichte für diese Eigenschaft ergeben für Besucher den Wert „true“, die die Berechtigung noch nicht ausdrücklich akzeptiert oder verweigert haben.

**`isComplete`**

„True“ oder „false“, je nach Statuswert. Opt-in meldet für diese Eigenschaft möglicherweise den Wert „false“, wenn ein Workflow-ähnliches Einverständnis gestartet, aber nicht abgeschlossen wurde.

## Methoden des Opt-in-Objekts  {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: Eine oder mehrere Kategorien, die genehmigt werden sollen. Zum Beispiel: `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**: (optional) boolescher Parameter, standardmäßig falsch. Wenn Sie „true“ übergeben, schließt Opt-in den Genehmigungsprozess erst beim Aufruf von `adobe.optIn.complete()` ab. Dieser Prozess ist einem Workflow ähnlich.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* Übergeben Sie mindestens eine oder mehrere Kategorie, um zu prüfen, ob sie genehmigt wurden.
* Wenn keine Kategorien übergeben werden, werden ALLE verfügbaren Kategorien überprüft.

**`isApproved(categories)`**

Prüft, ob eine oder mehrere Kategorien vom Kunden genehmigt wurden.

**`isPreApproved(categories)`**

Prüft, ob eine oder mehrere Kategorien vom Kunden vorab genehmigt wurden (d. h., ob sie in der `preOptInApprovals`-Konfiguration übergeben wurden).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

Async-API zum Abrufen der Liste von Berechtigungen. Der Rückruf wird mit Liste von Berechtigungen aufgerufen, sobald der Prozess zum Gewähren/Ablehnen von Berechtigungen abgeschlossen ist. **`shouldAutoSubscribe`:** Hilfsdienstprogramm, mit dem dieser Callback automatisch alle zukünftigen Ereignisse abonniert. Das bedeutet, dass der Rückruf jedes Mal aufgerufen wird, wenn ein Genehmigungs- oder Verweigerungs-Trigger in Opt-in ausgelöst wird. So bleiben Sie immer auf dem aktuellen Stand, ohne die Ereignisse selbst abonnieren zu müssen.

**Beispiel**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>Verwenden Sie dies nur, wenn Sie den `shouldWaitForComplete` Parameter zur Genehmigung oder Ablehnung übergeben haben. Diese API schließt den Genehmigungsprozess ab. Beispiel: `adobe.optIn.complete()`.

**`approveAll()`:**

Genehmigt alle vorhandenen Kategorien.

**`denyAll()`**

Lehnt alle vorhandenen Kategorien ab.

## Ereignisse des Opt-in-Objekts  {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

Das Complete-Ereignis wird ausgelöst, wenn der Genehmigungsprozess abgeschlossen ist. Wenn Sie die Funktion „approve“ oder „deny“ aufrufen, ohne `shouldWaitForComplete` oder `approveAll`/`denyAll` zu übergeben, wird dieses Ereignis ausgelöst. Wenn Sie `shouldWaitForComplete` übergeben, wird dieses Ereignis ausgelöst, nachdem `complete` aufgerufen wurde.

**Beispiel**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
