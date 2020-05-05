---
description: Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud AMCV-Cookie und ein demdex-Cookie, um eindeutige, beständige IDs für Ihre Site-Besucher zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
keywords: playstation;ID Service
seo-description: Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud AMCV-Cookie und ein demdex-Cookie, um eindeutige, beständige IDs für Ihre Site-Besucher zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
seo-title: Cookies und der Experience Cloud Identity-Dienst.
title: Cookies und der Experience Cloud Identity-Dienst.
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Cookies und der Experience Cloud Identity-Dienst {#cookies-and-the-experience-cloud-id-service}

Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud AMCV-Cookie und ein demdex-Cookie, um eindeutige, beständige IDs für Ihre Site-Besucher zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.

## Grundlegendes zu ID-Dienst-Cookies {#section-f438168beaec409ab8b2cc58bd021e26}

Der ID-Dienst nutzt die Cookies AMCV, AMCVS und demdex, um ordnungsgemäß zu funktionieren. Bei diesen Cookies handelt es sich lediglich um Dateien, in denen vom ID-Dienst verwendete Daten gespeichert werden. Diese ID-Dienst-Cookies sind nicht gefährlich, bösartig oder unterscheiden sich von anderen Erstanbieter- oder Drittanbieter-Cookies, die von einer Website oder einem Dienst in einem Browser gespeichert werden, und befolgen die gleichen Regeln wie für andere Erstanbieter- und Drittanbieter-Cookies. Weitere Informationen zu den vom ID-Dienst verwendeten Cookies erhalten Sie in der nachstehenden Tabelle und den darauf folgenden Abschnitten.

### Was die ID-Dienst-Cookies können

* Legen Sie eine eindeutige ID für Ihre Site-Besucher (die MID) fest und speichern Sie diese.
* Behalten Sie diese eindeutige ID bei, damit der ID-Dienst Daten erfassen und für andere Experience Cloud-Lösungen freigeben kann.
* Verfolgen Sie Benutzer domänenübergreifend. Dies erfordert jedoch, dass Sie Eigentümer dieser anderen Domänen sind und ID-Dienst-Code auf ihnen bereitgestellt wird.

### Was die ID-Dienst-Cookies nicht können

* Speichern, übertragen oder führen Sie Computerviren aus.
* Greifen Sie auf personenbezogene Daten (PII) wie Ihre E-Mail-Adresse zu oder speichern Sie sie.
* Steuern Sie Computerhardware oder -software.
* Machen Sie Computer instabil oder verursachen Sie Leistungsprobleme.
* Verfolgen Sie Benutzer auf Sites, die den ID-Dienst nicht verwenden.

## AMCV-Cookie {#section-c55af54828dc4cce89f6118655d694c8}

Die folgenden Attribute des Cookies werden vom ID-Dienst gesetzt.

**Name**

Der Name des AMCV-Cookies folgt der Syntax `AMCV_<variable name>@AdobeOrg`. Im Namen sind die `<variable name>` Elemente Platzhalter für einen Teil Ihrer Experience Cloud Organisations-ID. Diese ID wird von der `Visitor.getInstance` Funktion im ID-Dienst-Code an den DES weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Der AMCV-Cookie enthält die Experience Cloud-Besucher-ID oder MID. Die MID wird in einem Schlüssel-Wert-Paar gespeichert, das dieser Syntax folgt: `mid|<Experience Cloud ID>`.

Ein vollständiges Schlüsselwertpaar würde in etwa wie folgt aussehen:

```
mid|20265673158980419722735089753036633573
```

Dieser beständige Bezeichner ermöglicht die lösungsübergreifende Datenfreigabe.

**Domäne**

Das AMCV-Cookie wird in der Erstanbieterdomäne eines Browsers eingestellt. Dies bedeutet, dass er in der Domäne der Site festgelegt ist, die derzeit von einem Benutzer besucht wird. Daher können ID-Dienst-Code und andere Experience Cloud-Codebibliotheken die im AMCV-Cookie gespeicherte MID lesen.

Da das AMCV-Cookie jedoch in der Erstanbieterdomäne festgelegt ist, kann es nicht zur domänenübergreifenden Verfolgung und Identifizierung von Benutzern verwendet werden. Stattdessen verwendet der ID-Dienst die Organisations-ID und die demdex-ID, um die richtige MID zurückzugeben, wenn ein Site-Besucher zu einer anderen Domäne navigiert.

## AMCVS-Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**Name**

Der Name des AMCVS-Cookies folgt der Syntax `AMCVS_####@AdobeOrg`. Die Zeichen #### im Namen sind Platzhalter für einen Teil Ihrer Experience Cloud-Organisations-ID. Diese ID wird von der `theVisitor.getInstance` Funktion im ID-Dienst-Code an den DCS weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Das AMCVS-Cookie dient als Flag, das anzeigt, dass die Sitzung initialisiert wurde. Der Wert entspricht immer `1` und wird nur bis zum Ende der Sitzung beibehalten.

**Domäne**

Das AMCVS-Cookie wird in der Erstanbieterdomäne eines Browsers gesetzt. Dies bedeutet, dass er in der Domäne der Site festgelegt ist, die derzeit von einem Benutzer besucht wird.

![](assets/AMCVS-cookie.png)

## Demdex-Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

In der folgenden Tabelle werden einige wichtige Attribute des demdex-Cookies Liste und definiert.

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
   <td colname="col2"> <p>Der Cookie-Name lautet "demdex". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Inhalt</b> </p> </td> 
   <td colname="col2"> <p>Das demdex-Cookie enthält die demdex-ID, die vom DCS generiert wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domäne</b> </p> </td> 
   <td colname="col2"> <p>Das demdex-Cookie wird in der Drittanbieter-demdex.net-Domäne im Browser gesetzt. Diese Domäne ist nicht mit der Site identisch, die derzeit von einem Benutzer besucht wird. </p> <p>Im Gegensatz zum Erstanbieter-AMCV-Cookie bestehen demdex-Cookie und -ID über verschiedene Domänen hinweg. Die demdex-ID und Ihre Organisations-ID sind die gemeinsamen Werte, die es dem ID-Dienst ermöglichen, einen Site-Besucher mit der richtigen Besucher-ID zurückzugeben und zu identifizieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

Weitere Informationen finden Sie unter [Aufrufe an die Domäne „demdex.net“](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/reference/demdex-calls.html).

## Generieren der Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

Die Experience Cloud ID (MID) wird mathematisch aus Ihrer Organisations-ID und der demdex-ID abgeleitet. Solange diese IDs konstant bleiben, stellt die Generierung der richtigen MID für einen bestimmten Benutzer einfach ein mathematisches Problem dar. Mit der gleichen Organisations-ID und demdex-ID erhalten Sie immer denselben MID-Wert. Auf diese Weise kann der ID-Dienst Besucher domänenübergreifend verfolgen, die Sie steuern und mit dem ID-Dienst-Code konfiguriert haben.

Die Beginn des ID-Diensts zum Erstellen einer MID beim Laden der Seite. Bei diesem Vorgang sendet der von der `visitorAPI.js` Code-Bibliothek bereitgestellte Code Ihre Organisations-ID in einem Ereignisaufruf an den ID-Dienst. Der ID-Dienst erstellt die MID und eine demdex-ID und gibt sie im AMCV- bzw. demdex-Cookie zurück.

## Cookie-Kennzeichnungen

Die folgende Tabelle beschreibt Kennzeichnungen der in Experience Cloud vewendeten Cookies.

| Cookie (gesetzt von) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| Demdex (HTTP-Antwort) | Nein | Ja | &quot;Keine&quot; |
| AMCV (JavaScript) | Nein | Konfigurierbar | Nicht eingestellt (Standard: Lax) |
| AMCVS (JavaScript) | Nein | Konfigurierbar | Nicht eingestellt (Standard: Lax) |

*Hinweis: Informationen zum Konfigurieren des AMCV- und AMCVS-Cookies mit sicheren Attributen finden Sie im Artikel zu [secureCookie](https://docs.adobe.com/content/help/de-DE/id-service/using/id-service-api/configurations/securecookie.html).*

## Nächste Schritte {#section-8db1727a63bc4ff68b495f270315d453}

Siehe [Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
