---
description: Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und über strenge CSPs verfügen, die Whitelists verwenden, um Ressourcen aus vertrauenswürdigen Domänen zu akzeptieren. Sie müssen die hier aufgeführten Adobe-Domänen zu Ihren CSP-Whitelists hinzufügen.
keywords: ID Service
seo-description: Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und über strenge CSPs verfügen, die Whitelists verwenden, um Ressourcen aus vertrauenswürdigen Domänen zu akzeptieren. Sie müssen die hier aufgeführten Adobe-Domänen zu Ihren CSP-Whitelists hinzufügen.
seo-title: Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst
title: Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 100%

---


# Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst {#content-security-policies-and-the-experience-cloud-id-service}

Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und über strenge CSPs verfügen, die Whitelists verwenden, um Ressourcen aus vertrauenswürdigen Domänen zu akzeptieren. Sie müssen die hier aufgeführten Adobe-Domänen zu Ihren CSP-Whitelists hinzufügen.

## CSP-Übersicht {#section-5fde5c00a678455c914b8307a8caab82}

CSPs verwenden den HTTP-Header `Content-Security-Policy`, um die Art der Ressourcen zu steuern, die ein Browser zulässt oder die auf einer Seite geladen werden. Durch die Anwendung eines CSP können Sie Folgendes verhindern:

* Das Laden von JavaScript-Dateien, wenn die Quelle unbekannt oder nicht in einer Whitelist enthalten ist.
* Cross-Site-Scripting-(XXS-) Angriffe.
* Angriffe durch Dateninjektion.
* Angriffe durch Site-Verunstaltung.
* Malware-Verteilung.

Die Verwendung von CSPs ist üblich und gut verstanden. Es ist nicht der Zweck dieser Dokumentation, CSPs im Detail zu erläutern (weitere Informationen finden Sie unter den entsprechenden Links weiter unten). Wichtig ist, dass Sie wissen, welche Adobe-Domänennamen Sie zu einem CSP hinzufügen sollten, wenn Sie diese verwenden und strenge Sicherheitsrichtlinien haben. Durch das Hinzufügen dieser Domänen können Besucher-Browser, die auf Ihre Website zugreifen, die von Ihnen verwendeten Experience Cloud-Ressourcen aufrufen.

## Experience Cloud-Domänen für Whitelists {#section-30693e9a96834edfbf04de9e698cf2aa}

Fügen Sie diese Domainnamen oder URLs für die von Ihnen verwendeten aufgelisteten Experience Cloud-Lösungen und -Dienste zu Ihrem CSP hinzu.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud-Lösung oder -Dienst </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>Nehmen Sie Folgendes in Ihre CSP auf: </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>Nehmen Sie <span class="codeph">*.tt.omtrdc.net</span> in Ihre CSP auf. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Experience Cloud ID-Dienst und Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>Nehmen Sie die folgenden Domänen in Ihre CSP auf.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Wenn Sie Tags mit Adobe Launch bereitstellen, müssen Sie der Liste der Domänen auch <code>https://assets.adobedtm.com</code> hinzufügen.</li></ul></p> <p>Aufrufe der Domain <span class="codeph">demdex.net</span> werden zur Generierung der <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies und des Experience Cloud Identity-Diensts</a> sowie zur ID-Synchronisation verwendet. Siehe auch <a href="https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Aufrufe an die Domäne „demdex.net“</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map-Plugin</b> </p> </td> 
 <td colname="col2"> <p>Nehmen Sie *.adobe.com in Ihre CSP auf. **Hinweis**: Wenn Activity Map bereits vor Januar 2020 installiert wurde, wird im Browser weiterhin zuerst eine Anfrage an *.omniture.com angezeigt, die jedoch an *.adobe.com weitergeleitet wird. </p></td> 
 </tr>
 <tr>
 <td colname="col1"> <p> <b>Advertising Analytics</b> </p> </td> 
 <td colname="col2"> <p>Wenn Sie über Steuerelemente für Abfragezeichenfolge-Parameter verfügen, nehmen Sie die Parameter „s_kwcid“ und „ef_id“ in die Whilist auf. Technisch gesehen verwendet Advertising Analytics nur „s_kwcid“, wenn Sie aber Ad Cloud Search oder DSP abrufen, wird auch „ef_id“ verwendet. Diese Abfragezeichenfolge-Parameter sind alphanumerisch. Der Parameter „s_kwcid“ verwendet das Zeichen „!“ und der Parameter „ef_id“ verwendet das Zeichen „:“. Wenn das Zeichen „!“ in der URL gesperrt ist, müssen Sie auch dieses in die Whitelist aufnehmen.</p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Content Security Policy](https://developer.mozilla.org/de/docs/Web/HTTP/CSP)
>* [Wikipedia: Content Security Policy](https://de.wikipedia.org/wiki/Content_Security_Policy)

