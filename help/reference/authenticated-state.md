---
description: Neben der Besucher-ID für Experience Cloud können Sie jedem Kunden eine weitere ID und einen Authentifizierungsstatus zuweisen.
keywords: ID-Dienst
title: Kunden-IDs und Authentifizierungsstatus
exl-id: 0215225c-20f5-4e44-a368-b2df683aca9d
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: ht
source-wordcount: '629'
ht-degree: 100%

---

# Kunden-IDs und Authentifizierungsstatus {#customer-ids-and-authentication-states}

Neben der Besucher-ID für Experience Cloud können Sie jedem Kunden eine weitere ID und einen Authentifizierungsstatus zuweisen.

## Authentifizierungsstatus {#section-68ad4065dfaa437d9070832d6e2bf85c}

Bei der `setCustomerIDs` Methode sind mehrere Kunden-IDs für den gleichen Besucher zulässig. Somit können Sie individuelle Benutzer über verschiedene Dienste hinweg einfacher identifizieren oder gezielt ansprechen. Sie können diese IDs beispielsweise als [Kundenattribute](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=de) in [!DNL Experience Cloud] hochladen und aus verschiedenen Lösungen auf die Daten zugreifen.

>[!IMPORTANT]
>
>`setCustomerIDs` (Synchronisierung der Kunden-ID) ist für Kundenattribute und die Funktionalität der Kerndienste erforderlich. Die Synchronisierung der Kunden-IDs ist eine optionale Identifikationsmethode für [!DNL Analytics]. Für [!DNL Target] ist `Visitor.AuthState.AUTHENTICATED` erforderlich, damit die Kundenattribute funktionieren. Beispiele hierzu finden Sie unter [Kerndienste – Aktivierung Ihrer Lösungen](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=de).

Ab der Experience Cloud Identity Serviceversion 1.5 enthält `setCustomerIDs` das optionale Objekt `AuthState`. `AuthState` identifiziert Benutzer anhand ihres Authentifizierungsstatus (z. B. angemeldet, abgemeldet). Sie legen den Authentifizierungsstatus mit einem in der Tabelle aufgeführten Statuswert fest. Der Authentifizierungsstatus wird als Ganzzahl zurückgegeben.

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

## Nutzungsszenarios für Authentifizierungsstatus  {#section-fe9560cc490943b29dac2c4fb6efd72c}

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
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Lesen einer E-Mail (bei diesem Vorgang ist der Leser der vorgesehene Empfänger, die E-Mail hätte aber auch weitergeleitet werden können). </li> 
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

## SDK-Unterstützung  {#section-861c6b3b1ba645dda133dccb22ec7bb0}

Der [!DNL Experience Cloud] ID-Dienst unterstützt Kunden-IDs und Authentifizierungsstatus in unserem Android- und iOS-SDK-Code. Siehe die folgenden Code-Bibliotheken:

* [ SDK-Methoden für Android ](https://experienceleague.adobe.com/docs/mobile-services/android/overview.html?lang=de)
* [iOS-SDK-Methoden](https://experienceleague.adobe.com/docs/mobile-services/ios/overview.html?lang=de)

## Hinweise für Kunden von Analytics und Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Sollten Sie deklarierte IDs an [!DNL Audience Manager] weiterleiten, muss das Objekt `userid` dem mit einer Datenquelle verknüpften Integrations-Code entsprechen. Weitere Informationen finden Sie im Abschnitt [!UICONTROL Besucher-ID-Dienst] in der Dokumentation [Konfiguration von Regelverschmelzungs-Code](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html?lang=de#configure-merge-rule-code).
