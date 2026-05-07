# 2. SEP-Richtlinien

## Was ist ein SEP

Ein SEP (Specification Enhancement Proposal) ist der formale Vorschlagsprozess für Änderungen an der iFay-Spezifikation. Jede wesentliche Änderung der iFay-Spezifikation — sei es das Hinzufügen eines neuen Moduls, die Änderung des Protokollverhaltens oder die Anpassung des iFay-Profile-Datenmodells — sollte den SEP-Prozess durchlaufen.

## Warum SEPs benötigt werden

iFay ist ein offenes Standardökosystem mit Multi-Vendor-Implementierungen, und jede Änderung der Spezifikation kann potenziell alle Implementierer betreffen. Der SEP-Prozess stellt sicher, dass die Weiterentwicklung der Spezifikation geordnet, transparent und nachvollziehbar erfolgt und allen Beteiligten die Möglichkeit gibt, an der Diskussion und Überprüfung teilzunehmen.

## SEP-Lebenszyklus

Ein SEP durchläuft vom Vorschlag bis zur endgültigen Umsetzung die folgenden Phasen:

### 1. Draft (Entwurf)

Der Vorschlagende erstellt ein SEP-Issue auf GitHub unter Verwendung der Standardvorlage und beschreibt die Motivation, die vorgeschlagene Lösung und die Auswirkungen. Ein SEP in der Draft-Phase kann unvollständig sein, sollte aber genügend Informationen enthalten, damit die Community die Absicht des Vorschlags verstehen kann.

### 2. Discussion (Diskussion)

Das SEP tritt in eine öffentliche Diskussionsphase ein, die mindestens **14 Tage** dauert. Während dieser Phase:

- Diskutieren Community-Mitglieder und relevante Arbeitsgruppen den Vorschlag
- Überarbeitet und verfeinert der Vorschlagende den Vorschlag basierend auf dem Feedback
- Bewerten Maintainer der betroffenen Teilprojekte die Auswirkungen auf ihre jeweiligen Bereiche

### 3. Review (Überprüfung)

Nach Ablauf der Diskussionsphase führen die Core Maintainer eine formale Überprüfung des SEP durch. Während der Überprüfung kann der Vorschlagende aufgefordert werden, weitere Überarbeitungen oder Ergänzungen vorzunehmen, wie zum Beispiel:

- Hinzufügen einer Abwärtskompatibilitätsanalyse
- Vervollständigung einer iFACTS-Testauswirkungsbewertung
- Bereitstellung einer vergleichenden Analyse alternativer Ansätze

### 4. Accepted / Rejected (Angenommen / Abgelehnt)

Die Core Maintainer entscheiden durch Abstimmung über das endgültige Ergebnis des SEP:

- **Accepted (Angenommen)**: Das SEP wird genehmigt und geht in die Umsetzungsphase über
- **Rejected (Abgelehnt)**: Das SEP wird abgelehnt, die Gründe werden dokumentiert. Der Vorschlagende kann den Vorschlag basierend auf dem Feedback überarbeiten und erneut einreichen

### 5. Implemented (Umgesetzt)

Ein angenommenes SEP tritt in die Umsetzungsphase ein. Die Umsetzungsarbeit kann vom Vorschlagenden oder anderen Mitwirkenden durchgeführt werden. Während der Umsetzung:

- Sollten die zugehörigen Spezifikationsdokumente aktualisiert werden
- Sollte Referenzcode implementiert werden (falls zutreffend)
- Sollten iFACTS-Testfälle geschrieben oder aktualisiert werden

### 6. Final (Endgültig)

Nach Abschluss der Umsetzung und bestandener Überprüfung erreicht das SEP seinen endgültigen Status. Zu diesem Zeitpunkt:

- Sind die Spezifikationsdokumente aktualisiert
- Ist die iFACTS-Testsuite entsprechend aktualisiert
- Sind die zugehörige Dokumentation und Anleitungen aktualisiert

## SEP-Vorlage

Bitte fügen Sie bei der Einreichung eines SEP die folgenden Informationen bei:

- **Titel**: Eine prägnante Beschreibung des Vorschlags
- **Motivation**: Warum ist diese Änderung erforderlich? Welches Problem wird gelöst?
- **Detailliertes Design**: Technische Details und Umsetzungsplan des Vorschlags
- **Abwärtskompatibilität**: Analyse der Auswirkungen auf bestehende Spezifikationen und Implementierungen
- **iFACTS-Auswirkungen**: Welche Konformitätstests müssen hinzugefügt oder geändert werden
- **Alternativen**: Andere in Betracht gezogene Ansätze und deren vergleichende Vor- und Nachteile

## Wer kann ein SEP einreichen

Jeder kann ein SEP einreichen. Ob Sie Core Maintainer, Maintainer, Mitwirkender oder Nutzer des iFay-Ökosystems sind — wenn Sie der Meinung sind, dass die Spezifikation verbessert werden muss, sind Sie herzlich eingeladen, einen Vorschlag einzureichen.

## Besondere Hinweise

SEPs, die Protokolländerungen betreffen, erfordern besondere Aufmerksamkeit: Da jedes iFay-Protokoll (Faying, Telepathy, ICP, CAP, DTP, SSP) einem unabhängigen Teilprojekt entspricht, müssen die Maintainer der betroffenen Protokolle an der Überprüfung teilnehmen. Beispielsweise erfordert ein SEP, das das Verhalten des Control Authority Protocol (CAP) ändert, dass die Maintainer der WG-Protocols-Arbeitsgruppe die Auswirkungen auf verwandte Module wie den Device Driver Hub und die FayGer-Laufzeitumgebung bewerten.
