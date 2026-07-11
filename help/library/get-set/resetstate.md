---
description: Diese Funktion wurde hauptsächlich für A4T-Kunden entwickelt, um sie bei der Lösung von Problemen bei der Arbeit mit IDs auf Single-Page-Sites/-Bildschirmen oder -Apps zu unterstützen.
keywords: Besucher-ID-Service
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
TQID: https://experienceleague.adobe.com/ud8yTufRC6V5T58oh20G65MYNTCZvMlK5FdHVrrZFpU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 377
ht-degree: 54%

---

# resetState{#resetstate}

Diese Funktion wurde hauptsächlich für A4T-Kunden entwickelt, um sie bei der Lösung von Problemen bei der Arbeit mit IDs auf Single-Page-Sites/-Bildschirmen oder -Apps zu unterstützen.

## Anwendungsfälle {#section-840b88a5cdb042488b340cad5d7b22a5}

Als A4T-Kunde, der den Besucher-ID-Service verwendet, empfiehlt es sich möglicherweise, die `visitor.resetState()`-Funktion zu verwenden, wenn Folgendes erforderlich ist:

* So übergeben Sie eine zusätzliche Daten-ID (SDID) oder eine andere ID über eine Umleitung von einer Seite oder einem Bildschirm an eine andere. Normalerweise gibt der Besucher-ID-Dienst diese ID ohne diese Funktion nicht weiter.
* Verwenden Sie Code, der nur bestimmte Abschnitte einer Seite oder eines Programms über Ajax-Aufrufe aktualisiert, wenn Sie diese Aktionen verfolgen möchten. Angenommen Sie haben eine Seite, auf der das Klicken auf ein Objekt nur einen bestimmten Abschnitt lädt oder ändert. In diesem Fall kann der Besucher-ID-Service keine andere ID anfordern, es sei denn, die Seite wird neu geladen. Mit `visitor.resetState()` können Sie eine neue ID unter diesen Bedingungen anfordern.

Siehe Codebeispiele weiter unten.

## Syntax {#section-9e63503e178f4be28ac850abf44d6d91}

**Syntax:** `visitor.resetState( *`state`*);`

## Code-Beispiele {#section-d75b211bb4ea473887eb284de2ad838b}

Die Implementierung des Besucher-ID-Service wirkt sich darauf aus, wie Sie diese Funktion verwenden. Beispiele finden Sie in der unten stehenden Tabelle.

**Serverseitige Implementierung**

Eine Server-seitige Implementierung ist für A4T-Kunden mit gemischten Server- und Client-seitigen Implementierungen von Target, Analytics und dem Besucher-ID-Service vorgesehen. Wenn Sie den Besucher-ID-Dienst mit dieser Methode eingerichtet haben, müssen Sie lediglich `visitor.resetState()` zur Seite hinzufügen. Aufrufe des Besucher-ID-Service geben automatisch eine neue ID und einen neuen Server-Status zurück.

**Benutzerdefinierte Implementierung** (mit ID)

Wenn Sie den Besucher-ID-Dienst mit einer [Nicht-Standardimplementierung](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113) eingerichtet haben, müssen Sie ein variables Objekt konfigurieren, das die SDID (oder andere IDs) enthält, die Sie mit `visitor.resetState()` übergeben möchten. Wie unten dargestellt, enthält dies Ihre [IMS-Organisations-ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) und die ID, die Sie übergeben möchten. Ihr Code sollte dem folgenden Beispiel ähneln.

```js
//Instantiate server state variable 
var serverState = { 
     "INSERT-IMS-ORG-ID-HERE": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Benutzerdefinierte Implementierung** (ohne Übergeben einer ID)

In diesem Fall kann mit `visitor.resetState()` eine neue ID generiert werden. Dies kann in einem einseitigen Programm nützlich sein, wenn ein Benutzer zu einem neuen Bildschirm navigiert, ohne die Seite zu aktualisieren, und Sie eine neue ID benötigen.

```js
 
//Instantiate Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

