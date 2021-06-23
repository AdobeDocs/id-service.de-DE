---
description: Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und persistente IDs für Ihre Site-Besucher zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
keywords: Playstation; ID-Dienst
title: Cookies und der Experience Cloud Identity-Dienst.
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 100%

---

# Cookies und der Experience Cloud Identity-Dienst {#cookies-and-the-experience-cloud-id-service}

Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und persistente IDs für Ihre Site-Besucher zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.

## Grundlegendes zu ID-Dienst-Cookies {#section-f438168beaec409ab8b2cc58bd021e26}

Der ID-Dienst ist auf die AMCV-, AMCVS- und demdex-Cookies angewiesen, um ordnungsgemäß zu funktionieren. Bei diesen Cookies handelt es sich lediglich um Dateien, in denen vom ID-Dienst verwendete Daten gespeichert werden. Diese ID-Dienst-Cookies sind nicht gefährlich, bösartig und unterscheiden sich nicht von anderen Erstanbieter- oder Drittanbieter-Cookies, die von einer Website oder einem Dienst in einem Browser gespeichert werden. Dabei gelten dieselben Regeln wie für andere Erst- und Drittanbieter-Cookies. Weitere Informationen zu den vom ID-Dienst verwendeten Cookies erhalten Sie in der nachstehenden Tabelle und den darauf folgenden Abschnitten.

### Was die ID-Dienst-Cookies können

* Eine eindeutige ID für Ihre Site-Besucher (die MID) festlegen und speichern.
* Diese eindeutige ID beibehalten, damit der ID-Dienst Daten erfassen und für andere Experience Cloud-Lösungen freigeben kann.
* Benutzer domänenübergreifend verfolgen. Dies setzt jedoch voraus, dass Sie Eigentümer dieser anderen Domänen sind und dass auf ihnen ID-Dienst-Code bereitgestellt wird.

### Was die ID-Dienst-Cookies nicht können

* Computerviren speichern, übertragen und ausführen.
* Auf personenbezogene Daten (PII) wie Ihre E-Mail-Adresse zugreifen oder speichern.
* Computerhardware oder -software steuern.
* Computer-Instabilitäten oder Leistungsprobleme verursachen.
* Benutzer auf Sites verfolgen, die den ID-Dienst nicht verwenden.

## AMCV-Cookie {#section-c55af54828dc4cce89f6118655d694c8}

Die folgenden Attribute des Cookies werden vom ID-Dienst gesetzt.

**Name**

Der Name des AMCV-Cookies folgt der Syntax `AMCV_<variable name>@AdobeOrg`. Im Namen sind die `<variable name>` Elemente Platzhalter für einen Teil Ihrer Experience Cloud Organisations-ID. Diese ID wird von der `Visitor.getInstance` Funktion im ID-Dienst-Code an den DES weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Der AMCV-Cookie enthält die Experience Cloud-Besucher-ID oder die MID. Die MID wird in einem Schlüssel-Wert-Paar gespeichert, das dieser Syntax folgt: `MCMID|<Experience Cloud ID>`.

Ein vollständiges Schlüsselwertpaar würde in etwa wie folgt aussehen:

```
MCMID|20265673158980419722735089753036633573
```

Diese persistente Kennung ermöglicht die lösungsübergreifende Datenfreigabe.

**Domäne**

Das AMCV-Cookie wird in der Erstanbieterdomäne eines Browsers gesetzt. Das bedeutet, dass es in der Domäne der Site festgelegt ist, die derzeit von einem Benutzer besucht wird. Daher können ID-Dienst-Code und andere Experience Cloud-Code-Bibliotheken die im AMCV-Cookie gespeicherte MID lesen.

Da das AMCV-Cookie jedoch in der Erstanbieterdomäne gesetzt ist, kann es nicht zum domänenübergreifenden Tracking oder zur domänenübergreifenden Identifizierung von Benutzern verwendet werden. Stattdessen verwendet der ID-Dienst die Organisations-ID und die demdex-ID, um die richtige MID zurückzugeben, wenn ein Site-Besucher zu einer anderen Domäne navigiert.

## AMCVS-Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**Name**

Der Name des AMCVS-Cookies folgt der Syntax `AMCVS_####@AdobeOrg`. Die Zeichen #### im Namen sind Platzhalter für einen Teil Ihrer Experience Cloud-Organisations-ID. Diese ID wird von der `theVisitor.getInstance` Funktion im ID-Dienst-Code an den DCS weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Das AMCVS-Cookie dient als Markierung, die angibt, dass die Sitzung initialisiert wurde. Der Wert entspricht immer `1` und wird nur bis zum Ende der Sitzung beibehalten.

**Domäne**

Das AMCVS-Cookie wird in der Erstanbieterdomäne eines Browsers gesetzt. Das bedeutet, dass es in der Domäne der Site festgelegt ist, die derzeit von einem Benutzer besucht wird.

![](assets/AMCVS-cookie.png)

## Demdex-Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

In der folgenden Tabelle werden einige wichtige Attribute des demdex-Cookies aufgeführt und definiert.

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
   <td colname="col2"> <p>Das demdex-Cookie enthält die demdex-ID, die vom DCS generiert wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domäne</b> </p> </td> 
   <td colname="col2"> <p>Das demdex-Cookie wird in der Drittanbieterdomäne „demdex.net“ im Browser gesetzt. Diese Domäne ist nicht mit der Site identisch, die derzeit von einem Benutzer besucht wird. </p> <p>Im Gegensatz zum Erstanbieter-AMCV-Cookie bestehen demdex-Cookie und -ID über verschiedene Domänen hinweg. Die demdex-ID und Ihre Organisations-ID sind die gemeinsamen Werte, die es dem ID-Dienst ermöglichen, einen Site-Besucher mit der richtigen Besucher-ID zurückzugeben und zu identifizieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

Weitere Informationen finden Sie unter [Aufrufe an die Domäne „demdex.net“](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de).

## Generieren der Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

Die Experience Cloud ID (MID) wird mathematisch aus Ihrer Organisations-ID und der demdex-ID abgeleitet. Solange diese IDs konstant bleiben, ist die Erzeugung der richtigen MID für einen bestimmten Benutzer einfach ein mathematisches Problem. Dieselbe Organisations-ID und dieselbe demdex-ID ergeben immer denselben MID-Wert. Auf diese Weise kann der ID-Dienst Besucher in über Domänen hinweg verfolgen, die Sie steuern und mit dem ID-Dienst-Code konfiguriert haben.

Der ID-Dienst erstellt beim Laden Ihrer Seite eine MID. Bei diesem Vorgang sendet der von der `visitorAPI.js` Code-Bibliothek bereitgestellte Code Ihre Organisations-ID in einem Ereignisaufruf an den ID-Dienst. Der ID-Dienst erstellt die MID und eine demdex-ID und gibt sie im AMCV- bzw. demdex-Cookie zurück.

## Cookie-Kennzeichnungen

Die folgende Tabelle beschreibt Kennzeichnungen der in Experience Cloud vewendeten Cookies.

| Cookie (gesetzt von) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| Demdex (HTTP-Antwort) | Nein | Ja | „Keine“ |
| AMCV (JavaScript) | Nein | Konfigurierbar | Nicht eingestellt (Standard: Lax) |
| AMCVS (JavaScript) | Nein | Konfigurierbar | Nicht eingestellt (Standard: Lax) |

*Hinweis: Informationen zum Konfigurieren des AMCV- und AMCVS-Cookies mit sicheren Attributen finden Sie im Artikel zu [secureCookie](../library/function-vars/securecookie.md).*

## Nächste Schritte {#section-8db1727a63bc4ff68b495f270315d453}

Siehe [Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
