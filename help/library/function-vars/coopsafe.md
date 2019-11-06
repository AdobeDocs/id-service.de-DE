---
description: Eine optionale boolesche Konfiguration, die festlegt, ob der ID-Dienst Daten an die Adobe Experience Cloud-Gerätekooperation sendet oder nicht.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Konfiguration, die festlegt, ob der ID-Dienst Daten an die Adobe Experience Cloud-Gerätekooperation sendet oder nicht.
seo-title: isCoopSafe
title: isCoopSafe
uuid: 4dfa1f35-0a88-48d1-9484-d88cb53ad461
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# isCoopSafe{#iscoopsafe}

Eine optionale boolesche Konfiguration, die festlegt, ob der ID-Dienst Daten an die Adobe Experience Cloud-Gerätekooperation sendet oder nicht.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Anforderungen </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Nutzungsszenarios </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Syntax und Codebeispiel </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> POST-Parameter für Ereignisaufrufe </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> Post-Instanziierungs-APIs </a> </li> 
</ul>

## Voraussetzungen {#section-4883eda6beb8437182bcc82bb58fae41}

Voraussetzungen zur Verwendung von `isCoopSafe`:

* Verwendung von ID-Dienstcode der Version 2.4 oder höher
* Teilnahme an der [Experience Cloud-Gerätekooperation](https://marketing.adobe.com/resources/help/de_DE/mcdc/). Zukünftige Mitglieder der Gerätekooperation sollten diese Dokumentation ebenfalls lesen, um festzustellen, ob `isCoopSafe` mögliche Fragen über die Verwendung der Daten zur Erstellung eines Gerätediagramms beantwortet.

* Wenden Sie sich an Ihren [!DNL Adobe]-Berater, wenn Sie eine Whitelist- oder Blacklist-Kennzeichnung für Ihr Gerätekooperationskonto erstellen möchten. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

## Nutzungsszenarios {#section-d18af2b903f248e18ae8108aaf0a8ebb}

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
   <td colname="col2"> <p>Fügen Sie <span class="codeph">isCoopSafe</span> Ihrem ID-Dienstcode hinzu, um zu steuern, wie Daten authentifizierter Besucher, die die Nutzungsvereinbarungen akzeptiert haben oder auch nicht, von der Gerätekooperation zum Erstellen des Gerätediagramms verwendet werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL auf Drittanbieter-Sites</b> </p> </td> 
   <td colname="col2"> <p>Fügen Sie <span class="codeph">isCoopSafe</span> Ihrem ID-Dienstcode auf Drittanbieter-Sites hinzu, wenn Folgendes zutrifft: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">Sie können nicht sicherstellen, dass authentifizierte Besucher die Nutzungsvereinbarungen akzeptiert haben. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Sie müssen steuern, wie die Daten durch die Gerätekooperation verwendet werden, um das Gerätediagramm zu erstellen. </li> 
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

Legen Sie dies fest, wenn Ihr ID-Dienstcode Folgendes instanziiert:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## POST-Parameter für Ereignisaufrufe   {#section-fcd441933506493faefaa6b51f194a17}

Abhängig von der festgelegten Kennzeichnung (`true` oder `false`) überträgt der ID-Dienst `isCoopSafe` in diese POST-Parameter und sendet sie in einem Ereignisaufruf an [!DNL Adobe]:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

Anhand der POST-Parameter stellt die [!DNL Experience Cloud]-Gerätekooperation fest, ob Benutzerdaten in das Gerätediagramm aufgenommen werden dürfen oder nicht. Die folgende Tabelle definiert die Beziehung zwischen den booleschen Kennzeichnungen von `isCoopSafe` und den im Ereignisaufruf übergebenen POST-Parametern. Wenn Sie `isCoopSafe` nicht verwenden, wird keiner von ihnen in einem Ereignisaufruf übergeben.

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

## Post-Instanziierungs-APIs   {#section-9281c39c8b6249d7864100b5cbca7dc6}

Mit diesen APIs können Sie den Status von `isCoopSafe` überschreiben. Sie ermöglichen es, den Status nach der Instanziierung bzw. Anmeldung eines Besuchers auf einer Site oder bei einer Single-Page-Anwendung zu ändern, wenn die Seite nicht aktualisiert wird. Beispielsweise müssen Sie diese APIs aufrufen, wenn sich ein Benutzer auf Ihrer Site oder bei Ihrer Anwendung authentifiziert und später eine Nutzungsrichtlinie akzeptiert, die der Gerätekooperation die Verwendung seiner Daten ermöglicht.

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
>* [DIL isCoopSafe](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.translate.html)

