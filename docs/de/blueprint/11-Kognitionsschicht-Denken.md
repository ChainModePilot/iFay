# 11. Kognitionsschicht — Denken

Das Denksubsystem der Kognitionsschicht ist iFays „Gedächtnis- und Verständniszentrum“ — es verwaltet iFays Gedächtnis, erwirbt externes Wissen und pflegt ein tiefes Verständnis von dir.


---

## 11.1 Persönlicher Datenspeicher

## Einzeilige Definition

Der Persönliche Datenspeicher ist iFays **Gedächtnis** — deine Fotos, Chat-Protokolle, Arbeitsdokumente, Gesundheitsdaten… verstreut über Handys, Computer und Cloud-Speicher. Der Persönliche Datenspeicher vereinheitlicht ihre Verwaltung und ermöglicht iFay, sich jederzeit an jeden Moment der Vergangenheit zu „erinnern".

## Warum er benötigt wird

Dein digitales Leben ist über ein Dutzend verschiedene Orte verstreut. Wenn iFay dein digitaler Avatar werden soll, muss sie sich an alles über dich „erinnern" können — aber sie kann nicht verlangen, dass du alle Daten an einen Ort verschiebst. Die Lösung des Persönlichen Datenspeichers: **Daten bleiben wo sie sind, aber iFay liest und schreibt sie alle über eine einheitliche Schnittstelle**.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht
│   ├── Wahrnehmung
│   │   ├── Sensor              ← Sensordaten fließen in den Datenspeicher
│   │   └── ...
│   └── Aktion
├── Kognitionsschicht          ← Persönlicher Datenspeicher ist hier
│   ├── Denken
│   │   ├── 👉 Persönlicher Datenspeicher    ← Gedächtnis: einheitliche Verwaltung aller privaten Daten
│   │   ├── Externes Wissen                   ← Externes Wissen wird auch hier gespeichert
│   │   └── Ausgerichtetes Bewusstsein        ← Schürft Human-Prime-Profil aus dem Datenspeicher
│   └── Skills
└── Ego-Schicht
```

## Funktionsweise

**1. Einheitlich — Eine Schnittstelle für alle Daten** — Deine Fotos auf iCloud, Dokumente auf Google Drive, Chat-Protokolle lokal — der Persönliche Datenspeicher bietet eine **einheitliche Lese-/Schreibschnittstelle**.

**2. Klassifiziert — Vier Datentypen**
- **Content**: Dinge, die du erstellst — Fotos, Videos, Artikel, Notizen, Code
- **Data**: Strukturierte Informationen — Gesundheitsdaten, Finanzaufzeichnungen, Standortverlauf
- **Knowledge Base**: Organisiertes Wissen — professionelle Notizen, Lernmaterialien
- **Info Feed**: Kontinuierlich aktualisierte Informationen — Nachrichtenabonnements, Social-Media-Feeds

**3. Persistent — Sichere Datenverwahrung** — Durch **DTP (Data Tunnel Protocol)** handhabt der Persönliche Datenspeicher persistente Speicherung und Verwahrung von Daten.

**4. Angereichert — Rohdaten wertvoller machen** — Kann Korrelationen generieren, z.B. Gesundheitsdaten mit Zeitplandaten verbinden, um personalisierte Erkenntnisse zu erzeugen.

## Szenario-Geschichten

### Szenario 1: Restaurant von vor drei Jahren finden

Du erinnerst dich an ein Restaurant in Hangzhou vor drei Jahren, hast aber den Namen vergessen. iFay durchsucht den Persönlichen Datenspeicher: Standortverlauf, Fotos, Chat-Protokolle — und findet „Hangzhou Geschmack · West-Lake-Filiale" durch Kreuzvalidierung über Datenquellen hinweg.

### Szenario 2: Angereicherte Erkenntnisse aus Gesundheitsdaten

iFay korreliert Schlafdaten, Herzfrequenz, Kalender und Handynutzung: „In den letzten zwei Wochen ist deine durchschnittliche Schlafzeit von 7,5 auf 6,2 Stunden gesunken. Ich bemerke viele Abendmeetings in deinem Kalender. Vorschlag: Soll ich alle Meetings nach 22 Uhr auf den nächsten Tag verschieben?"

## Für Entwickler

Der Persönliche Datenspeicher gehört zu **Phase 2 (Direkte Client-Übernahme)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 11 (Persönlicher Datenspeicher)
- **Schnittstellenspezifikation**: `PersonalDataHeap`-Schnittstelle mit vier Kernmethoden: `read()`, `write()`, `enrich()`, und `persist()`
- **Unterstützte Speicherorte**: `runtime_memory`, `cloud`, `vector_db`, `local`
- **Zugehöriges Protokoll**: DTP (Data Tunnel Protocol)
- **Konformitätstests**: iFACTS L1 validiert Lese-/Schreibfähigkeiten für alle vier Datentypen; L2 validiert Datenschnittstellen; L3 validiert die vollständige Kette


---

## 11.2 Externes Wissen

## Einzeilige Definition

Externes Wissen ist iFays **Bibliothek und Expertenberater** — der Persönliche Datenspeicher ist iFays eigenes Gedächtnis, während Externes Wissen die Bibliothek ist, die iFay konsultieren kann, und die Experten, die sie fragen kann. Es gibt iFay Wissen jenseits der eigenen Fähigkeiten des Human Prime.

## Warum es benötigt wird

Egal wie gut dein Gedächtnis ist, du kannst dir nicht alles merken. iFay funktioniert genauso. Das Modul Externes Wissen lässt iFay **über ihr eigenes Gedächtnis hinausgehen**, um externe Wissensdatenbanken zu konsultieren und externe intelligente Modelle abzufragen.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht
├── Kognitionsschicht          ← Externes Wissen ist hier
│   ├── Denken
│   │   ├── Persönlicher Datenspeicher      ← Dein eigenes Gedächtnis
│   │   ├── 👉 Externes Wissen              ← Bibliothek und Expertenberater
│   │   └── Ausgerichtetes Bewusstsein
│   └── Skills
│       ├── Registrierte Skills         ← Externe Wissensquellen sind auch ein „Skill"-Typ
│       └── ...
└── Ego-Schicht
```

Externe Wissensquellen werden als **Skill-Typ** innerhalb von iFays System behandelt. Die Beziehung zwischen Externem Wissen und dem Persönlichen Datenspeicher ist wie „Bibliothek" und „persönliches Notizbuch": Informationen, die iFay aus externen Quellen erwirbt, werden in den Persönlichen Datenspeicher integriert.

## Funktionsweise

**1. Verbinden — Externe Wissensquellen anbinden** — Wissensdatenbanken, große Sprachmodelle, Expertensysteme, Suchmaschinen — verbunden über **SSP (Skill Sharing Protocol)**.

**2. Abfragen — Wie einen Experten konsultieren** — Jedes Abfrageergebnis kommt mit einem Konfidenzwert. iFay kann Antworten aus mehreren Quellen synthetisieren.

**3. Integrieren — Gelerntes Wissen wird eigenes** — Wichtiges Wissen wird in den Persönlichen Datenspeicher integriert.

**Wenn eine Wissensquelle nicht verfügbar ist?** Das Modul Externes Wissen **fällt auf zwischengespeichertes Wissen im Persönlichen Datenspeicher zurück** und benachrichtigt die Kognitionsschicht.

## Szenario-Geschichten

### Szenario 1: Gesundheitsbericht verstehen helfen

Du erhältst deinen Gesundheitsbericht mit unverständlichen Indikatoren. iFay ruft deine historischen Daten aus dem Persönlichen Datenspeicher ab, fragt dann eine externe medizinische Wissensdatenbank ab und gibt dir personalisierte Gesundheitsratschläge.

### Szenario 2: Vertragsklauseln entwerfen helfen

Du brauchst eine Vertragsbruchklausel. iFay fragt eine juristische Wissensdatenbank ab, referenziert deine früheren Verträge und erstellt einen Entwurf — mit dem Hinweis: „Dies ist ein Entwurf aus der juristischen Wissensdatenbank. Ich empfehle eine Überprüfung durch einen Fachanwalt vor der formellen Unterzeichnung."

## Für Entwickler

Externes Wissen gehört zu **Phase 3 (iFay als Schnittstelle zur virtuellen Welt)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 12 (Externes Wissen Integration)
- **Schnittstellenspezifikation**: `ExternalKnowledge`-Schnittstelle mit drei Kernmethoden: `query()`, `registerSource()`, und `fallbackToCache()`
- **Wissensquellentypen**: `knowledge_base`, `llm`, `expert_system`, `search_engine`
- **Zugehöriges Protokoll**: SSP (Skill Sharing Protocol)
- **Konformitätstests**: iFACTS L1 validiert Wissensabfrage und Cache-Fallback; L2 validiert Wissensintegration mit Persönlichem Datenspeicher; L3 validiert die vollständige Kette


---

## 11.3 Ausgerichtetes Bewusstsein

## Einzeilige Definition

Ausgerichtetes Bewusstsein ist iFays **vollständiges Verständnis von dir** — wenn das Ego-Modell iFays „Persönlichkeit" ist, dann ist Ausgerichtetes Bewusstsein iFays tiefe Kognition von dir als Person — deine Werte, Präferenzen, Gewohnheiten und Grenzen. Es ist die Baseline für alles Verhalten von iFay.

## Warum es benötigt wird

Jede Aktion, die iFay unternimmt, braucht eine „Baseline" zur Beurteilung: Soll das getan werden? Wie soll es getan werden? In welchem Ausmaß? Diese Baseline ist das Human-Prime-Profil, das vom Ausgerichteten Bewusstsein bereitgestellt wird.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht
│   ├── Wahrnehmung
│   │   └── Selbstwahrnehmung         ← Beobachtet dich in Echtzeit → aktualisiert Ausgerichtetes Bewusstsein
│   └── Aktion
├── Kognitionsschicht          ← Ausgerichtetes Bewusstsein ist hier
│   ├── Denken
│   │   ├── Persönlicher Datenspeicher      ← Schürft Daten von hier, um dich zu verstehen
│   │   ├── Externes Wissen
│   │   └── 👉 Ausgerichtetes Bewusstsein    ← Vollständiges Verständnis von dir
│   └── Skills
│       └── Interne Skills          ← Verwendet Ausgerichtetes Bewusstsein zur Verhaltenseinschränkung
└── Ego-Schicht
    └── Ego-Modell                   ← Ausgerichtetes Bewusstsein ist Input für Ego
```

## Funktionsweise — Drei Aktualisierungsmethoden

Das Human-Prime-Profil enthält: **Wertorientierung, Interessenpräferenzen, Gewohnheitsmuster, kognitive Grenzen, Skill-Grenzen, Berechtigungsgrenzen und Arbeitsstil**.

**1. Data Mining — Dich aus deinen Daten verstehen** — Analysiert Verhaltensmuster aus dem Persönlichen Datenspeicher. Passiv und kontinuierlich.

**2. Echtzeitanpassung — Dich aus deinen Reaktionen lesen** — Das Selbstwahrnehmungsmodul beobachtet deine Reaktionen in Echtzeit. Aktiv und unmittelbar.

**3. Manuelle Definition — Du sagst iFay direkt** — „Ich will keine Meetings vor 10 Uhr." Explizit und unmittelbar.

Die drei Methoden ergänzen sich: Data Mining liefert langfristige Trends, Echtzeitanpassung erfasst unmittelbare Änderungen, und manuelle Definition setzt explizite Grenzen.

## Szenario-Geschichten

### Szenario 1: Entdeckung, dass du Vegetarier geworden bist

Über drei Monate analysiert Ausgerichtetes Bewusstsein deine Essensbestellungen: Fleischanteil sank von 70% auf 0%. Aktualisiert dein Profil: **Ernährungspräferenz hat sich zu vegetarisch verschoben**. Dieses Update beeinflusst sofort iFays Verhalten bei Restaurantempfehlungen, Reiseplanung und Essenseinladungen.

### Szenario 2: Du sagst iFay direkt eine Regel

„Ab jetzt keine Meetings vor 10 Uhr." Ausgerichtetes Bewusstsein aktualisiert sofort dein Profil. Die Auswirkung ist unmittelbar: Wenn jemand ein 9-Uhr-Meeting buchen will, antwortet iFay: „XX ist vor 10 Uhr nicht verfügbar."

## Für Entwickler

Ausgerichtetes Bewusstsein gehört zu **Phase 4 (iFay + coFay Vollständige Personifizierung)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 16 (Ausgerichtetes Bewusstsein)
- **Schnittstellenspezifikation**: `AlignedConsciousness`-Schnittstelle mit vier Kernmethoden: `getProfile()`, `mineFromDataHeap()`, `adjustFromAwareness()`, und `manualUpdate()`
- **Profildimensionen**: `values`, `preferences`, `habits`, `cognitiveBoundaries`, `skillBoundaries`, `permissionBoundaries`, `workingStyle`
- **Konformitätstests**: iFACTS L1 validiert drei Profil-Aktualisierungsmethoden; L2 validiert Profillieferungsschnittstellen; L4 validiert tatsächliche Auswirkung auf Verhaltenseinschränkungen
