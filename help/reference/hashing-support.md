---
description: Der Experience Cloud ID-Dienst (ECID) unterstützt den SHA -256-Hashing-Algorithmus, der es Ihnen ermöglicht, Kunden-IDs oder E-Email-Adressen zu übermitteln und Hash-IDs auszugeben. Dies ist eine optionale Javascript-Methode zum Senden von Hash-Identifikatoren an Experience Cloud. Sie können Ihre eigenen Hashmethoden weiter verwenden, bevor Sie Kunden-IDs senden.
keywords: ID-Dienst
seo-description: Der Experience Cloud ID-Dienst (ECID) unterstützt den SHA -256-Hashing-Algorithmus, der es Ihnen ermöglicht, Kunden-IDs oder E-Email-Adressen zu übermitteln und Hash-IDs auszugeben. Dies ist eine optionale Javascript-Methode zum Senden von Hash-Identifikatoren an Experience Cloud. Sie können Ihre eigenen Hashmethoden weiter verwenden, bevor Sie Kunden-IDs senden.
seo-title: SHA 256 Hashing-Unterstützung für setcustomerids
title: SHA 256 Hashing-Unterstützung für setcustomerids
translation-type: tm+mt
source-git-commit: ac1131be75fd04b51cd1d646086e1802a43afb18

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

Der Experience Cloud ID-Dienst (ECID) unterstützt den SHA -256-Hashing-Algorithmus, der es Ihnen ermöglicht, Kunden-IDs oder E-Email-Adressen zu übermitteln und Hash-IDs auszugeben. Dies ist eine optionale Javascript-Methode zum Senden von Hash-Identifikatoren an Experience Cloud. Sie können Ihre eigenen Hashmethoden weiter verwenden, bevor Sie Kunden-IDs senden.
Es gibt zwei Möglichkeiten, um Hashunterstützung mit setcustomerids zu implementieren, wie in den folgenden Abschnitten beschrieben:

* [Methode setcustomerids in ECID verwenden](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Eine Aktion in Adobe Experience Platform starten](/help/reference/hashing-support.md#add-action-launch)

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

Vor dem Hashing führt die ECID-Bibliothek die Datennormalisierung auf den customerids durch. Durch diesen Prozess werden die Leerräume der customerids auf beiden Enden zugeschnitten und alle Zeichen in Kleinbuchstaben umgewandelt. Beispiel: Bei E-Mail-Adressen: " ecid@adobe.com "wird" ecid@adobe.com "

Unter einem Codebeispiel wird beschrieben, wie Sie eine einzelne Kunden-ID (die oben erwähnte E-Email-Adresse) mit SHA -256-Hashing festlegen.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Zusammen mit der Experience Cloud-Besucher-ID können Sie jedem Besucher weitere Kunden-IDs, Authentifizierungsstatus und Hash-Typen (SHA -256) zuweisen. Wenn Sie keinen Hash-Typ angeben, wird dies als kein Hashing betrachtet.

Bei der `setCustomerIDs` Methode sind mehrere Kunden-IDs für den gleichen Besucher zulässig. Somit können Sie individuelle Benutzer über verschiedene Dienste hinweg einfacher identifizieren oder gezielt ansprechen. Sie können diese IDs beispielsweise als [Kundenattribute](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) in Experience Cloud hochladen und aus verschiedenen Lösungen auf die Daten zugreifen.

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. Ein Beispielaufruf könnte wie folgt aussehen. Zeilenumbrüche wurden zur Klarheit hinzugefügt.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| Parameter | Beschreibung |
|------------|----------|
| `d_cid_ic` | Übergibt den Integrationscode, die eindeutige Benutzer-ID (DPUUID) und eine authentifizierte Status-ID an den ID-Dienst. Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Authentifizierungsstatus</b> <br> Dies ist eine optionale ID im Parameter d_ cid_ ic. Sie wird als Ganzzahl ausgedrückt und gibt den Authentifizierungsstatus von Benutzern an, wie unten gezeigt: <br> <ul><li>0 (Unbekannt oder nie authentifiziert)</li><li>1 (Aktuell authentifiziert für diese Instanz/Seite/App-Kontext)</li><li>2 (Abgemeldet)</li></ul> <br> Beispiele: <br> <ul><li>Unbekannt: ...d_cid=123%01456%01<b>0</b></li><li>Authentifiziert: ...d_cid=123%01456%01<b>1</b></li><li>Abgemeldet: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch ist die nächste Generation von Tag-Management-Funktionen von Adobe. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

Nachdem Sie Ihre Konfiguration bestätigt haben, werden die Daten wie unten dargestellt in ein Objekt aufgenommen:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Hier ein Codebeispiel:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.