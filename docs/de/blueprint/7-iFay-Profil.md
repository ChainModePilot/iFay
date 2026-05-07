# 7. iFay-Profil

Das iFay-Profil ist iFays vollständiger „Personalausweis" — eine semantisch interpretierbare sechs-dimensionale Attributtabelle. Es lässt nicht nur Menschen eine iFay identifizieren, sondern auch Systeme sie parsen, und vor allem Fays sich gegenseitig erkennen.

Das Human-Prime-Profil (Ausgerichtetes Bewusstsein) ist eine Teilmenge und Eingabequelle des iFay-Profils. Das Human-Prime-Profil beschreibt „was für ein Mensch der Human Prime ist", während das iFay-Profil beschreibt „was für eine Entität diese iFay ist" — es umfasst die Persönlichkeitsmerkmale des Prime, aber auch iFays eigene unabhängige Attribute wie Skills, Hardware und Berechtigungen.

Das Human-Prime-Profil wird vom Modul [Ausgerichtetes Bewusstsein](./11.3-Ausgerichtetes-Bewusstsein) gepflegt. Die Skills-Dimension wird von [Registrierte Skills](./12.2-Registrierte-Skills) verwaltet, die Hardware-Dimension vom [Gerätetreiber-Hub](./12.1-Gerätetreiber-Hub) und die Berechtigungsdimension von der [Anmeldeinformationen-Verwaltung](./8.1-Anmeldeinformationen-Verwaltung).

---

## iFay-Identität

Die iFay-Identität besteht aus FayID und Metadaten. FayID ist ein global eindeutiger, menschenlesbarer, maschinenlesbarer persistenter Bezeichner — die Grundlage dafür, dass iFay in allen Interaktionsszenarien identifiziert und verfolgt werden kann.

Die iFay-Identität unterstützt reibungslose Identitätsmigration — wenn iFay sich von einem persönlichen Assistenten zu einer autonomen sozialen Rolle entwickelt, muss sich die FayID nicht ändern; die Identität setzt sich natürlich fort.

---

## Ego-Modell

Die Ego-Dimension im Profil zeichnet die Referenz auf die aktuell aktive Ego-Version auf.

Das Ego-Modell ist ein steckbares, umschaltbares Edge-Kleinmodell, das auf jedes Endgerät geladen werden kann, um diesem Gerät die Persönlichkeit des Prime zu verleihen. iFay unterstützt mehrere Ego-Versionen, um der vielseitigen Persönlichkeit des Human Prime gerecht zu werden — aber nur eine Version ist zu jedem Zeitpunkt aktiv, um „gespaltene Persönlichkeit" zu verhindern.

Es gibt zwei Umschaltmethoden: manuell vom Human Prime ausgelöst oder automatisch von iFay basierend auf dem Kontext bestimmt. Nach dem Umschalten wird die aktive Ego-Versionsreferenz im Profil synchron aktualisiert.

### Szenario

> Zhang Lei ist ein Produktmanager, der zwei Ego-Versionen für seine iFay konfiguriert hat: „Professioneller Modus" und „Lockerer Modus".
>
> An Wochentag-Morgen wechselt iFay automatisch zum „Professionellen Modus" — E-Mail-Antworten sind rigoros formuliert, Meetings werden mit Effizienz als Priorität geplant, und Anforderungsdokumente werden mit Betonung auf logische Vollständigkeit behandelt.
>
> An Wochenendabenden erkennt iFay, dass Zhang Lei Essensempfehlungen durchstöbert, und wechselt automatisch zum „Lockeren Modus" — Restaurantempfehlungen konzentrieren sich mehr auf Ambiente und Geschmackspräferenzen, und der Ton wird entspannt und locker.
>
> Zwei Versionen, derselbe Zhang Lei.

---

## Faying-Denken

Faying-Denken sind iFays kognitive Ressourcen, die vier Untertypen enthalten:

| Untertyp | Beschreibung | Beispiele |
|----------|-------------|----------|
| **Content** | Strukturierte oder unstrukturierte Inhaltsressourcen | Fotosammlung des Human Prime, geschriebene Artikel, komponierte Musik, aufgenommene Videos |
| **Data** | Persönliche Daten | Gesundheitsüberwachungsdaten, Ausgabenaufzeichnungen, App-Nutzungsgewohnheiten, Standortverlauf |
| **Knowledge Base** | Organisierte Wissenssysteme | Professionelle Fachnotizen, Lernmaterialbibliotheken, Arbeitserfahrungszusammenfassungen, Branchenforschungsberichte |
| **Info Feed** | Echtzeit-Informationsabonnements | Verfolgte Nachrichtenquellen, Branchen-Update-Feeds, Social-Media-Updates, Aktienkurse |

Die Daten in der Denken-Dimension stammen aus der Initialisierung und kontinuierlichen Akkumulation des Persönlichen Datenspeichers und bilden die Grundlage dafür, dass iFay die Welt versteht und Urteile fällt.

---

## Faying-Skills

Faying-Skills sind iFays Handlungsfähigkeiten, die sechs Skill-Typen enthalten:

| Typ | Beschreibung |
|-----|-------------|
| **API** | Direkt aufrufbare Programmierschnittstellen, wie Wetterabfrage-API, Übersetzungs-API |
| **Workflow** | Mehrstufige automatisierte Prozesse, wie „jeden Montag Wochenbericht generieren und an Team senden" |
| **Bot** | Konversationsbots für bestimmte Szenarien, wie Kundenservice-Bot, Termin-Bot |
| **Agent** | Intelligente Agenten mit autonomer Entscheidungsfindung, wie Investitionsanalyse-Agent |
| **APP** | Vollständige Anwendungen, wie Kalenderverwaltungs-APP, Gesundheitstracking-APP |
| **Microservice** | Unabhängig bereitgestellte Diensteinheiten, wie Bilderkennungsdienst, Sprache-zu-Text-Dienst |

Skill-Registrierung ist eine Voraussetzung dafür, dass iFay jede Aktion ausführen kann. Registrierte Skills schließen die Vorautorisierung ab und stellen sicher, dass während der Ausführung keine zusätzliche Authentifizierung benötigt wird.

---

## Faying-Hardware

Hardware ist iFays „Gliedmaßen". iFay ist eine Persönlichkeits- und Kognitionsentität; Hardware ist ihr Vehikel für die Interaktion mit der physischen Welt.

### Drei Hardware-Untertypen

| Untertyp | Beschreibung | Beispiele |
|----------|-------------|----------|
| **Device** | Endgerät-Hardware | Handy, Computer, Smartwatch, Drohne, Smart-Home-Geräte |
| **Storage** | Datenspeicherressourcen | Cloud-Speicher, lokale Festplatte, NAS, Vektordatenbank |
| **Computing** | Rechenressourcen | GPU, Cloud-Computing-Knoten, Edge-Computing-Geräte |

### Hardware-Erkennungsmechanismus

Wenn iFay in eine neue Umgebung migriert, ist das Endgerät dafür verantwortlich, Faying-fähige Hardware in der aktuellen Umgebung zu scannen — ähnlich wie Bluetooth oder WiFi nach Geräten in der Nähe scannt. iFay selbst führt kein Hardware-Scanning durch; stattdessen führt es Fähigkeitsabgleich basierend auf Scan-Ergebnissen durch.

Es gibt hier eine wichtige Unterscheidung:

- **Welche Hardware iFay bedienen kann** hängt von ihren kognitiven Fähigkeiten ab (Registrierte Skills, Interne Skills)
- **Mit welcher Hardware iFay sich verbinden kann** hängt von den tatsächlich in der aktuellen Umgebung verfügbaren Geräten ab

### Szenario

> Stell dir eine Person vor, die Badminton spielen kann und eine Sporthalle betritt.
>
> „Badminton spielen können" ist ihr **Skill** — es ist ihre eigene Fähigkeit, die sie überallhin mitnimmt. Aber ob sie tatsächlich spielen kann, hängt davon ab, ob die Halle **Schläger** hat — das ist die von der Umgebung bereitgestellte Hardware.
>
> iFay funktioniert genauso. Sie könnte den Skill haben, eine Drohne zu steuern (eine Flugsteuerungs-API registriert), aber wenn es keine verbindbare Drohne in der aktuellen Umgebung gibt, kann dieser Skill nicht ausgeübt werden. Umgekehrt, selbst wenn ein 3D-Drucker in der Umgebung vorhanden ist, kann iFay, wenn sie den relevanten Bedienungs-Skill nicht registriert hat, das Gerät nur „sehen", aber nicht verwenden.

---

## Faying-Berechtigungen

Berechtigungen sind iFays „Beziehungen" — sie definieren die Vertrauensgrenzen zwischen iFay und der Außenwelt.

### Drei Berechtigungslebenszyklen

| Lebenszyklus | Beschreibung | Beispiele |
|-------------|-------------|----------|
| **Inhärent** | Berechtigungen, die von der Erstellung an besessen werden | Zugriff auf den Kalender des Human Prime, Lesen der Präferenzeinstellungen des Prime |
| **Persistent** | Langfristig gültige Berechtigungen | Lese-/Schreibzugriff auf die E-Mail des Prime, Zugang zum Unternehmensintranet |
| **Ephemer** | Bei Bedarf beantragt, nach Gebrauch freigegeben | Einmaliger Zugriff auf Krankenakten, temporäre API-Aufrufrechte |

### Erweiterbare Authentifizierungsmethoden

iFays Authentifizierungsmethoden sind erweiterbar und unterstützen SSO, OAuth, Fingerprint und andere Methoden. „Fingerprint" ist hier ein Sammelbegriff, der jeden identitätserkennbaren Bezeichner abdeckt — Gesichtserkennung, Stimmabdruck, Geräte-Fingerprint usw. Verschiedene Fingerprint-Typen haben unterschiedliche Konfidenzniveaus: Gesichtserkennung kann höhere Konfidenz haben als Geräte-Fingerprint, während Multi-Faktor-Kombinationen höhere Konfidenz haben als einzelne Faktoren.

### Szenario

> Wang Fangs iFay hat drei Berechtigungen mit unterschiedlichen Lebenszyklen:
>
> **Inhärent**: Als iFay erstellt wurde, erhielt sie automatisch Zugriff auf Wang Fangs Kalender — dies ist eine Grundfähigkeit jeder iFay, die keine zusätzliche Beantragung erfordert.
>
> **Persistent**: Wang Fang autorisierte iFay, ihre Arbeits-E-Mail langfristig zu verwalten. iFay kann E-Mails lesen, Antworten entwerfen und Labels verwalten — diese Berechtigung bleibt gültig, bis Wang Fang sie aktiv widerruft.
>
> **Ephemer**: Wang Fang muss den Gesundheitsbericht vom letzten Jahr einsehen. Sie bittet iFay, Aufzeichnungen aus dem Krankenhaussystem abzurufen. iFay beantragt vorübergehend eine einmalige Zugriffsberechtigung für medizinische Daten, und nach Erhalt des Berichts wird die Berechtigung automatisch freigegeben — beim nächsten Mal ist eine neue Beantragung erforderlich.

---

## Profil-Sichtbarkeit

Profil-Sichtbarkeit ist eine Anwendungsschicht-Angelegenheit, bestimmt durch spezifische Anwendungsszenarien und Interaktionsmethoden.

Dasselbe iFay-Profil zeigt in verschiedenen Szenarien unterschiedliche Dimensionen: Bei der Inter-Fay-Zusammenarbeit muss die andere Partei möglicherweise nur die Skills- und Berechtigungsdimensionen sehen; in der Human-Prime-Verwaltungsoberfläche sind alle sechs Dimensionen vollständig sichtbar; in öffentlichen sozialen Szenarien werden möglicherweise nur Identitäts- und teilweise Skill-Informationen angezeigt.

Das Profil selbst definiert nicht „wer was sehen kann" — diese Entscheidung wird der Anwendung überlassen, die das Profil verwendet.
