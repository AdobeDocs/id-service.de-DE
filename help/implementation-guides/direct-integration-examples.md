---
description: Diese Beispiele decken zwei gängige Anwendungsfälle im Zusammenhang mit einer direkten Integration und der ECID ab. Dies ist eine eindeutige, dauerhafte ID für Ihre Site-Besucher.
keywords: Besucher-ID-Service
title: Anwendungsfälle der direkten Integration
exl-id: f2a55b90-8307-4242-b20a-6a3c367a251b
TQID: https://experienceleague.adobe.com/1vfYQsSZiqM3SrnP0lmSrZEWpAMsbwVK8sR0MNitetQ
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 456
ht-degree: 53%

---

# Anwendungsfälle der direkten Integration {#direct-integration-use-cases}

Diese Beispiele decken zwei gängige Anwendungsfälle im Zusammenhang mit einer direkten Integration und der ECID (auch als MID bezeichnet) ab. Dies ist eine eindeutige, dauerhafte ID für Ihre Site-Besucher.

>[!TIP]
>
>* Bevor Sie sich mit den Nutzungsszenarios befassen, sollten Sie sichergehen, dass Sie [Codesyntax und Variablen](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) verstehen.
>* Weitere Informationen zur MID finden Sie unter [Cookies und der Besucher-ID-Dienst](../introduction/cookies.md).
>

## Anwendungsfall 1: Ich habe eine ECID, möchte jedoch meine Besucher-IDs übergeben und einen Authentifizierungsstatus festlegen {#section-a67d89a343754d1286d03cf08d34b806}

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
   <td colname="col2"> <p>Rufen Sie unter diesen Bedingungen den Besucher-ID-Dienst auf, der Folgendes enthält: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">Die MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">Ihre Datenanbieter-ID. Dies ist die eindeutige ID, die Ihrer Firma zugewiesen wird. Nennen wir diese ID 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">Ihre ID für den Besucher (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Optional)</i> Eine Status-ID zum Definieren des Authentifizierungsstatus für diesen Besucher. </li> 
    </ul> <p>Und wenn Sie einen der anderen Parameter haben, die im Handbuch zur <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> Direct Integration aufgeführt sind</a> (z. B. <span class="codeph"> d_blob</span> oder <span class="codeph"> dcs_region</span>, usw.) Es ist in Ordnung, diese auch zu übergeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung und Codebeispiel</b> </p> </td> 
   <td colname="col2"> <p>Formatieren Sie den Aufruf an den Besucher-ID-Dienst wie folgt: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&d_cid=4444%019876%011&d_ver=2</span> </p> <p>Wie Sie sehen, enthält der Beispielaufruf Folgendes: </p> 
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
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Muss eine MID vom Besucher-ID-Service anfordern. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Ermitteln Sie Ihre <a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local"> IMS-Organisations-ID</a>. Nennen wir diese 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Aktionen</b> </p> </td> 
   <td colname="col2"> <p>Rufen Sie unter diesen Bedingungen den Besucher-ID-Dienst auf, der Ihre IMS-Organisations-ID enthält. </p> <p>Und wenn Sie einen der anderen Parameter haben, die im Handbuch zur <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> Direct Integration aufgeführt sind</a> (z. B. <span class="codeph"> d_blob</span> oder <span class="codeph"> dcs_region</span>, usw.) Es ist in Ordnung, diese auch zu übergeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung und Codebeispiel</b> </p> </td> 
   <td colname="col2"> <p>Formatieren Sie den Aufruf an den Besucher-ID-Dienst wie folgt: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&d_ver=2</span> </p> <p>Beachten Sie, dass der Beispielaufruf Ihre IMS-Organisations-ID (d<span class="codeph">orgid=5555) </span>. Gibt eine ECID für diesen Besucher zurück. </p> </td> 
  </tr> 
 </tbody> 
</table>

