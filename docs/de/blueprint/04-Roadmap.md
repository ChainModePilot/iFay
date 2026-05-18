# 4. Roadmap: 5 Phasen

Wir befinden uns noch in der „Ära der menschlichen Bedienung" — Hardware und Software sind darauf angewiesen, dass Menschen über Oberflächen interagieren, um Geräte zu steuern und Funktionen auszuführen.

![](./illustration/human-operation-era.png)

Derzeit ist die Beziehung zwischen Menschen, Geräten und Dienstanbietern wie im obigen Diagramm dargestellt.

<br>

---

## 1️⃣ Phase 1: Simulation menschlicher Bedienung
Auf der bestehenden Hardware- und Software-Architektur lassen wir iFay menschliche UI-Bedienungen simulieren.

![Phase 1 Konzept](./illustration/phase1-concept.png)

Um dies zu erreichen, müssen wir mindestens 2 Dinge bewerkstelligen:
1. Anmeldeinformationen-Delegation: Menschliche Nutzer müssen in der Lage sein, iFay sicher zu autorisieren, ihre [Anmeldeinformationen](./02-Definition-und-Konzept#allgemeine-begriffsklärungen) (Konten, Passwörter, Zertifikate, Zugriffsberechtigungen, Verträge usw.) durch einen kontrollierbaren und auditierbaren Delegationsmechanismus zu verwenden.
2. Interaktion mit iFay: Hauptsächlich über eine Konversationsschnittstelle. Allerdings ist sorgfältiges Design erforderlich — wenn Aufgaben höhere Interaktionskomplexität oder Präzision erfordern, können strukturierte Oberflächen effizienter sein als reiner Chat.

<br>

Basierend auf den obigen Überlegungen wird iFay v1.0 bei der Veröffentlichung die folgenden 5 Module enthalten (die orangefarbenen Abschnitte im Diagramm unten):

![Phase 1: Simulation menschlicher Bedienung](./illustration/phase1-architecture.png)

### 1. FayID
Dies ist iFays eindeutiger Bezeichner. Tatsächlich werden sowohl iFay als auch [coFay](https://github.com/ChainModePilot/coFay/wiki) einheitliche eindeutige IDs zugewiesen.

Der Zweck ist sicherzustellen, dass wenn persönliche iFays schließlich bedeutungsvolle soziale Rollen übernehmen, die Identität reibungslos übergehen kann — so wie einige einzelne YouTuber sich zu wichtigen Rollen im öffentlichen Diskurs und der Bürgerbildung entwickeln.

Hier adressieren wir zwei Kernprobleme:
- _**FayID-Generierung und -Verwaltung**_: Fays werden exponentiell wachsen und schließlich die Anzahl menschlicher Nutzer übersteigen. Dies erfordert einen skalierbaren, benutzerfreundlichen, leicht erkennbaren ID-Generierungs- und Verwaltungsmechanismus.
- _**Aktivierungszustand**_: Um sicherzustellen, dass iFay niemals ohne das Wissen oder die Absicht des Human Prime (menschliches Original) operiert, definieren wir strenge Aktivierungsregeln. Keine iFay sollte ohne explizite Absicht autonom handeln. Dies wird durch das Open-Source [Faying-Protokoll](https://github.com/ChainModePilot/Faying-Protocol/wiki) geregelt, das spezifiziert, wie natürliche Personen und iFay sicher pairen und unter welchen Bedingungen iFay autorisiert ist, in einem aktivierten Zustand zu operieren.

### 2. Anmeldeinformationen-Verwaltung
„Anmeldeinformationen" ist hier ein breites Konzept. Für natürliche Personen müssen Nutzer die meiste Zeit ein oder mehrere Tickets besitzen, um das Recht zur Nutzung von Hardware und Software zu haben. Die folgenden 7 Typen werden kollektiv als Anmeldeinformationen bezeichnet (weitere Typen können mit Iterationen hinzugefügt werden):
- Identitätsbezeichner (FayID)
- Konto / Passwort
- Zertifikat
- Autorisierung
- Zugriffstoken
- Smart Contract
- Digitaler Token ([MeriTokens](https://github.com/ChainModePilot/Global-Merit-Chain/wiki))

Hinweis: Anfänglich stammen alle diese Tickets vom Human-Prime-Nutzer. Für höhere Sicherheit und bequemere Verwaltung werden alle Anmeldeinformationen des Human Prime gegen Kopien ausgetauscht, die den Originalen entsprechen. iFay verwendet diese Kopien für Login und Authentifizierung.

Natürlich gehen wir nicht davon aus, dass iFay keine eigenen Anmeldeinformationen besitzen kann, die der Human Prime nicht verwenden kann. Daher gibt jeder Anmeldeinformationstyp an, ob sein ursprünglicher Eigentümer der Human Prime oder iFay selbst ist.

Zum Beispiel: Wenn wir die Authentizität persönlicher Informationen einer Person verifizieren müssen, könnten wir iFay autorisieren, sich direkt in eine Datenbank einzuloggen, um abzufragen. Um private Datenlecks zu verhindern, muss iFay nur zurückmelden, ob es wahr oder falsch ist.

### 3. Ego-Perspektive-Tracker
Um iFay zu ermöglichen, direkt mit bestehender Software zu arbeiten — anstatt darauf zu warten, dass jede Anwendung für KI neu gestaltet wird — muss iFay mindestens visuelle und auditive Fähigkeiten haben.

Wir betonen visuelle Wahrnehmung gegenüber dem Parsen strukturierter Dokumente (wie HTML), weil viele Dokumentelemente für Menschen nicht wahrnehmbar sind. Versteckte Elemente, wie SEO-Keyword-Stuffing, fügen der Benutzererfahrung typischerweise keinen echten Wert hinzu.

Durch die Abstimmung seiner sensorischen Wahrnehmung mit dem Human Prime kann iFay Urteile und Entscheidungen treffen, die eng mit der menschlichen Absicht übereinstimmen.

Die zentrale Herausforderung ist die Erreichung der Hand-Auge-Koordination für iFay. Visuelle und auditive Wahrnehmung müssen über die passive Verarbeitung von Software-Feedback hinausgehen — iFay muss auch Änderungen verfolgen, die durch seine eigenen Operationen verursacht werden.

Zum Beispiel muss es Cursorbewegungen verfolgen, neu freigegebene Bereiche nach Fensterbewegungen erkennen und sich an dynamische Oberflächenänderungen anpassen. Dies erfordert eine enge Kopplung zwischen Ego-Perspektive-Tracking und simulierter Interaktion, um sicherzustellen, dass iFay die Umgebung wie ein menschlicher Bediener wahrnimmt und darauf reagiert.

### 4. Simulierte Bedienung
Hier beziehen wir uns speziell auf die Simulation menschlicher Interaktion mit UIs. iFay klickt nicht nur — es kann ziehen, scrollen, Randgesten oder Mehrfingergesten ausführen, abhängig von den Oberflächenkomponenten.

Die zentrale Herausforderung ist, dass die Anpassung von Bedienungssequenzen für jede Oberfläche nicht machbar ist. Stattdessen muss iFays simulierte Interaktion auch die menschliche Erkundung von Oberflächen simulieren, wobei Feedback vom Ego-Perspektive-Tracking verwendet wird, um zu bestimmen, welche Operationen machbar oder effektiv sind. Dieser Ansatz unterscheidet sich grundlegend von traditionellen RPA-Implementierungen, die auf vordefinierten Skripten basieren, anstatt auf adaptiver, wahrnehmungsgesteuerter Erkundung.

### 5. Ego-Modell
Wir nennen es **[Ego](https://github.com/ChainModePilot/Ego/wiki)** und betonen, dass es kein großes AGI-Modell ist. Ego stimmt mit dem Profil einer bestimmten Person oder Rolle überein.

Viele supergroße Modelle, die AGI anstreben, haben eine zentrale Einschränkung: Egal wie umfangreich ihr Wissen und ihre Fähigkeiten sind, sie können nicht die einzigartigen Präferenzen und den Kontext jeder Person oder jedes Szenarios vollständig befriedigen.

Ego bietet ein Basisparadigma, das (aber nicht beschränkt auf) die folgenden Dimensionen einschränkt:
- Wertorientierung
- Interessenpräferenzen
- Gewohnheiten
- Kognitive Grenzen
- Skill-Grenzen
- Berechtigungsgrenzen
- Arbeitsstil

Es ist wichtig zu beachten, dass die Einbettung des Ego-Modells iFay nicht daran hindert, externe Skills oder andere große Modelle zu nutzen. Die Entscheidung, ein internes Mikromodell einzubeziehen, basiert auf zwei Überlegungen:
1. _**Offline-Gerätesteuerung**_: In Szenarien, in denen Endgeräte nicht mit dem Internet verbunden sind, unterstützt das eingebettete Mikromodell die lokale Nahfeldgerätesteuerung.
2. _**Persönlichkeitsstabilität**_: Verhindert plötzliche Persönlichkeitsänderungen bei iFay durch Updates großer Modelle oder absichtliche Manipulation und stellt sicher, dass Ego konsistent bleibt.

<br>

---

## 2️⃣ Phase 2: Direkte Client-Übernahme
Während KI, die UI-Operationen simuliert, die Effizienz verbessert, haben visuelle Oberflächen immer noch Einschränkungen:

- _**Informationsverlust**_: Begrenzte Ansichten und statische Elemente behindern effektive Kommunikation.
- _**Hohe Lernkosten**_: Inkonsistente Oberflächen verschiedener Anbieter zwingen Nutzer, mehrere Interaktionsmuster zu erlernen.
- _**Oberflächenstarrheit**_: Sobald Hardware/Software eine UI gestaltet, ist sie für die aktuelle Version fixiert. Nutzer müssen Oberflächen neu erlernen, wenn sie verschiedene Geräte oder Anwendungen verwenden.
- _**Niedrige Informationsübertragungseffizienz**_: Absicht muss erst in eine visuelle Oberfläche übersetzt und dann durch Nutzeroperationen an die Maschine zurückgemeldet werden.
- _**Hohe Entwicklungskosten**_: Der Aufbau funktionaler UIs erfordert interdisziplinäre Koordination (z.B. Produktmanager, UI/UE-Designer, Frontend-Entwickler).

![Phase 2 Konzept](./illustration/phase2-concept.png)

Im Gegensatz dazu kann iFay, wenn Endgeräte Client-Protokolle unterstützen (wie oben gezeigt), Hardware und Software direkt steuern. Dieser Ansatz adressiert alle fünf Probleme:
- _**Unbegrenzte Ausgabe**_: Informationen sind nicht mehr durch UI-Anzeigebeschränkungen eingeschränkt.
- _**Absichtsbasierte Interaktion**_: Nutzer drücken Absicht aus, iFay übersetzt sie in API-Aufrufe oder Befehle.
- _**Reiche Daten, prägnante Lieferung**_: Terminals können reichhaltige strukturierte Daten ausgeben, iFay filtert und fasst sie zu klaren Essentials zusammen.
- _**Direkte Übertragung**_: Kein visuelles Rendering nötig, ermöglicht effizienteren Datenfluss.
- _**Kein Frontend nötig**_: UI-Design und -Entwicklung können minimiert oder eliminiert werden.

Ich habe zwei Protokolle definiert, die auf Terminals anwendbar sind:
- [CAP (Control Authority Protocol)](https://github.com/ChainModePilot/Control-Authority-Protocol/wiki): Zum Inhabiten von Endgerät-Hardware und bestimmter Software, direktes Aufrufen von Treibern, lokalen Schnittstellen und Befehlen, damit iFay Terminals steuern kann.
- [DTP (Data Tunnel Protocol)](https://github.com/ChainModePilot/Data-Tunnel-Protocol/wiki): Ein bidirektionales Übertragungsprotokoll:
  - _**Terminal → iFay**_: Persistente Benutzerdatenspeicherung und Datenverwahrung.
  - _**iFay → Terminal**_: Datenanreicherung und personalisierte Verarbeitung.

Im Diagramm unten entsprechen die blauen Abschnitte diesen beiden Protokollen, die auf Gerätefunktionalität bzw. Daten abzielen.

![Phase 2: Direkte Client-Übernahme](./illustration/phase2-architecture.png)

Im Vergleich zu [Phase 1](./04-Roadmap#1️⃣-phase-1-simulation-menschlicher-bedienung) fügt iFay fünf neue interne Module hinzu, beginnend mit:

<br>

### Wahrnehmung → Sensor
Der Sensor muss auf dem CAP (Control Authority Protocol) und DTP (Data Tunnel Protocol) implementiert werden. Er dient als Brücke zu Endgerät-Sensoren und empfängt Datenströme aus der externen Umgebung — deshalb nennen wir ihn iFays Nervensystem.

Entscheidend ist, dass iFay nicht alle eingehenden Daten jederzeit verarbeiten muss. Der Sensor kann seine Empfindlichkeit dynamisch anpassen, um besser zum umgebenden Kontext zu passen.

Betrachte den Sensor als einen Empfindlichkeitsregler. Die tatsächlichen Schnittstellen zur Außenwelt werden vom Gerätetreiber-Hub und dem Persönlichen Datenspeicher verwaltet.

<br>

### Skills → Gerätetreiber-Hub
Zur Klarstellung: Dies ist kein einzelner Gerätetreiber und auch keine Sammlung von Treibern.

Er fungiert als Treiber-Hub-Schicht und stellt sicher, dass bei der kontinuierlichen Integration neuer Gerätetreiber iFays interne Architektur stabil bleibt, ohne bei jedem Update modifiziert werden zu müssen.

<br>

### Skills → Registrierte Skills
Registrierung ist eine Voraussetzung für jede iFay-Aktion.

Wenn ein Skill bei iFay registriert ist, bedeutet das, dass iFay ihn jederzeit aufrufen kann. Registrierung ist nicht nur einfache Aufzeichnung — sie dient typischerweise als Vorautorisierungsschritt, der sicherstellt, dass während der Ausführung keine zusätzliche Authentifizierung benötigt wird, wodurch die Latenz reduziert wird.

Ein weiterer wichtiger Vorteil ist die Offline-Resilienz: Wenn iFay offline ist, kann es ausstehende Aktionen zwischenspeichern und sie asynchron ausführen, wenn die Konnektivität wiederhergestellt ist.

<br>

### Denken → Persönlicher Datenspeicher
Diese Komponente ist für die einheitliche Verwaltung aller privaten Daten von iFay verantwortlich. Sie unterstützt mehrere Speicherformate und -orte — zum Beispiel können einige Daten im Laufzeitspeicher von iFay liegen, einige in Google Drive und einige in einer dedizierten Vektordatenbank.

Aus iFays interner Perspektive muss es nur aus dem Datenspeicher lesen und in ihn schreiben, ohne sich darum zu kümmern, wo oder wie Daten physisch gespeichert sind.

<br>

### Aktion → Skill-Aufruf
Dies ist iFays primäre Aktion — im Wesentlichen kannst du es dir als ein Aufrufverhalten vorstellen.

<br>

---

## 3️⃣ Phase 3: iFay als Schnittstelle zur virtuellen Welt

Wenn iFay den Client inhabitet, entwickelt sich die Client-Server (C/S)-Architektur zu einem Client-Fay-Server (C/F/S)-Modell.
Nutzer müssen nicht mehr manuell Clients bedienen, um auf Backend-Dienste zuzugreifen — stattdessen kann iFay offene Dienste im Internet direkt erfassen und nutzen.

![Phase 3 Konzept](./illustration/phase3-concept.png)

Um dies zu erreichen, sollten Dienste und Schnittstellen, die zuvor nur für Clients offen waren, über ein standardisiertes Remote-Protokoll netzwerkweit verfügbar gemacht werden.

Dieses Remote-Protokoll ist das [SSP (Skill Sharing Protocol)](https://github.com/ChainModePilot/Skill-Sharing-Protocol/wiki), das im Diagramm unten gezeigt wird.

![Phase 3: iFay als Schnittstelle zur virtuellen Welt](./illustration/phase3-architecture.png)

Wie gezeigt, steuert iFay sowohl die Client-Seite (Edge-Geräte) als auch die Server-Seite (oder Cloud-Dienste).

Der Human Prime muss nur mit seiner eigenen iFay kommunizieren, und iFay ruft dann die erforderlichen Dienste basierend auf der Absicht des Prime auf.

Da die Oberfläche, über die der Human Prime Informationen betrachtet, von iFay zusammengestellt und gerendert wird, spielt sie effektiv die Rolle eines Browsers.

Da die Kernmotivation für die Einführung von iFay darin besteht, sie zu einer intelligenten Erweiterung jenseits des Human Prime zu machen, werden ihre erweiterten Fähigkeiten durch Registrierte Skills erreicht.
Im Denkbereich führen wir das folgende Modul ein:

<br>

### Denken → Externes Wissen

Aus Implementierungsperspektive behandeln wir externe Wissensdatenbanken und Modelle als einen Skill-Typ, der es iFay ermöglicht, auf externe Intelligenz zuzugreifen, wie das Konsultieren eines Wissenshubs oder Expertenberaters.
Wissen und Informationen, die durch diesen Skill erworben werden, werden zusammen mit iFays persönlichen Daten verwaltet und erreichen letztendlich eine Intelligenz, die die eigenen Fähigkeiten des Human Prime übersteigt.

<br>

---

## 4️⃣ Phase 4: iFay + coFay — Vollständige Personifizierung von Software

In dieser Phase ist die Verkörperung von Fay im Wesentlichen abgeschlossen.
Allerdings fehlt ihnen noch die Fähigkeit, wie echte Mitglieder der Gesellschaft autonom zu handeln.
Damit iFay unabhängig und effektiv operieren kann, müssen 2 Schlüsselbedingungen erfüllt sein:
- Intern: iFay muss selbstgesteuerte Motivation entwickeln — eine kontinuierliche „Aktion → Feedback → Re-Aktion"-Schleife.
- Extern: iFay und coFay müssen weit verbreitet sein und in der Lage sein, eine gemeinsame Sprache zu verwenden.
Mit dieser Grundlage kann iFay mit Menschen, anderen iFays oder ihren dedizierten coFays zusammenarbeiten, um vordefinierte Aufgaben autonom auszuführen.

![Phase 4 Konzept](./illustration/phase4-concept.png)

Um dies zu erreichen, müssen wir selbstgesteuerte Fähigkeiten in vier Kernmodulen einbetten — Wahrnehmung, Aktion, Skills und Denken.

<br>

### Wahrnehmung → Selbstwahrnehmung
Ein wirklich lebendes Wesen nimmt nicht nur wahr — es fühlt auch.
Im Gegensatz zu Maschinen kann iFay selbst keine echten Emotionen haben. Aber durch die Beobachtung seines Human Prime und des umgebenden Kontexts kann es Gefühle aus der Wahrnehmung ableiten.
Dies ist die Kernstrategie zum Aufbau von iFays Selbstwahrnehmung.

<br>

### Aktion → Selbstgesteuertes Verhalten
Da iFay Aufgaben autonom bewältigen muss, muss es eigene Verhaltensauslösemechanismen haben.
Diese Auslöser können kommen von:
- Geplanten Aufgaben
- Selbstwahrnehmungs-Inferenz
- Persistenten Skills, einschließlich Registrierter Skills und Interner Skills.

<br>

### Skills → Interne Skills
Wir führen das Modul Interne Skills für drei Hauptzwecke ein:
- Gewohnheiten etablieren, die mit der Persönlichkeit des Human Prime übereinstimmen, einschließlich potenzieller Einschränkungen oder Governance über externe Skills.
- Einen Introspektionsmechanismus bereitstellen, um sicherzustellen, dass externes Wissen niemals mit der Absicht des Human Prime in Konflikt steht.
- Feste Prime-spezifische Fähigkeiten einbetten, wie professionelle Skills und Expertise.

<br>

### Denken → Ausgerichtetes Bewusstsein
Im Wesentlichen repräsentiert dies eine vollständige Beschreibung des persönlichen Profils des Human Prime.
Es kann durch drei Hauptmethoden (möglicherweise mehr) etabliert werden:
- Mining von Daten aus dem Persönlichen Datenspeicher.
- Echtzeitanpassung durch Selbstwahrnehmung.
- Manuelle Definition durch den Human Prime.

<br>

![Phase 4: iFay + coFay — Vollständige Personifizierung von Software](./illustration/phase4-architecture.png)

Allerdings reicht dies allein nicht aus, damit iFay sich in soziale Beziehungen integrieren kann.
Dafür müssen wir iFay mit Kommunikationsfähigkeiten ausstatten, die zwei Kernprotokolle umfassen:
- [Telepathie-Protokoll](https://github.com/ChainModePilot/Telepathy-Protocol/wiki) — Ein Fay-freundliches semantisches Kommunikationsprotokoll, das die UI-Übersetzungsschicht entfernt und es ermöglicht, Bedeutung und Absicht direkt zwischen iFay und coFay zu übertragen. Es verwendet vereinbarte vektorkodierte Token anstelle von strukturiertem Text.
- [Interaktives Konversationsprotokoll](https://github.com/ChainModePilot/Interactive-Conversation-Protocol/wiki) — Ein menschliches UI-freundliches Protokoll, das semantische Inhalte modularisiert und multimodalisiert, damit Client-Oberflächen lesbare, benutzerfreundliche Nachrichtenanzeigen rekonstruieren können.

<br>

---

## 5️⃣ Phase 5: Fay gestaltet Arbeitsstruktur und Wertverteilung neu

Letztendlich ist unser Ziel, ein Ökosystem mit starken sozialen Attributen aufzubauen, anstatt KI als ein fortschrittlicheres Werkzeug zu behandeln.
Diese neue soziale Form wird sich unweigerlich von der menschlichen Gesellschaft unterscheiden, wie wir sie heute kennen.
Wir können mindestens 5 grundlegende Verschiebungen vorhersehen:
1. _**Ausstieg menschlicher Arbeit**_ — Programmatische Arbeit wird vollständig von KI und Robotern übernommen, was die Personalkosten gegen Null treibt.
2. _**Wissensverflachung**_ — Professionelles Wissen und Expertise werden durch KI angeglichen, was Lieferketten extrem flach macht.
3. _**Universelle Existenzgarantie**_ — Jeder wird Zugang zu grundlegenden Lebensressourcen haben, wodurch die Notwendigkeit entfällt, für das Überleben zu arbeiten.
4. _**Neue Wertschöpfung**_ — Menschliche Beteiligung wird sich auf Sinnschöpfung, menschenzentriertes Handwerk und das KI + Roboter-Produktionsökosystem konzentrieren.
5. _**Neue soziale Schichtung**_ — Der Besitz autonomer Produktionsressourcen wird zum neuen Treiber von Wohlstand und Klassendifferenzierung.

Dies wird das auf dem Besitz materieller Ressourcen (d.h. Produktionsmittel) aufgebaute wirtschaftliche Ökosystem grundlegend umgestalten.
Aus wirtschaftlicher Perspektive werden 2 große Verschiebungen eintreten:
- _**Minimierte menschliche Beteiligung an der Realwirtschaft**_ — Sehr wenige Menschen werden direkt an traditionellen Produktionsaktivitäten teilnehmen.
- _**Dramatischer Anstieg des Einheitswerts menschlicher Arbeit**_ — Wenn menschliche Arbeit nicht hoch geschätzt wird, werden sich Menschen vollständig aus der physischen Arbeit zurückziehen.

Wenn die meisten Menschen in virtuelle Arbeit eingetaucht sind, werden traditionelle Wertmetriken — wie Arbeitsstunden, monetäres Einkommen oder physische Gütermengen — unzureichend.
Daher erfordert die Messung sozialen Werts einen Konsensmechanismus, ähnlich wie Auktionen den Wert von Kunst oder Aktien bestimmen. Auktionen sind nur eine Möglichkeit, Konsens herzustellen.

Um diesen Konsens aufrechtzuerhalten, wird eine dedizierte Plattform benötigt. Derzeit ist Blockchain eine geeignete Wahl mit jahrelanger gesammelter Erfahrung.

Wir quantifizieren soziale Beiträge in einer einheitlichen Einheit (μ, Merit Unit) und geben entsprechende digitale Token (MeriToken) auf der Blockchain aus, was wir die [Global Merit Chain](https://github.com/ChainModePilot/Global-Merit-Chain) nennen.

In Zukunft wird der Erwerb von MeriTokens nicht davon abhängen, Rechenleistung für technische Blockchain-Arbeit zu verbrauchen, sondern davon, sozialen Wert zu schaffen.

![Phase 5 Konzept](./illustration/phase5-concept.png)
