---
description: Hierbei handelt es sich um eine asynchrone API, die standardmäßig Kennungen für Analytics, den Besucher-ID-Service, das Opt-out von der Datenerfassung, den geografischen Standort und „Blob“-Inhalte von Metadaten zurückgibt. Sie können auch mit dem optionalen Aufzählungswert visitor.FIELDS steuern, welche IDs zurückgegeben werden.
keywords: Besucher-ID-Service
title: getVisitorValues
exl-id: bd023e8d-a804-4205-989f-e1e58080b63c
TQID: https://experienceleague.adobe.com/CF9G6wKlDxjklwedJk8KVmYH7KjA7CRkxtNu-mQ-Kjs
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 420
ht-degree: 77%

---

# getVisitorValues{#getvisitorvalues}

Hierbei handelt es sich um eine asynchrone API, die standardmäßig Kennungen für Analytics, den Besucher-ID-Service, das Opt-out von der Datenerfassung, den geografischen Standort und „Blob“-Inhalte von Metadaten zurückgibt. Sie können auch mit dem optionalen Aufzählungswert visitor.FIELDS steuern, welche IDs zurückgegeben werden.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Syntax </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Nutzungsszenario 1: Standarddatensatz anfordern </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Nutzungsszenario 2: Benutzerdefinierten Datensatz anfordern </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Definierte Antwortparameter </a> </li> 
</ul>

## Syntax {#section-5aebe3907b2b46e997f45a1d1ed35c09}

Diese Funktion verwendet die folgende Syntax (kursiv stellt einen Platzhalter für eine Variable dar): `var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

In den Funktionsparametern:

* `*`callback`*` entspricht Ihrem eigenen Rückrufcode, der die zurückgegebenen IDs erhält.
* *(Optional)* `visitor.FIELDS. *`ID type`*` ist eine Enumeration, mit der Sie [ID-Werte](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) angeben können, die von dieser Funktion zurückgegeben werden sollen.

Weitere Informationen finden Sie in den folgenden Nutzungsszenarios und Definitionen.

## Nutzungsszenario 1: Standarddatensatz anfordern {#section-36a31683558742a5915db3a391e09f7b}

Dieser Code gibt den Standarddatensatz zurück. Ihre Anforderung und Ihre Antwort könnten den folgenden Beispielen ähneln.

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

Im Beispiel für die standardmäßige Antwort wurden einige Werte zu Demonstrationszwecken gekürzt.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## Nutzungsszenario 2: Benutzerdefinierten Datensatz anfordern {#section-467b2f4e513344c89b7332b05f6f59f3}

In diesem Code wird ein optionales Array verwendet, um einen spezifischen Satz von IDs mit der `visitor.FIELDS`-Aufzählung zurückzugeben. In diesem Fall benötigen wir nur die ECID (MCID) und Analytics ID (MCAID) des Besuchers. Ihre Anforderung und Ihre Antwort könnten den folgenden Beispielen ähneln.

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

Die benutzerdefinierte Antwort im Beispiel gibt nur die in der Anforderung angegebenen IDs zurück.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Definierte Antwortparameter {#section-4c4c300167694c6fbff1d6c612f372b5}

In der folgenden Tabelle sind die Antwortparameter aufgeführt und definiert. Dies sind auch alle Werte in der `visitor.FIELDS`-Aufzählung. Beachten Sie, dass diese Methode eine leere Zeichenfolge zurückgibt, wenn es für eine bestimmte Variable keine Werte gibt.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Wert </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>Verschlüsselte <span class="keyword">Audience Manager</span>-Metadaten, auch „Blob“ genannt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>Die Regions-ID für die Datenerfassung. Dies ist eine numerische Kennung für den geografischen Standort eines bestimmten Besucher-ID-Service-Rechenzentrums. </p> <p>Siehe <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=de" format="https" scope="external"> DCS-Regions-IDs, Standorte und Hostnamen </a> und <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>Die <span class="keyword">Analytics</span>-ID des Besuchers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>Die ECID des Besuchers. </p> <p>Siehe <a href="../../introduction/cookies.md" format="dita" scope="local"> von Cookies und die </a> des Besucher-ID-Diensts . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Eine Markierung, die angibt, ob ein Besucher die Datenerfassung ablehnt. </p> <p>Die Werte umfassen: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: Ein Besucher möchte von der Datenerfassung ausgeschlossen werden. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: Ein Besucher möchte nicht von der Datenerfassung ausgeschlossen werden. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

