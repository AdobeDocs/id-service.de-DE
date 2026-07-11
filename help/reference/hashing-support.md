---
description: Der Besucher-ID-Dienst (ECID) unterstützt den SHA-256-Hash-Algorithmus, mit dem Sie Kunden-IDs oder E-Mail-Adressen eingeben und Hash-IDs weitergeben können. Dies ist eine optionale JavaScript-Methode zum Senden von Hash-Kennungen an CX Enterprise. Sie können auch weiterhin Ihre eigenen Hash-Methoden beim Senden von Kunden-IDs verwenden.
keywords: Besucher-ID-Service
title: SHA-256-Hash-Unterstützung für setCustomerIDs
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
TQID: https://experienceleague.adobe.com/-JBVon-Qf2jtfd5f4UdWcHVyO7c887p1w-k3GnntUCA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 580
ht-degree: 56%

---

# SHA-256-Hash-Unterstützung für `setCustomerIDs` {#hashing-support}

Der Besucher-ID-Dienst (ECID) unterstützt den SHA-256-Hash-Algorithmus, mit dem Sie Kunden-IDs oder E-Mail-Adressen eingeben und Hash-IDs weitergeben können. Dies ist eine optionale JavaScript-Methode zum Senden von Hash-Kennungen an CX Enterprise. Sie können auch weiterhin Ihre eigenen Hash-Methoden beim Senden von Kunden-IDs verwenden.Es gibt folgende zwei Möglichkeiten, um Hash-Unterstützung mit setCustomerIDs zu implementieren:

* [Verwenden der setCustomerIDs-Methode in ECID](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Hinzufügen einer Aktion in Tags](/help/reference/hashing-support.md#add-action-launch)

## Verwenden der `setCustomerIDs`-Methode in ECID {#use-setcustomerids-method}

In der ersten Variante wird die Methode [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) verwendet.

Vor dem Hashing führt die ECID-Bibliothek eine Datennormalisierung der customerIDs durch. Durch diesen Prozess werden die Leerzeichen zu beiden Enden der customerIDs entfernt und alle Zeichen in Kleinbuchstaben umgewandelt. Beispiel: Die E-Mail-Adresse “ecid@adobe.com“ wird in “ecid@adobe.com“ umgewandelt.

Unten finden Sie ein Code-Beispiel dafür, wie eine einzelne Kunden-ID (die oben genannte E-Mail-Adresse) mit SHA -256-Hashing eingerichtet werden kann.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

Neben der ECID können Sie jedem Besucher weitere Kunden-IDs, einen Authentifizierungsstatus und einen Hash-Typ (SHA-256) zuweisen. Wenn Sie keinen Hash-Typ angeben, wird angenommen, dass kein Hashing stattfindet.

Bei der `setCustomerIDs` Methode sind mehrere Kunden-IDs für den gleichen Besucher zulässig. Somit können Sie individuelle Benutzer über verschiedene Dienste hinweg einfacher identifizieren oder gezielt ansprechen. Beispielsweise können Sie diese IDs als „Kundenattribute[ in ](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=de) Enterprise hochladen und lösungsübergreifend auf diese Daten zugreifen.

Kunden-IDs, der Authentifizierungsstatus und der Hash-Typ *werden nicht* in einem Cookie für die spätere Verwendung gespeichert. Stattdessen sollten Kunden-IDs, Authentifizierungsstatus und Hash-Typ in einer Instanzvariablen gespeichert werden, die wie unten dargestellt mithilfe von [`getCustomerIDs`](/help/library/get-set/getcustomerids.md) abgerufen werden kann:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Die Verwendung der `setCustomerIDs` führt zu einem Aufruf des Besucher-ID-Service an `dpm.demdex.net`, wobei der Abfrageparameter `d_cid_ic` hinzugefügt wird, der die gehashte Kunden-ID enthält. Ein Beispiel für eine Anfrage finden Sie unten. Zum besseren Verständnis wurden Zeilenumbrüche hinzugefügt.

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
| `d_cid_ic` | Übergibt den Integrations-Code, die Unique User ID (DPUUID) und eine authentifizierte Status-ID an den Besucher-ID-Service. Trennen Sie den Integrations-Code und die DPUUID durch das nicht druckbare Steuerzeichen, <code>%01</code>: <br> Beispiel: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Authentifizierungsstatus</b> <br> Dies ist eine optionale ID im Parameter d_cid_ic. Sie wird als Ganzzahl ausgedrückt und gibt den Authentifizierungsstatus von Benutzern an, wie unten gezeigt: <br> <ul><li>0 (Unbekannt oder noch nie authentifiziert)</li><li>1 (Aktuell authentifiziert für diese Instanz/Seite/App-Kontext)</li><li>2 (Abgemeldet)</li></ul> <br> Beispiele: <br> <ul><li>Unbekannt: ...d_cid=123%01456%01<b>0</b></li><li>Authentifiziert: ...d_cid=123%01456%01<b>1</b></li><li>Abgemeldet: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Hinzufügen einer Aktion in Tags {#add-action-launch}

Tags in der Adobe Experience Platform-Datenerfassung stellen die nächste Generation der Tag-Management-Funktionen von Adobe dar. Weitere Informationen finden Sie in der [Tags-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de).

Um eine Aktion in Tags hinzuzufügen, lesen Sie die [Regeldokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html?lang=de) und sehen Sie sich die Bildschirmaufzeichnung unten an:

![](/help/reference/assets/hashing-support.png)

<br> 

Nach Bestätigung Ihrer Konfiguration schließen Tags die Daten in ein -Objekt ein, wie unten dargestellt:

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

Ähnlich wie bei der im ersten Abschnitt beschriebenen `setCustomerIDs` führt dies zu einem Aufruf des Besucher-ID-Service, wobei der `d_cid_ic` Abfrageparameter hinzugefügt wird.

