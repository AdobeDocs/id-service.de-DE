---
description: Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Web-Seite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den Besucher-ID-Service verwenden und über strikte CSPs verfügen, die Zulassungslisten verwenden, um Ressourcen von vertrauenswürdigen Domains zu akzeptieren. Sie müssen die hier aufgeführten Adobe-Domains zu Ihren CSP-Zulassungslisten hinzufügen.
keywords: Besucher-ID-Service
title: Inhaltssicherheitsrichtlinien und der Besucher-ID-Service von Adobe
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
TQID: https://experienceleague.adobe.com/UX0RWE7v912XEHJCJE49yt1sy13t1P0I0I79gG9Z7m8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 527
ht-degree: 70%

---

# Inhaltssicherheitsrichtlinien und der Besucher-ID-Service von Adobe {#content-security-policies-and-the-experience-cloud-id-service}

Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit der Browser steuern können, welche Ressourcen auf einer Web-Seite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den Besucher-ID-Service verwenden und über strikte CSPs verfügen, die Zulassungslisten verwenden, um Ressourcen von vertrauenswürdigen Domains zu akzeptieren. Sie müssen die hier aufgeführten Adobe-Domains zu Ihren CSP-Zulassungslisten hinzufügen.

## Zusammenfassung zu CSPs {#section-5fde5c00a678455c914b8307a8caab82}

CSPs verwenden den HTTP-Header `Content-Security-Policy`, um die Art der Ressourcen zu steuern, die ein Browser zulässt oder die auf einer Seite geladen werden. Durch die Anwendung eines CSP können Sie Folgendes verhindern:

* Das Laden von JavaScript-Dateien, wenn die Quelle unbekannt oder nicht in einer Zulassungsliste enthalten ist.
* Cross-Site-Scripting-(XXS-) Angriffe.
* Angriffe durch Dateninjektion.
* Angriffe durch Site-Verunstaltung.
* Malware-Verteilung.

Die Verwendung von CSPs ist üblich und gut verstanden. Es ist nicht der Zweck dieser Dokumentation, CSPs im Detail zu erläutern (weitere Informationen finden Sie unter den entsprechenden Links weiter unten). Wichtig ist, dass Sie wissen, welche Adobe-Domänennamen Sie zu einem CSP hinzufügen sollten, wenn Sie diese verwenden und strenge Sicherheitsrichtlinien haben. Durch Hinzufügen dieser Domains können Besucher-Browser, die auf Ihre Website zugreifen, diese wichtigen Aufrufe an die von Ihnen verwendeten CX Enterprise-Ressourcen ausführen.

## CX Unternehmens-Domains für die Zulassungsauflistung {#section-30693e9a96834edfbf04de9e698cf2aa}

Fügen Sie diese Domain-Namen oder URLs für jede Liste der von Ihnen verwendeten CX Enterprise-Lösungen oder -Services Ihrem CSP hinzu.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">CX Enterprise-Lösung oder -Service</th>
   <th colname="col2" class="entry">Beschreibung</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>Nehmen Sie Folgendes in Ihre CSP auf:</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Target</b></p>
   </td>
   <td colname="col2">
    <p>Nehmen Sie <span class="codeph">*.tt.omtrdc.net</span> in Ihre CSP auf.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Visitor ID Service und Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>Nehmen Sie die folgenden Domänen in Ihre CSP auf.</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>Wenn Sie Tags verwenden, müssen Sie auch <code>https://assets.adobedtm.com</code> zur Liste der Domains hinzufügen.</li>
    </ul>
    <p>Aufrufe der Domain <span class="codeph">demdex.net</span> werden zur Generierung der <a href="../introduction/cookies.md" format="dita" scope="local">Cookies und des Besucher-ID-</a> sowie zur ID-Synchronisierung verwendet. Siehe auch <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de" format="https" scope="external">Verstehen von Aufrufen an die Demdex-Domain</a>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Activity Map-Plug-in</b></p>
   </td>
   <td colname="col2">
    <p>Nehmen Sie *.adobe.com in Ihre CSP auf. **Hinweis**: Wenn Activity Map bereits vor Januar 2020 installiert wurde, wird im Browser weiterhin zuerst eine Anfrage an *.omniture.com angezeigt, die jedoch an *.adobe.com weitergeleitet wird.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>Wenn Sie Abfragezeichenfolgenparameter einschränken, setzen Sie die folgenden Parameter auf die Zulassungsliste:</p>
    <ul>
     <li><code>s_kwcid</code> (wobei <code>!</code>verwendet wird)</li>
     <li><code>ef_id</code> (wobei <code>:</code>verwendet wird)</li>
    </ul>
    <p>Wenn Sie das Zeichen „<code>!</code>“ in URLs blockieren, setzen Sie es ebenfalls auf die Zulassungsliste.</p>
    <p>Advertising Analytics verwendet ausschließlich <code>s_kwcid</code>, aber Advertising Search, Social und Commerce sowie Advertising DSP verwenden auch <code>ef_id</code>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>Nehmen Sie die folgenden Domains in Ihre CSP auf:</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: Content Security Policy](https://de.wikipedia.org/wiki/Content_Security_Policy)

