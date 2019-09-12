---
description: Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.
keywords: ID-Dienst
seo-description: Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.
seo-title: ID-Synchronisation nach URL oder Datenquelle
title: ID-Synchronisation nach URL oder Datenquelle
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: tm+mt
source-git-commit: 5345d0d58367bcfa30a98d76cadc28ffb0caa225

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
       Zwischen verschiedenen Datenpartnern und Audience Manager. Beispielsweise würde Partner x damit eine Benutzer-ID mit Partner y synchronisieren und diese dann an Audience Manager senden. 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Wenn Sie die DPID und DPUUID bereits kennen und sie im URL-Format für die ID-Standardsynchronisierung an <span class="keyword">Audience Manager</span> senden möchten. </p> <p> 
     <draft-comment>
       Wenn Sie die Benutzer-ID bereits kennen und an Audience Manager senden möchten. 
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
   <td colname="col2"> Zahl </td> 
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

* `%TIMESTAMP%`: Generiert einen Zeitstempel (in Millisekunden). Wird für das Cache-Busting verwendet.
* `%DID%`: Fügt die Audience Manager-ID für den Benutzer ein.
* `%HTTP_PROTO%`: Setzt das Kommunikationsprotokoll ( `http` oder `https`).

## Beispielcode und -ausgabe {#section-0115615c37584a19a2ab11e917c4e7e9}

Beide Funktionen melden `Successfully queued` bei Erfolg. Falls nicht, wird eine Fehlermeldungszeichenfolge zurückgegeben.

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
   <td colname="col1"> <p> <code class="syntax javascript"> //Instatiate Visitor 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    // Fires url with macros replacedvisitor
    . idsyncbyurl ({
    dpid: ' 24 ', // muss eine Zeichenfolge
    sein: '//su.addthis.com/red/usync?pid=16&amp;puid=%DID%&amp;url=%HTTP_PROTO%://dpm.demdex.net/ibs:dpid=420&amp;dpuuid= {{uid}}',
    minutestolive: 20160 // optional, Standard auf 20160 Minuten (14 Tage)
    });
    
    &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
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
   <td colname="col1"> <p> <code class="syntax javascript"> //Instantiate Visitor 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    // Fires ' http:/https:' +'//dpm.demdex.net/ibs:dpid= &lt; dpid &gt; &amp; dpuuid = &lt; dpuuid &gt;'
    visitor. idsyncbydatasource ({
    dpid: ' 24 ', // muss eine Zeichenfolge
    sein: ' 98765 ', // muss ein stringminutestolive
    sein: 20160 // optional, Standard auf 20160 Minuten (14 Tage)
    });
    &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

