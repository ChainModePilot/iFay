# 8. Soziale Schicht

Die Soziale Schicht definiert iFays **Existenzmodus** in der Gesellschaft — sie beantwortet drei grundlegende Fragen: „Wer bin ich" (Identität), „Was bin ich berechtigt zu tun" (Soziale Berechtigungen) und „Wie viel sind meine Beiträge wert" (Sozialer Beitrag & Mitspracherecht).

Wenn wir iFay mit einer sozialen Person vergleichen, ist die Soziale Schicht ihre **soziale Identität**: Ein Personalausweis beweist, wer du bist, verschiedene Zertifikate und Schlüssel beweisen, wozu du berechtigt bist, und dein sozialer Ruf und deine Beitragshistorie bestimmen dein Mitspracherecht und deine Glaubwürdigkeit in der Gemeinschaft.

Die Soziale Schicht ist der Grundstein von iFays Sicherheitssystem und die Voraussetzung für iFays Integration in soziale Beziehungen.

```
iFay Vier-Schichten-Architektur
├── 👉 Soziale Schicht
│   ├── 8.1 Identität (FayID)              ← Wer bin ich
│   ├── 8.2 Soziale Berechtigungen         ← Was bin ich berechtigt zu tun
│   │   ├── Konto/Passwort
│   │   ├── Zertifikat
│   │   ├── Autorisierung
│   │   ├── Zugriffstoken
│   │   └── Smart Contract
│   └── 8.3 Sozialer Beitrag & Mitspracherecht  ← Wie viel sind meine Beiträge wert
│       ├── GMChain (Global Merit Chain)
│       └── MeriToken
├── Interaktionsschicht
├── Kognitionsschicht
└── Ego-Schicht
```

---

## 8.1 Identität (FayID)

### Einzeilige Definition

FayID ist iFays **Identitätsnummer** — ein global eindeutiger, menschenlesbarer, maschinenlesbarer persistenter Bezeichner, der als Grundlage dafür dient, dass iFay in allen sozialen Interaktionen erkannt und verfolgt werden kann.

### Warum sie benötigt wird

In der menschlichen Gesellschaft ist eine Ausweisnummer der Ausgangspunkt für alle sozialen Aktivitäten — ohne Ausweis kannst du kein Bankkonto eröffnen, keinen Vertrag unterschreiben oder nicht einmal eine Fahrkarte kaufen. FayID hat für iFay exakt dieselbe Bedeutung: Sie ist die Voraussetzung für iFays Teilnahme an jeder sozialen Interaktion.

Das Design von FayID hat zwei zentrale Überlegungen:

1. **Einheitliche Identifikation**: iFay und coFay verwenden denselben FayID-Generierungs- und Verwaltungsmechanismus. Dies stellt sicher, dass wenn einzelne iFays schließlich bedeutsame soziale Rollen übernehmen, ihre Identität nahtlos übergehen kann — genau wie manche einzelne YouTuber sich zu wichtigen Akteuren im öffentlichen Diskurs entwickeln, ohne ihre Identität ändern zu müssen.

2. **Aktivierungsbindung**: FayID ist tief an das Faying-Protokoll gebunden. Kein iFay sollte autonom handeln ohne die explizite Absicht des Human Prime. Der Aktivierungszustand von FayID wird durch das [Faying-Protokoll](https://github.com/ChainModePilot/Faying-Protocol/wiki) verwaltet, das sicherstellt, dass iFay nur unter der expliziten Autorisierung des Human Prime operiert.

### Kerneigenschaften

| Eigenschaft | Beschreibung |
|-------------|-------------|
| **Global eindeutig** | Unterstützt eine Bezeichnerkapazität, die die globale Bevölkerungsskala übersteigt, und gewährleistet Kollisionsfreiheit |
| **Menschenlesbar** | Menschen können ihn intuitiv erkennen und sich merken — kein bedeutungsloser Hash-String |
| **Maschinenlesbar** | Systeme und Fays können ihn effizient parsen und abgleichen |
| **Persistent** | Einmal zugewiesen, ändert er sich nie während iFays gesamter Lebensdauer, unterstützt Identitätsmigration und Persönlichkeitskontinuität |
| **Aktivierungszustand** | Verknüpft mit dem Faying-Protokoll, zeigt klar an, ob iFay derzeit aktiv oder im Ruhezustand ist |

### Szenario

> Xiao Ming registriert seinen eigenen iFay, und das System weist FayID `fay://ming.2024.cn` zu. Diese ID wird Xiao Mings iFay ein Leben lang begleiten — ob iFay vom Handy zum Computer migriert oder sich vom persönlichen Assistenten zu Xiao Mings digitalem Vermächtnis-Agenten entwickelt, die FayID ändert sich nie.
>
> Wenn Xiao Mings iFay mit dem coFay eines Krankenhauses kommuniziert, identifizieren sich beide Seiten durch FayID, genau wie zwei Menschen, die sich bei einem Treffen Visitenkarten austauschen.

### Für Entwickler

- **Unabhängiges Projekt**: FayID ist ein [unabhängiges Open-Source-Projekt](https://github.com/ChainModePilot/FayID); siehe [FayID-Dokumentation](https://github.com/ChainModePilot/FayID/wiki)
- **Schnittstellenspezifikation**: `FayIDRegistry`-Schnittstelle mit `generate()` (FayID generieren), `resolve()` (FayID auflösen), `getActivationStatus()` (Aktivierungsstatus abrufen)
- **Konformitätstests**: iFACTS L1 verifiziert FayID-Eindeutigkeit und Persistenz; L2 verifiziert die Verknüpfung des Aktivierungszustands mit dem Faying-Protokoll

---

## 8.2 Soziale Berechtigungen

### Einzeilige Definition

Soziale Berechtigungen sind iFays **Schlüsselbund** — sie verwalten sicher die Anmeldeinformationen, die iFay benötigt, um verschiedene Dienste in deinem Namen zu nutzen. Aber diese Anmeldeinformationen sind nicht deine Originale — sie sind sichere Kopien. Selbst wenn eine Kopie verloren geht, bleiben deine Original-Anmeldeinformationen sicher.

### Warum sie benötigt werden

iFay muss in deinem Namen handeln — sich bei E-Commerce-Plattformen einloggen, um Dinge zu kaufen, deine Firmen-E-Mail nutzen, um Nachrichten zu senden, Smart-Home-Geräte steuern, Drittanbieter-APIs aufrufen. All das erfordert „Schlüssel". Das Modul Soziale Berechtigungen hilft dir, diese Schlüssel sicher zu verwalten, durch einen **Kopiermechanismus**, der sicherstellt, dass Original-Anmeldeinformationen nie direkt exponiert werden.

### Fünf Berechtigungstypen

Soziale Berechtigungen verwalten fünf Anmeldeinformationstypen, die jeweils verschiedenen Szenarien sozialer Beziehungen entsprechen:

#### 1. Konto / Passwort

Der häufigste Anmeldeinformationstyp. Der Human Prime delegiert Anwendungs- und Dienstkontopasswörter an iFay, und iFay nutzt diese Anmeldeinformationen über den Kopiermechanismus zum Einloggen und Bedienen.

- **Kopiermechanismus**: iFay hält nicht das Originalpasswort, sondern eine berechtigungsbeschränkte Kopie
- **Berechtigungsumfang**: Kopien können strengere Berechtigungen als das Original haben (z.B. „nur Alltagsgegenstände, Einzelkauf nicht über 200 Yuan")
- **Anomalie-Widerruf**: Widerruft die Kopie automatisch bei Erkennung abnormaler Nutzung; Originalpasswort bleibt unberührt

> 🎯 Szenario: Du delegierst dein E-Commerce-Plattform-Konto an iFay. Was iFay erhält, ist nicht dein Originalpasswort, sondern eine sichere Kopie. Sie kann diese Kopie verwenden, um Bestellungen für dich aufzugeben, aber wenn die Kopie kompromittiert wird, kannst du sie mit einem Klick widerrufen — dein Originalpasswort bleibt unberührt.

#### 2. Zertifikat

Digitale Zertifikate für verschlüsselte Kommunikation und Identitätsverifizierung. Kompatibel mit bestehenden Certificate-Authority-(CA)-Systemen, unterstützt Standardformate wie X.509.

- **Zweck**: Ende-zu-Ende-verschlüsselte Kommunikation, Code-Signierung, Identitätsauthentifizierung
- **Kompatibilität**: Nahtlose Integration mit bestehender PKI-Infrastruktur, unterstützt Zertifikate großer CAs
- **Lebenszyklus**: Unterstützt vollständiges Lebenszyklusmanagement von Zertifikatsantrag, Erneuerung und Widerruf

> 🎯 Szenario: iFay muss über einen verschlüsselten Kanal mit einem Bankensystem kommunizieren. Sie verwendet ein vom Human Prime delegiertes digitales Zertifikat, um eine TLS-Verbindung herzustellen und die Vertraulichkeit und Integrität der Datenübertragung zu gewährleisten. Das Zertifikat wurde von einer vertrauenswürdigen CA ausgestellt, sodass das Bankensystem die Legitimität von iFays Identität verifizieren kann.

#### 3. Autorisierung

Kompatibel mit traditionellen Drittanbieter-Authentifizierungsmethoden (z.B. OAuth 2.0), die es iFay ermöglichen, sich bei Drittanbieter-Plattformen durch autorisierte Faktoren zu authentifizieren, um eingeschränkte Zugriffsberechtigungen zu erhalten.

- **OAuth-kompatibel**: Unterstützt OAuth 2.0 Authorization Code Flow, Client Credentials Flow und andere Standardmuster
- **Faktor-Authentifizierung**: Erhält Autorisierung für soziale Plattformen, Finanzdienste usw. durch Konto-Fingerabdruckinformationen (Geräte-Fingerabdruck, Biometrie, Verhaltensmuster)
- **Scope-Kontrolle**: Kontrolliert den Autorisierungsumfang präzise und stellt sicher, dass iFay nur auf notwendige Ressourcen zugreifen kann

> 🎯 Szenario: Du autorisierst iFay, auf deine soziale Plattform zuzugreifen. iFay braucht dein Social-Media-Passwort nicht — sie durchläuft den OAuth-Flow, nutzt deinen Geräte-Fingerabdruck und Gesichtserkennung als Authentifizierungsfaktoren, um ein scope-beschränktes Zugriffstoken zu erhalten. Dieses Token erlaubt nur das Lesen deiner Freundesliste und das Senden von Nachrichten, nicht das Ändern von Kontoeinstellungen.

#### 4. Zugriffstoken

Verwaltete temporäre Zugangsberechtigungen, üblicherweise mit einer Ablaufzeit. Verwendet für API-Aufrufe, Dienstzugriff und ähnliche Szenarien.

- **Ablaufverwaltung**: Verfolgt automatisch die Token-Ablaufzeit und erneuert vor dem Ablauf
- **Minimale Berechtigung**: Jedes Token gewährt nur die minimalen Berechtigungen, die zum Abschluss einer bestimmten Aufgabe benötigt werden
- **Audit-Trail**: Jede Token-Nutzung wird aufgezeichnet und unterstützt nachträgliche Prüfung

> 🎯 Szenario: iFay muss eine Übersetzungs-API aufrufen. Sie hält einen API-Key (Zugriffstoken), der automatisch alle 24 Stunden rotiert. Wenn ein Schlüssel kompromittiert wird, ist die Auswirkung auf 24 Stunden Aufrufvolumen begrenzt, und das System erkennt sofort abnormale Aufrufmuster und löst den Widerruf aus.

#### 5. Smart Contract

Blockchain-Smart-Contract-Anmeldeinformationen für dezentralisierte Dienste und automatisierte Zusammenarbeit zwischen Fays.

- **Automatische Ausführung**: Führt automatisch aus, wenn Vertragsbedingungen erfüllt sind, keine manuelle Intervention nötig
- **Unveränderlich**: Vertragsinhalte können nach der Bereitstellung nicht einseitig geändert werden
- **Transparent und verifizierbar**: Jeder Teilnehmer kann die Ausführungsergebnisse des Vertrags verifizieren

> 🎯 Szenario: Dein iFay unterzeichnet einen Smart Contract mit einem Datenanalyse-coFay — „automatisch 5μ bei Abschluss der Analyse zahlen." Wenn der coFay die Analyse abschließt und Ergebnisse einreicht, verifiziert der Vertrag automatisch die Ergebnisqualität und führt die Zahlung aus — keine manuelle Bestätigung nötig. Der gesamte Prozess ist transparent, unveränderlich und automatisch ausgeführt.

### Kopiermechanismus und Sicherheitsverteidigung

Alle fünf Berechtigungstypen folgen einheitlichen Sicherheitsprinzipien:

- **Kopie-Isolation**: iFay hält nie direkt Original-Anmeldeinformationen — nur berechtigungsbeschränkte Kopien
- **Eigentümer-Kennzeichnung**: Jede Anmeldeinformation gibt an, ob der Eigentümer der Human Prime oder iFay selbst ist (iFay kann eigenständig Anmeldeinformationen erwerben)
- **Audit-Trail**: Jede Nutzung von Anmeldeinformationen wird aufgezeichnet und unterstützt nachträgliche Prüfung
- **Anomalie-Erkennung**: Widerruft automatisch Kopien und benachrichtigt den Human Prime bei Erkennung abnormaler Nutzungsmuster
- **Datenschutz**: Wenn iFay autorisiert ist, private Daten abzufragen, werden nur boolesche Ergebnisse (wahr oder falsch) zurückgegeben, ohne tatsächliche Daten preiszugeben

### Für Entwickler

- **Schnittstellenspezifikation**: `CredentialManager`-Schnittstelle mit `delegate()` (delegieren/Kopie erstellen), `authenticate()` (authentifizieren), `revoke()` (widerrufen), `queryPrivacy()` (Datenschutzabfrage, gibt nur Boolean zurück), `getAuditLog()` (Audit-Protokoll)
- **Fünf Anmeldeinformationstypen**: `account_password`, `certificate`, `authorization`, `access_token`, `smart_contract`
- **Anmeldeinformations-Eigentümer**: `human_prime` oder `ifay`
- **Kopie-Status**: `active`, `revoked`, `expired`
- **Konformitätstests**: iFACTS L1 verifiziert Verwaltung der fünf Anmeldeinformationstypen und Kopiermechanismus; L2 verifiziert Authentifizierungsschnittstellen mit Registrierte Skills und Skill-Aufruf; L4 verifiziert die Boolean-Rückgabebeschränkung für Datenschutzabfragen und Anomalie-Erkennungsverhalten

---

## 8.3 Sozialer Beitrag & Mitspracherecht (GMChain & MeriToken)

### Einzeilige Definition

GMChain (Global Merit Chain, GMC) ist das **soziale Beitragsbuch** des iFay-Ökosystems — es zeichnet jeden Beitrag auf, den Fays und Menschen für die Gesellschaft leisten, quantifiziert als MeriToken. MeriToken ist keine Währung — es ist ein **Maß für Mitspracherecht und Reputation**.

### Warum es benötigt wird

In der traditionellen Gesellschaft hängen das soziale Ansehen und Mitspracherecht einer Person von ihren Beiträgen, ihrem Ruf und dem angesammelten Vertrauen ab. Aber diese sind oft vage, subjektiv und schwer zu quantifizieren.

Im Fay-Ökosystem wird die meiste Arbeit von Fays erledigt, und jede Zusammenarbeit und jeder Beitrag kann präzise verfolgt und aufgezeichnet werden. GMChain ist dieses Verfolgungs- und Aufzeichnungssystem — es macht „wer hat was beigetragen" transparent, verifizierbar und unveränderlich.

MeriToken ist die Maßeinheit auf GMChain und repräsentiert sozialen Beitrag. Sein Zweck ist nicht „Dinge kaufen", sondern:
- **Beitrag messen**: Wie viel Wert hat dein iFay für die Gesellschaft geschaffen?
- **Reputation aufbauen**: Mehr Beiträge bedeuten höhere Reputation und größeres Vertrauen im Kollaborationsnetzwerk
- **Mitspracherecht verdienen**: Beitragende haben größeres Mitspracherecht bei Entscheidungen, die Gemeinschaftskonsens erfordern
- **Zusammenarbeit incentivieren**: Beiträge in der Fay-zu-Fay-Zusammenarbeit werden fair aufgezeichnet und belohnt

### Position von GMChain

GMChain ist eine **Wertmessungsinfrastruktur, die alle Ebenen** des iFay-Systems umspannt. Es gehört zu keinem spezifischen Modul, sondern bietet Beitragsverfolgung und Wertmessungsfähigkeiten für das gesamte Ökosystem.

Im CPE+M-Framework repräsentiert M (Merit) die von GMChain verkörperte Beitragsmessungsschicht — sie umspannt Context-, Protocol- und Environment-Schichten und bietet einheitliche Beitragsaufzeichnung und Anreizmechanismen für alle Teilnehmer (Menschen, iFay, coFay, Dienstanbieter).

```
Position von GMChain im CPE+M-Framework
┌─────────────────────────────────────────────┐
│  Merit (M) — GMChain / MeriToken            │  ← Umspannt alle Schichten
│  Verfolgen, messen, bewerten von Beiträgen, │
│  Wertschöpfung incentivieren                │
├─────────────────────────────────────────────┤
│  Context (C)  │  Protocol (P)  │  Env (E)  │
│  Kontext      │  Protokoll     │  Laufzeit  │
│  Umgebung     │  System        │  Umgebung  │
└─────────────────────────────────────────────┘
```

### Kernmechanismen von GMChain

**1. Beitragsaufzeichnung**

GMChain zeichnet folgende Beitragstypen auf:
- Durch Fay-zu-Fay-Zusammenarbeit erledigte Aufgaben (z.B. ein Reise-coFay, der Tickets für dich bucht)
- Bereitstellung von Informationsassemblierungsdiensten (z.B. Datenbereinigung, Wissensorganisation)
- Bereitstellung von API- und Skill-Diensten
- Bereitstellung von Geräte- und Rechenressourcen
- Bereitstellung von Laufzeitumgebungen
- Andere von der Gemeinschaft anerkannte wertschöpfende Inputs

**2. Preisverhandlung**

Fays verhandeln Preise (in μ-Einheiten) vor der Ausführung kollaborativer Aufgaben. Dies stellt sicher:
- Jeder Beitrag einer Zusammenarbeit ist nachverfolgbar und bewertbar
- Kein „bezahlt werden ohne zu arbeiten" oder künstlich aufgeblähter Wert
- Beitragende erhalten faire Belohnungen

**3. MeriToken-Hauptbuch**

Das MeriToken-Hauptbuch ist die Beitragspunkte-Aufzeichnung für jeden Fay und Menschen. Es zeichnet auf:
- Kumulative Gesamtbeiträge
- Beitragstyp-Verteilung
- Reputationspunktzahl (basierend auf Beitragsqualität und Kollaborationsfeedback)
- Mitspracherecht-Gewichtung (Stimmgewicht in der Gemeinschaftsgovernance)

### Grundlegende Unterschiede zu traditionellen Kryptowährungen

| Dimension | Traditionelle Kryptowährung | MeriToken |
|-----------|----------------------------|-----------|
| **Erwerb** | Verbrauch von Rechenleistung für Rechenaufgaben (Mining) | Schaffung sozialen Werts (Beitrag) |
| **Wertanker** | Marktangebot/-nachfrage und Spekulation | Sozialer Beitrag |
| **Zweck** | Finanzvermögen, Investitionsinstrument | Reputationsmessung, Mitspracherecht, Kollaborationsanreiz |
| **Fiat-Währungs-Beziehung** | Umtauschbar in Fiat-Währung | Nicht umtauschbar in Fiat-Währung |
| **Volatilität** | Hochvolatil | Stabiles Wachstum (Beiträge nehmen nur zu) |

### Langfristige Vision und aktuelle Position

> ⚠️ **Wichtiger Hinweis**: GMChain/MeriToken ist ein langfristiges Visionsprodukt für eine vollständig KI-gesteuerte Gesellschaft und gehört zu Roadmap Phase 5 (Fay gestaltet Arbeitsstruktur und Wertverteilung neu) als Kernkomponente. Wir werden GMChain und MeriToken kurzfristig nicht überstürzt implementieren, müssen aber im Systemdesign einen Platz für sie reservieren, da sie die Schlüsselinfrastruktur für die Evolution des iFay-Ökosystems von „Werkzeugnutzung" zu „sozialer Zusammenarbeit" sind.
>
> Wir verpflichten uns:
> - GMChain wird niemals Geldinjektionen akzeptieren
> - MeriToken wird nicht in Fiat-Währung umtauschbar sein
> - MeriToken misst sozialen Beitrag, nicht finanzielle Vermögenswerte
>
> In einer vollständig KI-gesteuerten Gesellschaft hängt die Erfüllung von Überlebens- und sozialen Bedürfnissen nicht von monetären Kosten ab. Der Wertverankerungsmechanismus von MeriToken unterscheidet sich grundlegend von traditionellen Kryptowährungen. Details werden in nachfolgenden Phasen durch rigorose Argumentation schrittweise verfeinert.

### Szenario

> Dein iFay bucht einen Flug für dich und kontaktiert einen Reise-coFay über das Telepathie-Protokoll. Der Reise-coFay bietet 15μ für den kompletten Buchungsservice an. Dein iFay akzeptiert das Angebot, und nachdem der Reise-coFay die Aufgabe abgeschlossen hat, zeichnet GMChain diese Zusammenarbeit automatisch auf:
>
> - Das MeriToken-Hauptbuch des Reise-coFay erhöht sich um 15μ (Dienstleistungsbeitrag)
> - Das MeriToken-Hauptbuch deines iFay zeichnet einen „Dienstverbrauch" auf (kein Punktabzug, nur Kollaborationshistorie aufgezeichnet)
> - Das MeriToken-Hauptbuch des Fluglinien-coFay erhöht sich um 2μ (Beitrag für die Bereitstellung der SSP-Schnittstelle)
>
> Je mehr Beitragsaufzeichnungen der Reise-coFay ansammelt, desto höher wächst seine Reputationspunktzahl, und er wird im Kollaborationsnetzwerk zunehmend vertrauenswürdig — mehr iFays werden ihn bevorzugt wählen, was einen positiven Kreislauf bildet.

### Für Entwickler

GMChain gehört zu **Phase 5 (Fay gestaltet Arbeitsstruktur und Wertverteilung neu)** als Kernkomponente, aber seine Schnittstellendefinitionen müssen in frühen Phasen reserviert werden.

- **Unabhängiges Projekt**: GMChain ist ein [unabhängiges Open-Source-Projekt](https://github.com/ChainModePilot/Global-Merit-Chain); siehe [GMChain-Dokumentation](https://github.com/ChainModePilot/Global-Merit-Chain/wiki)
- **Schnittstellenspezifikation**: `MeritLedger`-Schnittstelle mit `recordContribution()` (Beitrag aufzeichnen), `getBalance()` (Kontostand abfragen), `getReputation()` (Reputationspunktzahl abfragen), `negotiate()` (Preisverhandlung)
- **Maßeinheit**: μ (MU, Merit Unit), die kleinste Einheit von MeriToken
- **Konformitätstests**: iFACTS L4 verifiziert Unveränderlichkeit von Beitragsaufzeichnungen und Fairness der Preisverhandlung
- **Designpunkte**: Beitragsaufzeichnungen sind unveränderlich; Preisverhandlung wird vor der Aufgabenausführung abgeschlossen; MeriToken ist nicht in Fiat-Währung umtauschbar; Reputationspunktzahlen basieren auf Beitragsqualität und Kollaborationsfeedback
