# 13. FayManifest Deklarative Assemblierung

FayManifest ist iFays „package.json". Entwickler listen einfach die erforderlichen Komponenten, Protokolle, Steuerungsmodi und Treiberkonfigurationen in einer einzigen JSON-Deklarationsdatei auf, und die FayGer-Laufzeitumgebung löst automatisch Abhängigkeiten auf und assembliert die iFay-Instanz. Du musst nicht die volle Komplexität des iFay-Systems verstehen — deklariere was du brauchst, und das System füllt den Rest.

---

## Warum FayManifest benötigt wird

Eines von iFays Designprinzipien ist **deklarative minimale Assemblierung + progressive Adoption**.

**Problem**: Eine vollständige iFay von Grund auf zu bauen ist komplex — 12 Kernmodule, 6 Protokolle, Berechtigungssysteme, Sicherheitskonformität, Multi-Terminal-Synchronisation…

**Lösung**: Entwickler deklarieren nur die Teilmenge der Komponenten, die ihr Geschäft erfordert, und das System ergänzt automatisch die notwendigen Infrastrukturabhängigkeiten.

---

## FayManifest Dateistruktur

| Feld | Typ | Erforderlich | Beschreibung |
|------|-----|-------------|-------------|
| `name` | string | ✅ | Name der iFay-Implementierung |
| `version` | string | ✅ | Versionsnummer |
| `description` | string | ✅ | Funktionsbeschreibung |
| `vendor` | string | ✅ | Entwickler-/Anbietername |
| `modules` | array | ✅ | Liste erforderlicher Module |
| `protocols` | array | ✅ | Liste erforderlicher Protokolle |
| `controlMode` | string | ✅ | Steuerungsmodus: `command` / `ego` / `autonomous` |
| `drivers` | array | ❌ | Treiberkonfigurationen |
| `ego` | object | ❌ | Ego-Modell-Konfiguration |
| `permissions` | object | ❌ | Berechtigungskonfiguration |

---

## Steuerungsmodi

| Modus | Name | Beschreibung |
|-------|------|-------------|
| `command` | **Befehlssteuerung** | Human Prime treibt jede Aktion explizit. Geeignet für Hochrisikoszenarien. |
| `ego` | **Ego-Steuerung** | Das Ego-Modell trifft autonome Entscheidungen innerhalb eingeschränkter Grenzen. Geeignet für tägliche Assistenzszenarien. |
| `autonomous` | **Autonome Steuerung** | Vollständig selbstgesteuertes Verhalten. Geeignet für Hochvertrauens-Langzeitkollaborationsszenarien. |

---

## Automatische Abhängigkeitsergänzung

Folgende Infrastruktur wird in allen iFay-Implementierungen automatisch hinzugefügt:
- **FayID** (Identität)
- **FayGer-Laufzeitumgebung** (Laufzeit-Container)
- **iFay-Profil** (Einheitliches Datenmodell)
- **Berechtigungssystem** (Berechtigungsverwaltung)
- **Sicherheits- & Ethik-Konformität** (Verhaltenseinschränkungen)
- **Multi-Terminal-Synchronisation** (Zustandssynchronisation)
- **Faying-Protokoll** (Sicheres Pairing)

---

## Vollständiges Beispiel: Drohnensteuerungs-iFay

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "iFay-Implementierung für Drohnensteuerung",
  "vendor": "DroneAI Corp",
  "modules": [
    { "id": "device_driver_hub", "version": "^1.0.0" },
    { "id": "sensor", "config": { "types": ["gps", "imu", "camera", "lidar"] } },
    { "id": "invoke_skill", "version": "^1.0.0" },
    { "id": "registered_skill", "config": { "preload": ["flight_control", "obstacle_avoidance"] } }
  ],
  "protocols": [
    { "id": "cap_protocol", "config": { "targets": ["flight_controller", "gimbal", "camera"] } },
    { "id": "dtp_protocol", "config": { "bandwidth": "high", "realtime": true } }
  ],
  "controlMode": "ego",
  "drivers": [
    { "name": "DJI Flight Controller", "type": "device", "driverPackage": "@drone-drivers/dji-fc", "config": { "model": "A3", "firmwareVersion": "^3.0.0" } },
    { "name": "Gimbal Controller", "type": "device", "driverPackage": "@drone-drivers/gimbal-generic" }
  ],
  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection", "mapping"],
    "constraints": { "skillBoundaries": { "allowed": ["flight", "camera", "navigation"], "restricted": ["financial", "social"] } }
  },
  "permissions": {
    "inherent": ["device_control", "sensor_read"],
    "persistent": ["flight_plan_execute"],
    "authMethods": ["device_fingerprint"]
  }
}
```

---

## Integration mit iFACTS

Nach der Abhängigkeitsauflösung bestimmt das System die iFay-Phase, die dem Manifest entspricht. Das obige Drohnensteuerungsbeispiel entspricht Phase 2 und muss daher alle Konformitätstests für Phase 1 und Phase 2 bestehen.

---

## Phasenweise Minimale Komponentenkonfiguration

| Phase | Neue Module | Neue Protokolle |
|-------|------------|----------------|
| **Phase 1**: Simulation menschlicher Bedienung | FayID, Anmeldeinformationen-Verwaltung, Ego-Perspektive-Tracker, Simulierte Bedienung, Ego-Modell | Faying-Protokoll, Interaktives Konversationsprotokoll |
| **Phase 2**: Direkte Client-Übernahme | Sensor, Gerätetreiber-Hub, Registrierte Skills, Skill-Aufruf, Persönlicher Datenspeicher | CAP (Control Authority Protocol), DTP (Data Tunnel Protocol) |
| **Phase 3**: Schnittstelle zur virtuellen Welt | Externes Wissen | SSP (Skill Sharing Protocol) |
| **Phase 4**: Vollständige Personifizierung | Selbstwahrnehmung, Selbstgesteuertes Verhalten, Interne Skills, Ausgerichtetes Bewusstsein | Telepathie-Protokoll |
| **Phase 5**: Wertverteilung | GMChain, MeriToken | — |

> **Phasenübergreifende Infrastruktur** (für alle Phasen erforderlich): FayGer-Laufzeitumgebung, iFay-Profil, Berechtigungssystem, Sicherheits- & Ethik-Konformität, Multi-Terminal-Synchronisation.

---

### Verwandte Dokumente

- [iFACTS](./14-iFACTS) — Konformitätstests
- [Roadmap](./4-Roadmap) — Phasenkonfiguration
- [Gerätetreiber-Hub](./12.1-Gerätetreiber-Hub) — Treiberkonfiguration
