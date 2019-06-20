---
description: Neben der Besucher-ID für Experience Cloud können Sie jedem Kunden eine weitere ID und einen Authentifizierungsstatus zuweisen.
keywords: ID-Dienst
seo-description: Neben der Besucher-ID für Experience Cloud können Sie jedem Kunden eine weitere ID und einen Authentifizierungsstatus zuweisen.
seo-title: Kunden-IDs und Authentifizierungsstatus
title: Kunden-IDs und Authentifizierungsstatus
uuid: 643 df 363-224 a -463 e-a 332-be 59926 b 47 e 7
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Kunden-IDs und Authentifizierungsstatus {#customer-ids-and-authentication-states}

Neben der Besucher-ID für Experience Cloud können Sie jedem Kunden eine weitere ID und einen Authentifizierungsstatus zuweisen.

## Authentifizierungsstatus {#section-68ad4065dfaa437d9070832d6e2bf85c}

Bei der Methode `setCustomerIDs` sind mehrere Kunden-IDs für den gleichen Besucher zulässig. Somit können Sie individuelle Benutzer über verschiedene Dienste hinweg einfacher identifizieren oder gezielt ansprechen. Sie können diese IDs beispielsweise als [Kundenattribute](https://marketing.adobe.com/resources/help/en_US/mcloud/?f=attributes.html) in [!DNL Experience Cloud] hochladen und aus verschiedenen Lösungen auf die Daten zugreifen.

>[!IMPORTANT]
>
>`setCustomerIDs` (Synchronisierung von Kunden-Ids) ist für Kundenattribute und Hauptdienste erforderlich. Die Synchronisierung der Kunden-IDs ist eine optionale Identifikationsmethode für [!DNL Analytics]. [!DNL Target] erfordert `Visitor.AuthState.AUTHENTICATED` , dass Kundenattribute funktionieren. Beispiele hierzu finden Sie unter [Kerndienste – Aktivierung Ihrer Lösungen](https://marketing.adobe.com/resources/help/en_US/mcloud/?f=core_services).

Beginning with Experience Cloud ID Service v1.5+, `setCustomerIDs` includes the optional `AuthState` object. `AuthState` identifiziert Benutzer anhand ihres Authentifizierungsstatus (z. B. angemeldet, abgemeldet). Der Authentifizierungsstatus wird von Ihnen mittels eines in der Tabelle aufgeführten Statuswerts festgelegt. Ein Authentifizierungsstatus wird immer als Ganzzahl ausgegeben.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Authentifizierungsstatus </th> 
   <th colname="col2" class="entry"> Statusganzzahl </th> 
   <th colname="col3" class="entry"> Benutzerstatus </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Unbekannt oder noch nie authentifiziert. </p> <p> „Unbekannt“ wird standardmäßig angewendet, wenn <span class="codeph">AuthState</span> bei einer Besucher-ID nicht verwendet wird oder nicht explizit auf jeder Seite des Anwendungskontexts angegeben ist. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Für eine bestimmte Instanz, Seite oder Anwendung authentifiziert. </p> <p> <p>Achtung: Für eine ordnungsgemäße Funktion erfordern Kundenattribute für <span class="keyword">Target</span> diesen Status. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">2</span> </p> </td> 
   <td colname="col3"> <p>Abgemeldet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Nutzungsszenarios für Authentifizierungsstatus {#section-fe9560cc490943b29dac2c4fb6efd72c}

Sie können Ihren Benutzern Authentifizierungsstatus zuweisen, je nachdem, welche Aktionen sie in Ihren Webeigenschaften durchführen und ob sie authentifiziert sind. Einige Beispiele finden Sie in der folgenden Tabelle:

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Authentifizierungsstatus </th> 
   <th colname="col2" class="entry"> Anwendungsfall </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>Dieser Status kann beispielsweise für folgende Szenarios verwendet werden: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Lesen einer E-Mail (bei dieser Aktion ist der Leser wahrscheinlich der vorgesehene Empfänger, die E-Mail kann jedoch auch weitergeleitet worden sein) </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Aufrufen einer Landingpage durch Klicken auf einen Link in einer E-Mail </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>Der Benutzer ist zurzeit in einer aktiven Sitzung auf Ihrer Website oder in Ihrer Applikation authentifiziert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>Der Benutzer war authentifiziert, hat sich dann aber aktiv abgemeldet. Der authentifizierte Status wurde absichtlich beendet. Der Benutzer möchte nicht mehr als authentifiziert behandelt werden. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Festlegen von Kunden-IDs und Authentifizierungsstatus {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Kunden-IDs können, wie im Folgenden dargestellt, aus Kombinationen aus IDs und Authentifizierungsstatus bestehen.

>[!IMPORTANT]
>
>* Bei IDs wird die Groß-/Kleinschreibung beachtet.
>* Für IDs sollten ausschließlich nicht codierte Werte verwendet werden.
>* Kunden-IDs und Authentifizierungsstatus werden nicht im Besucher-ID-Cookie gespeichert. Sie müssen für jede Seite und jeden Anwendungskontext separat festgelegt werden.
>* In den Kunden-IDs dürfen keinerlei personenbezogene Informationen (PII) enthalten sein. Wenn Sie zur Besucheridentifizierung PII verwenden (z. B. eine E-Mail-Adresse), sollten Sie stattdessen eine Hash- oder verschlüsselte Version dieser Daten verwenden.
>



```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Ausgabe von Kunden-IDs und Authentifizierungsstatus {#section-71a610546188478fa9a3185a01d6e83b}

Mit `getCustomerIDs` können Sie Kunden-IDs und zugehörige Authentifizierungsstatus ausgeben. Anhand dieser Methode wird der Authentifizierungsstatus eines Besuchers als Ganzzahl ausgegeben.

**Syntax**

`getCustomerIDs` gibt nach folgender Syntax Daten aus.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**Beispiele**

Ausgegebene Kunden-IDs und Authentifizierungsstatus sollten in etwa wie folgt aussehen.

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"puuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK-Unterstützung {#section-861c6b3b1ba645dda133dccb22ec7bb0}

Der [!DNL Experience Cloud] ID-Dienst unterstützt Kunden-IDs und Authentifizierungsstatus in unserem Android- und iOS-SDK-Code. Siehe die folgenden Codebibliotheken:

* [Android SDK-Methoden](https://marketing.adobe.com/resources/help/en_US/mobile/android/?f=c_marketing_cloud.html)
* [iOS SDK-Methoden](https://marketing.adobe.com/resources/help/en_US/mobile/ios/?f=marketing_cloud.html)

## Hinweise für Kunden von Analytics und Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Sollten Sie deklarierte IDs an [!DNL Audience Manager] weiterleiten, muss das Objekt `userid` dem mit einer Datenquelle verknüpften Integrations-Code entsprechen. For more information, see the [!DNL Visitor ID Service] section in the [Configure Merge Rules Code](https://marketing.adobe.com/resources/help/en_US/aam/?f=merge-rules-configure-code.html) documentation.
