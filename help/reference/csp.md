---
description: Eine Content Security Policy (CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und strenge CSPs verwenden, die mithilfe von Whitelists Ressourcen von vertrauenswürdigen Domänen akzeptieren. Sie müssen die hier aufgelisteten Adobe-Domänen zu Ihren CSP-Whitelists hinzufügen.
keywords: ID Service
seo-description: Eine Content Security Policy (CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und strenge CSPs verwenden, die mithilfe von Whitelists Ressourcen von vertrauenswürdigen Domänen akzeptieren. Sie müssen die hier aufgelisteten Adobe-Domänen zu Ihren CSP-Whitelists hinzufügen.
seo-title: Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst
title: Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst {#content-security-policies-and-the-experience-cloud-id-service}

Eine Content Security Policy (CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und strenge CSPs verwenden, die mithilfe von Whitelists Ressourcen von vertrauenswürdigen Domänen akzeptieren. Sie müssen die hier aufgelisteten Adobe-Domänen zu Ihren CSP-Whitelists hinzufügen.

## CSP-Übersicht {#section-5fde5c00a678455c914b8307a8caab82}

CSPs verwenden den HTTP-Header `Content-Security-Policy`, um die Art der Ressourcen zu steuern, die ein Browser zulässt oder die auf einer Seite geladen werden. Durch die Anwendung eines CSP können Sie Folgendes verhindern:

* JavaScript-Dateien können nicht geladen werden, wenn die Quelle unbekannt ist oder nicht in einer Whitelist enthalten ist.
* Cross-Site-Scripting-(XXS-) Angriffe
* Angriffe auf die Dateninjizierung.
* Angriffe auf die Site-Verwerfung.
* Malware-Distribution.

Die Verwendung von CSPs ist häufig und gut verstanden. Diese Dokumentation dient nicht dazu, CSPs detailliert zu erklären (weitere Informationen finden Sie in den entsprechenden Informationslinks unten). Wichtig ist, dass Sie wissen, welche Adobe-Domänennamen Sie zu einem CSP hinzufügen sollten, wenn Sie diese verwenden und strenge Sicherheitsrichtlinien haben. Durch Hinzufügen dieser Domänen können Besucher, die auf Ihre Site zugreifen, diese wichtigen Aufrufe an Experience Cloud-Ressourcen tätigen, die Sie verwenden.

## Experience Cloud-Domänen für Whitelists {#section-30693e9a96834edfbf04de9e698cf2aa}

Hinzufügen Sie diese Domänennamen oder URLs für jede von Ihnen verwendete Liste Experience Cloud-Lösung oder jeden von Ihnen verwendeten Dienst in Ihr CSP ein.

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
   <td colname="col2"> <p>Ändern Sie Ihren CSP so, dass Folgendes enthalten ist: </p> <p> 
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
   <li>Wenn Sie Tags mit Adobe Launch bereitstellen, müssen Sie der Liste der Domänen auch <code>https://assets.adobedtm.com</code> hinzufügen.</li></ul></p> <p>Aufrufe der Domain <span class="codeph"> demdex.net</span> werden zur Generierung der <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies und des Experience Cloud Identity-Diensts</a> sowie zur ID-Synchronisation verwendet. Siehe auch <a href="https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Aufrufe an die Domäne „demdex.net“</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map-Plugin</b> </p> </td> 
 <td colname="col2"> <p>Nehmen Sie *.adobe.com in Ihre CSP auf. **Hinweis**: Wenn Activity Map bereits vor Januar 2020 installiert wurde, wird im Browser weiterhin zuerst eine Anfrage an *.omniture.com angezeigt, die jedoch an *.adobe.com weitergeleitet wird. </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Content Security Policy](https://developer.mozilla.org/de/docs/Web/HTTP/CSP)
>* [Wikipedia: Content Security Policy](https://de.wikipedia.org/wiki/Content_Security_Policy)

