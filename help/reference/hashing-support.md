---
description: Experience Cloud ID Service (ECID) unterstützt den SHA-256-Hash-Algorithmus, mit dem Sie Kunden-IDs oder E-Mail-Adressen importieren und Hash-IDs exportieren können. Dies ist eine optionale JavaScript-Methode zum Senden von Hash-Identifikatoren an Experience Cloud. Sie können auch weiterhin Ihre eigenen Hash-Methoden beim Senden von Kunden-IDs verwenden.
keywords: ID-Dienst
title: SHA-256-Hash-Unterstützung für setCustomerIDs
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 97%

---

# SHA-256-Hash-Unterstützung für `setCustomerIDs` {#hashing-support}

Experience Cloud ID Service (ECID) unterstützt den SHA-256-Hash-Algorithmus, mit dem Sie Kunden-IDs oder E-Mail-Adressen importieren und Hash-IDs exportieren können. Dies ist eine optionale JavaScript-Methode zum Senden von Hash-Identifikatoren an Experience Cloud. Sie können auch weiterhin Ihre eigenen Hash-Methoden beim Senden von Kunden-IDs verwenden.
Es gibt folgende zwei Möglichkeiten, um Hash-Unterstützung mit setCustomerIDs zu implementieren:

* [Verwenden der setCustomerIDs-Methode in ECID](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Hinzufügen einer Aktion in Adobe Experience Platform Launch](/help/reference/hashing-support.md#add-action-launch)

## Verwenden der `setCustomerIDs`-Methode in ECID {#use-setcustomerids-method}

In der ersten Variante wird die Methode [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) verwendet.

Vor dem Hashing führt die ECID-Bibliothek eine Datennormalisierung der customerIDs durch. Durch diesen Prozess werden die Leerzeichen zu beiden Enden der customerIDs entfernt und alle Zeichen in Kleinbuchstaben umgewandelt. Beispiel: Die E-Mail-Adresse “ecid@adobe.com“ wird in “ecid@adobe.com“ umgewandelt.

Unten finden Sie ein Code-Beispiel dafür, wie eine einzelne Kunden-ID (die oben genannte E-Mail-Adresse) mit SHA -256-Hashing eingerichtet werden kann.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Neben der Besucher-ID für Experience Cloud können Sie jedem Kunden eine weitere ID, einen Authentifizierungsstatus und einen Hash-Typ (SHA-256) zuweisen. Wenn Sie keinen Hash-Typ angeben, wird angenommen, dass kein Hashing stattfindet.

Bei der `setCustomerIDs` Methode sind mehrere Kunden-IDs für den gleichen Besucher zulässig. Somit können Sie individuelle Benutzer über verschiedene Dienste hinweg einfacher identifizieren oder gezielt ansprechen. Sie können diese IDs beispielsweise als [Kundenattribute](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=de) in Experience Cloud hochladen und aus verschiedenen Lösungen auf die Daten zugreifen.

Kunden-IDs, der Authentifizierungsstatus und der Hash-Typ *werden nicht* in einem Cookie für die spätere Verwendung gespeichert. Stattdessen sollten Kunden-IDs, Authentifizierungsstatus und Hash-Typ in einer Instanzvariablen gespeichert werden, die wie unten dargestellt mithilfe von [`getCustomerIDs`](/help/library/get-set/getcustomerids.md) abgerufen werden kann:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Mit der Methode `setCustomerIDs` wird der Experience Cloud ID-Dienst, nämlich `dpm.demdex.net`, unter Zusatz des Abfrageparameters `d_cid_ic` aufgerufen, der die gehashte Kunden-ID enthält. Ein Beispiel für eine Anfrage finden Sie unten. Zum besseren Verständnis wurden Zeilenumbrüche hinzugefügt.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

In der unten stehenden Tabelle finden Sie eine Beschreibung des `d_cid_ic`-Parameters und des Authentifizierungsstatus.

| Parameter | Beschreibung |
|------------|----------|
| `d_cid_ic` | Übergibt den Integrationscode, die eindeutige Benutzer-ID (DPUUID) und eine Authentifizierungsstatus-ID an den ID-Dienst. Trennen Sie den Integrationscode und die DPUUID durch das nicht druckbare Steuerzeichen <code>%01</code>: <br> Beispiel: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Authentifizierungsstatus</b> <br> Dies ist eine optionale ID im Parameter d_cid_ic. Sie wird als Ganzzahl ausgedrückt und gibt den Authentifizierungsstatus von Benutzern an, wie unten gezeigt: <br> <ul><li>0 (Unbekannt oder noch nie authentifiziert)</li><li>1 (Aktuell authentifiziert für diese Instanz/Seite/App-Kontext)</li><li>2 (Abgemeldet)</li></ul> <br> Beispiele: <br> <ul><li>Unbekannt: ...d_cid=123%01456%01<b>0</b></li><li>Authentifiziert: ...d_cid=123%01456%01<b>1</b></li><li>Abgemeldet: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Hinzufügen einer Aktion in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch bietet die nächste Generation der Tag-Management-Funktionen von Adobe.
Weitere Informationen über Platform Launch finden Sie in der [Launch-Produktdokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de).

Um eine Aktion in Launch hinzuzufügen, lesen Sie die [Dokumentation zu Regeln](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html?lang=de) in Adobe Launch und sehen Sie sich unten den Screenshot an:

![](/help/reference/assets/hashing-support.png)

<br> 

Nachdem Sie Ihre Konfiguration bestätigt haben, werden die Daten wie unten dargestellt von Launch in ein Objekt aufgenommen:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Hier ein Code-Beispiel:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Ähnlich wie bei der im ersten Abschnitt beschriebenen `setCustomerIDs`-Methode führt dies zu einem Aufruf des Experience Cloud ID-Service, wobei der Abfrageparameter `d_cid_ic` hinzugefügt wird.
