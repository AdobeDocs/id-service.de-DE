---
description: Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.
keywords: ID-Dienst
seo-description: Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.
seo-title: ID-Synchronisation nach URL oder Datenquelle
title: ID-Synchronisation nach URL oder Datenquelle
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# ID-Synchronisation nach URL oder Datenquelle{#id-synchronization-by-url-or-data-source}

Mit den ID-Dienstfunktionen „idSyncByURL“ und „idSyncByDataSource“ können Sie eine ID-Synchronisierung in Destination Publishing iFrame manuell implementieren. Sie stehen in VisitorAPI.js 1.10 oder höher zur Verfügung.

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
   <td colname="col2"> <p>Zwischen unterschiedlichen Datenpartnern und <span class="keyword">Audience Manager</span> mithilfe einer benutzerdefinierten URL für die ID-Synchronisierung. </p> </td> 
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
* `%HTTP_PROTO%`: Legt das Kommunikationsprotokoll fest (`http` oder `https`).

## Beispielcode und -ausgabe {#section-0115615c37584a19a2ab11e917c4e7e9}

Beide Funktionen melden `Successfully queued` bei Erfolg. Falls nicht, wird eine Fehlermeldungszeichenfolge zurückgegeben.

### visitor.idSyncByURL

**Beispielcode**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Beispielausgabe**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**Beispielcode**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dpuuid: '98765', // must be a string 
     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Beispielausgabe**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)

