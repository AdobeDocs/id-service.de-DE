---
description: Neben der ECID können Sie jedem Besucher zusätzliche Kunden-IDs und einen Authentifizierungsstatus zuweisen.
keywords: Besucher-ID-Service
title: Kunden-IDs und Authentifizierungsstatus
exl-id: 0215225c-20f5-4e44-a368-b2df683aca9d
TQID: https://experienceleague.adobe.com/0z2HaRyNYcuJhE6WMkTZVXK-DiPu2S5bdnOiYsZwxYg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 642
ht-degree: 78%

---

# Kunden-IDs und Authentifizierungsstatus {#customer-ids-and-authentication-states}

Neben der ECID können Sie jedem Besucher zusätzliche Kunden-IDs und einen Authentifizierungsstatus zuweisen.

## Authentifizierungsstatus {#section-68ad4065dfaa437d9070832d6e2bf85c}

Bei der `setCustomerIDs` Methode sind mehrere Kunden-IDs für den gleichen Besucher zulässig. Somit können Sie individuelle Benutzer über verschiedene Dienste hinweg einfacher identifizieren oder gezielt ansprechen. Beispielsweise können Sie diese IDs als „Kundenattribute[ in ](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=de) Enterprise hochladen und lösungsübergreifend auf diese Daten zugreifen.

>[!IMPORTANT]
>
>`setCustomerIDs` (Synchronisierung der Kunden-ID) ist für Kundenattribute und die Funktionalität der Kerndienste erforderlich. Das Synchronisieren von Kunden-IDs ist eine optionale Identifizierungsmethode für Analytics. Target erfordert `Visitor.AuthState.AUTHENTICATED`, damit Kundenattribute funktionieren. Beispiele hierzu finden Sie unter [Kerndienste – Aktivierung Ihrer Lösungen](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=de).

Ab der Visitor ID Service-Version 1.5 enthält `setCustomerIDs` das optionale `AuthState`. `AuthState` identifiziert Benutzer anhand ihres Authentifizierungsstatus (z. B. angemeldet, abgemeldet). Sie legen den Authentifizierungsstatus mit einem in der Tabelle aufgeführten Statuswert fest. Der Authentifizierungsstatus wird als Ganzzahl zurückgegeben.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Authentifizierungsstatus </th> 
   <th colname="col2" class="entry"> Ganzzahl des Status </th> 
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
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>Abgemeldet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Nutzungsszenarios für Authentifizierungsstatus {#section-fe9560cc490943b29dac2c4fb6efd72c}

Sie können Ihren Benutzern Authentifizierungsstatus zuweisen, je nachdem, welche Aktionen sie für Ihre Web-Eigenschaften durchführen und ob sie authentifiziert sind. In der unten stehenden Tabelle finden Sie einige Beispiele:

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
   <td colname="col2"> <p>Dieser Status kann beispielsweise für folgende Szenarien verwendet werden: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Lesen einer E-Mail (bei dieser Aktion ist der Leser der vorgesehene Empfänger, die E-Mail hätte aber auch weitergeleitet werden können). </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Öffnen einer Landingpage durch Klicken auf eine E-Mail. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>Der Benutzer ist zurzeit in einer aktiven Sitzung auf Ihrer Website oder in Ihrer Applikation authentifiziert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>Der Benutzer war authentifiziert, hat sich dann aber aktiv abgemeldet. Der Benutzer beabsichtigte, die Verbindung zum authentifizierten Status zu trennen. Der Benutzer möchte nicht mehr als authentifiziert gehandhabt werden. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Festlegen von Kunden-IDs und Authentifizierungsstatus {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Kunden-IDs können, wie im Folgenden dargestellt, aus Kombinationen aus IDs und Authentifizierungsstatus bestehen.

>[!IMPORTANT]
>
>* Bei IDs wird die Groß-/Kleinschreibung beachtet.
>* Für IDs sollten ausschließlich nicht codierte Werte verwendet werden.
>* Kunden-IDs und Authentifizierungsstatus werden nicht im Besucher-ID-Cookie gespeichert. Sie müssen für jede Seite oder jeden Anwendungskontext festgelegt werden.
>* Sie sollten keine persönlich identifizierbaren Informationen (PII) in die Kunden-IDs aufnehmen. Wenn Sie zur Besucheridentifizierung PII verwenden (z. B. eine E-Mail-Adresse), sollten Sie stattdessen eine Hash- oder verschlüsselte Version dieser Daten verwenden. Die ECID-Bibliothek unterstützt das Hashing von Benutzer-IDs. Siehe [SHA-256-Hashing-Unterstützung für setCustomerIDs](/help/reference/hashing-support.md).

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
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
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
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Ausgabe von Kunden-IDs und Authentifizierungsstatus {#section-71a610546188478fa9a3185a01d6e83b}

Mit `getCustomerIDs` können Sie Kunden-IDs und zugehörige Authentifizierungsstatus ausgeben. Diese Methode gibt den authentifizierten Status eines Besuchers als Ganzzahl zurück.

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

Die zurückgegebenen Kunden-IDs und Authentifizierungsstatusdaten sollten in etwa wie folgt aussehen:

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
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK-Unterstützung {#section-861c6b3b1ba645dda133dccb22ec7bb0}

Der Besucher-ID-Dienst unterstützt Kunden-IDs und Authentifizierungszustände in unserem Android- und iOS SDK-Code. Siehe die folgenden Code-Bibliotheken:

* [ SDK-Methoden für Android ](https://experienceleague.adobe.com/docs/mobile-services/android/overview.html?lang=de)
* [iOS SDK-Methoden](https://experienceleague.adobe.com/docs/mobile-services/ios/overview.html?lang=de)

## Hinweise für Kunden von Analytics und Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Wenn Sie deklarierte IDs an Audience Manager übergeben, muss das `userid`-Objekt mit dem Integrations-Code übereinstimmen, der mit einer Datenquelle verknüpft ist. Weitere Informationen finden Sie im Abschnitt [!UICONTROL Visitor ID Service] in der Dokumentation [Konfigurieren von Zusammenführungsregeln](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html?lang=de#configure-merge-rule-code).

