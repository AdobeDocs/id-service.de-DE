---
description: Bei dieser Hilfsmethode wird die Zusatzdaten-ID (Supplemental Data ID, SDID) als Abfragezeichenfolgenparameter an eine Umleitungs-URL angehängt. Dies ist nützlich, wenn Sie A4T verwenden, die SDID beim Wechsel auf eine andere Seite beibehalten werden soll und die einzelnen Besuche zusammengefasst werden sollen. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst mit derselben Organisations-ID in der Quell- und Zieldomäne implementiert haben.
keywords: ID-Dienst
seo-description: Bei dieser Hilfsmethode wird die Zusatzdaten-ID (Supplemental Data ID, SDID) als Abfragezeichenfolgenparameter an eine Umleitungs-URL angehängt. Dies ist nützlich, wenn Sie A4T verwenden, die SDID beim Wechsel auf eine andere Seite beibehalten werden soll und die einzelnen Besuche zusammengefasst werden sollen. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst mit derselben Organisations-ID in der Quell- und Zieldomäne implementiert haben.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Bei dieser Hilfsmethode wird die Zusatzdaten-ID (Supplemental Data ID, SDID) als Abfragezeichenfolgenparameter an eine Umleitungs-URL angehängt. Dies ist nützlich, wenn Sie A4T verwenden, die SDID beim Wechsel auf eine andere Seite beibehalten werden soll und die einzelnen Besuche zusammengefasst werden sollen. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst mit derselben Organisations-ID in der Quell- und Zieldomäne implementiert haben.

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
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## Beispielausgabe  {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Wie im Folgenden gezeigt, enthält die URL-Umleitung die SDID des Besuchers, Ihre Organisations-ID und einen UNIX-Zeitstempel im Aufruf an die empfangende Seite.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Ändern der SDID-Zeitüberschreitung mit sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

Die [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458)-Konfiguration ermöglicht es Ihnen, das standardmäßige SDID-Ablaufintervall zu ändern, wenn Sie die ID mit der Hilfsfunktion `appendSupplementalDataIDTo` an eine andere Seite übergeben. Standardmäßig muss der ID-Dienstcode auf der empfangenden Seite die SDID innerhalb von 30 Sekunden aus der URL abrufen, die von der verweisenden Seite gesendet wird. Wenn der ID-Dienstcode auf der empfangenden Seite die SDID nicht in weniger als 30 Sekunden abrufen kann, fordert er eine neue SDID an. Diese Funktion ist hauptsächlich für A4T-Kunden vorgesehen, die die SDID seitenübergreifend übergeben müssen und dieses Zeitüberschreitungsintervall steuern möchten.

Wenn Sie die SDID-Standardzeitüberschreitung ändern müssen, fügen Sie `sdidParamExpiry` der `Visitor.getInstance` Funktion mit der folgenden Syntax hinzu:

**Syntax:** ` sdidParamExpiry: *`Zeit in Sekunden`*`

**Codebeispiel**

Der konfigurierte ID-Dienstcode sollte in etwa wie im folgenden Beispiel aussehen. In diesem Beispiel wird die SDID-Zeitüberschreitung auf 15 Sekunden eingestellt.

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

