# 10. Interaktionsschicht — Aktion

Das Aktionssubsystem der Interaktionsschicht ist iFays „Effektoren“ — es lässt iFay Oberflächen bedienen, Dienste aufrufen und proaktiv handeln.


---

## 10.1 Simulierte Bedienung

## Einzeilige Definition

Simulierte Bedienung ist iFays **Hände** — sie kann wie ein Mensch klicken, ziehen, scrollen und tippen und jede bestehende Software-Oberfläche bedienen, ohne dass die Software KI-spezifische Modifikationen benötigt.

## Warum sie benötigt wird

Simulierte Bedienung lässt iFay dir **jetzt sofort** helfen, Dinge zu erledigen, ohne darauf zu warten, dass jede Software der Welt für KI neu gestaltet wird.

Aber Simulierte Bedienung unterscheidet sich grundlegend von traditionellen „Automatisierungsskripten" (wie RPA). RPA folgt einem vorgeschriebenen Skript Schritt für Schritt. iFays Simulierte Bedienung ist **wahrnehmungsgesteuert**: Sie „sieht" den Bildschirm durch den Ego-Perspektive-Tracker, versteht den aktuellen Oberflächenzustand und entscheidet dann, was als nächstes zu tun ist.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht          ← Simulierte Bedienung ist hier
│   ├── Wahrnehmung (Sense)
│   │   ├── Ego-Perspektive-Tracker   ← Augen: sieht den Bildschirm
│   │   ├── Sensor                     ← Nervensystem
│   │   └── Selbstwahrnehmung          ← Herz: liest deine Absicht
│   └── Aktion
│       ├── 👉 Simulierte Bedienung    ← Hände: klicken, ziehen, tippen
│       ├── Skill-Aufruf               ← Mund: „ruft" Dienste direkt auf
│       └── Selbstgesteuertes Verhalten ← Wille: entscheidet wann zu handeln
├── Kognitionsschicht
└── Ego-Schicht
```

## Funktionsweise

**1. Wahrnehmen — Erst schauen, dann handeln** — Vor jeder Operation „sieht" iFay die aktuelle Oberfläche durch den Ego-Perspektive-Tracker.

**2. Bedienen — Wie ein Mensch interagieren** — Unterstützt: Klicken, Ziehen, Scrollen, Tippen, Randgesten, Mehrfingergesten.

**3. Feedback — Nach jeder Aktion Ergebnis prüfen** — Nach jeder Operation „schaut" iFay erneut auf die Oberfläche, um zu bestätigen, ob die Operation erfolgreich war.

Diese „bedienen → beobachten → anpassen"-Schleife ist der fundamentale Unterschied zu RPA-Skripten.

**Unbekannte Oberflächen?** iFay **erkundet** wie ein Mensch: versucht einen Button zu klicken, fährt mit der Maus über ein Icon, scrollt die Seite.

## Szenario-Geschichten

### Szenario 1: Komplexes Versicherungsschadenformular ausfüllen

Du sagst iFay: „Hilf mir, den Kfz-Versicherungsschaden auszufüllen." iFay loggt sich ein, findet den „Schadenantrag"-Eintrag, füllt Felder aus, lädt Fotos hoch, wählt Dropdown-Optionen — alles durch visuelles Verständnis der Oberfläche, nicht durch vorgefertigte Skripte.

### Szenario 2: Essen bestellen, App-Update anpassen

Die App hat gerade aktualisiert, das Homepage-Layout hat sich geändert. iFay scannt das neue Layout, findet das Suchsymbol an neuer Position, sucht das Restaurant, bestellt — demonstriert **adaptive Erkundung**.

## Für Entwickler

Simulierte Bedienung gehört zu **Phase 1 (Simulation menschlicher Bedienung)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 5 (Simulierte Bedienung)
- **Schnittstellenspezifikation**: `SimulatedOperation`-Schnittstelle mit drei Kernmethoden: `execute()`, `explore()`, und `getPostActionState()`
- **Unterstützte Operationstypen**: `click`, `drag`, `scroll`, `gesture`, `type`
- **Konformitätstests**: iFACTS L1 verifiziert Ausführungsfähigkeit für jeden Operationstyp; L2 verifiziert Hand-Auge-Koordinationsschnittstelle
- **iFay Ready Relevanz**: Bronze-Zertifizierung erfordert, dass Anwendungen iFay-Bedienung durch Simulierte Bedienung unterstützen


---

## 10.2 Skill-Aufruf

## Einzeilige Definition

Skill-Aufruf ist iFays **Mund und Telefon** — wenn Simulierte Bedienung iFays Hände sind, die Oberflächen bedienen, ist Skill-Aufruf iFay, die direkt einen Dienst „anruft" — keine Oberfläche nötig, direkt APIs aufrufen oder Aufgaben auslösen.

## Warum er benötigt wird

Stell dir vor, du musst ein Dokument übersetzen. Du hast zwei Optionen:

**Option 1**: Browser öffnen, Übersetzungswebsite aufrufen, Text einfügen, auf Übersetzung warten, Ergebnis kopieren. Das ist der „Simulierte Bedienung"-Ansatz.

**Option 2**: Direkt den Übersetzungsdienst anrufen, „übersetze diesen Absatz für mich" sagen, und sie sagen dir das Ergebnis direkt. Das ist der „Skill-Aufruf"-Ansatz — **den Dienst direkt aufrufen**.

Skill-Aufruf ermöglicht iFay, alle registrierten Dienste effizient zu nutzen — APIs, Workflows, Bots, Agents, Apps, Microservices.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht          ← Skill-Aufruf ist hier
│   ├── Wahrnehmung (Sense)
│   └── Aktion
│       ├── Simulierte Bedienung  ← Hände: bedient Oberflächen
│       ├── 👉 Skill-Aufruf       ← Mund: „ruft" Dienste direkt auf
│       └── Selbstgesteuertes Verhalten ← Wille: entscheidet wann zu handeln
├── Kognitionsschicht
│   └── Skills
│       └── Registrierte Skills     ← Skill-Aufruf kann nur registrierte Skills aufrufen
└── Ego-Schicht
```

## Funktionsweise

**1. Absicht** — iFay empfängt eine Aufgabenabsicht.
**2. Abgleich** — iFay gleicht die Absicht mit dem registrierten Skill-Inventar ab.
**3. Aufruf** — iFay ruft den abgeglichenen Skill auf. Da der Skill bei der Registrierung vorautorisiert wurde, wird der Aufruf sofort ohne Verzögerung ausgeführt.
**4. Aufzeichnung** — Der Aufruf und sein Ergebnis werden aufgezeichnet. Wenn GMChain aktiv ist, wird der Beitrag auch für MeriToken-Abrechnung protokolliert.

## Szenario-Geschichten

### Szenario 1: Sofortige Übersetzung ohne App zu öffnen

Du erhältst eine japanische E-Mail. iFay ruft direkt den registrierten Übersetzungs-API-Skill auf — zwei Sekunden später liegt das Ergebnis vor. Kein Popup für Passwörter, kein Authentifizierungsrad.

### Szenario 2: Multi-Skill-Orchestrierung

Du sagst: „Hilf mir, das morgige Kundenmeeting vorzubereiten." iFay orchestriert: Kalender-API → E-Mail-API → Dokumentengenerierungs-Workflow → Büroservice-API. Alles in unter einer Minute erledigt.

## Für Entwickler

Skill-Aufruf gehört zu **Phase 2 (Direkte Client-Übernahme)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 10 (Skill-Aufruf)
- **Schnittstellenspezifikation**: `InvokeSkillService`-Schnittstelle mit Kernmethoden: `invoke()`, `matchIntent()`, und `getInvocationLog()`
- **Voraussetzung**: Skills müssen über `RegisteredSkillManager` registriert sein, bevor sie aufgerufen werden können
- **Konformitätstests**: iFACTS L1 verifiziert Absichtsabgleich und Skill-Aufruffähigkeit; L2 verifiziert Schnittstellenintegration mit Registrierte Skills; L3 verifiziert die vollständige Kette


---

## 10.3 Selbstgesteuertes Verhalten

## Einzeilige Definition

Selbstgesteuertes Verhalten ist iFays **autonomer Wille** — Simulierte Bedienung sind die Hände, Skill-Aufruf ist der Mund, und Selbstgesteuertes Verhalten ist iFay, die selbst entscheidet „wann zu handeln und wann zu sprechen". Es verwandelt iFay von einem passiven Ausführer in einen proaktiven Akteur.

## Warum es benötigt wird

Ein wirklich guter Assistent handelt **proaktiv**: Bereitet automatisch jeden Montagmorgen die Wochenzusammenfassung vor (geplante Aufgabe), bemerkt dein Stirnrunzeln und fragt proaktiv nach Schwierigkeiten (nach dem Lesen der Situation handeln), erinnert sich immer daran, die Logistik zu prüfen, wenn eine Lieferbenachrichtigung kommt (kontinuierlich ausgeführte Gewohnheiten).

Wichtiger Sicherheitsmechanismus: Wenn etwas, das iFay autonom tut, sich als falsch herausstellt, **pausiert sie und fragt dich**.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht          ← Selbstgesteuertes Verhalten ist hier
│   ├── Wahrnehmung (Sense)
│   │   └── Selbstwahrnehmung    ← Leitet deine Absicht ab ──┐
│   └── Aktion                                                │
│       ├── Simulierte Bedienung  ← Hände                     │
│       ├── Skill-Aufruf          ← Mund                      │
│       └── 👉 Selbstgesteuertes Verhalten ← Wille ←──────────┘
├── Kognitionsschicht
│   └── Skills
│       ├── Registrierte Skills     ← Persistente Skill-Quelle
│       └── Interne Skills          ← Persistente Skill-Quelle
└── Ego-Schicht
```

## Funktionsweise — Drei Auslösertypen

**1. Geplante Aufgaben — Tun wenn die Zeit kommt**

Der einfachste Auslöser. Du sagst iFay: „Generiere jeden Montagmorgen um 9 Uhr den Wochenbericht der letzten Woche."

**2. Selbstwahrnehmungs-Inferenz — Spüren, dass du etwas brauchst, proaktiv handeln**

Der „intelligenteste" Auslöser. iFay beobachtet deinen Zustand und deine Umgebung, leitet ab, was du möglicherweise brauchst, und handelt dann proaktiv.

**3. Persistente Skills — Gewohnheiten, die kontinuierlich im Hintergrund laufen**

Einige Skills sind nicht einmalig — sie laufen kontinuierlich. Zum Beispiel: „Überwache diese Aktie und alarmiere mich, wenn sie unter 50 fällt."

**Die Aktion → Feedback → Re-Aktion-Schleife**

1. **Aktion**: iFay führt eine autonom entschiedene Aufgabe aus
2. **Feedback**: Beobachtet Ausführungsergebnisse
3. **Re-Aktion**: Wenn Ergebnisse den Erwartungen entsprechen, weiter; wenn nicht, Strategie anpassen oder pausieren und fragen

**Sicherheitsventil: Pausieren und Bestätigen**

Wenn iFay feststellt, dass autonome Verhaltensergebnisse nicht mit deiner Absicht übereinstimmen, **pausiert sie alle nachfolgenden autonomen Aktionen** und fragt dich.

## Szenario-Geschichten

### Szenario 1: Wochenbericht automatisch generieren (Geplante Aufgabe)

Montagmorgen 8:55, du bist noch in der U-Bahn. iFays geplante Aufgabe löst aus: extrahiert Arbeitsdaten, generiert Wochenbericht, prüft Inhalt. Um 9:00 findest du den Bericht auf deinem Desktop mit dem Hinweis: „Du hast letzte Woche die meiste Zeit für Projekt A aufgewendet. Projekt B hat zwei verzögerte Aufgaben — soll ich helfen, den Plan dieser Woche anzupassen?"

### Szenario 2: Proaktiv Lebensmittel nachbestellen (Selbstwahrnehmungs-Auslöser)

iFay entdeckt durch Smart-Kühlschrank-Sensordaten: nur noch eine Packung Milch, 3 Eier, Gemüsefach fast leer. Kombiniert mit deinen Essgewohnheiten und Einkaufsaufzeichnungen handelt iFay proaktiv — aber pausiert vor der Bestellung, weil der Betrag dein übliches Budget übersteigt: „Der Kühlschrank wird leer. Ich habe eine Einkaufsliste erstellt — 186 Yuan insgesamt. Soll ich bestellen?"

## Für Entwickler

Selbstgesteuertes Verhalten gehört zu **Phase 4 (iFay + coFay Vollständige Personifizierung)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 14 (Selbstgesteuertes Verhalten)
- **Schnittstellenspezifikation**: `SelfDrivenBehavior`-Schnittstelle mit vier Kernmethoden: `scheduleTask()`, `handleInference()`, `pauseAndConfirm()`, und `getLoopStatus()`
- **Drei Auslöserquellen**: `scheduled`, `self_awareness`, `registered_skill` / `internal_skill`
- **Konformitätstests**: iFACTS L1 verifiziert Reaktionsfähigkeit auf drei Auslöserquellen; L2 verifiziert Schnittstelle mit Selbstwahrnehmungsmodul; L4 verifiziert Sicherheitsbeschränkungen autonomen Verhaltens
