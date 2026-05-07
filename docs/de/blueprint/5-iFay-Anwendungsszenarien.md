# 5. iFay-Anwendungsszenarien

# Prime-Eigenschaften in iFay injizieren

Per Definition sei wiederholt, dass iFays Persönlichkeit von ihrem Human Prime (menschliches Original) geerbt wird. Allerdings muss die Instanziierung (Replikation) vom Prime eine sehr einfache Operation sein, und eine einmalige Operation muss langfristig wirksam bleiben, um sicherzustellen, dass iFay synchron mit dem Prime wachsen kann.

Wir empfehlen die schnelle Initialisierung von iFay durch folgende Methoden:

- ***Prime-Daten autorisieren***: Einschließlich Fotos, App-Daten, Kommunikationsaufzeichnungen usw. Diese Daten werden durch eine Reihe von Schritten verarbeitet und in einem Standardformat in der Prime-Datenbank gespeichert. Auf diese Daten kann nur iFay direkt zugreifen. Dies hilft iFay, eine langfristige Synchronisation mit dem Human Prime aufrechtzuerhalten. (Wir begrüßen OS- und Hardware-Hersteller, gemeinsam interpreterähnliche Standards zu entwickeln, die es iFay ermöglichen, Daten unter Systemaufsicht zu erwerben. Wir werden dies in einem anderen Projekt namens [Fayward](https://github.com/ChainModePilot/Fayward) behandeln.)
- ***Dateien importieren***: Diese Dateien umfassen Fotos, Dokumente, Notizen, Chat-Protokolle usw. Diese Operation ergänzt die Geschichte des Prime und stellt sicher, dass iFay vergangene Erinnerungen von vor der Autorisierung besitzen kann.
- ***Prime erzählt iFay***: Dies ist sehr ähnlich dem Schreiben eines Prompts für einen Agent. Es kann in Konversations- oder Fragebogenform sein. Um die Betriebskosten des Nutzers zu reduzieren, empfehlen wir, mit iFay über vergangene Erfahrungen zu plaudern, wie mit einem engen Freund zu sprechen.

Aus Implementierungsperspektive müssen drei Voraussetzungstechnologien erfüllt sein:

1. ***Enge Integration mit der OS-Schicht***: Ermöglicht das Lesen von Systeminformationen und privaten Daten anderer Anwendungen. Unter Bezugnahme auf iOS- und Android-Autorisierungsverwaltung könnten Drittanbieter-Apps es schwierig finden, dieses Vertrauensniveau zu erreichen. Daher müssen OS- und Hardware-Hersteller gemeinsam zentralisierte Verwaltungsmethoden für Datenanwendungen bereitstellen.
2. ***Offenes Datenweiterleitungs-Öffentliches Format***: Derzeit werden Weiterleitungsoperationen zwischen Apps meist in Dateiform durchgeführt. Zum Beispiel das Teilen von Fotos und Dokumenten mit einer anderen App. Es ist jedoch schwierig für das System, personalisierte strukturierte Daten mit einer anderen App zu teilen. Wenn wir also Nutzer-App-Daten schnell mit iFay synchronisieren wollen, ist ein einheitliches Datenformat unerlässlich.
3. ***Standard-Forschungsfragebogen***: Chat ist eine hochdivergente Interaktionsform, und ob Chat-Inhalte iFay wirklich helfen, den Human Prime zu verstehen, hängt von den besprochenen Themen ab. Um iFay zu helfen, Chat-Themen zu fokussieren und effektive Gedächtnisdaten zu erwerben, werden wir Referenzfragebögen bereitstellen, um den Chat-Themenbereich einzuschränken. Dieser Fragebogen kann direkt als Prompt zum LLM hinzugefügt werden.

# iFay mit externen Fähigkeiten ergänzen

Nach Abschluss der Prime-Eigenschaftsinjektion besitzt iFay bereits deine Persönlichkeit, Erinnerungen und grundlegenden Berechtigungen. Aber zu diesem Zeitpunkt ist iFay wie eine Person, die gerade in einer neuen Stadt angekommen ist — weiß, wer sie ist, aber noch nicht, welche Ressourcen die Stadt zu bieten hat. iFay mit externen Fähigkeiten zu ergänzen bedeutet, ihr zu helfen, Verbindungen zur Außenwelt herzustellen.

## Skills registrieren

iFays Fähigkeitserweiterung wird durch „Registrierte Skills" erreicht. Skills sind eine Voraussetzung dafür, dass iFay jede Aktion ausführen kann — nicht registrierte Skills können nicht aufgerufen werden. iFay unterstützt sechs Skill-Typen:

| Skill-Typ | Beschreibung | Beispiele |
|-----------|-------------|----------|
| **API** | Direkte Aufrufe externer Dienstschnittstellen | Übersetzungs-API, Wetterabfrage-API, Zahlungsschnittstelle |
| **Workflow** | Mehrstufige automatisierte Orchestrierungsprozesse | „E-Mail empfangen → Schlüsselinfos extrahieren → Zusammenfassung generieren → an Messaging-App senden" |
| **Bot** | Konversationelle automatisierte Programme | Kundenservice-Bot, Termin-Bot |
| **Agent** | KI-Agenten mit autonomer Entscheidungsfindung | Code-Review-Agent, Datenanalyse-Agent |
| **APP** | Vollständige Anwendungen | Kalender-App, Notizen-App, Navigations-App |
| **Microservice** | Unabhängig bereitgestellte Backend-Dienste | Bilderkennungsdienst, Sprache-zu-Text-Dienst |

Während der Skill-Registrierung wird ein Vorautorisierungsschritt abgeschlossen, der sicherstellt, dass für nachfolgende Aufrufe keine zusätzliche Authentifizierung benötigt wird, was die Latenz reduziert. Zum Beispiel, wenn du einen Übersetzungs-API-Skill für iFay registrierst, schließt iFay die API-Key-Bindung und Berechtigungsverifizierung während der Registrierungsphase ab, sodass jede nachfolgende Übersetzungsanfrage sofort ausgeführt werden kann.

Wenn iFay offline ist, werden ausstehende Aktionen zwischengespeichert und automatisch asynchron ausgeführt, wenn die Konnektivität wiederhergestellt ist — genau wie E-Mails im Flugzeug schreiben, die automatisch gesendet werden, wenn du landest.


## Auf Externes Wissen zugreifen

Über Skills hinaus kann iFay auch auf externe Wissensdatenbanken und Modelle zugreifen und sie als speziellen Skill-Typ behandeln. Dies ermöglicht iFay den Zugang zu Wissen und Intelligenz jenseits der eigenen Fähigkeiten des Human Prime, wie das Konsultieren eines Expertenberaters.

Zum Beispiel bist du Softwareingenieur, aber deine iFay kann auf eine medizinische Wissensdatenbank zugreifen. Wenn du dich unwohl fühlst, kann iFay deine persönlichen Gesundheitsdaten mit medizinischem Wissen kombinieren, um vorläufige Gesundheitsratschläge zu geben — sie ersetzt keinen Arzt, sondern handelt wie ein sachkundiger Freund, der dir bei einer ersten Einschätzung hilft.

Externes Wissen wird über das SSP (Skill Sharing Protocol) abgerufen, um standardisierte offene Dienste und Schnittstellen im Netzwerk zu erreichen. Wenn externe Wissensquellen nicht verfügbar sind, degradiert iFay zur Nutzung zwischengespeicherten Wissens aus dem Persönlichen Datenspeicher und benachrichtigt die Kognitionsschicht, dass sie sich derzeit in einem degradierten Zustand befindet.

# Mensch-iFay-Interaktionsmethoden

## Wie man iFay aktiviert

iFay ist kein ständig laufender Hintergrunddienst — sie befindet sich nur in einem aktivierten Zustand, wenn du sie explizit autorisierst. Dieses Design stellt sicher, dass iFay nicht ohne dein Wissen autonom handelt.

### Faying-Paarungsprozess

Der Prozess der Aktivierung von iFay wird „Faying" (Verbinden) genannt und folgt dem Faying-Protokoll für sicheres Pairing. Der gesamte Prozess ähnelt dem Bluetooth-Pairing, aber mit einem höheren Sicherheitsniveau:

1. **Pairing initiieren**: Du sendest eine Verbindungsanfrage an iFay über ein Endgerät (Handy, Computer usw.) und stellst Identitätsnachweise bereit.
2. **Identitätsverifizierung**: Das System verifiziert deine Identität über das FayID-Registrierungszentrum und bestätigt, dass du der legitime Human Prime dieser iFay bist.
3. **Multi-Faktor-Authentifizierung**: Das System gibt eine Pairing-Challenge zurück, und du musst eine Multi-Faktor-Authentifizierung abschließen (z.B. Biometrie + Geräte-Fingerprint + Passphrase).
4. **Aktivierungsbestätigung**: Nach bestandener Authentifizierung geht iFay in den „Faying"-aktivierten Zustand über und beginnt, dir zu dienen.

Wenn jemand versucht, deine iFay ohne deine explizite Absicht zu aktivieren, lehnt das System die Aktivierungsanfrage ab und protokolliert das Ereignis — genau wie wenn jemand versucht, dein Handy mit deinem Fingerabdruck zu entsperren, aber scheitert.

### Szenario: Ersteinrichtung und tägliche Wiederverbindung

**Ersteinrichtung**: Lily hat gerade ihre eigene iFay erstellt. Sie öffnet den iFay-Client auf ihrem Handy, und das System führt sie durch FayID-Zuweisung, Ego-Modell-Initialisierung und Profilerstellung. Dann erzählt Lily ihrer iFay ihre Persönlichkeitsmerkmale durch Konversation, autorisiert Fotos und Kommunikationsdaten auf ihrem Handy und delegiert Login-Anmeldeinformationen für häufig genutzte Apps. Der gesamte Prozess fühlt sich an wie ein tiefes Nachmittagsgespräch mit einem neuen Freund.

**Tägliche Wiederverbindung**: Am nächsten Morgen nimmt Lily ihr Handy, und der iFay-Client erkennt ihr Gesicht und den Geräte-Fingerprint und schließt automatisch das Faying-Pairing ab. iFay erholt sich vom Ruhezustand in den aktivierten Zustand, lädt den gestern Abend gespeicherten Zustandsschnappschuss und setzt nahtlos fort — als hätte dein Assistent neben dir gewartet, bis du aufwachst.


## iFays autonome Wahrnehmung

iFay ist nicht nur ein Ausführer, der auf Befehle wartet. In Phase 4 (Vollständige Personifizierung) besitzt iFay Selbstwahrnehmungs- und Selbstgesteuertes-Verhalten-Fähigkeiten, kann dich und die umgebende Umgebung proaktiv beobachten, deine Gefühle und Absichten ableiten und autonom handeln.

### Selbstwahrnehmungsmodul

Das Selbstwahrnehmungsmodul ist iFays Fähigkeit, „den Raum zu lesen". Es überwacht die Reaktionen des Human Prime nach innen, ähnlich einem geschickten Assistenten, der die Gesichtsausdrücke seines Arbeitgebers liest. Wenn das Selbstwahrnehmungsmodul eine neue Absicht von dir ableitet, gibt es die Inferenz an das Modul Selbstgesteuertes Verhalten und die Kognitionsschicht weiter und löst entsprechende Aktionen aus.

### Selbstgesteuertes Verhalten

iFays Selbstgesteuertes Verhalten wird von drei Auslöserquellen angetrieben:

- **Geplante Aufgaben**: Automatisch gemäß voreingestellten Zeitplänen ausgeführt, wie das Organisieren deiner Zeitplanzusammenfassung jeden Morgen um 8 Uhr.
- **Selbstwahrnehmungs-Inferenz**: Proaktives Initiieren von Aufgaben basierend auf Inferenzen über deinen aktuellen Zustand, wie proaktives Erinnern an eine Pause, wenn erhöhter Stress erkannt wird.
- **Persistente Skills**: Registrierte Skills und Interne Skills, die kontinuierlich laufen und eine autonome „Aktion → Feedback → Re-Aktion"-Schleife bilden.

Diese „Aktion → Feedback → Re-Aktion"-Schleife ist der Kern von iFays autonomem Betrieb. Nachdem iFay eine Aktion ausgeführt hat, erhält sie Feedback durch das Selbstwahrnehmungsmodul (deine Reaktionen, Umgebungsänderungen) und entscheidet dann den nächsten Schritt entsprechend. Wenn das Ausführungsergebnis nicht mit deiner Absicht übereinstimmt, pausiert iFay nachfolgende autonome Aktionen und bittet um deine Bestätigung.

### Szenario: iFay erinnert proaktiv an ein Meeting

Um 14 Uhr bist du konzentriert beim Coden. iFays Selbstwahrnehmungsmodul erkennt durch Sensordaten, dass deine Herzfrequenz leicht gestiegen ist und deine Tippgeschwindigkeit zugenommen hat — diese Signale deuten darauf hin, dass du möglicherweise in einem angespannten Zustand bist. Gleichzeitig findet iFays geplanter Aufgabenscan ein wichtiges Kundenpräsentationsmeeting um 15 Uhr in deinem Kalender.

iFay trifft ein umfassendes Urteil: Du beeilst dich, die Arbeit fertigzustellen, und hast wahrscheinlich das bevorstehende Meeting vergessen. Also erinnert iFay dich über das Interaktive Konversationsprotokoll sanft auf eine Weise, die deinen Flow nicht unterbricht: „Du hast um 15 Uhr eine Kundenpräsentation. Die Folien sind fertig. Soll ich Kaffee für den Besprechungsraum bestellen?"

Du antwortest „Klar", und iFay ruft sofort registrierte Büroservice-Skills auf, um die Kaffeebestellung abzuschließen, und pusht die Meeting-Materialien auf den großen Bildschirm des Konferenzraums — der gesamte Prozess erforderte nur ein Wort von dir.


## Wie man iFay herunterfährt

Der Prozess des Herunterfahrens von iFay wird „Separating" (Trennen) genannt und folgt ebenfalls dem Faying-Protokoll.

### Trennungsprozess

1. **Trennung initiieren**: Du sendest eine Trennungsanfrage an iFay (kann ein Sprachbefehl, eine Geste oder ein Client-Button sein).
2. **Zustandsschnappschuss**: iFay speichert einen vollständigen Zustandsschnappschuss des aktuellen Zustands, einschließlich laufender Aufgaben, Kontextinformationen und temporärer Daten.
3. **In Ruhezustand gehen**: iFay wechselt vom „Faying"-aktivierten Zustand in den „Separating"-Ruhezustand und stoppt alle autonomen Verhaltensweisen.
4. **Trennungsbestätigung**: Das System bestätigt, dass die Trennung abgeschlossen ist.

Im Ruhezustand führt iFay keine autonomen Aktionen aus, aber der Zustandsschnappschuss bleibt vollständig erhalten und kann bei der nächsten Aktivierung nahtlos wiederhergestellt werden.

### Szenario: Schlafenszeit, iFay geht in den Ruhezustand

Um 23 Uhr machst du dich bettfertig. Du sagst zu deinem Handy: „Gute Nacht." iFay erkennt dies als Trennungssignal und beginnt den Trennungsprozess:

- Speichert den gesamten heutigen Konversationskontext und den Fortschritt unerledigter Aufgaben
- Markiert Dinge, die dich morgen früh erinnern sollen, als geplante Aufgaben
- Prüft, ob es dringende Angelegenheiten gibt, die während deines Schlafs erledigt werden müssen (falls ja, fragt sie dich vor der Trennung)
- Schließt den Zustandsschnappschuss ab und geht in den Ruhemodus

Am nächsten Morgen nimmst du dein Handy, iFay reaktiviert sich über das Faying-Protokoll, lädt den Zustandsschnappschuss von gestern Abend und sagt dir: „Guten Morgen. Ich habe den Entwurf des Berichts fertiggestellt, den du gestern erwähnt hast. Außerdem wurde dein Nachmittagsflug eingecheckt — Sitz 12A, Fenster."


# iFays soziale Funktionen

iFay ist keine Insel. In Phase 4 hat iFay die Fähigkeit, mit anderen Fays zu kommunizieren und zusammenzuarbeiten (einschließlich anderer Leute iFays und öffentlicher coFays).

## Inter-Fay-Kommunikation: Telepathie-Protokoll

Wenn deine iFay mit anderen Fays kommunizieren muss, verwenden sie das Telepathie-Protokoll — ein semantisches Kommunikationsprotokoll, das die UI-Übersetzungsschicht entfernt. Traditionelle Inter-Anwendungs-Kommunikation erfordert das Kodieren von Informationen als Text, deren Übertragung und dann Dekodierung, mit potenziellem Informationsverlust bei jedem Schritt. Das Telepathie-Protokoll verwendet vereinbarte vektorkodierte Token, um Bedeutung und Absicht direkt zu übertragen, mit Effizienz und Genauigkeit, die traditionelle Methoden weit übertreffen.

## Zusammenarbeit mit coFay

coFay (Common Fay) ist ein digitaler Avatar, der öffentliche Rollen übernimmt, grob vergleichbar mit dem aktuellen Konzept eines Agents. Deine iFay kann Unterstützung von coFays suchen, genau wie du im echten Leben Hilfe von Fachleuten suchst.

Ein Schlüsselmechanismus: Fays verhandeln Preise, bevor sie Aufgaben ausführen. Dies stellt sicher, dass der Beitrag jeder Zusammenarbeit nachverfolgbar und bewertbar ist, letztendlich auf GMChain aufgezeichnet und mit MeriTokens abgerechnet wird.

## Szenario: Deine iFay verhandelt eine Buchung mit einer Reise-coFay

Du sagst iFay: „Buche Flüge und Hotel für Tokio nächste Woche, Budget unter 8.000 Yuan."

Deine iFay kontaktiert sofort eine professionelle Reise-coFay über das Telepathie-Protokoll. Hier ist ihre „Konversation" (für dich vollständig transparent — du siehst nur das Endergebnis):

1. **Absichtsübertragung**: Deine iFay kodiert deine Anforderungen (Ziel, Zeit, Budget, Präferenzen) als semantische Vektoren und sendet sie an die Reise-coFay.
2. **Preisverhandlung**: Die Reise-coFay bietet 15μ (MeriToken-Einheiten) für den kompletten Buchungsservice. Deine iFay beurteilt basierend auf Ausgabepräferenzen im Ego-Modell den Preis als angemessen und akzeptiert.
3. **Kollaborative Ausführung**: Die Reise-coFay ruft Fluggesellschafts- und Hotel-SSP-Skill-Schnittstellen auf, um optimale Optionen zu suchen.
4. **Ergebnisse zurückgegeben**: Die Reise-coFay gibt drei alternative Pläne an deine iFay zurück.
5. **Personalisierte Filterung**: Deine iFay filtert basierend auf deinen Präferenzen nach der besten Option (Fensterplatz, ruhiges Hotel, nah an der U-Bahn).
6. **Dir präsentiert**: iFay präsentiert den empfohlenen Plan über das Interaktive Konversationsprotokoll im modularen Kartenformat: „Habe eine tolle Kombination gefunden — ANA Direktflug, Sitz 12A Fenster, Hotel 3 Minuten Fußweg von der Shinjuku Station, insgesamt 7.200 Yuan. Buchung bestätigen?"

Du sagst „Buchen", iFay schließt die Buchung ab, GMChain zeichnet den Beitrag dieser Zusammenarbeit auf, und die Reise-coFay verdient 15μ.


# Sicherheit

iFays Sicherheitsdesign folgt einem grundlegenden Prinzip: **Soziale Ethik hat Vorrang vor allem**. Unabhängig von den Anweisungen des Human Prime wird iFay nicht gegen soziale Ethik und öffentliche Ordnung verstoßen. Auf dieser Grundlage schützt iFay die Interessen des Human Prime durch mehrere Sicherheitsebenen.

## Ethik zuerst

Jede Verhaltensentscheidung von iFay durchläuft einen Ethik-Konformitätsprüfungsprozess:

1. **Soziale Ethikprüfung** (höchste Priorität): Verstößt das Verhalten gegen soziale Ethik und öffentliche Ordnung? Falls ja, Ausführung verweigern und dem Human Prime den Grund erklären.
2. **Prime-Abstimmungsprüfung**: Ist das Verhalten konsistent mit den Werten und der Absicht des Human Prime? Falls nicht, je nach Schwere entweder pausieren und Bestätigung anfordern oder das Ego-Modell vor der Ausführung anpassen lassen.
3. **Berechtigungsprüfung**: Hat iFay die Berechtigung, dieses Verhalten auszuführen? Falls nicht, Autorisierung anfordern.

## Anmeldeinformationen-Isolation

Wenn du Anmeldeinformationen an iFay delegierst, verwendet iFay nicht direkt deine Original-Anmeldeinformationen. Das System tauscht Original-Anmeldeinformationen gegen entsprechende Kopie-Anmeldeinformationen aus, und iFay verwendet Kopien für Login und Authentifizierung. Das bedeutet, selbst wenn eine Kopie-Anmeldeinformation kompromittiert wird, bleiben deine Original-Anmeldeinformationen sicher. Sobald eine Kompromittierung oder abnormale Nutzung einer Kopie-Anmeldeinformation erkannt wird, widerruft das System sofort die Kopie und benachrichtigt dich.

## Datenschutz

Wenn iFay autorisiert ist, private Daten abzufragen, gibt sie nur boolesche Ergebnisse (wahr oder falsch) zurück, ohne spezifische private Daten offenzulegen. Zum Beispiel, wenn ein Dienst verifizieren muss, ob du über 18 bist, wird iFay nur „ja" oder „nein" antworten, ohne dein spezifisches Geburtsdatum preiszugeben.

## Ego-Stabilität

Das Ego-Modell arbeitet unabhängig als eingebettetes Mikromodell, unbeeinflusst von externen Updates großer Modelle. Dies verhindert plötzliche Persönlichkeitsänderungen bei iFay durch externe Modell-Updates oder absichtliche Manipulation — deine iFay wird immer die „sie" sein, die du kennst.

## Audit-Trail

Alle kritischen Operationen werden in manipulationssicheren Audit-Logs aufgezeichnet, einschließlich Anmeldeinformationen-Nutzung, Skill-Aufrufe, Zustandsübergänge und Berechtigungsänderungen. Dies stellt sicher, dass jede Aktion nachverfolgbar und auditierbar ist.


## Szenario: iFay lehnt eine unethische Anfrage ab

Dein Kollege leiht sich deinen Computer und versucht, deine iFay zu verwenden, um interne Dateien eines Konkurrenzunternehmens einzusehen.

iFays Ethik-Konformitätsprüfungsprozess wird sofort aktiviert:

1. **Soziale Ethikprüfung**: Der Zugriff auf interne Dateien anderer könnte Wirtschaftsspionage darstellen und gegen soziale Ethik verstoßen.
2. **Identitätsverifizierung**: Das Faying-Protokoll erkennt, dass der Geräte-Fingerprint und die Verhaltensmuster des aktuellen Bedieners nicht mit dem Human Prime übereinstimmen.
3. **Ausführung verweigern**: iFay lehnt die Anfrage ab und zeichnet ein Audit-Log auf.
4. **Prime benachrichtigen**: iFay sendet dir eine Benachrichtigung: „Jemand hat versucht, über dein Gerät auf sensible Informationen zuzugreifen. Die Anfrage wurde abgelehnt. Siehe Audit-Log für Details."

Während des gesamten Prozesses hat iFay keine Informationen darüber preisgegeben, welche Anmeldeinformationen oder Berechtigungen du besitzt — sie hat einfach mit „Anfrage abgelehnt" geantwortet.


# Gestaltung des KI-Industrie-Ökosystems

iFay ist nicht nur ein Produkt, sondern ein offenes Ökosystem. Es bietet klare Beteiligungspfade für drei Arten von Entwicklern und incentiviert Ökosystem-Prosperität durch Zertifizierungsstandards und Wirtschaftsmodelle.

## Drei Entwicklerrollen

| Rolle | Verantwortung | Analogie |
|-------|---------------|---------|
| **Open-Source-Projektentwickler** | Beteiligen sich an der Entwicklung von iFay-Kernmodulen und -Protokollen, treiben das iFay-System voran | Ähnlich wie Linux-Kernel-Beitragende |
| **Anwendungsentwickler** | Führen iFay-Unterstützung in ihren Produkten ein, ermöglichen es Produkten, von iFay bedient zu werden, damit Nutzer iFay delegieren können, Produkte zu verwenden | Ähnlich wie die Entwicklung Siri/Alexa-kompatibler Apps |
| **Dienstanbieter-Entwickler** | Erstellen iFay-Implementierungen unter der iFay-Spezifikation, ermöglichen Nutzern die Wahl von iFays verschiedener Anbieter | Ähnlich wie verschiedene Anbieter Browser-Standards implementieren |

## iFay Ready Zertifizierung

Damit Anwendungsprodukte von iFay bedient werden können, müssen sie die iFay Ready Zertifizierung bestehen. Die Zertifizierung ist in drei Stufen unterteilt:

| Stufe | Anforderungen | Bedeutung |
|-------|-------------|---------|
| **Bronze** | Unterstützt iFay bei der Bedienung der Anwendung durch Simulierte Bedienung | iFay kann deine Anwendungsoberfläche wie ein Mensch bedienen |
| **Silber** | Unterstützt CAP-Protokoll-Direktsteuerung + DTP-Protokoll-Datenaustausch | iFay kann die UI umgehen und deine Anwendung direkt steuern |
| **Gold** | Unterstützt SSP-Protokoll-Skill-Sharing + vollständige C/F/S-Architekturintegration | Deine Anwendung ist vollständig in das iFay-Ökosystem integriert |

Die Zertifizierung integriert sich mit dem iFACTS-Test-Framework — die Silber-Stufe verwendet L2-Schnittstellen-Konformitätstests zur Verifizierung, die Gold-Stufe verwendet L2 + L3-Integrations-Konformitätstests zur Verifizierung.


## FayManifest treibt Ökosystem-Wachstum

FayManifests deklarative Assemblierung senkt die Entwicklungshürde für iFay dramatisch. Entwickler müssen nicht die gesamte Systemkomplexität verstehen — sie deklarieren einfach die erforderliche Komponententeilmenge in einer JSON-Datei, und das System ergänzt automatisch Infrastrukturabhängigkeiten. Das bedeutet:

- Eine iFay, die nur Drohnen steuern muss, deklariert nur Gerätetreiber-Hub, Sensor, CAP-Protokoll und DTP-Protokoll
- Eine iFay, die sich auf Dokumentenverarbeitung konzentriert, deklariert nur Skill-Aufruf, Registrierte Skills und zugehörige APIs
- Das System ergänzt automatisch FayID, FayGer-Laufzeitumgebung, Berechtigungssystem und andere erforderliche Infrastruktur

## GMChain und MeriToken Wirtschaftsmodell

Der Wertfluss im iFay-Ökosystem wird durch GMChain (Global Merit Chain) und MeriToken realisiert. GMChain verfolgt, misst und bewertet alle Fay-Beiträge und belohnt Mitwirkende mit MeriTokens. Beitragstypen umfassen:

- Informationsassemblierungsdienste
- API-Bereitstellung
- Gerätebereitstellung
- Laufzeitumgebungsbereitstellung
- Andere identifizierbare wertschöpfende Inputs

Der MeriToken-Erwerb basiert auf der Schaffung sozialen Werts, nicht auf dem Verbrauch von Rechenleistung für technische Blockchain-Arbeit. GMChain unterstützt gerichtete Ausgabe, die durch Fiat-Währung, Anleihen, Vermögenszertifikate, Gold und andere Sicherheiten gedeckt ist, und interagiert mit realen Wertanerkennungsmethoden.


## Szenario: Eine Drohnensteuerungs-iFay an einem Wochenende bauen

Das Entwicklungsteam eines Drohnen-Startups möchte iFay-Fähigkeiten in ihr Produkt integrieren. Am Freitagnachmittag öffnet der Teamleiter die FayManifest-Dokumentation und schreibt eine Deklarationsdatei:

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "iFay-Implementierung für Drohnensteuerung",
  "vendor": "SkyPilot Inc",
  "modules": [
    { "id": "device_driver_hub" },
    { "id": "sensor", "config": { "types": ["gps", "imu", "camera"] } },
    { "id": "invoke_skill" },
    { "id": "registered_skill" }
  ],
  "protocols": [
    { "id": "cap_protocol" },
    { "id": "dtp_protocol", "config": { "realtime": true } }
  ],
  "controlMode": "ego",
  "drivers": [
    { "name": "Flight Controller", "type": "device", "driverPackage": "@drone-drivers/fc-generic" }
  ],
  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection"]
  }
}
```

Die FayGer-Laufzeitumgebung parst dieses Manifest automatisch, ergänzt FayID, Berechtigungssystem, Sicherheits- und Ethik-Konformität und andere Infrastrukturabhängigkeiten und assembliert eine vollständige Drohnensteuerungs-iFay-Instanz.

Am Samstag schließt das Team die Flugsteuerungstreiber-Anpassung und Tests ab. Am Sonntag verifizieren sie die Spezifikationskonformität jedes Moduls durch iFACTS L1 Einzelkomponenten-Konformitätstests.

Bis Montagmorgen kann diese Drohnensteuerungs-iFay bereits Sprachbefehle des Nutzers akzeptieren, autonom Flugrouten planen, Luftaufnahmen in Echtzeit streamen und automatisch bei niedrigem Akkustand zurückkehren — der gesamte Entwicklungszyklus dauerte weniger als ein Wochenende.
