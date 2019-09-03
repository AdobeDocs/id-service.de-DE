---
description: Mit dem Opt-in-Dienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie ein Cookie auf dem Gerät oder Browser des Benutzers erstellen können, wenn dieser Ihre Site besucht.
seo-description: Mit dem Opt-in-Dienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie ein Cookie auf dem Gerät oder Browser des Benutzers erstellen können, wenn dieser Ihre Site besucht.
seo-title: Opt-in-Dienst
title: Opt-in-Dienst
uuid: aebd72ad-4118-471b-9755-d08a72caa0fd
translation-type: ht
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c

---


# Opt-in-Dienst{#opt-in-service}

Mit dem Opt-in-Dienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie ein Cookie auf dem Gerät oder Browser des Benutzers erstellen können, wenn dieser Ihre Site besucht.

Der Opt-in-Dienst ist eine Erweiterung des Dienstes Experience Cloud ID (ECID) und ermöglicht Ihnen zu steuern, ob und welche Experience Cloud-Lösungen Cookies auf Webseiten für Besucher erstellen können, bevor die Besucher zugestimmt haben. Mit dem Opt-in-Dienst können Sie auch Protokolle festlegen, die sich im Rahmen Ihres größeren Designs in Ihre Consent Management Platform (CMP) und bestehende Systeme integrieren lassen.

Mit dem Opt-in-Dienst können Sie festlegen, ob ein Besucher allen Adobe-Lösungen gleichzeitig zustimmen kann oder die Lösungen einzeln angezeigt werden, um die Zustimmung einzuholen. Sobald der Genehmigungsprozess abgeschlossen und vom Kunden aufgezeichnet wurde, können Sie die CMP-Besuchergenehmigungen aus allen Adobe-Lösungen abrufen.

Der Opt-in-Dienst ist über [Adobe Experience Platform Launch](https://docs.adobelaunch.com/) mit der [Opt-in-Erweiterung](../../implementation-guides/opt-in-service/launch.md) einfach zu implementieren und zu konfigurieren. Ebenfalls möglich ist eine Implementierung und Konfiguration mit [DTM](../../implementation-guides/opt-in-service/optin-dtm.md).

Siehe [Einrichtung des Opt-in-Dienstes](../../implementation-guides/opt-in-service/getting-started.md) zu den ersten Schritten.

>[!NOTE]
>
>Der Opt-in-Dienst kann nur zur Einrichtung eines Systems verwendet werden, mit dem die Zustimmung der Benutzer zum Herunterladen von Adobe-Cookies eingeholt wird. Es können keine Zustimmungsvoreinstellungen von Benutzern erfasst werden und das Objekt kann auch nicht als Repository für Voreinstellungen verwendet werden.

>[!IMPORTANT]
>
>Der Inhalt dieses Dokuments ist keine Rechtsberatung und soll keine Rechtsberatung ersetzen. Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um sich über die Zustimmung und die Vorgehensweisen bei der Einrichtung Ihrer Opt-in-Implementierung zu informieren.

## Opt-in für mehrere Experience Cloud-Lösungen {#section-053e6224505542cf961896f0ca869e52}

Der Opt-in-Dienst ist ein Tool zum Einrichten eines Opt-in-Workflows, der Ihren Anforderungen entspricht. Es ermöglicht Ihnen, einen Workflow zu entwerfen, der vor und nach der Zustimmung des Benutzers oder Ihres Zustimmungsverantwortlichen durch Auslösen von Tags reagiert.

Mit dem Opt-in-Dienst können Sie Folgendes für die Zustimmungsverwaltung von Adobe-Lösungen einstellen:

* Sie können angeben, ob die Anforderungen für die Zustimmungserfassung im Allgemeinen auf einen Benutzer zutreffen.
* Sie können festlegen, welche Lösungen Cookies generieren dürfen.
* Sie können Standardeinstellungen für alle Lösungen anwenden, deren Kategorien nicht ausdrücklich vom Benutzer genehmigt oder abgelehnt werden.
* Sie können eine benutzerdefinierte Reaktion auf Änderungen an den Zustimmungseinstellungen eines Benutzers auslösen, um die Einstellungen des Benutzers beizubehalten oder zu aktualisieren.

Mit dem Opt-in-Dienst können Sie Ihre Site so konfigurieren, dass einige Cookies mit einer Vorabzustimmung geladen werden, bevor der Benutzer eine Auswahl vornimmt. Sie können Opt-in-Dienste für Neukunden so einstellen, dass Cookies nach Zustimmung des Benutzers oder nach Bereitstellung einer Auswahl geladen werden können. Außerdem können Sie die Zustimmung in Ihrer bestehenden Consent Management-Plattform speichern und abrufen oder Opt-in-Berechtigungen einfach in einem Cookie speichern.

![](assets/Opt-in-approval.png)

Adobe-Lösungen können dann überprüfen, ob das Tag genehmigt wurde, Änderungen abonnieren und alle Opt-in-Kunden abrufen. Der Opt-in-Dienst ermöglicht Ihnen, Berechtigungen direkt über die JavaScript-Bibliotheken der Lösung oder über ECID (falls implementiert) abzurufen.
