# 12. Kognitionsschicht — Skills

Das Skills-Subsystem der Kognitionsschicht ist iFays „Fähigkeitsbibliothek“ — es verwaltet Hardware-Treiber, extern registrierte Skills und inhärente Fähigkeiten.


---

## 12.1 Gerätetreiber-Hub

## Einzeilige Definition

Der Gerätetreiber-Hub ist iFays **motorische Nerven** — wenn Hardware iFays „Gliedmaßen" ist, dann ist der Gerätetreiber-Hub das motorische Nervensystem, das das Gehirn mit den Gliedmaßen verbindet. Er stellt sicher, dass iFay verschiedene Hardware-Geräte korrekt steuern kann und dass neue Geräte verbunden werden können, ohne „neu laufen lernen" zu müssen.

## Warum er benötigt wird

Smart-Lampen, Klimaanlagen, Vorhänge, Saugroboter, Drohnen… jedes Gerät hat seine eigene „Sprache" und Steuerungsmethode. Wenn iFay bei jeder neuen Geräteverbindung ihre Interna umstrukturieren müsste, wäre das so absurd wie bei jeder neuen Bewegung neu laufen lernen zu müssen.

Der Gerätetreiber-Hub ist eine **Hub-Schicht**, kein spezifisches Treiberprogramm oder eine einfache Sammlung von Treibern. Er bietet eine standardisierte Schnittstelle, die es jedem neuen Gerätetreiber ermöglicht, nahtlos einzustecken, während iFays andere Module von der Änderung völlig unberührt bleiben.

## Funktionsweise

**1. Standardisiert — Einheitlicher Schnittstellenvertrag** — Jeder Gerätetreiber muss derselben Schnittstellenspezifikation folgen: Treiber registrieren, Gerät aufrufen, Status abfragen.

**2. Transparent — Vollständig transparent für andere Module** — Wenn ein neuer Gerätetreiber hinzugefügt wird, brauchen andere Module keine Modifikationen.

**3. Graceful Degradation — Treiberausfall lässt iFay nicht abstürzen** — Meldet den nicht verfügbaren Status, bietet Degradationsvorschläge, andere Geräte bleiben unberührt.

## Szenario-Geschichten

### Szenario 1: Smart Home steuern

Du sagst: „Stelle mein Zuhause auf Kinomodus." iFay steuert gleichzeitig über den Gerätetreiber-Hub: Smart-Lampe dimmen, Klimaanlage auf leise, Vorhänge schließen, Projektor einschalten — vier Geräte verschiedener Marken, verschiedener Protokolle, aber iFay gibt einfach vier standardisierte Befehle.

### Szenario 2: Neuer Saugroboter — Plug and Play

Du kaufst einen neuen Saugroboter. Nach der Netzwerkverbindung entdeckt iFay die neue Hardware, der Gerätetreiber-Hub lädt automatisch den Treiber. Am nächsten Morgen startet iFay den Saugroboter, wenn du zur Arbeit gehst — ohne jegliche Konfiguration deinerseits.

## Für Entwickler

Der Gerätetreiber-Hub gehört zu **Phase 2 (Direkte Client-Übernahme)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 8 (Gerätetreiber-Hub)
- **Schnittstellenspezifikation**: `DeviceDriverHub`-Schnittstelle mit vier Kernmethoden: `registerDriver()`, `invokeDevice()`, `getDriverStatus()`, und `unregisterDriver()`
- **Treiberzustände**: `loaded`, `active`, `error`, `unavailable`
- **Zugehöriges Protokoll**: CAP (Control Authority Protocol)
- **Konformitätstests**: iFACTS L1 validiert Treiberregistrierung und -aufruf; L2 validiert Schnittstellenintegration; L4 validiert Degradationsverhalten bei Treiberausfall


---

## 12.2 Registrierte Skills

✅ „Registrierte Skills" bezieht sich auf einen Skill, den iFay bereits beherrscht oder die Fähigkeit zur Nutzung erlangt hat.

❌ Es bedeutet nicht, ein Konto in einem externen System zu registrieren oder zu erstellen.

## Einzeilige Definition

Registrierte Skills sind iFays **Skill-Zertifizierung** — genau wie Menschen einen Führerschein zum Fahren oder eine Approbation zum Praktizieren brauchen, muss iFay einen Skill „registrieren", bevor sie ihn nutzen kann. Registrierung ist nicht nur Aufzeichnung — es ist Vorautorisierung, die sicherstellt, dass zur Ausführungszeit keine zusätzliche Authentifizierung benötigt wird.

## Warum sie benötigt werden

Die Registrierung ist wie das Erhalten einer Zertifizierung: Fähigkeit bestätigen, Vorautorisierung abschließen, auf Datei aufzeichnen. Vorautorisierung stellt sicher, dass iFay **sofort handeln** kann, ohne Verzögerungen durch Authentifizierungsprozesse.

iFay unterstützt sechs Skill-Typen: **API, Workflow, Bot, Agent, APP, Microservice**. Unabhängig vom Typ ist Registrierung die Voraussetzung für die Nutzung.

## Funktionsweise

**1. Registrieren — Skill „Onboarding"** — Schlüsselinformationen aufzeichnen: Name, Typ, Zugriffsendpunkt, Authentifizierungsmethode, Fähigkeitsbeschreibung.

**2. Vorautorisieren — Den „Pass" im Voraus erhalten** — Alle Authentifizierungsschritte im Voraus abschließen — Zugriffstoken erhalten, sichere Verbindungen herstellen, Berechtigungen verifizieren.

**3. Zwischenspeichern — Funktioniert auch offline** — Wenn iFay offline ist, werden ausstehende Aktionen zwischengespeichert und bei Netzwerkwiederherstellung asynchron ausgeführt.

**4. Aktualisieren — Autorisierung gültig halten** — Periodisch den Autorisierungsstatus aktualisieren, um sicherzustellen, dass Berechtigungen beim Aufruf gültig sind.

## Szenario-Geschichten

### Szenario 1: Übersetzungs-API registrieren — Sofortige Antwort durch Vorautorisierung

Du registrierst einen professionellen Übersetzungs-API-Skill. Eine Woche später erhältst du eine japanische E-Mail — iFay ruft sofort die API auf, Ergebnis in zwei Sekunden. Kein Popup, kein Warten — alles wurde bei der Registrierung vorbereitet.

### Szenario 2: Offline-Zwischenspeicherung im Flugzeug

Im Flugzeug gibst du iFay drei Aufgaben. Das Modul Registrierte Skills speichert sie zwischen und sagt: „Verstanden. Ich erledige sie sofort nach der Landung." Nach der Landung werden alle drei Aktionen automatisch ausgeführt.

## Für Entwickler

Registrierte Skills gehören zu **Phase 2 (Direkte Client-Übernahme)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 9 (Registrierte Skills Verwaltung)
- **Schnittstellenspezifikation**: `RegisteredSkillManager`-Schnittstelle mit fünf Kernmethoden: `register()`, `query()`, `refreshAuthorization()`, `cacheOfflineAction()`, und `flushCachedActions()`
- **Sechs Skill-Typen**: `api`, `workflow`, `bot`, `agent`, `app`, `microservice`
- **Vorautorisierungszustände**: `pre_authorized`, `pending`, `expired`
- **Konformitätstests**: iFACTS L1 validiert Registrierung und Vorautorisierung für alle sechs Typen; L2 validiert Schnittstellenintegration; L3 validiert den End-to-End Offline-Caching-Flow


---

## 12.3 Interne Skills

## Einzeilige Definition

Interne Skills sind iFays **Intuition und Grundlinie** — Registrierte Skills sind Fähigkeiten, die iFay extern gelernt hat (wie erworbene Zertifizierungen), während Interne Skills Fähigkeiten sind, mit denen iFay geboren wurde (wie Intuition und moralische Grenzen). Sie stellen sicher, dass externe Skill-Ausgaben nicht gegen die Absicht des Human Prime verstoßen.

## Warum sie benötigt werden

Interne Skills erfüllen drei Aufgaben:

**Erstens** etablieren sie Gewohnheiten, die mit der Persönlichkeit des Human Prime übereinstimmen, einschließlich Governance über externe Skills — eine „Intuitionsprüfung" externer Skill-Ausgaben.

**Zweitens** bieten sie einen Introspektionsmechanismus, der sicherstellt, dass externes Wissen nicht mit der Absicht des Human Prime in Konflikt steht.

**Drittens** betten sie die spezifischen inhärenten Fähigkeiten des Human Prime ein — professionelle Skills und Expertise, die bei der Initialisierung eingebettet werden.

Registrierte Skills sind iFays „externe Kampfkünste", Interne Skills sind iFays „innere Kultivierung".

## Funktionsweise

**1. Governance — „Intuitionsprüfung" externer Skill-Ausgaben** — Prüft: Passt der Ton zum Human Prime? Verstößt das Ergebnis gegen Werte? Überschreitet es Grenzen? Bei Problemen abfangen und anpassen.

**2. Introspektion — Sicherstellen, dass externes Wissen iFay nicht „irreführt"** — Prüft: Steht dieses Wissen im Konflikt mit bestehender Kognition des Prime? Würde die Übernahme iFays Verhalten von der Absicht des Prime abweichen lassen?

**3. Befähigung — Professionelle Fähigkeiten des Human Prime einbetten** — Wenn du Finanzanalyst bist, besitzt deine iFay inhärent Finanzanalysefähigkeiten — kein extern registrierter Skill, sondern „Fachkompetenz".

## Szenario-Geschichten

### Szenario 1: Stilkorrektur von Übersetzungsergebnissen

Du bist CEO eines Tech-Unternehmens mit warmem aber professionellem Kommunikationsstil. Die Übersetzungs-API übersetzt zu direkt: „We need the report by Friday." Interne Skills greifen ein und passen an zu: „Would it be possible to have the report ready by Friday? That would be really helpful for our planning." — genau wie du es sagen würdest.

### Szenario 2: Inhärente Fähigkeiten eines Finanzanalysten

Deine iFay scannt einen Marktanalysebericht mit den in Internen Skills eingebetteten Finanzanalysefähigkeiten und bemerkt: Das DCF-Modell fehlt vergleichbare Unternehmensanalyse, Wachstumserwartungen sind zu optimistisch, Risikoabschnitt fehlt geopolitische Faktoren — alles basierend auf deiner professionellen Erfahrung.

## Für Entwickler

Interne Skills gehören zu **Phase 4 (iFay + coFay Vollständige Personifizierung)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 15 (Interne Skills)
- **Schnittstellenspezifikation**: `InternalSkill`-Schnittstelle mit drei Kernmethoden: `introspect()`, `intercept()`, und `getHostCapabilities()`
- **Drei Verantwortlichkeiten**: (1) Governance externer Skill-Ausgaben; (2) Introspektionsmechanismus; (3) Einbettung inhärenter Fähigkeiten des Human Prime
- **Konformitätstests**: iFACTS L1 validiert Introspektion und Abfangfähigkeiten; L2 validiert Ausgabe-Audit-Schnittstellen; L4 validiert ob Anpassungen dem Human-Prime-Profil entsprechen
