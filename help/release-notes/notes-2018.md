---
description: Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts im Jahr 2018.
keywords: ID-Dienst
seo-description: Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts im Jahr 2018.
seo-title: Versionshinweise für 2018
title: Versionshinweise für 2018
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Versionshinweise für 2018 {#release-notes}

Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts im Jahr 2018.

## Version 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elementbeschreibung </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Verbesserte Sicherheit für AMCV-Cookies </p> </td> 
   <td colname="col2"> <p>Im Rahmen einer internen Sicherheitsprüfung wurde festgestellt, dass bei der Verwendung der DTM-Bibliothek in den für die Sitzungsverwaltung verwendeten Cookies nicht die richtigen Attribute angegeben werden. Das konnte dazu führen, dass Cookie-Informationen versehentlich freigegeben wurden. Um dieses Problem zu beheben, wurde eine Konfiguration hinzugefügt, mit der Kunden dem AMCV-Cookie das Attribut „Secure“ hinzufügen können. Siehe <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elementbeschreibung </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Verbesserte Sicherheit für AMCV-Cookies </p> </td> 
   <td colname="col2"> <p>Im Rahmen einer internen Sicherheitsprüfung wurde festgestellt, dass bei der Verwendung der DTM-Bibliothek in den für die Sitzungsverwaltung verwendeten Cookies nicht die richtigen Attribute angegeben werden. Das konnte dazu führen, dass Cookie-Informationen versehentlich freigegeben wurden. Um dieses Problem zu beheben, wurde eine Konfiguration hinzugefügt, mit der Kunden dem AMCV-Cookie das Attribut „Secure“ hinzufügen können. Siehe secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Integrationscode und ID müssen Zahlen oder nicht leere Zeichenfolgen sein. </p> </td> 
   <td colname="col2"> <p>Fehlerkorrektur – Jetzt tritt kein Fehler mehr bei der Validierung von „setCustomerIDs“ auf, wenn die Daten einen Integrationscode oder eine Integrations-ID enthalten, bei denen es sich weder um eine Zahl noch um eine nicht leere Zeichenfolge handelt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS ist im öffentlichen Git-Repository verfügbar </td> 
   <td colname="col2"> ECID JS ist jetzt für alle Experience Cloud-Kunden im öffentlichen Git-Repository unter https://github.com/Adobe-Marketing-Cloud/id-service/releases verfügbar. </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elementbeschreibung </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Unrealistischer Anstieg der Unique Visitor-Anzahl </p> </td> 
   <td colname="col2"> <p>Bei Version 3.1.0 des Experience Cloud Identity-Diensts haben wir ein Problem erkannt, das bei Implementierung der Version zu einem unrealistischen Anstieg der Unique Visitor-Anzahl führte. Dieses Verhalten tritt nur bei der letzten Version (3.1.0) des ECID auf und wenn Benutzer die Option „Nur von aktueller Website erlauben“ in den Datenschutzeinstellungen des Safari-Browsers ausgewählt haben. Dieses Problem wurde in Version 3.1.2 behoben. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>Es wird empfohlen, von Version 3.1.0 umgehend auf die neueste Version zu aktualisieren. Siehe Beschreibung für Version 3.1.2. Das neueste Bundle ist über Adobe Experience Platform Launch, DTM und AppMeasurement verfügbar.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elementbeschreibung </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie in falscher Domäne erstellt </p> </td> 
   <td colname="col2"> <p>Es wurde ein Fehler behoben, durch den ein temporäres Visitor-Cookie in der Cookie-Domäne „default“ gesetzt wurde, statt in der durch die Konfiguration festgelegten Domäne (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elementbeschreibung </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Thread-Yielding für mehrere ID-Synchronisierungsanfragen </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>Bei Kunden, die mehrere ID-Synchronisierungen durchführen, wird die Benutzeroberfläche aufgrund der fortlaufend durchgeführten CPU-Berechnungen in manchen Fällen blockiert. Wir führen jetzt das Thread-Yielding ein, um die ID-Synchronisierungsanfragen um je 100 Millisekunden zu trennen. </p> <p>Diese Änderung verbessert die Leistung bei Kunden, die Visitor 2.3.0 oder höher und DIL 6.10 oder höher verwenden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Neue Möglichkeit zur Aktivierung von Drittanbieteraufrufen </td> 
   <td colname="col2"> <p><b>JavaScript – 3.0.0</b> </p> <p>Adobe hat folgende Konfigurationen umbenannt, um das Deaktivieren von Synchronisierungsaufrufen von Drittanbietern zu ermöglichen. </p> <p>idSyncDisableSyncs zu disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing zu disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Unterstützung für Internet Explorer </p> </td> 
   <td colname="col2"> <p>Internet Explorer 6, 7, 8 und 9 werden vom ID-Dienst nicht mehr unterstützt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Aktualisierung der getInstance-Dokumentation </p> </td> 
   <td colname="col2"> <p>Der Funktion Visitor wurde eine neue Funktion zur Nicht-Instanziierung dieser Funktion mit var visitor = new Visitor hinzugefügt. </p> </td> 
  </tr> 
 </tbody> 
</table>

