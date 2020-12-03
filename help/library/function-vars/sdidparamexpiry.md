---
description: Mit dieser Konfiguration können Sie das standardmäßige SDID-Ablaufintervall überschreiben, wenn Sie diese ID mithilfe der Funktion appendSupplementalDataIDTo von einer Seite an eine andere weiterleiten. Standardmäßig hat der ID-Dienst-Code auf der empfangenden Seite 30 Sekunden, um die SDID von der URL abzurufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, wird eine neue SDID angefordert. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und die Kontrolle über dieses Zeitüberschreitungsintervall benötigen.
keywords: ID Service
seo-description: Mit dieser Konfiguration können Sie das standardmäßige SDID-Ablaufintervall überschreiben, wenn Sie diese ID mithilfe der Funktion appendSupplementalDataIDTo von einer Seite an eine andere weiterleiten. Standardmäßig hat der ID-Dienst-Code auf der empfangenden Seite 30 Sekunden, um die SDID von der URL abzurufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, wird eine neue SDID angefordert. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und die Kontrolle über dieses Zeitüberschreitungsintervall benötigen.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 11%

---


# sdidParamExpiry{#sdidparamexpiry}

Mit dieser Konfiguration können Sie das standardmäßige SDID-Ablaufintervall überschreiben, wenn Sie diese ID mithilfe der Funktion appendSupplementalDataIDTo von einer Seite an eine andere weiterleiten. Standardmäßig hat der ID-Dienst-Code auf der empfangenden Seite 30 Sekunden, um die SDID von der URL abzurufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, wird eine neue SDID angefordert. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und die Kontrolle über dieses Zeitüberschreitungsintervall benötigen.

**SDID-Timeout überschreiben**

Wenn Sie die SDID-Standardzeitüberschreitung ändern müssen, fügen Sie `sdidParamExpiry` der `Visitor.getInstance` Funktion mit der folgenden Syntax hinzu:

**Syntax:** ` sdidParamExpiry: *`Zeit in Sekunden`*`

**Codebeispiel**

Bei der Konfiguration könnte Ihr ID-Dienst-Code diesem Beispiel ähnlich aussehen. In diesem Beispiel wird die SDID-Zeitüberschreitung auf 15 Sekunden eingestellt. Diese Konfiguration funktioniert mit der Hilfsmethode [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

