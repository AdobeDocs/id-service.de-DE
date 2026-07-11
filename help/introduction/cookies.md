---
description: Der Besucher-ID-Dienst verwendet Ihre IMS-Organisations-ID, das AMCV-Cookie von CX Enterprise und ein demdex-Cookie, um eindeutige und persistente IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der Besucher-ID-Service Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen verschiedenen CX Enterprise-Lösungen ermöglichen.
keywords: Playstation;Besucher-ID-Service
title: Cookies und der Besucher-ID-Dienst von Adobe
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
TQID: https://experienceleague.adobe.com/iLOFGQ9t-DqYfqOZs3K5yZI7903dMPEjANaJ7lH8K0o
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 990
ht-degree: 42%

---

# Cookies und der Besucher-ID-Dienst von Adobe{#cookies-and-the-experience-cloud-id-service}

Der Besucher-ID-Dienst verwendet Ihre IMS-Organisations-ID, das AMCV-Cookie von CX Enterprise und ein demdex-Cookie, um eindeutige und persistente IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der Besucher-ID-Service Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen verschiedenen CX Enterprise-Lösungen ermöglichen.

## Cookies des Besucher-ID-Service {#section-f438168beaec409ab8b2cc58bd021e26}

Der Besucher-ID-Dienst ist auf die AMCV-, AMCVS- und demdex-Cookies angewiesen, um ordnungsgemäß zu funktionieren. Bei diesen Cookies handelt es sich lediglich um Dateien, in denen vom Besucher-ID-Dienst verwendete Daten gespeichert werden. Diese Besucher-ID-Dienst-Cookies sind nicht gefährlich, bösartig und unterscheiden sich nicht von anderen Erstanbieter- oder Drittanbieter-Cookies, die von einer Website oder einem Service in einem Browser gespeichert werden. Dabei gelten dieselben Regeln wie für andere Erst- und Drittanbieter-Cookies. Weitere Informationen zu den vom Besucher-ID-Dienst verwendeten Cookies finden Sie in den folgenden Abschnitten.

### Was die Besucher-ID-Service-Cookies können

* Eine eindeutige ID für Ihre Site-Besucher (die MID) festlegen und speichern.
* Behalten Sie diese eindeutige ID bei, damit der Besucher-ID-Service Daten erfassen und für andere CX Enterprise-Lösungen freigeben kann.
* Benutzer domänenübergreifend verfolgen. Dazu müssen Sie jedoch Eigentümer dieser anderen Domains sein und den Besucher-ID-Service-Code auf ihnen bereitstellen.

### Was die Besucher-ID-Service-Cookies nicht können

* Computerviren speichern, übertragen und ausführen.
* Auf personenbezogene Daten (PII) wie Ihre E-Mail-Adresse zugreifen oder speichern.
* Computerhardware oder -software steuern.
* Computer-Instabilitäten oder Performance-Probleme verursachen.
* Tracken Sie Benutzer auf Sites, die den Besucher-ID-Service nicht verwenden.

## AMCV-Cookie {#section-c55af54828dc4cce89f6118655d694c8}

Die folgenden Attribute des Cookies werden vom Besucher-ID-Service gesetzt.

**Name**

Der Name des AMCV-Cookies folgt der Syntax `AMCV_<variable name>@AdobeOrg`. Im Namen sind die `<variable name>`-Elemente Platzhalter für einen Teil Ihrer IMS-Organisations-ID. Diese ID wird von der `Visitor.getInstance` im Code des Besucher-ID-Service an den DCS weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Das AMCV-Cookie enthält die ECID oder MID. Die MID wird in einem Schlüssel-Wert-Paar gespeichert, das dieser Syntax folgt: `MCMID|<ECID>`.

Ein vollständiges Schlüsselwertpaar würde in etwa wie folgt aussehen:

```
MCMID|20265673158980419722735089753036633573
```

Diese persistente Kennung ermöglicht die lösungsübergreifende Datenfreigabe.

**Domain**

Das AMCV-Cookie wird in der Erstanbieterdomäne eines Browsers gesetzt. Das bedeutet, dass es in der Domain der Site festgelegt ist, die derzeit von einem Benutzer besucht wird. Daher können der Besucher-ID-Dienst-Code und andere CX Enterprise-Code-Bibliotheken die im AMCV-Cookie gespeicherte MID lesen.

Da das AMCV-Cookie jedoch in der Erstanbieterdomäne gesetzt ist, kann es nicht zum domänenübergreifenden Tracking oder zur domänenübergreifenden Identifizierung von Benutzern verwendet werden. Stattdessen verwendet der Besucher-ID-Dienst die IMS-Organisations-ID und die demdex-ID, um die richtige MID zurückzugeben, wenn ein Site-Besucher zu einer anderen Domain navigiert.

## AMCVS-Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**Name**

Der Name des AMCVS-Cookies folgt der Syntax `AMCVS_####@AdobeOrg`. Im Namen sind die ####-Elemente Platzhalter für einen Teil Ihrer IMS-Organisations-ID. Diese ID wird von `theVisitor.getInstance` Funktion im Code des Besucher-ID-Service an den DCS weitergeleitet.

Ein vollständiger Cookie-Name würde in etwa wie folgt aussehen:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhalt**

Das AMCVS-Cookie dient als Markierung, die angibt, dass die Sitzung initialisiert wurde. Der Wert entspricht immer `1` und wird nur bis zum Ende der Sitzung beibehalten.

**Domain**

Das AMCVS-Cookie wird in der Erstanbieterdomäne eines Browsers gesetzt. Das bedeutet, dass es in der Domain der Site festgelegt ist, die derzeit von einem Benutzer besucht wird.

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
   <td colname="col1"> <p> <b>Domain</b> </p> </td> 
   <td colname="col2"> <p>Das demdex-Cookie wird in der Drittanbieterdomäne „demdex.net“ im Browser gesetzt. Diese Domain ist nicht mit der Site identisch, die derzeit von einem Benutzer besucht wird. </p> <p>Im Gegensatz zum Erstanbieter-AMCV-Cookie bestehen demdex-Cookie und -ID über verschiedene Domänen hinweg. Die demdex-ID und Ihre IMS-Organisations-ID sind die gemeinsamen Werte, die es dem Besucher-ID-Service ermöglichen, einen Site-Besucher mit der richtigen Besucher-ID zurückzugeben und zu identifizieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

Informationen zu Demdex-Offenlegungen finden Sie in den [Offenlegungen zum Audience Manager-Gerätespeicher](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json).

Weitere Informationen finden Sie in der Dokumentation zum [Verstehen von Aufrufen an die Demdex-Domain](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de).

## Generieren der ECID {#section-15f69c0bac394b4b9966a23fbc586d17}

Die ECID wird mathematisch aus Ihrer IMS-Organisations-ID und der demdex-ID abgeleitet. Solange diese IDs konstant bleiben, ist die Erzeugung der richtigen MID für einen bestimmten Benutzer einfach ein mathematisches Problem. Bei gleicher IMS-Organisations-ID und demdex-ID erhalten Sie jedes Mal denselben MID-Wert. Dadurch kann der Besucher-ID-Service Besucher über Domänen hinweg verfolgen, die Sie steuern und mit dem Besucher-ID-Service-Code konfiguriert haben.

Der Besucher-ID-Service erstellt beim Laden Ihrer Seite eine MID. Während dieses Vorgangs sendet der von der `VisitorAPI.js` Code-Bibliothek bereitgestellte Code Ihre IMS-Organisations-ID in einem Ereignisaufruf an den Besucher-ID-Service. Der Besucher-ID-Dienst erstellt die MID und eine demdex-ID und gibt sie im AMCV- bzw. demdex-Cookie zurück.

## Cookie-Kennzeichnungen

In der folgenden Tabelle werden Flags für CX Enterprise-Cookies beschrieben:

| Cookie (gesetzt von) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| Demdex (HTTP-Antwort) | Nein | Ja | „Keine“ |
| AMCV (JavaScript) | Nein | Konfigurierbar | Nicht eingestellt (Standard: Lax) |
| AMCVS (JavaScript) | Nein | Konfigurierbar | Nicht eingestellt (Standard: Lax) |

*Hinweis: Informationen zum Konfigurieren des AMCV- und AMCVS-Cookies mit sicheren Attributen finden Sie im Artikel zu [secureCookie](../library/function-vars/securecookie.md).*

## Nächste Schritte {#section-8db1727a63bc4ff68b495f270315d453}

Siehe [Anfordern und Festlegen von IDs durch den Besucher-ID-Service](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

