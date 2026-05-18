# 9. Interaktionsschicht — Wahrnehmung

Das Wahrnehmungssubsystem der Interaktionsschicht ist iFays „Sinne“ — es lässt iFay den Bildschirm sehen, die Umgebung wahrnehmen und deine Absichten lesen.


---

## 9.1 Ego-Perspektive-Tracker

## Einzeilige Definition

Der Ego-Perspektive-Tracker ist iFays **Augen und Ohren** — er lässt iFay die Bilder sehen, die du siehst, und die Geräusche hören, die du hörst, und gibt ihr exakt dieselbe Ego-Perspektive wie du.

## Warum er benötigt wird

Stell dir vor, du hast einen Assistenten eingestellt, der dir beim Ausfüllen eines Webformulars helfen soll. Wenn dieser Assistent blind wäre — unfähig, die Eingabefelder, Buttons und Fehlermeldungen auf dem Bildschirm zu sehen — wie könnte er helfen?

Das wäre iFay ohne den Ego-Perspektive-Tracker.

Wenn Menschen Computer und Handys bedienen, verlassen sie sich auf Augen, um den Bildschirm zu sehen, und Ohren, um Benachrichtigungstöne zu hören. iFay braucht dieselben Fähigkeiten. Der Ego-Perspektive-Tracker ist das Modul, das iFay diese Fähigkeit gibt — er lässt iFay **den Bildschirm sehen wie du**, anstatt Code wie ein Programmierer zu lesen.

Es gibt hier eine wichtige Unterscheidung: iFay sieht, was du **mit bloßem Auge siehst**, nicht den versteckten Code hinter Webseiten (wie HTML-Tags, SEO-Keywords — Dinge, die du überhaupt nicht sehen kannst). iFay priorisiert „visuelles" Verständnis von Oberflächen gegenüber dem Parsen strukturierter Dokumente.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht          ← Ego-Perspektive-Tracker ist hier
│   ├── Wahrnehmung (Sense)
│   │   ├── 👉 Ego-Perspektive-Tracker   ← Schaut nach außen, sieht den Bildschirm
│   │   ├── Sensor                       ← Nimmt die Umgebung wahr
│   │   └── Selbstwahrnehmung            ← Schaut nach innen, liest dich
│   └── Aktion
│       ├── Simulierte Bedienung
│       ├── Skill-Aufruf
│       └── Selbstgesteuertes Verhalten
├── Kognitionsschicht
└── Ego-Schicht
```

## Funktionsweise

**1. Die Anzeige sehen** — iFay erfasst, was aktuell auf deinem Bildschirm angezeigt wird.

**2. Geräusche hören** — Benachrichtigungstöne, Sprachansagen oder Video-Audio erfassen.

**3. Echtzeit-Änderungsverfolgung** — Nach jeder Operation sofort das Ergebnis sehen: Hat sich die Seite geändert? Ist eine Fehlermeldung erschienen?

**4. Hand-Auge-Koordination** — Der Ego-Perspektive-Tracker und das Modul Simulierte Bedienung sind eng gepaarte „Partner" — wie Augen und Hände einer Person. Diese „sehen → tun → wieder sehen"-Schleife ist iFays Hand-Auge-Koordinationsfähigkeit.

**5. „Kann nicht sehen" melden** — Wenn der Tracker die Anzeige nicht erfassen kann, meldet er ehrlich der Kognitionsschicht: „Ich kann nicht sehen."

## Beziehungen zu anderen Modulen

| Verwandtes Modul | Beziehung | Körperanalogie |
|-----------------|-----------|----------------|
| **Simulierte Bedienung** | Eng gekoppelt, Hand-Auge-Koordination | Augen ↔ Hände |
| **Kognitionsschicht** | Meldet Wahrnehmungsstatus | Augen → Gehirn |
| **Sensor** | Beide im Wahrnehmungssubsystem, aber verschiedene Rollen | Augen vs. Hautnerven |
| **Selbstwahrnehmung** | Beide im Wahrnehmungssubsystem, aber verschiedene Richtungen | Augen vs. emotionale Intelligenz |

## Szenario-Geschichten

### Szenario 1: Behördenwebsite-Formular ausfüllen

iFays Ego-Perspektive-Tracker „sieht" das Formular: Namenseingabefeld, Ausweisnummernfeld, ein Dropdown-Menü, ein CAPTCHA-Bild, einen blauen „Absenden"-Button. Er gibt diese visuellen Informationen an das Modul Simulierte Bedienung weiter, das Felder einzeln ausfüllt, Optionen auswählt, das CAPTCHA eingibt und auf Absenden klickt.

Nach dem Absenden „schaut" der Ego-Perspektive-Tracker sofort auf das Ergebnis — wenn eine rote Fehlermeldung „Ausweisnummernformat falsch" erscheint, erfasst er diese Änderung, und iFay weiß, dass sie korrigieren und erneut absenden muss.

### Szenario 2: Echtzeit-Aktienüberwachung

Du bittest iFay, das Echtzeit-Chart einer Aktie zu beobachten. Der Ego-Perspektive-Tracker „beobachtet" kontinuierlich die K-Linien-Chart und Zahlenänderungen auf dem Bildschirm. Wenn der Preis deinen Zielpreis erreicht, benachrichtigt iFay dich sofort — ohne Ablenkung, ohne Müdigkeit, 24/7.

## Für Entwickler

Der Ego-Perspektive-Tracker gehört zu **Phase 1 (Simulation menschlicher Bedienung)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 4 (Ego-Perspektive-Tracker)
- **Schnittstellenspezifikation**: `FirstPersonTracer`-Schnittstelle mit vier Kernmethoden: `captureVisual()`, `captureAudio()`, `trackChanges()`, und `getPerceptionStatus()`
- **Konformitätstests**: iFACTS L1 verifiziert visuelle Erfassungsfähigkeit; L2 verifiziert Hand-Auge-Koordinationsschnittstelle mit Simulierte Bedienung


---

## 9.2 Sensor

## Einzeilige Definition

Der Sensor ist iFays **Nervensystem** — er lässt iFay alle Veränderungen in der umgebenden Umgebung wahrnehmen, von Temperatur und Standort bis zu Herzfrequenz und Licht, genau wie die Nervenenden, die über deinen gesamten Körper verteilt sind.

## Warum er benötigt wird

Wenn der Ego-Perspektive-Tracker iFays Augen und Ohren ist, dann ist der Sensor iFays **gesamtes neuronales Netzwerk**.

Dein Handy und deine Smartwatch haben GPS, Beschleunigungsmesser, Lichtsensor, Herzfrequenzsensor usw. iFays Sensormodul **vereinheitlicht den Zugang** zu all diesen Sensoren über Geräte hinweg und gibt iFay ein vollständiges Nervensystem. Und dieses Nervensystem ist kontinuierlich erweiterbar.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht          ← Sensor ist hier
│   ├── Wahrnehmung (Sense)
│   │   ├── Ego-Perspektive-Tracker   ← Schaut nach außen, sieht den Bildschirm
│   │   ├── 👉 Sensor                  ← Nimmt Umgebung wahr (Temperatur, Standort, Bewegung…)
│   │   └── Selbstwahrnehmung          ← Schaut nach innen, liest dich
│   └── Aktion
├── Kognitionsschicht
│   ├── Denken
│   │   ├── Persönlicher Datenspeicher    ← Sensordaten werden hier gespeichert
│   │   └── ...
│   └── Skills
│       ├── Gerätetreiber-Hub     ← Hardware-Schnittstellen des Sensors werden hier verwaltet
│       └── ...
└── Ego-Schicht
```

Der Sensor hat eine besondere Eigenschaft: Er handhabt nur **Empfindlichkeitsanpassung** (entscheidet, wann mehr und wann weniger Daten gesammelt werden), während die tatsächlichen Hardware-Verbindungen und Datenspeicherung vom **Gerätetreiber-Hub** bzw. **Persönlichen Datenspeicher** der Kognitionsschicht gehandhabt werden.

## Funktionsweise

**1. Brücke — Gerätesensoren verbinden**

Das Sensormodul fungiert als „Übersetzer" und übersetzt Daten von allen verschiedenen Geräten und Sensortypen einheitlich in ein Format, das iFay verstehen kann. Es verwendet **CAP (Control Authority Protocol)** und **DTP (Data Tunnel Protocol)** für diese Überbrückung.

**2. Regulieren — Dynamische Empfindlichkeit**

iFays Sensor muss nicht ständig Daten von allen Sensoren mit maximaler Präzision sammeln. Zum Beispiel:
- Wenn du ruhig im Büro arbeitest, muss GPS nicht jede Sekunde deine Position aktualisieren
- Aber wenn du mit Navigation fährst, braucht GPS hochfrequente Updates
- Wenn du schläfst, kann der Herzfrequenzsensor seine Abtastfrequenz senken
- Aber wenn eine abnormale Herzfrequenz erkannt wird, erhöht sich die Abtastfrequenz sofort

**3. Erweitern — Zukünftige Sensoren können auch integriert werden**

Das Design des Sensormoduls ist offen — wenn neue Sensortypen erscheinen, muss nur ein neuer Treiber über den Gerätetreiber-Hub registriert werden.

## Szenario-Geschichten

### Szenario 1: Intelligente Gesundheitserinnerung

Um 15 Uhr sitzt du seit drei Stunden am Computer. iFay entdeckt durch Smartwatch-Sensordaten: Beschleunigungsmesser zeigt kaum Bewegung, Herzfrequenz von 72 auf 85 bpm gestiegen, Hauttemperatur leicht erhöht. Das Sensormodul aggregiert diese Daten und gibt sie an iFays Kognitionsschicht weiter. iFay erinnert dich sanft: „Du sitzt seit 3 Stunden und deine Herzfrequenz ist etwas hoch. Wie wäre es, aufzustehen und dich zu strecken?"

### Szenario 2: Autonomer Drohnenflug

iFay ist auf einer Drohne für eine Luftaufnahmemission eingesetzt. Das Sensormodul vereinheitlicht alle Datenströme (GPS, IMU, Kamera, Ultraschall/LiDAR, Barometer, Windgeschwindigkeitssensor). Während des stabilen Flugs kann die IMU-Empfindlichkeit gesenkt werden; aber bei plötzlichen Windgeschwindigkeitsänderungen erhöht das Sensormodul sofort die IMU- und Barometer-Empfindlichkeit.

## Für Entwickler

Das Sensormodul gehört zu **Phase 2 (Direkte Client-Übernahme)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 7 (Sensormodul)
- **Schnittstellenspezifikation**: `SensorModule`-Schnittstelle mit vier Kernmethoden: `registerSource()`, `adjustSensitivity()`, `getDataStream()`, und `getActiveStatus()`
- **Zugehörige Protokolle**: CAP für Übernahme von Sensor-Hardware; DTP für bidirektionale Datenübertragung
- **Konformitätstests**: iFACTS L1 verifiziert Empfindlichkeitsanpassungsfähigkeit; L2 verifiziert Schnittstellenintegration mit Gerätetreiber-Hub und Persönlichem Datenspeicher


---

## 9.3 Selbstwahrnehmung

## Einzeilige Definition

Selbstwahrnehmung ist iFays **emotionale Intelligenz** — sie schaut nicht auf den Bildschirm und nimmt nicht die Umgebung wahr. Stattdessen **schaut sie nach innen auf dich**, leitet deine Gefühle und Absichten durch deine Reaktionen ab, wie ein alter Freund, der gut darin ist, Menschen zu lesen.

## Warum sie benötigt wird

iFays Wahrnehmungssubsystem hat drei Module, die jeweils in eine andere Richtung schauen:
- **Ego-Perspektive-Tracker** schaut nach außen — sieht, was auf dem Bildschirm ist
- **Sensor** nimmt die Umgebung wahr — spürt Temperatur, Standort, Bewegung
- **Selbstwahrnehmung** schaut nach innen — beobachtet **dich**

Selbstwahrnehmung hebt iFay von „du sagst, ich tue" auf „du sagst nichts, ich verstehe trotzdem". Sie beobachtet deine Mikroausdrücke, Änderungen in deinen Bedienungsgewohnheiten und emotionale Schwankungen, leitet dann ab, was du möglicherweise brauchst — noch bevor du es selbst realisierst.

## Position in der Architektur

```
iFay Vier-Schichten-Architektur
├── Soziale Schicht
├── Interaktionsschicht          ← Selbstwahrnehmung ist hier
│   ├── Wahrnehmung (Sense)
│   │   ├── Ego-Perspektive-Tracker   ← Schaut nach außen
│   │   ├── Sensor                     ← Nimmt Umgebung wahr
│   │   └── 👉 Selbstwahrnehmung       ← Schaut nach innen, liest dich
│   └── Aktion
│       └── Selbstgesteuertes Verhalten  ← Selbstwahrnehmungs-Inferenzen lösen Verhalten aus
├── Kognitionsschicht
│   └── Denken
│       └── Ausgerichtetes Bewusstsein ← Selbstwahrnehmung passt es in Echtzeit an
└── Ego-Schicht
```

Die Ausgabe der Selbstwahrnehmung fließt in zwei Richtungen gleichzeitig:
1. **Abwärts** zum **Modul Selbstgesteuertes Verhalten** — löst iFays proaktive Aktionen aus
2. **Einwärts** zum **Modul Ausgerichtetes Bewusstsein** — aktualisiert iFays Verständnis von dir in Echtzeit

## Funktionsweise

**1. Deine Reaktionen beobachten** — Überwacht kontinuierlich Signale: Änderungen deiner Bedienungsgeschwindigkeit, Browsing-Verhalten, Ausdrücke und Ton, Akzeptanz- oder Ablehnungsmuster.

**2. Deine Absicht ableiten** — Basierend auf beobachteten Signalen leitet Selbstwahrnehmung deinen aktuellen Zustand und mögliche Absichten ab. Zum Beispiel: Du liest einen Artikel, die Scrollgeschwindigkeit verlangsamt sich merklich bei einem bestimmten Abschnitt — Selbstwahrnehmung leitet ab, dass du besonders an diesem Absatz interessiert bist.

**3. Inferenzergebnisse weitergeben** — Teilt dem Modul Selbstgesteuertes Verhalten mit: „Der Human Prime könnte an diesem Thema interessiert sein" und dem Modul Ausgerichtetes Bewusstsein: „Human-Prime-Profil aktualisieren."

**4. Echtzeitanpassung** — Läuft kontinuierlich und revidiert ständig Inferenzen basierend auf deinen neuesten Reaktionen.

## Szenario-Geschichten

### Szenario 1: Du liest einen Artikel, iFay findet proaktiv Materialien

An einem Wochenendnachmittag durchstöberst du einen langen Artikel über „nachhaltiges Gebäudedesign". Selbstwahrnehmung bemerkt: Du scrollst schnell durch die erste Hälfte, aber beim Abschnitt „Passivhaus-Energiespartechnologie" verlangsamt sich deine Scrollgeschwindigkeit merklich, du scrollst einmal zurück. Selbstwahrnehmung leitet ab: Du bist besonders am Thema „Passivhaus" interessiert und löst das Modul Selbstgesteuertes Verhalten aus, das proaktiv vertiefende Artikel sucht.

### Szenario 2: Aufmerksamer Assistent während einer Videokonferenz

Du bist in einer Videokonferenz. Selbstwahrnehmung erfasst deine Gesichtsmikroausdrücke: Als ein Kollege Budgetkürzungen bespricht, runzelt sich deine Stirn leicht. Selbstwahrnehmung leitet ab: Du bist unwohl mit dem aktuellen Diskussionsthema und bereitet still einen Budgetanalysebericht vor, den du zuvor erstellt hast.

## Für Entwickler

Das Selbstwahrnehmungsmodul gehört zu **Phase 4 (iFay + coFay Vollständige Personifizierung)** als Kernmodul.

- **Anforderungs-ID**: Anforderung 13 (Selbstwahrnehmung)
- **Schnittstellenspezifikation**: `SelfAwareness`-Schnittstelle mit drei Kernmethoden: `inferIntent()`, `monitorHostReaction()`, und `adjustAlignment()`
- **Konformitätstests**: iFACTS L1 verifiziert Absichtsinferenzfähigkeit; L2 verifiziert Schnittstellen mit Selbstgesteuertem Verhalten und Ausgerichtetem Bewusstsein; L4 verifiziert Inferenzgenauigkeit und Datenschutz
