---
description: Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit deren Hilfe Browser steuern können, welche Art von Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und strenge CSPs festgelegt haben, die mithilfe von Whitelists Ressourcen von vertrauenswürdigen Domänen zulassen. Sie müssen die hier aufgeführten Adobe-Domänen Ihren CSP-Whitelists hinzufügen.
keywords: ID-Dienst
seo-description: Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit deren Hilfe Browser steuern können, welche Art von Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und strenge CSPs festgelegt haben, die mithilfe von Whitelists Ressourcen von vertrauenswürdigen Domänen zulassen. Sie müssen die hier aufgeführten Adobe-Domänen Ihren CSP-Whitelists hinzufügen.
seo-title: Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst
title: Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst {#content-security-policies-and-the-experience-cloud-id-service}

Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) ist eine HTTP-Header- und Sicherheitsfunktion, mit deren Hilfe Browser steuern können, welche Art von Ressourcen auf einer Webseite geladen werden. Lesen Sie diesen Abschnitt, wenn Sie den ID-Dienst verwenden und strenge CSPs festgelegt haben, die mithilfe von Whitelists Ressourcen von vertrauenswürdigen Domänen zulassen. Sie müssen die hier aufgeführten Adobe-Domänen Ihren CSP-Whitelists hinzufügen.

## CSP-Übersicht {#section-5fde5c00a678455c914b8307a8caab82}

CSPs verwenden den HTTP-Header `Content-Security-Policy`, um die Art der Ressourcen zu steuern, die ein Browser zulässt oder die auf einer Seite geladen werden. Durch Anwenden einer CSP können Sie Folgendes vermeiden:

* Laden von JavaScript-Dateien, deren Quelle unbekannt ist oder die nicht in einer Whitelist enthalten ist
* Cross-Site-Scripting-(XXS-) Angriffe
* Angriffe zur Dateneinspeisung
* Angriffe zur Website-Verunstaltung
* Malware-Verbreitung

CSPs werden häufig verwendet und sind hinlänglich bekannt. In dieser Dokumentation sollen CSPs nicht ausführlich erklärt werden (klicken Sie auf die unten stehenden Links, um weitere Informationen zu erhalten). Wichtig ist, dass Sie wissen, welche Adobe-Domänenamen Sie einer CSP hinzufügen sollten, wenn Sie eine solche verwenden und über strenge Sicherheitsrichtlinien verfügen. Durch Hinzufügen dieser Domänen können die Browser von Besuchern, die auf Ihre Site zugreifen, diese wichtigen Aufrufe an die von Ihnen verwendeten Experience Cloud-Ressourcen tätigen.

## Experience Cloud-Domänen für Whitelists {#section-30693e9a96834edfbf04de9e698cf2aa}

Fügen Sie diese Domänenamen oder URLs Ihrer CSP für alle aufgeführten Experience Cloud-Lösungen oder -Dienste hinzu, die Sie verwenden.

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
   <td colname="col1"> <p> <b>Besucher-ID-Dienst</b> </p> </td> 
   <td colname="col2"> <p>Nehmen Sie <span class="codeph">*.demdex.net</span> in Ihre CSP auf. </p> <p>Aufrufe der Domain <span class="codeph"> demdex.net</span> werden zur Generierung der <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies und des Experience Cloud Identity-Diensts</a> sowie zur ID-Synchronisation verwendet. Siehe auch <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Aufrufe an die Domäne „demdex.net“</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy)

