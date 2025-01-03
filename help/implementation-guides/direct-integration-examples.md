---
description: Diese Beispiele decken zwei gängige Nutzungsszenarios im Zusammenhang mit einer direkten Integration und der Experience Cloud ID (MID) ab. Dies ist eine eindeutige, dauerhafte ID für Ihre Site-Besucher.
keywords: ID-Dienst
title: Anwendungsfälle der direkten Integration
exl-id: f2a55b90-8307-4242-b20a-6a3c367a251b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 86%

---

# Anwendungsfälle der direkten Integration {#direct-integration-use-cases}

Diese Beispiele decken zwei gängige Nutzungsszenarios im Zusammenhang mit einer direkten Integration und der Experience Cloud ID (ECID oder MID) ab. Dies ist eine eindeutige, dauerhafte ID für Ihre Site-Besucher.

>[!TIP]
>
>* Bevor Sie sich mit den Nutzungsszenarios befassen, sollten Sie sichergehen, dass Sie [Codesyntax und Variablen](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) verstehen.
>* Weitere Informationen über die MID finden Sie unter [Cookies und der Experience Cloud Identity Service](../introduction/cookies.md).
>

## Nutzungsszenario 1: Ich habe eine Experience Cloud ID (MID), möchte jedoch meine eigenen Besucher-IDs verwenden und einen Authentifizierungsstatus festlegen {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nutzungsszenario </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Bedingungen</b> </p> </td> 
   <td colname="col2"> <p>Dieser Anwendungsfall setzt Folgendes: </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Sie verwenden eine MID für den Site-Besucher. Nennen wir diese ID 1234. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Identifizieren Sie diesen Besucher mit Ihrer eigenen eindeutigen ID. Nennen wir diese ID 9876. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Sie möchten die MID (1234) mit Ihrer eigenen eindeutigen ID (9876) verknüpfen. </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(Optional)</i> Sie möchten einen Authentifizierungsstatus für diesen Besucher festlegen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Aktionen</b> </p> </td> 
   <td colname="col2"> <p>Unter diesen Bedingungen rufen Sie den ID-Dienst auf, der Folgendes umfasst: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">Die MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">Ihre Datenanbieter-ID. Dies ist die eindeutige ID, die Ihrer Firma zugewiesen wird. Nennen wir diese ID 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">Ihre ID für den Besucher (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Optional)</i> Eine Status-ID zum Definieren des Authentifizierungsstatus für diesen Besucher. </li> 
    </ul> <p>Und wenn Sie einen der anderen im Handbuch zur <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> Direct Integration aufgelisteten Parameter haben</a> (z. B. <span class="codeph"> d_blob</span> oder <span class="codeph"> dcs_region</span> usw.), ist es in Ordnung, diese ebenfalls zu übergeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung und Codebeispiel</b> </p> </td> 
   <td colname="col2"> <p>Formatieren Sie Ihren Aufruf an den ID-Dienst wie folgt: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Wie Sie sehen, enthält der Beispielaufruf Folgendes: </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID: <span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">MID in Verbindung mit Ihrer eindeutigen ID für den Besucher: <span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">ID für den Authentifizierungsstatus: <span class="codeph">...d_cid=4444%019876%011</span> (Tipp: Es ist die letzte Ziffer.) </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Nutzungsszenario 2: Ich habe keine MID und muss eine generieren {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nutzungsszenario </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Bedingungen</b> </p> </td> 
   <td colname="col2"> <p>Dieser Anwendungsfall setzt Folgendes: </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">Sie verwenden keine MID für den Site-Besucher. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Eine MID muss vom ID-Dienst angefordert werden. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Sie kennen Ihre <a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">Organisations-ID</a>. Nennen wir diese 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Aktionen</b> </p> </td> 
   <td colname="col2"> <p>Unter diesen Bedingungen rufen Sie den ID-Dienst mit Ihrer Organisations-ID auf. </p> <p>Und wenn Sie einen der anderen im Handbuch zur <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> Direct Integration aufgelisteten Parameter haben</a> (z. B. <span class="codeph"> d_blob</span> oder <span class="codeph"> dcs_region</span> usw.), ist es in Ordnung, diese ebenfalls zu übergeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung und Codebeispiel</b> </p> </td> 
   <td colname="col2"> <p>Formatieren Sie Ihren Aufruf an den ID-Dienst wie folgt: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Wie Sie sehen, enthält der Beispielaufruf Ihre Organisations-ID <span class="codeph">d_orgid=5555</span>. Hiermit wird eine <span class="keyword">Experience Cloud</span> ID für diesen Besucher zurückgegeben. </p> </td> 
  </tr> 
 </tbody> 
</table>
