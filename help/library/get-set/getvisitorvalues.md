---
description: Hierbei handelt es sich um eine asynchrone API, die standardmäßig IDs für Analytics, den ID-Dienst, die Abmeldung von der Datenerfassung, den geografischen Standort und Metadateninhalte („Blob“) zurückgibt. Sie können auch mit dem optionalen Enum-Wert visitor.FIELDS steuern, welche IDs zurückgegeben werden.
keywords: ID-Dienst
seo-description: Hierbei handelt es sich um eine asynchrone API, die standardmäßig IDs für Analytics, den ID-Dienst, die Abmeldung von der Datenerfassung, den geografischen Standort und Metadateninhalte („Blob“) zurückgibt. Sie können auch mit dem optionalen Enum-Wert visitor.FIELDS steuern, welche IDs zurückgegeben werden.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7 fb 831 b 3-cf 7 e -40 e 2-a 219-07 fec 28 ad 49 c
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getVisitorValues{#getvisitorvalues}

Hierbei handelt es sich um eine asynchrone API, die standardmäßig IDs für Analytics, den ID-Dienst, die Abmeldung von der Datenerfassung, den geografischen Standort und Metadateninhalte („Blob“) zurückgibt. Sie können auch mit dem optionalen Enum-Wert visitor.FIELDS steuern, welche IDs zurückgegeben werden.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Syntax </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Nutzungsszenario 1: Standarddatensatz anfordern </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Nutzungsszenario 2: Benutzerdefinierten Datensatz anfordern </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Definierte Antwortparameter </a> </li> 
</ul>

## Syntax {#section-5aebe3907b2b46e997f45a1d1ed35c09}

This function uses the following syntax (italics represents a placeholder for a variable): ` var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

In den Funktionsparametern:

* ` *`callback`*` stellt Ihren eigenen Callback-Code dar, der die zurückgegebenen IDs erhält.
* *(Optional)* ` visitor.FIELDS. *`Der ID-Typ`*` ist ein Enum, mit dem Sie angeben können, welche [ID-Werte](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) diese Funktion zurückgeben soll.

Weitere Informationen finden Sie in den folgenden Nutzungsszenarios und Definitionen.

## Nutzungsszenario 1: Standarddatensatz anfordern {#section-36a31683558742a5915db3a391e09f7b}

Dieser Code gibt den Standarddatensatz zurück. Ihre Anforderung und die Antwort sollten etwa wie in den folgenden Beispielen aussehen.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

In der Standardbeispielantwort wurden einige Werte zu Demonstrationszwecken gekürzt.

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

In diesem Code wird ein optionales Array verwendet, um einen spezifischen Satz von IDs mit der `visitor.FIELDS`-Enumeration zurückzugeben. In diesem Fall werden nur die Experience Cloud ID (MCID) und die Analytics ID (MCAID) benötigt. Ihre Anforderung und die Antwort sollten etwa wie in den folgenden Beispielen aussehen.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

Die benutzerdefinierte Beispielantwort gibt nur die in der Anforderung angegebenen IDs zurück.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Definierte Antwortparameter {#section-4c4c300167694c6fbff1d6c612f372b5}

In der folgenden Tabelle sind die Antwortparameter aufgeführt und definiert. Dies sind auch alle Werte in der `visitor.FIELDS`-Enumeration. Beachten Sie, dass diese Methode eine leere Zeichenfolge zurückgibt, wenn keine Werte für eine bestimmte Variable vorhanden sind.

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
   <td colname="col2"> <p>Die Regions-ID für die Datenerfassung. Hierbei handelt es sich um eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. </p> <p>Siehe <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external"> DCS Regions-IDs, Speicherorte und Hostnamen </a> und <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getlocationhint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>Die <span class="keyword">Analytics</span>-ID des Besuchers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>Die Experience Cloud ID des Besuchers. </p> <p>Siehe <a href="../../introduction/cookies.md" format="dita" scope="local"> Cookies und der Experience Platform Identity Service </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Eine Kennzeichnung, die angibt, ob ein Besucher von der Datenerfassung ausgeschlossen werden möchte. </p> <p>Gültige Werte: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: Ein Besucher möchte von der Datenerfassung ausgeschlossen werden. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: Ein Besucher möchte nicht von der Datenerfassung ausgeschlossen werden. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

