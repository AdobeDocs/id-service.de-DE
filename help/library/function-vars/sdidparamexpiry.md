---
description: Diese Konfiguration ermöglicht es Ihnen, das standardmäßige Supplemental Data ID (SDID)-Ablaufintervall zu ändern, wenn Sie die ID mit der Hilfsfunktion „appendSupplementalDataIDTo “ an eine andere Seite übergeben. Standardmäßig hat der ID-Dienst-Code auf der empfangenden Seite 30 Sekunden, um die SDID von der URL abzurufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, wird eine neue SDID angefordert. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und Kontrolle über dieses Zeitüberschreitungsintervall haben möchten.
keywords: ID-Dienst
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '257'
ht-degree: 100%

---

# sdidParamExpiry{#sdidparamexpiry}

Diese Konfiguration ermöglicht es Ihnen, das standardmäßige Supplemental Data ID (SDID)-Ablaufintervall zu ändern, wenn Sie die ID mit der Hilfsfunktion „appendSupplementalDataIDTo “ an eine andere Seite übergeben. Standardmäßig hat der ID-Dienst-Code auf der empfangenden Seite 30 Sekunden, um die SDID von der URL abzurufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, wird eine neue SDID angefordert. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und Kontrolle über dieses Zeitüberschreitungsintervall haben möchten.

**SDID-Timeout überschreiben**

Wenn Sie die SDID-Standardzeitüberschreitung ändern müssen, fügen Sie `sdidParamExpiry` der `Visitor.getInstance` Funktion mit der folgenden Syntax hinzu:

**Syntax:** ` sdidParamExpiry: *`Zeit in Sekunden`*`

**Codebeispiel**

Bei der Konfiguration könnte Ihr ID-Dienst-Code diesem Beispiel ähnlich aussehen. In diesem Beispiel wird die SDID-Zeitüberschreitung auf 15 Sekunden eingestellt. Diese Konfiguration funktioniert mit der Hilfsmethode  [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```
