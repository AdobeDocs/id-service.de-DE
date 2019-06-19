---
description: Mit dem Anmeldedienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie beim Besuch Ihrer Site ein Cookie auf dem Gerät oder Browser des Benutzers festlegen können.
seo-description: Mit dem Anmeldedienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie beim Besuch Ihrer Site ein Cookie auf dem Gerät oder Browser des Benutzers festlegen können.
seo-title: Anmeldedienst
title: Anmeldedienst
uuid: aebd 72 ad -4118-471 b -9755-d 08 a 72 caa 0 fd
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Anmeldedienst{#opt-in-service}

Mit dem Anmeldedienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie beim Besuch Ihrer Site ein Cookie auf dem Gerät oder Browser des Benutzers festlegen können.

Der Anmeldedienst ist eine Erweiterung des [Experience Cloud ID-](https://marketing.adobe.com/resources/help/en_US/mcvid/) Diensts (ECID), mit dem Sie steuern können, ob und welche Erlebniscloud-Lösungen Cookies auf Webseiten vor der Zustimmung des Benutzers erstellen können. Mit dem Anmeldedienst können Sie außerdem Protokolle für die Integration in Ihre CMP (Opt-Management-Plattform) und Ihre vorhandenen Systeme als Teil Ihres größeren Designs festlegen.

Mit dem Opt-in-Dienst können Sie angeben, ob ein Besucher Adobe-Lösungen gleichzeitig auswählen kann oder Lösungen für Berechtigungen in der Reihe präsentieren. Sobald der Genehmigungsprozess abgeschlossen und vom Kunden aufgezeichnet wurde, können Sie die CMP-Besuchergenehmigungen aus allen Adobe-Lösungen abrufen.

Der Anmeldedienst wird mit Adobe [Launch](https://docs.adobelaunch.com/) mit der [Teilnahme an der Teilnahme implementiert und konfiguriert](../../implementation-guides/opt-in-service/launch.md). Sie kann auch mithilfe von [DTM implementiert und](../../implementation-guides/opt-in-service/optin-dtm.md)konfiguriert werden.

Weitere [Informationen finden Sie unter Einrichten des Opt-in-Diensts](../../implementation-guides/opt-in-service/getting-started.md) .

>[!NOTE]
>
>Mit dem Anmeldedienst können Sie ein System einrichten, das das Herunterladen von Adobe-Cookies genehmigen oder verweigern kann. Es können keine Zustimmungsvoreinstellungen von Benutzern erfasst werden und das Objekt kann auch nicht als Repository für Voreinstellungen verwendet werden.

>[!IMPORTANT]
>
>Der Inhalt dieses Dokuments ist keine rechtliche Beratung und soll keine rechtlichen Hinweise ersetzen. Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um sich über die Zustimmung und die Vorgehensweisen bei der Einrichtung Ihrer Opt-in-Implementierung zu informieren.

## Opt-in für mehrere Experience Cloud-Lösungen {#section-053e6224505542cf961896f0ca869e52}

Der &quot;Opt-in&quot; -Dienst ist ein Tool zum Erstellen einer Einwilligung zur Teilnahme an einem Arbeitsablauf, die Ihren eigenen Anforderungen entspricht. So können Sie einen Workflow entwerfen, der vor und nach der Bestätigung vom Benutzer oder vom Controller zu reagieren (Feuer-Tags).

Mit dem Opt-In-Dienst können Sie die Praktiken zur Genehmigungsverwaltung für Adobe-Lösungen einrichten:

* Sie können angeben, ob die Anforderungen für die Zustimmungserfassung im Allgemeinen auf einen Benutzer zutreffen.
* Sie können festlegen, welche Lösungen Cookies generieren dürfen.
* Sie können Standardeinstellungen für alle Lösungen anwenden, deren Kategorien nicht ausdrücklich vom Benutzer genehmigt oder abgelehnt werden.
* Sie können eine benutzerdefinierte Reaktion auf Änderungen an den Zustimmungseinstellungen eines Benutzers auslösen, um die Einstellungen des Benutzers beizubehalten oder zu aktualisieren.

Mithilfe der Opt-in-Dienste können Sie Ihre Site so konfigurieren, dass einige Cookies mit vorab einwilligtem Einverständnis geladen werden können, bevor die Benutzer die Auswahl treffen. Sie können die Opt-in-Dienste für neue Kunden festlegen, damit Cookies geladen werden können, nachdem der Benutzer zugestimmt hat oder nachdem eine Auswahl verfügbar gemacht wurde. Außerdem können Sie die Zustimmung in Ihrer bestehenden Consent Management-Plattform speichern und abrufen oder Opt-in-Berechtigungen einfach in einem Cookie speichern.

![](assets/Opt-in-approval.png)

Adobe-Lösungen können dann überprüfen, ob das Tag genehmigt wurde, Änderungen abonnieren und alle Opt-in-Kunden abrufen. Mit dem Anmeldedienst können Sie Berechtigungen direkt über die javascript-Bibliotheken oder über ECID erhalten, wenn sie implementiert sind.
