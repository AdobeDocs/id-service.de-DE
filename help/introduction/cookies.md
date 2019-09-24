---
description: Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
keywords: Playstation; ID-Dienst
seo-description: Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
seo-title: Cookies und der Experience Cloud Identity-Dienst.
title: Cookies und der Experience Cloud Identity-Dienst.
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Cookies und der Experience Cloud Identity-Dienst{#cookies-and-the-experience-cloud-id-service}

Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.

## Grundlegendes zu ID-Dienst-Cookies {#section-f438168beaec409ab8b2cc58bd021e26}

Für den ID-Dienst müssen AMCV-, AMCVS- und Demdex-Cookies ordnungsgemäß funktionieren. Bei diesen Cookies handelt es sich einfach nur um Dateien, in denen die vom ID-Dienst verwendeten Daten gespeichert sind. Diese ID-Dienst-Cookies sind weder gefährlich noch böswillig und unterscheiden sich nicht von anderen Erstanbieter- oder Drittanbieter-Cookies, die auf einer Website oder von einem Dienst in einem Browser gespeichert werden. Sie unterliegen denselben Regeln, die für Erstanbieter- und Drittanbieter-Cookies gelten. Weitere Informationen zu den vom ID-Dienst verwendeten Cookies erhalten Sie in der nachstehenden Tabelle und den darauf folgenden Abschnitten.

### Was die ID-Dienst-Cookies können

* Eine eindeutige ID für Ihre Site-Besucher (MID) festlegen und speichern.
* Diese eindeutige ID beibehalten, sodass der ID-Dienst Daten erfassen und an Experience Cloud-Lösungen weitergeben kann.
* Benutzer domänenübergreifend verfolgen. Dafür müssen Sie jedoch Inhaber dieser anderen Domänen sein und den ID-Dienstcode in diesen Domänen implementiert haben.

### Was die ID-Dienst-Cookies nicht können

* Computerviren speichern, übertragen oder ausführen
* Auf personenbezogene Informationen (PII), beispielsweise Ihre E-Mail-Adresse, zugreifen und sie speichern
* Computer-Hardware oder Software steuern
* Instabilität oder Leistungsprobleme auf Computern hervorrufen
* Benutzer auf Sites verfolgen, die den ID-Dienst nicht verwenden

## AMCV-Cookie {#section-c55af54828dc4cce89f6118655d694c8}

Die folgenden Attribute des Cookies werden vom ID-Dienst gesetzt.

**Name**

Der Name des AMCV-Cookies folgt der Syntax `AMCV_<variable name>@AdobeOrg`. Im Namen sind die `<variable name>` Elemente Platzhalter für einen Teil Ihrer Experience Cloud Organisations-ID. Diese ID wird von der `Visitor.getInstance` Funktion im ID-Dienst-Code an den DES weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Der AMCV-Cookie enthält die Experience Cloud-Benutzer-ID, auch als MID bezeichnet. Die MID wird in einem Schlüssel-Wert-Paar gespeichert, das dieser Syntax folgt: `mid|<Experience Cloud ID>`.

Ein vollständiges Schlüsselwertpaar würde in etwa wie folgt aussehen:

```
mid|20265673158980419722735089753036633573
```

Dieser beständige Identifikator ermöglicht eine lösungsübergreifende Datenweitergabe.

**Domäne**

Der AMCV-Cookie wird in der Erstanbieterdomäne eines Browsers festgelegt. Das bedeutet, dass er auf die Domäne der Seite festgelegt ist, die der Benutzer aktuell besucht. Somit können der ID-Dienstcode und andere Experience Cloud-Code-Bibliotheken die im AMCV-Cookie gespeicherte MID auslesen.

Da der AMCV-Cookie jedoch als Erstanbieterdomäne festgelegt ist, kann er nicht zur domänenübergreifenden Verfolgung und Identifikation von Benutzern eingesetzt werden. Stattdessen setzt der ID-Dienst bei der Rückgabe der korrekten MID auf die Organisations-ID und die demdex-ID, wenn der Besucher einer Site zu einer anderen Domäne wechselt.

## AMCVS-Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**Name**

Der Name des AMCVS-Cookies folgt der Syntax `AMCVS_####@AdobeOrg`. Die Zeichen #### im Namen sind Platzhalter für einen Teil Ihrer Experience Cloud-Organisations-ID. Diese ID wird von der `theVisitor.getInstance` Funktion im ID-Dienst-Code an den DCS weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Das AMCVS-Cookie dient als Kennzeichnung und gibt an, dass die Sitzung initialisiert wurde. Der Wert entspricht immer `1` und wird nur bis zum Ende der Sitzung beibehalten.

**Domäne**

Das AMCVS-Cookie wird in der Erstanbieterdomäne eines Browsers festgelegt. Das bedeutet, dass er auf die Domäne der Seite festgelegt ist, die der Benutzer aktuell besucht.

![](assets/AMCVS-cookie.png)

## Demdex-Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

In der folgenden Tabelle finden Sie eine Auflistung und Definition einiger wichtiger Attribute des demdex-Cookies.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Attribut </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Name</b> </p> </td> 
   <td colname="col2"> <p>Der Name des Cookies lautet „demdex“. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Inhalt</b> </p> </td> 
   <td colname="col2"> <p>Der demdex-Cookie enthält die demdex-ID, die vom DES generiert wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domäne</b> </p> </td> 
   <td colname="col2"> <p>Der demdex-Cookie wird in der Drittanbieter-demdex.net-Domäne im Browser gesetzt. Diese Domäne ist nicht mit der aktuell vom Benutzer besuchten Domäne identisch. </p> <p>Im Gegensatz zum Erstanbieter-AMCV-Cookie bestehen demdex-Cookie und demdex-ID auch domänenübergreifend fort. Die demdex-ID und Ihre Organisations-ID stellen die gemeinsamen Werte dar, mit denen der ID-Dienst einen Site-Besucher identifizieren und die richtige Besucher-ID zurückgeben kann. </p> </td> 
  </tr> 
 </tbody> 
</table>

For related information, see [Understanding Calls to the Demdex Domain](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

## Generieren der Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

Die Experience Cloud ID (MID) wird mathematisch aus Ihrer Organisations-ID und der demdex-ID abgeleitet. Solange diese IDs konstant bleiben, ist das Generieren der richtigen MID für einen bestimmten Benutzer einfach nur eine Rechenaufgabe. Mit der gleichen Organisations-ID und demdex-ID erhalten Sie jedes Mal den gleichen MID-Wert. So kann der ID-Dienst Besucher in allen Domänen verfolgen, die Sie verwalten und mit dem Code des ID-Diensts konfiguriert haben.

Der ID-Dienst beginnt mit der Erstellung einer MID, während Ihre Seite geladen wird. Bei diesem Vorgang sendet der von der `visitorAPI.js` Code-Bibliothek bereitgestellte Code Ihre Organisations-ID in einem Ereignisaufruf an den ID-Dienst. Der ID-Dienst erstellt die MID und eine demdex-ID und gibt sie im AMCV- bzw. demdex-Cookie zurück.

## Nächste Schritte {#section-8db1727a63bc4ff68b495f270315d453}

Siehe [Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
