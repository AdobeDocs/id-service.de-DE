---
description: Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.
keywords: ID-Dienst
seo-description: Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.
seo-title: ID-Synchronisation nach URL oder Datenquelle
title: ID-Synchronisation nach URL oder Datenquelle
uuid: ff 83 d 910-8375-4295-9 f 2 a-e 14 c 15 eee 09 a
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# ID-Synchronisation nach URL oder Datenquelle{#id-synchronization-by-url-or-data-source}

Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> Syntax, Eigenschaften und Makros </a> </li> 
 <li> <a href="../../library/get-set/idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> Beispielcode und -ausgabe </a> </li> 
</ul>

## Syntax, Eigenschaften und Makros {#section-90ac61617482463aaf4c57009b830332}

**Syntax**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Code </th> 
   <th colname="col2" class="entry"> Synchronisiert Benutzer-IDs </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Zwischen unterschiedlichen Datenpartnern und <span class="keyword">Audience Manager</span> mithilfe einer benutzerdefinierten URL für die ID-Synchronisierung. </p> <p> 
     <draft-comment>
       Zwischen verschiedenen Datenpartnern und Audience Manager. Beispiel: Partner X verwendet dies zur Synchronisierung einer Benutzer-ID mit Partner Y und sendet diese dann an Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Wenn Sie die DPID und DPUUID bereits kennen und sie im URL-Format für die ID-Standardsynchronisierung an <span class="keyword">Audience Manager</span> senden möchten. </p> <p> 
     <draft-comment>
       Wenn Sie die Benutzer-ID bereits kennen und sie an Audience Manager senden möchten. 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**Eigenschaften**

In der folgenden Tabelle sind die für beide Funktionen verfügbaren Eigenschaften aufgeführt und definiert.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Name </th> 
   <th colname="col2" class="entry"> Typ </th> 
   <th colname="col3" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> Zeichenfolge </td> 
   <td colname="col3"> <p>Durch Audience Manager zugewiesene Datenanbieter-ID. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> Zeichenfolge </td> 
   <td colname="col3"> <p>Die eindeutige Datenanbieter-ID für den Benutzer. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Nummer </td> 
   <td colname="col3"> <p> <i>(Optional)</i> Legt die Cookie-Ablaufzeit fest. Hierbei muss es sich um eine Ganzzahl handeln. Der Standardwert lautet 20.160 Minuten (14 Tage). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> Zeichenfolge </td> 
   <td colname="col3"> <p>Ziel-URL. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Makros**

Beide Funktionen akzeptieren die folgenden Makros:

* ** `%TIMESTAMP%`: ** Generiert einen Zeitstempel (in Millisekunden). Wird für das Cache-Busting verwendet.
* ** `%DID%`: **Fügt die Audience Manager-ID für den Benutzer ein.
* ** `%HTTP_PROTO%`: ** Legt das Kommunikationsprotokoll ( `http` oder `https`) fest.

## Beispielcode und -ausgabe {#section-0115615c37584a19a2ab11e917c4e7e9}

Beide Funktionen kehren bei `Successfully queued` Erfolg zurück. Falls nicht, wird eine Fehlermeldungszeichenfolge zurückgegeben.

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Beispielcode </th> 
   <th colname="col2" class="entry"> Beispielausgabe </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instatiate Besucher 
 var visitor = Visitor. getinstance ("MARKETING-CLOUD-ORG-ID-HERE", {});

    // &amp; amp; nbsp; Ausgelöst &amp; amp; nbsp; url &amp; amp; nbsp; with &amp; amp; nbsp; macros &amp; amp; nbsp; replacedvisitor
    . idsyncbyurl ({
    &amp; amp; nbsp; dpid: &amp; amp; nbsp; &#39; 24 &#39;, &amp; amp; nbsp; // &amp; amp; nbsp; must &amp; amp; nbsp; be &amp; amp; nbsp; a &amp; amp; nbsp; string
    &amp; amp; nbsp; url: &amp; amp; nbsp; &#39;//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D&#39;,&amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp
    ;
    }); &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Beispielcode </th> 
   <th colname="col2" class="entry"> Beispielausgabe </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instantiate Besucher 
 var visitor = Visitor. getinstance ("MARKETING-CLOUD-ORG-ID-HERE", {});

    // &amp; amp; nbsp; Ausgelöst &amp; amp; nbsp; &#39; http:/https:&#39;&amp;nbsp;+&amp;nbsp;&#39;//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;&#39;visitor.idSyncByDataSource(
    {
    &amp; amp; nbsp; dpid: &amp; amp; nbsp; &#39; 24 &#39;, &amp; amp; nbsp; // &amp; amp; nbsp; must &amp; amp; nbsp; be &amp; amp; nbsp; a &amp; amp; nbsp; string
    &amp; amp; nbsp; dpuuid: &amp; amp; nbsp; &#39; 98765 &#39;, &amp; amp; nbsp; // &amp; amp; nbsp; must &amp; amp; nbsp; be &amp; amp; nbsp; a &amp; amp; nbsp; string
    &amp; amp; nbsp; Minutestolive: &amp; amp; nbsp; 20160 &amp; amp; nbsp; // &amp; amp; nbsp; optional, &amp; amp; nbsp; default &amp; amp; nbsp; to &amp; amp; nbsp; 20160 &amp; amp; nbsp; minutes &amp; amp; nbsp; (14 &amp; amp; nbsp; days) &amp; amp; nbsp;
    }); &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ LIKE_ THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

