---
description: Mit dieser Konfiguration können Sie das standardmäßige Ablaufintervall der Zusatzdaten-ID (Supplemental Data ID, SDID) überschreiben, wenn Sie die ID mit der Hilfsfunktion appendSupplementalDataIDTo an eine andere Seite übergeben. Standardmäßig muss der ID-Dienstcode auf der empfangenden Seite die SDID innerhalb von 30 Sekunden aus der URL abrufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienstcode auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, fordert er eine neue SDID an. Diese Funktion ist hauptsächlich für A4T-Kunden vorgesehen, die die SDID seitenübergreifend übergeben müssen und dieses Zeitüberschreitungsintervall steuern möchten.
keywords: ID-Dienst
seo-description: Mit dieser Konfiguration können Sie das standardmäßige Ablaufintervall der Zusatzdaten-ID (Supplemental Data ID, SDID) überschreiben, wenn Sie die ID mit der Hilfsfunktion appendSupplementalDataIDTo an eine andere Seite übergeben. Standardmäßig muss der ID-Dienstcode auf der empfangenden Seite die SDID innerhalb von 30 Sekunden aus der URL abrufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienstcode auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, fordert er eine neue SDID an. Diese Funktion ist hauptsächlich für A4T-Kunden vorgesehen, die die SDID seitenübergreifend übergeben müssen und dieses Zeitüberschreitungsintervall steuern möchten.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf 7 e 2 d-b 196-4 c 70-936 d -8 a 98191 cbb 85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# sdidParamExpiry{#sdidparamexpiry}

Mit dieser Konfiguration können Sie das standardmäßige Ablaufintervall der Zusatzdaten-ID (Supplemental Data ID, SDID) überschreiben, wenn Sie die ID mit der Hilfsfunktion appendSupplementalDataIDTo an eine andere Seite übergeben. Standardmäßig muss der ID-Dienstcode auf der empfangenden Seite die SDID innerhalb von 30 Sekunden aus der URL abrufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienstcode auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, fordert er eine neue SDID an. Diese Funktion ist hauptsächlich für A4T-Kunden vorgesehen, die die SDID seitenübergreifend übergeben müssen und dieses Zeitüberschreitungsintervall steuern möchten.

**Überschreiben der SDID-Zeitüberschreitung**

Wenn Sie die SDID-Standardzeitüberschreitung ändern müssen, fügen Sie `sdidParamExpiry` der Funktion `Visitor.getInstance` mit der folgenden Syntax hinzu:

**Syntax:**` sdidParamExpiry: *`Zeit in Sekunden`*`

**Codebeispiel**

Der konfigurierte ID-Dienstcode sollte in etwa wie in diesem Beispiel aussehen. In diesem Beispiel wird die SDID-Zeitüberschreitung auf 15 Sekunden eingestellt. Diese Konfiguration funktioniert mit der Hilfsmethode [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

