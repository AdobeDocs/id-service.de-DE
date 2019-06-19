---
description: Diese Funktion wurde hauptsächlich für A4T-Kunden entwickelt, um sie bei der Lösung von Problemen bei der Arbeit mit IDs auf Single-Page-Sites/-Bildschirmen oder -Apps zu unterstützen.
keywords: ID-Dienst
seo-description: Diese Funktion wurde hauptsächlich für A4T-Kunden entwickelt, um sie bei der Lösung von Problemen bei der Arbeit mit IDs auf Single-Page-Sites/-Bildschirmen oder -Apps zu unterstützen.
seo-title: resetState
title: resetState
uuid: ed 7 be 76 d-a 7 ee -4 e 51-b 26 c -456 ff 85 fd 96
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetState{#resetstate}

Diese Funktion wurde hauptsächlich für A4T-Kunden entwickelt, um sie bei der Lösung von Problemen bei der Arbeit mit IDs auf Single-Page-Sites/-Bildschirmen oder -Apps zu unterstützen.

## Anwendungsbeispiele {#section-840b88a5cdb042488b340cad5d7b22a5}

Als A 4 T-Kunde, der den ID-Dienst verwendet, möchten Sie die `visitor.resetState()` Funktion verwenden, wenn Sie Folgendes benötigen:

* Sie möchten eine Zusatzdaten-ID (Supplemental Data ID, SDID) oder andere ID durch eine Umleitung an eine andere Seite oder einen anderen Bildschirm übergeben. Normalerweise übergibt der ID-Dienst diese ID nicht ohne diese Funktion.
* Sie möchten Code verwenden, der nur bestimmte Abschnitte einer Seite oder Anwendung über Ajax-Aufrufe aktualisiert, und diese Aktionen verfolgen. Angenommen, auf einer Seite wird durch Klicken auf ein Objekt nur ein bestimmter Abschnitt geladen oder geändert. In diesem Fall kann der ID-Dienst eine andere ID nur dann anfordern, wenn die Seite neu geladen wird. Sie `visitor.resetState()`können jedoch unter diesen Bedingungen eine neue ID anfordern.

Siehe Codebeispiele weiter unten.

## Syntax {#section-9e63503e178f4be28ac850abf44d6d91}

**Syntax:**` visitor.resetState( *`state`*);`

## Codebeispiele {#section-d75b211bb4ea473887eb284de2ad838b}

Die Verwendung dieser Funktion ist von der Implementierung des ID-Diensts abhängig. Beispiele finden Sie in der nachstehenden Tabelle.

**Serverseitige Implementierung**

Eine serverseitige Implementierung gilt für A 4 T-Kunden mit gemischten Server- und clientseitigen Implementierungen von [!DNL Target], [!DNL Analytics]und und dem ID-Dienst. Wenn Sie den ID-Dienst mit dieser Methode eingerichtet haben, müssen Sie lediglich `visitor.resetState()` der Seite hinzufügen. Aufrufe an den ID-Dienst geben automatisch eine neue ID und einen Serverstatus zurück.

**Nicht standardisierte Implementierung** (mit ID)

Wenn Sie den ID-Dienst mit einer [benutzerdefinierten Implementierung](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113) einrichten, müssen Sie ein Variablenobjekt zur Aufnahme der SDID (oder anderer IDs) konfigurieren, die Sie mit `visitor.resetState()` () übergeben möchten. Wie unten gezeigt, schließt dies Ihre [ Organisations-ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) und die ID ein, die Sie übergeben möchten. Ihr Code sollte dem folgenden Beispiel ähneln.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Nicht standardisierte Implementierung** (ohne Weitergabe einer ID)

In diesem Fall `visitor.resetState()` kann eine neue ID generiert werden. Dies kann in einer Single-Page-Anwendung nützlich sein, wenn ein Benutzer zu einem neuen Bildschirm navigiert, ohne die Seite zu aktualisieren, und Sie eine neue ID benötigen.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
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

**Dynamischer Tag-Manager (DTM)**

Zurzeit gibt es keinen DTM-Konfigurationspfad für `visitor.resetState()`.
