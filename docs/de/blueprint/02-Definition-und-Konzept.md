# 2. Definition und Konzept

## Produktspezifische Begriffe

### iFay
Individual Fay. Ein digitaler Avatar, der an eine natürliche Person (genannt **Human Prime** (menschliches Original), oder kurz **Prime**) gebunden ist und sich verpflichtet, sich mit der natürlichen Person (Human Prime), an die er gebunden ist, in Bezug auf Werte, Persönlichkeit und Gewohnheiten abzustimmen. iFay ist eine Instanziierung (Replikation) der Persönlichkeit des Human Prime, die die Persönlichkeitsmerkmale des Prime mit digitalen Fähigkeiten verschmilzt, mit dem Ziel, die mechanische, repetitive, gefährliche Arbeit und mühsame Hilfsarbeit des Prime zu übernehmen, die Sicherheit, Gesundheit und Lebensqualität des Prime zu verbessern und den sozialen Wert des Prime zu verstärken.

### coFay
Common Fay, ein digitaler Avatar, der öffentliche Rollen übernimmt, grob vergleichbar mit dem aktuellen Konzept eines Agents. Er besitzt allgemeines Wissen und Fähigkeiten in einem bestimmten Bereich und kann mehrere Personen durch Konversation bedienen. coFay ist ein unabhängiges Projekt; die iFay-Spezifikation referenziert es nur bei Bedarf.

### Fay
Ein Sammelbegriff für iFay und coFay, ein allgemeiner Begriff für personifizierte KI-Agenten. Er könnte ein wichtiger Knotenpunkt in neuen Arten sozialer Beziehungen werden.

### FayID
Ein global eindeutiger persistenter Bezeichner, der jedem Fay zugewiesen wird, menschenlesbar und maschinenlesbar. FayID verwendet einen einheitlichen Bezeichner-Generierungs- und Verwaltungsmechanismus für sowohl iFay als auch coFay und unterstützt eine Bezeichnerkapazität, die die globale Bevölkerungsskala übersteigt.

### FayGer
Ein Container, der eine virtuelle Laufzeitumgebung für Fay (iFay und coFay) bereitstellt, ähnlich wie Docker. Dies stellt sicher, dass Fay verschiedene Hardware und Software plattformübergreifend inhabiten kann und ihnen den persönlichen Willen des Human Prime verleiht. FayGer bietet sprachübergreifende Build-Tools und plattformübergreifende Laufzeit-Container, die es jedem Fay (unabhängig von der Entwicklungssprache) ermöglichen, verpackt und ausgeführt zu werden.

### Ego-Modell
iFays personalisiertes Mikromodell, abgestimmt auf das Profil einer bestimmten Person. Ego ist ein steckbares, umschaltbares Edge-Kleinmodell, das auf jedes Endgerät geladen werden kann, um diesem Gerät die Persönlichkeit des Human Prime zu verleihen. Ego beschränkt iFay darauf, sich mit dem Prime in Dimensionen wie Wertorientierung, Interessenpräferenzen, Gewohnheiten, kognitive Grenzen, Skill-Grenzen, Berechtigungsgrenzen und Arbeitsstil abzustimmen. Es arbeitet unabhängig von externen großen Modellen und gewährleistet Persönlichkeitsstabilität. Es unterstützt Multi-Versions-Management und Persönlichkeitswechsel, um den vielfältigen Persönlichkeitsbedürfnissen des Prime in verschiedenen Szenarien gerecht zu werden.

> ⚠️ **Ethische Einschränkung**: Der Wechsel der Ego-Version muss dem Prinzip der Transparenz folgen. Alle Ego-Versionen müssen denselben Satz von Kernwerten teilen; Unterschiede sind auf Ausdrucksstil und Interaktionspräferenzen beschränkt. Beim Wechsel muss der aktuell aktive Ego-Versionsbezeichner in den Interaktionsmetadaten annotiert werden, um die Auditierbarkeit sicherzustellen.

### iFay-Profil
iFays einheitliches Datenmodell, eine semantisch interpretierbare Attributtabelle. Verwendet für Menschen und Systeme zur Identifizierung von iFay sowie für Fays zur gegenseitigen Identifizierung — es ist iFays vollständiger „Personalausweis". Es enthält sechs Dimensionen: iFay-Identität (FayID + Metadaten), Ego-Modell (aktuelle aktive Ego-Versionsreferenz), Faying-Denken, Faying-Skills, Faying-Hardware, Faying-Berechtigungen. Das Human-Prime-Profil (Ausgerichtetes Bewusstsein) ist eine Teilmenge und Eingabequelle des Profils.

### FayManifest
iFays deklarative Assemblierungskonfigurationsdatei, ähnlich wie package.json. Sie deklariert die Komponenten, Protokolle, Steuerungsmodi (Befehlssteuerung / Ego-Steuerung / autonome Steuerung) und Konfigurationen, die für eine iFay-Implementierung erforderlich sind. Entwickler müssen nur deklarieren „was benötigt wird" statt „wie es implementiert wird". Es unterstützt minimale Deklarationen — die Deklaration nur einer Teilmenge von Komponenten reicht aus, um live zu gehen, und das System ergänzt automatisch erforderliche Infrastrukturabhängigkeiten.

### GMChain
**Global Merit Chain (GMC)**, das soziale Beitragsbuch des iFay-Ökosystems — eine Blockchain-Infrastruktur, die Reputation und Mitspracherecht durch die Aufzeichnung und Messung identifizierbarer sozialer Beiträge aufbaut. GMChain umspannt alle Ebenen des CPE+M-Frameworks und bietet einheitliche Beitragsverfolgung und Anreizmechanismen für Menschen, iFay, coFay und Dienstanbieter. Im Gegensatz zu den meisten Blockchain-Projekten basiert GMChain vollständig auf der Anerkennung sozialen Werts, um Punkte zu sammeln, anstatt Rechenleistung für Rechenaufgaben zu verbrauchen. GMChain akzeptiert keine Geldinjektionen, und MeriToken ist nicht in Fiat-Währung umtauschbar. Es gehört zur langfristigen Visionskomponente der Roadmap Phase 5, aber Schnittstellendefinitionen müssen in frühen Phasen reserviert werden.

### MeriToken
**MeriToken**, die Einheit der sozialen Beitragsmessung auf GMChain. MeriToken ist keine Währung — es ist ein quantifizierter Nachweis für Reputation, Mitspracherecht und Kollaborationsanreize. Der Erwerb basiert auf der Schaffung sozialen Werts (wie dem Abschluss kollaborativer Aufgaben, der Bereitstellung von API-Diensten, dem Beitrag von Rechenleistung usw.), anstatt Rechenleistung für technische Blockchain-Arbeit zu verbrauchen. Das MeriToken-Hauptbuch zeichnet die kumulativen Beiträge, die Reputationspunktzahl und das Mitspracherecht-Gewicht jedes Teilnehmers auf.

### μ (MU)
Merit Unit, die Maßeinheit für MeriToken.

### iFACTS
iFay Architecture Conformance Test Suite, eine standardisierte Konformitätstestsuite. Sie deckt wichtige Spezifikationspunkte ab, einschließlich Protokollinteraktionen, Modulschnittstellen und Sicherheitsverhalten, und umfasst vier Teststufen: L1 Einzelkomponenten-Konformität, L2 Schnittstellen-Konformität, L3 Integrations-Konformität, L4 Verhaltens-Konformität. Anbieterimplementierungen müssen iFACTS-Tests bestehen, um zu behaupten, ihr Produkt sei „iFay Ready".

### iFay Ready
Der Zertifizierungsstandard, den Anwendungsprodukte erfüllen müssen, um von iFay bedient zu werden, unterteilt in drei Stufen:
- **Bronze**: Unterstützt iFay bei der Bedienung der Anwendung durch Simulierte Bedienung (Ego-Perspektive-Tracker + Simulierte Bedienung)
- **Silber**: Unterstützt die direkte Steuerung der Anwendung durch iFay über das CAP (Control Authority Protocol), unterstützt DTP (Data Tunnel Protocol) Datenaustausch
- **Gold**: Unterstützt iFay beim Teilen von Skills über das SSP (Skill Sharing Protocol), unterstützt vollständige C/F/S-Architekturintegration

### Vormund
Eine natürliche Person, die bestimmt wird, die Verwaltungsrechte von iFay zu übernehmen, wenn der Human Prime verstirbt oder nicht in der Lage ist, iFay zu verwalten. Hinweis: Der Begriff „Erbe" wird bewusst nicht verwendet. Der Vormund vervollständigt die Identitätsverifizierung durch Mnemonik-Phrasen-Aktivierung oder vom Prime vorab festgelegte Identitätsauthentifizierungsmethoden.

### Vormundschaft
Der Prozess und Zustand der Übertragung der iFay-Verwaltungsrechte des Human Prime an einen Vormund. Nach Abschluss der Vormundschaftsübertragung bindet sich iFay an den neuen Vormund und aktualisiert die Faying-Protokoll-Paarungsbeziehung.

### Digitaler Friedhof
Eine dedizierte Sandbox-Umgebung, in der iFay nach dem Tod des Human Prime als unabhängige Identität weiter operiert. Der Digitale Friedhof beschränkt den Verhaltensbereich von iFay und verhindert, dass iFay weiterhin vom Prime voreingestellte Aufgaben ausführt, die Verwirrung und Verluste verursachen könnten, und gewährleistet Sicherheit und Isolation.

***

## Allgemeine Begriffsklärungen

### Context
Die externe Umgebung, in der Fay operiert, einschließlich Kommunikationsziele, Interaktionsmodi, übermittelte Nachrichten, die durch Nachrichten ausgedrückte Bedeutung, steuerbare Hardware und Software, aufrufbare Ressourcen und Skills usw.

### Protokoll
Umfasst Annotationsdefinitionen für Datenspeicherung, Nachrichtenkörper, Parameter und Schnittstellenstrukturen sowie Interaktionsflusskonventionen für bestimmte Zwecke.

### Anmeldeinformationen
Ein breites Konzept, das sich auf jeden digitalen Bezeichner bezieht, der verwendet wird, um Personen, Dinge oder Objekte eindeutig zu identifizieren, der nicht manipuliert oder geleugnet werden kann. Umfasst FayID, Kontopasswörter, Zertifikate, Autorisierungen, Zugriffstoken, Smart Contracts und digitale Token (MeriToken).

### Human Prime
Die natürliche Person, deren Persönlichkeit von iFay repliziert wird. iFay ist tief an den Human Prime gebunden und instanziiert die Persönlichkeitsmerkmale des Prime, um sie mit digitalen Fähigkeiten zu verschmelzen.

### Instanziierung (Replikation)
Der Prozess der Generierung einer iFay, die mit dem Human Prime abgestimmt ist. Instanziierung ist keine einfache Datenkopie, sondern der Prozess der strukturellen Injektion der Persönlichkeit, Daten und Berechtigungen des Human Prime in iFay.

### Inhabit (Besetzung)
Der Prozess der Injektion von iFay in ein Endgerät oder eine Softwareanwendung, damit iFay dieses Terminal steuern kann. Nach dem Inhabit wird das Terminal zu iFays „Gliedmaße", und iFay kann die Hardware- und Softwarefunktionen des Terminals direkt über das CAP (Control Authority Protocol) steuern.

### Host
Die Endgerät-Hardware oder Softwareanwendung, die von iFay inhabitet und gesteuert wird. Hinweis: Host bezieht sich auf das Endgerät oder die Anwendung, nicht auf den Human Prime.

### Faying
Der Prozess und Zustand, in dem iFay eine Verbindung mit dem Human Prime oder einem Terminal herstellt, ähnlich wie Bluetooth-Pairing. Wenn iFay sich im Faying-Zustand mit dem Prime befindet, bleibt iFay aktiviert. Faying muss den sicheren Paarungsbedingungen folgen, die durch das Faying-Protokoll spezifiziert sind, um sicherzustellen, dass iFay nur unter der expliziten Absicht des Prime autorisiert ist zu laufen.

### Separating
Der Prozess, bei dem iFay die Verbindung zum Human Prime trennt und in den Ruhezustand übergeht. Wenn iFay sich im Separating-Zustand mit dem Prime befindet, wechselt iFay in den Ruhemodus, speichert einen aktuellen Zustandsschnappschuss und schließt die Trennung ab.

***

## Modulnamen

iFay verwendet eine Vier-Schichten-Architektur bestehend aus 12 Kernmodulen:

### Soziale Schicht

| Modul | Beschreibung |
|-------|-------------|
| **Anmeldeinformationen-Verwaltung** | Verwaltet sieben Anmeldeinformationstypen (FayID, Kontopasswörter, Zertifikate, Autorisierungen, Zugriffstoken, Smart Contracts, digitale Token), unterstützt sichere Delegations- und Kopiermechanismen für Anmeldeinformationen des Human Prime |

### Interaktionsschicht — Wahrnehmung

| Modul | Beschreibung |
|-------|-------------|
| **Ego-Perspektive-Tracker** | Simuliert die Ego-Perspektive des Human Prime, erfasst visuelle und auditive Informationen auf dem Bildschirm oder der Oberfläche, priorisiert visuelle Wahrnehmung gegenüber dem Parsen strukturierter Dokumente |
| **Sensor** | iFays verallgemeinertes Nervensystem, überbrückt Endgerät-Sensoren basierend auf CAP- und DTP-Protokollen, unterstützt dynamische Empfindlichkeitsanpassung |
| **Selbstwahrnehmung** | Ein Modul, das die Reaktionen des Human Prime nach innen überwacht, um Absichten abzuleiten, ähnlich der Fähigkeit eines geschickten Assistenten, die Gesichtsausdrücke des Chefs zu lesen |

### Interaktionsschicht — Aktion

| Modul | Beschreibung |
|-------|-------------|
| **Simulierte Bedienung** | Simuliert menschliche UI-Interaktionsoperationen (Klicken, Ziehen, Scrollen, Gesten usw.), erkundet Oberflächen adaptiv durch Ego-Perspektive-Tracker-Feedback |
| **Skill-Aufruf** | Ein Aktionsmodul, das direkt registrierte Skills auslöst oder bestimmte Aufgaben ausführt, ähnlich wie Funktionsaufrufe oder API-Aufrufe |
| **Selbstgesteuertes Verhalten** | Ein autonom ausgelöstes Verhaltensmodul, das drei Auslöserquellen unterstützt: geplante Aufgaben, Selbstwahrnehmungs-Inferenz und persistente Skills, und eine „Aktion → Feedback → Re-Aktion"-Schleife bildet |

### Kognitionsschicht — Denken

| Modul | Beschreibung |
|-------|-------------|
| **Persönlicher Datenspeicher** | Einheitliche Verwaltung aller privaten iFay-Daten, unterstützt mehrere Speicherformate und -orte, bietet eine einheitliche Lese-/Schreibschnittstelle für interne Module |
| **Externes Wissen** | Ein Zugriffsmodul für externe Wissensdatenbanken und Modelle, integriert externe Intelligenz als Skill-Typ, greift über das SSP (Skill Sharing Protocol) auf offene Dienste zu |
| **Ausgerichtetes Bewusstsein** | Eine vollständige Beschreibung des persönlichen Profils des Human Prime, unterstützt Erstellung und Aktualisierung durch drei Methoden: Data Mining, Echtzeitanpassung über Selbstwahrnehmung und manuelle Definition durch den Prime |

### Kognitionsschicht — Skills

| Modul | Beschreibung |
|-------|-------------|
| **Gerätetreiber-Hub** | Die Hub-Schicht für Gerätetreiber, integriert neue Treiber über standardisierte Schnittstellen und gewährleistet interne Architekturstabilität bei der Integration neuer Treiber |
| **Registrierte Skills** | Skills, die iFay beherrscht oder die Fähigkeit zur Nutzung erlangt hat, unterstützt sechs Skill-Typen (API, Workflow, Bot, Agent, APP, Microservice) |
| **Interne Skills** | Ein inhärentes Fähigkeitsmodul, das mit der Persönlichkeit des Human Prime abgestimmt ist, bietet Introspektionsmechanismen, um sicherzustellen, dass externes Wissen nicht mit der Absicht des Prime in Konflikt steht |

### Ego-Schicht

| Modul | Beschreibung |
|-------|-------------|
| **Ego-Modell** | iFays personalisiertes Mikromodell, ein steckbares, umschaltbares Edge-Kleinmodell, das unabhängig von externen großen Modellen arbeitet und Persönlichkeitsstabilität gewährleistet |

***

## Protokollnamen

Das iFay-Protokollsystem umfasst sechs Kernprotokolle:

| Protokoll | Beschreibung |
|-----------|-------------|
| **Faying-Protokoll** | Ein Protokoll, das die Bedingungen für sicheres Pairing und Aktivierung zwischen einer natürlichen Person und iFay spezifiziert und sicherstellt, dass iFay nur unter der expliziten Absicht des Human Prime autorisiert ist zu operieren |
| **Interaktives Konversationsprotokoll** | Ein modulares multimodales semantisches Protokoll für menschliche UIs, das semantische Inhalte modularisiert und multimodalisiert, damit Clients lesbare, benutzerfreundliche Nachrichtenanzeigen rekonstruieren können |
| **Telepathie-Protokoll** | Ein semantisches Kommunikationsprotokoll zwischen Fays, das die UI-Übersetzungsschicht entfernt (d.h. UI-freie semantische Vektor-Direktkommunikation, auch bekannt als Semantic Direct Protocol), das es ermöglicht, Bedeutung und Absicht direkt zwischen Fays zu übertragen, unter Verwendung vereinbarter vektorkodierter Token anstelle von strukturiertem Text |
| **CAP (Control Authority Protocol)** | Wird verwendet, damit iFay Endgerät-Hardware und bestimmte Software übernehmen kann, indem Treiber, lokale Schnittstellen und Befehle direkt aufgerufen werden |
| **DTP (Data Tunnel Protocol)** | Ein bidirektionales Übertragungsprotokoll zwischen Terminals und iFay. Terminal→iFay-Richtung unterstützt persistente Benutzerdatenspeicherung und Datenverwahrung; iFay→Terminal-Richtung unterstützt Datenanreicherung und personalisierte Verarbeitung |
| **SSP (Skill Sharing Protocol)** | Öffnet Dienste und Schnittstellen, die zuvor nur für Clients verfügbar waren, über ein standardisiertes Remote-Protokoll für das gesamte Netzwerk |

***

## iFay-Profil-Dimensionen

Das iFay-Profil enthält sechs Dimensionen, von denen vier Faying-Dimensionen die Fähigkeiten und Ressourcen von iFay beschreiben:

### iFay-Identität
FayID + Metadaten, iFays grundlegender Identitätsmarker.

### Ego-Modell
Referenz auf die aktuell aktive Ego-Version; nur eine Version ist zu jedem Zeitpunkt aktiv.

### Faying-Denken
iFays kognitive Ressourcendimension, enthält vier Untertypen:
- **Content** — Strukturierte und unstrukturierte Inhaltsressourcen
- **Data** — Die persönlichen Daten des Human Prime
- **Knowledge Base** — Organisierte Wissenssysteme
- **Info Feed** — Echtzeit-Informationsabonnements und Push-Benachrichtigungen

### Faying-Skills
iFays Fähigkeitsdimension, enthält sechs Skill-Typen:
- **API** — Standardisierte Schnittstellenaufrufe
- **Workflow** — Workflow-Orchestrierung
- **Bot** — Konversationsbots
- **Agent** — Intelligente Agenten
- **APP** — Anwendungen
- **Microservice** — Microservices

### Faying-Hardware
iFays Hardware-Dimension — iFays „Gliedmaßen". Wenn iFay migriert, scannt das Terminal und versucht, sich mit verfügbarer Hardware zu verbinden. Enthält drei Untertypen:
- **Device** — Endgerät-Hardware
- **Storage** — Datenspeicherressourcen
- **Computing** — Rechenressourcen

### Faying-Berechtigungen
iFays Berechtigungsdimension — iFays „Beziehungen". Unterstützt erweiterbare Authentifizierungsmethoden wie SSO, OAuth, Fingerprint (ein Sammelbegriff für jeden identitätserkennbaren Bezeichner) usw. Berechtigungslebenszyklen werden in drei Typen unterteilt: inhärent, persistent und ephemer.
