---
description: Diese Konfiguration ermöglicht es Ihnen, das standardmäßige Supplemental Data ID (SDID)-Ablaufintervall zu ändern, wenn Sie die ID mit der Hilfsfunktion „appendSupplementalDataIDTo “ an eine andere Seite übergeben. Standardmäßig verfügt der Besucher-ID-Dienst-Code auf der empfangenden Seite über 30 Sekunden, um die SDID aus der URL abzurufen, die von der verweisenden Seite gesendet wurde. Wenn der Besucher-ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, fordert er eine neue SDID an. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und Kontrolle über dieses Zeitüberschreitungsintervall haben möchten.
keywords: Besucher-ID-Service
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
TQID: https://experienceleague.adobe.com/PUHy-KpWKY0BQSMkKidwpLYES6FvME2EtKCbCpfMFrw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 54%

---

# sdidParamExpiry{#sdidparamexpiry}

Diese Konfiguration ermöglicht es Ihnen, das standardmäßige Supplemental Data ID (SDID)-Ablaufintervall zu ändern, wenn Sie die ID mit der Hilfsfunktion „appendSupplementalDataIDTo “ an eine andere Seite übergeben. Standardmäßig verfügt der Besucher-ID-Dienst-Code auf der empfangenden Seite über 30 Sekunden, um die SDID aus der URL abzurufen, die von der verweisenden Seite gesendet wurde. Wenn der Besucher-ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, fordert er eine neue SDID an. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und Kontrolle über dieses Zeitüberschreitungsintervall haben möchten.

**SDID-Timeout überschreiben**

Wenn Sie die SDID-Standardzeitüberschreitung ändern müssen, fügen Sie `sdidParamExpiry` der `Visitor.getInstance` Funktion mit der folgenden Syntax hinzu:

**Syntax:** `sdidParamExpiry: *`Zeit in Sekunden`*`

**Codebeispiel**

Wenn Ihr Besucher-ID-Dienst-Code konfiguriert ist, könnte er in etwa wie im folgenden Beispiel aussehen. In diesem Beispiel wird die SDID-Zeitüberschreitung auf 15 Sekunden eingestellt. Diese Konfiguration funktioniert mit der Hilfsmethode [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

