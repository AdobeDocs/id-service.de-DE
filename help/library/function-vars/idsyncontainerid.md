---
description: Diese Eigenschaft legt die Container-ID der Datenquelle fest, die Sie für ID-Synchronisierungen verwenden möchten.
keywords: ID-Dienst
title: idSyncContainerID
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '319'
ht-degree: 100%

---

# idSyncContainerID{#idsynccontainerid}

Diese Eigenschaft legt die Container-ID der Datenquelle fest, die Sie für ID-Synchronisierungen verwenden möchten.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Syntax und Codebeispiel </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local"> Was sind Container und wann werden sie verwendet? </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Einrichten von Container-IDs bei Verwendung von DIL und VisitorAPI.js </a> </li> 
</ul>

## Syntax und Codebeispiel {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Syntax:** ` idSyncContainerID: *`container ID value`*`

**Codebeispiel:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## Was sind Container und wann werden sie verwendet?  {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Behälter**

Container sind Objekte, die von [!DNL Audience Manager] erstellt werden. Obwohl kein externer Zugriff möglich ist, listen diese Container alle Datenquellen auf, die

* für Sie verfügbar sind, jedoch nicht für die ID-Synchronisierung verwendet werden. 
* die für die ID-Synchronisierung verwendet werden.

Auch wenn Sie kein [!DNL Audience Manager]-Kunde sind, enthält Ihr Konto diese Container, wenn Sie IDs mit verschiedenen Datenquellen auf unterschiedlichen Seiten in Ihrer Domäne austauschen. Der Grund dafür ist, dass [!DNL Audience Manager] die Technologie und die Backend-Funktionalität zur Verfügung stellt, die eine ID-Synchronisierung ermöglichen.

**Nutzungsszenarios**

Je nach Situation müssen Sie diese Konfiguration möglicherweise Ihrem ID-Dienst-Code hinzufügen.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Bedingung </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Nicht erforderlich</b> </p> </td> 
   <td colname="col2"> <p>Unter folgenden Bedingungen müssen Sie diese Konfiguration nicht verwenden: </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">Wenn Sie den ID-Dienst mit einer beliebigen <span class="keyword">Experience Cloud</span>-Lösung verwenden und keine ID-Synchronisierungen mit anderen Datenquellen durchführen. In diesem Fall hat Ihr Konto einen Standard-Container mit der ID 0, und es ist keine Aktion erforderlich. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">Alle Ihre Datenquellen befinden sich in einem einzigen Container. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Erforderlich</b> </p> </td> 
   <td colname="col2"> <p>Sie müssen diese Konfiguration verwenden, wenn alle der folgenden Bedingungen zutreffen: </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">Sie verwenden <span class="keyword">Audience Manager</span> nicht. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">Sie müssen IDs mit anderen Datenquellen synchronisieren, die von Containern organisiert werden. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">Sie müssen IDs mit Datenquellen in unterschiedlichen Containern auf verschiedenen Seiten Ihrer Domain synchronisieren. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Einrichten von Container-IDs bei Verwendung von DIL und VisitorAPI.js  {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Wenn Sie [!UICONTROL DIL ]* und* VisitorAPI.js auf derselben Seite bereitgestellt haben:

* Der Dienstcode für die Besucher-ID hat bei ID-Synchronisierungen Vorrang vor DIL.
* Legen Sie die `idSyncContainerID`-Konfiguration nur im Code des ID-Diensts fest.
