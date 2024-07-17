---
description: Bei dieser Helfermethode wird die Zusatzdaten-ID (Supplemental Data ID/SDID) als Abfragezeichenfolgenparameter an eine Umleitungs-URL angehängt. Dies ist nützlich, wenn Sie A4T verwenden und die SDID von einer Seite zur nächsten beibehalten und diese separaten Besuche miteinander verbinden müssen. Um diese Funktion verwenden zu können, müssen Sie den ID-Dienst mit derselben Organisations-ID für die Quell- und Zieldomänen implementiert haben.
keywords: ID-Dienst
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
source-git-commit: 5710539b45a81394061cd4af2ef3edc27b49092e
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# appendSupplementalDataIDTo {#appendsupplementaldataidto}

Bei dieser Helfermethode wird die Zusatzdaten-ID (Supplemental Data ID/SDID) als Abfragezeichenfolgenparameter an eine Umleitungs-URL angehängt. Dies ist nützlich, wenn Sie A4T verwenden und die SDID von einer Seite zur nächsten beibehalten und diese separaten Besuche miteinander verbinden müssen. Um diese Funktion verwenden zu können, müssen Sie den ID-Dienst mit derselben Organisations-ID für die Quell- und Zieldomänen implementiert haben.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntax und Codebeispiel </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Beispielausgabe </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntax und Codebeispiel </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Ändern der SDID-Zeitüberschreitung mit sdidParamExpiry </a> </li> 
</ul>

## Syntax und Codebeispiel {#section-cbb0b2f73bcc418386796c24c01b2365}

**Syntax:** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Codebeispiel**

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## Beispielausgabe {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Wie im Folgenden gezeigt, enthält die URL-Umleitung die SDID des Besuchers, Ihre Organisations-ID und einen UNIX-Zeitstempel im Aufruf an die empfangende Seite.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Ändern der SDID-Zeitüberschreitung mit sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

Die [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458)-Konfiguration ermöglicht es Ihnen, das standardmäßige SDID-Ablaufintervall zu ändern, wenn Sie die ID mit der Hilfsfunktion `appendSupplementalDataIDTo` an eine andere Seite übergeben. Standardmäßig hat der ID-Dienst-Code auf der empfangenden Seite 30 Sekunden, um die SDID von der URL abzurufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienst-Code auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, wird eine neue SDID angefordert. Diese Funktion ist vor allem für A4T-Kunden gedacht, die die SDID von einer Seite zur nächsten weiterleiten müssen und Kontrolle über dieses Zeitüberschreitungsintervall haben möchten.

Wenn Sie die SDID-Standardzeitüberschreitung ändern müssen, fügen Sie `sdidParamExpiry` der `Visitor.getInstance` Funktion mit der folgenden Syntax hinzu:

**Syntax:** ` sdidParamExpiry: *`Zeit in Sekunden`*`

**Codebeispiel**

Nach der Konfiguration könnte der ID-Dienst-Code ähnlich aussehen wie in diesem Beispiel. In diesem Beispiel wird die SDID-Zeitüberschreitung auf 15 Sekunden eingestellt.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```
