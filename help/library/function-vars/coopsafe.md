---
description: Eine optionale boolesche Konfiguration, die bestimmt, ob der Besucher-ID-Service Daten an die Adobe Device Co-op sendet (oder nicht sendet).
keywords: Besucher-ID-Service
title: isCoopSafe
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 69%

---

# isCoopSafe{#iscoopsafe}

Eine optionale boolesche Konfiguration, die bestimmt, ob der Besucher-ID-Service Daten an die Adobe Device Co-op sendet (oder nicht sendet).

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Anforderungen </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Nutzungsszenarios </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Syntax und Codebeispiel </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> POST-Parameter für Ereignisaufrufe </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> Post-Instanziierungs-APIs </a> </li> 
</ul>

## Anforderungen {#section-4883eda6beb8437182bcc82bb58fae41}

Voraussetzungen zur Verwendung von `isCoopSafe`:

* Verwenden Sie den Visitor ID Service-Code der Version 2.4 oder höher.
* Beteiligen Sie sich an der [Adobe Device Co-op](https://experienceleague.adobe.com/docs/device-co-op/using/about/overview.html?lang=de). Zukünftige Mitglieder der Gerätekooperation sollten diese Dokumentation ebenfalls lesen, um festzustellen, ob `isCoopSafe` mögliche Fragen über die Verwendung der Daten zur Erstellung eines Gerätediagramms beantwortet.

* Arbeiten Sie mit Ihrem Adobe-Berater zusammen, um für Ihr Device Co-op-Konto eine Whitelist- oder eine Blacklist-Markierung festzulegen. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

## Anwendungsfälle {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` ist in zwei Nutzungsszenarios hilfreich, in denen es um die Erfassung der Daten von aktuellen oder zukünftigen Mitgliedern der Gerätekooperation geht. Diese Nutzungsszenarios beziehen sich darauf, wie Site-Besucherdaten an die Gerätekooperation übergeben werden, um das Gerätediagramm zu erstellen. In der folgenden Tabelle wird beschrieben, wie `isCoopSafe` in diesen Nutzungsszenarios verwendet wird, um Daten an das Gerätediagramm zu senden oder die Datenübergabe zu blockieren.

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Anwendungsfall </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Authentifizierte Besucher</b> </p> </td> 
   <td colname="col2"> <p>Fügen Sie <span class="codeph"> isCoopSafe-</span> zu Ihrem Besucher-ID-Service-Code hinzu, um zu steuern, wie Daten für authentifizierte Besucher, die Nutzungsbedingungen akzeptiert haben oder nicht akzeptiert haben, von der Gerätekooperation zum Erstellen des Gerätediagramms verwendet werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL auf Drittanbieter-Sites</b> </p> </td> 
   <td colname="col2"> <p>Fügen Sie <span class="codeph"> isCoopSafe-</span> zu Ihrem Besucher-ID-Service-Code hinzu, um sie auf Websites von Drittanbietern zu verwenden, auf denen Sie: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">Es kann nicht sichergestellt werden, dass authentifizierte Besucher Nutzungsvereinbarungen akzeptiert oder nicht akzeptiert haben. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Es muss gesteuert werden, wie diese Daten von der Gerätekooperation zum Erstellen des Gerätediagramms verwendet werden. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Syntax und Codebeispiel {#section-952f56724a2b4d349340e26fbaf33ddd}

**Syntax:** `isCoopSafe: true | false`

Die booleschen Optionen bestimmen, ob Kundendaten von der Gerätekooperation verwendet werden können.

* `isCoopSafe: true`: Von einem Mobile-SDK oder einer Website erfasste Besucherdaten *können* zur Erstellung des Gerätediagramms verwendet werden.

* `isCoopSafe: false`: Von einem Mobile-SDK oder einer Website erfasste Besucherdaten *können nicht* zur Erstellung des Gerätediagramms verwendet werden.

**Codebeispiel**

Legen Sie dies fest, wenn Ihr Besucher-ID-Service-Code instanziiert:

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
     ... 
     isCoopSafe: true 
});
```

## POST-Parameter für Ereignisaufrufe {#section-fcd441933506493faefaa6b51f194a17}

Je nach festgelegtem Flag (`true` oder `false`) übersetzt der Besucher-ID-Dienst `isCoopSafe` in diese POST-Parameter und sendet sie in einem Ereignisaufruf an Adobe:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

Die POST-Parameter teilen der Adobe-Gerätekooperation mit, ob Benutzerdaten in das Gerätediagramm aufgenommen werden können oder nicht. Die folgende Tabelle definiert die Beziehung zwischen den booleschen Kennzeichnungen von `isCoopSafe` und den im Ereignisaufruf übergebenen POST-Parametern. Wenn Sie `isCoopSafe` nicht verwenden, wird keiner von ihnen in einem Ereignisaufruf übergeben.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Konfigurationsstatus </th> 
   <th colname="col2" class="entry"> POST-Parameter </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>Die Gerätekooperation kann Besucherdaten verwenden, um das Gerätediagramm zu erstellen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>Die Gerätekooperation kann keine Besucherdaten verwenden, um das Gerätediagramm zu erstellen. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Post-Instanziierungs-APIs {#section-9281c39c8b6249d7864100b5cbca7dc6}

Mit diesen APIs können Sie den Status von `isCoopSafe` überschreiben. Diese sind erforderlich, damit Sie den Status eines Besuchers nach der Instanziierung/nach der Anmeldung auf einer Website oder in einer Einzelseitenanwendung ändern können, wenn die Seite nicht aktualisiert wird. Beispielsweise müssen Sie diese APIs aufrufen, wenn sich ein Benutzer bei Ihrer Site oder App authentifiziert und später eine Nutzungsrichtlinie akzeptiert, die es der Gerätekooperation ermöglicht, ihre Daten zu verwenden.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>Legt den POST-Parameter <span class="codeph">d_coop_safe=1</span> in allen nachfolgenden Ereignisaufrufen fest. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Legt den POST-Parameter <span class="codeph">d_coop_unsafe=1</span> in allen nachfolgenden Ereignisaufrufen fest. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html?lang=de)
